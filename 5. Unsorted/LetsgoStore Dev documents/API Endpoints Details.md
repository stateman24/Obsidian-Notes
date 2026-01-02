Here’s the **complete API endpoints** for LetshgoStore, including the **Interswitch payment integration**, structured like a professional API contract (OpenAPI/Swagger-style):

---

### **1. Authentication & User Service**
| Endpoint             | Method | Description            | Request                                         | Response                              |
| -------------------- | ------ | ---------------------- | ----------------------------------------------- | ------------------------------------- |
| `/api/auth/register` | POST   | Register new user      | `{ email, password, name }`                     | `{ id, email, name }`                 |
| `/api/auth/login`    | POST   | Login (email/Google)   | `{ email, password }` or `{ googleToken }`      | `{ jwtToken }`                        |
| `/api/users/me`      | GET    | Get user profile       | -                                               | `{ id, email, name, billingAddress }` |
| `/api/users/me`      | PUT    | Update profile/address | `{ billingAddress: { street, city, country } }` | `{ message }`                         |

---

### **2. Product Service**
| Endpoint               | Method | Description     | Parameters                     | Response                                         |
| ---------------------- | ------ | --------------- | ------------------------------ | ------------------------------------------------ |
| `/api/products`        | GET    | List products   | `?category=Electronics&page=1` | `{ products: [ { id, name, price } ] }`          |
| `/api/products/search` | GET    | Search products | `?q=earbuds`                   | Same as above                                    |
| `/api/products/{id}`   | GET    | Product details | -                              | `{ id, name, description, images[], reviews[] }` |

---

### **3. Cart Service**
| Endpoint | Method | Description | Request | Response |
|----------|--------|-------------|---------|----------|
| `/api/cart/items` | POST | Add to cart | `{ productId, quantity }` | `{ grandTotal, tax, shipping }` |
| `/api/cart` | GET | View cart | - | `{ items: [ { productId, name, quantity } ], grandTotal }` |
| `/api/cart/items/{productId}` | DELETE | Remove item | - | Updated cart |

---

### **4. Order & Payment Service**  
#### **Order Management**
| Endpoint | Method | Description | Request | Response |
|----------|--------|-------------|---------|----------|
| `/api/orders` | POST | Create order (checkout) | `{ shippingAddressId }` | `{ orderId, status: "PENDING_PAYMENT" }` |
| `/api/orders` | GET | Order history | - | `{ orders: [ { id, date, total, status } ] }` |
| `/api/orders/{orderId}` | GET | Order details | - | `{ id, items[], status, trackingUrl }` |

#### **Interswitch Payment Integration**  
| Endpoint | Method | Description | Request | Response |
|----------|--------|-------------|---------|----------|
| `/api/payments/initiate` | POST | Initiate payment | `{ orderId, card: { number, expiry, cvv } }` | `{ paymentUrl, transactionId }` |
| `/api/payments/callback` | POST | Interswitch webhook | Interswitch payload | (ACK) |
| `/api/payments/verify/{transactionId}` | GET | Verify payment | - | `{ status: "SUCCESS"\|"FAILED" }` |

---

### **Key Payment Workflow**
1. **Frontend** → Calls `/api/orders` to create an order (status: `PENDING_PAYMENT`).  
2. **Frontend** → Calls `/api/payments/initiate` with card details.  
   - *Backend generates Interswitch token and returns `paymentUrl`*.  
3. **User** → Redirected to `paymentUrl` to complete payment.  
4. **Interswitch** → Sends callback to `/api/payments/callback`.  
   - *Backend updates order to `PAID`*.  
5. **Frontend** → Polls `/api/orders/{orderId}` for status.  

---

### **Example Payment API Requests**
#### **Initiate Payment**
```http
POST /api/payments/initiate
Headers:
  Authorization: Bearer <user-jwt>
Body:
{
  "orderId": "ord_123",
  "card": {
    "number": "5061 0666 6666 6666",
    "expiry": "12/25",
    "cvv": "123"
  }
}
Response:
{
  "paymentUrl": "https://sandbox.interswitch.com/pay?token=xyz",
  "transactionId": "txn_123"
}
```

#### **Payment Callback (Web-hook)**
```http
POST /api/payments/callback
Body (Interswitch):
{
  "transactionId": "txn_123",
  "status": "SUCCESS",
  "amount": 10000
}
```

---

### **Security Practices**
1. **PCI Compliance**:  
   - Use **Interswitch.js** on front-end to avoid handling raw card data.  
   - If backend processes cards, ensure **PCI-DSS Level 4** compliance.  
2. **Idempotency**:  
   - Add `Idempotency-Key` header to `/api/payments/initiate` to prevent duplicate charges.  
3. **Webhook Validation**:  
   - Verify signatures from Inter-switch.  
