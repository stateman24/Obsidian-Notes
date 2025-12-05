#ziPayProject 

## Tasks 
- Getting Fx rate from Currnecy Layer 
- How to correctly parse the data to the database 
- Create a Cron job update the database with latest Fx rates

### Getting FX rate from Currency Layer 
Currencies supported now 
- NGN 
- GBP 
- USD 
- CAD
- RAD
- KES
- GHS 
So each currency will be a base currency to all other currencies e.g 

| Base Currency | Quote Currencies             |
| ------------- | ---------------------------- |
| NGN           | GBP, USD, CAD, RAD, KES, GHS |
| GBP           | NGN, USD, CAD, RAD, KES, GHS |
From the DB POV
- 1 base currency will have 6 quotes currencies 
-  That mean we have For NGN  as base currency, it will have 6 fx rates to 6 quotes currencies 
- So there will be 42 fx_rate rows 


So I will get all the quote currencies for each base currencies and save to the DB 
**Reason For this approach**
1. For accurate Fx rate for currency conversion
2. I want the sender currency to a the base currency on lookup so as to get the actual fx rate to the quote rate i.e sender currency - NGN and receiver currency - USD, NGN is the base currency and fx rate will be NGNUSD maybe 0.34USD as the rate 

**Algorithm to get the fx rate from currency Layer**
There will be for major steps 
- [x] Get the currencies for the db 
```typescript
private async getCurrenciesCode() {  
  const currencies = await this.currencyRepo.find();  
  const currencyCodes = currencies.map((currency) => currency.code);  
  const baseQuoteCurrency: Record<string, string> = {};  
  for (const code of currencyCodes) {  
    const otherCodes = currencyCodes.filter((otherCode) => otherCode != code);  
    baseQuoteCurrency[code] = otherCodes.join(',');  
  }  
  return baseQuoteCurrency;  
}
```
- [x] Call the api and get the quotes for each base currency 
```typescript 
async getLiveRate(baseQuote: Record<string, string>) {  
  this.BASE_URL = `https://api.currencylayer.com/live`;  
  const liveRates: Record<string, Record<string, number>> = {};  
  for (const base in baseQuote) {  
    const quotes = baseQuote[base];  
    const params = {  
      access_key: this.API_KEY,  
      source: base,  
      currencies: quotes,  
      format: 1,  
    };  
    try {  
      const response = await firstValueFrom(  
        this.httpService.get<CurrrencyLayerApiResponse>(this.BASE_URL, {  
          params,  
        }),  
      );  
      if (response.data.success) {  
        liveRates[base] = response.data.quotes;  
      } else {  
        console.error(  
          `Error fetching rates for base ${response.data.error?.info}`,  
        );  
      }  
    } catch (error) {  
      console.error(`HTTP error fetching rates for base ${base}:`, error);  
    }  
  }  
  return liveRates;  
}
```
- [x]  process the data and save to db
```typescript
async syncRatesToDb(): Promise<void> {  
  try {  
    const baseQuoteMap = await this.getCurrenciesCode();  
    const liveRates =  
      await this.currencyLayerService.getLiveRate(baseQuoteMap);  
  
    const ratesToUpsert: Partial<FX_Rate>[] = [];  
  
    for (const base in liveRates) {  
      const quotes = liveRates[base];  
  
      for (const [pair, rate] of Object.entries(quotes)) {  
        const baseCode = this.toCurrencyCode(pair.slice(0, 3));  
        const quoteCode = this.toCurrencyCode(pair.slice(3));  
  
        const baseCurrency = await this.currencyRepo.findOne({  
          where: { code: baseCode },  
          select: ['id', 'code'],  
        });  
        const quoteCurrency = await this.currencyRepo.findOne({  
          where: { code: quoteCode },  
          select: ['id', 'code'],  
        });  
  
        if (!baseCurrency || !quoteCurrency) {  
          console.warn(`Skipping unknown currency pair ${pair}`);  
          continue;  
        }  
  
        ratesToUpsert.push({  
          base_currency: { id: baseCurrency.id, code: baseCode } as Currency,  
          quote_currency: {  
            id: quoteCurrency.id,  
            code: quoteCode,  
          } as Currency,  
          rate: Number(rate),  
          provider: 'CurrencyLayer',  
        });  
      }
```
- [x]  Create an cron job / updater function that fetches the data from time to time and update the db
```typescript
export class FxUpdateService {  
  private readonly logger = new Logger(FxUpdateService.name);  
  
  constructor(private readonly fxService: FxService) {}  
  
  @Cron(CronExpression.EVERY_DAY_AT_9AM)  
  async handleCron() {  
    this.logger.log('⏳ Running scheduled FX rate sync...');  
    try {  
      await this.fxService.syncRatesToDb();  
      this.logger.log('✅ FX rates updated successfully');  
    } catch (error) {  
      this.logger.error('❌ Failed to update FX rates', error);  
    }  
  }  
}
```


