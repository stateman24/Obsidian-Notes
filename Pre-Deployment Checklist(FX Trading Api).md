## ✅ **Pre-Deployment Checklist**

1. **Environment Configuration**
    
    - Set up `.env.production` file with secure values (DB, JWT, mail, etc.).
        
    - Ensure no sensitive data is hardcoded.
        
    - Set up `ConfigModule` to load proper env file based on `NODE_ENV`.
        
2. **Database Setup**
    
    - Ensure your database schema is migrated (via TypeORM migrations).
        
    - Seed necessary initial data (e.g., default wallets, roles if needed).
        
    - Use `UUID` primary keys and verify indexes for performance.
        
3. **Security Enhancements**
    
    - Enable CORS and Helmet.
        
    - Rate limiting (e.g., with `@nestjs/throttler`).
        
    - Validate and sanitize inputs (`class-validator` / `class-transformer`).
        
    - Secure JWT secrets and mail credentials.
        
4. **Testing**
    
    - Confirm all **end-to-end tests** pass.
        
    - Run basic **unit tests** on critical modules (auth, wallet, transactions).
        
    - Test with Postman for manual confirmation.