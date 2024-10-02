# GranularX API Documentation

Welcome to the API documentation for GranularX. This documentation covers the various services provided by GranularX, including user authentication, transactions, mailbox management, wallet top-ups, and in-chat payments.

## Base URLs
- **UMS (User Management System)**: `https://ums.granularx.com`
- **Wallet**: `https://api.granularx.com/wallet`
- **Fiaton Service**: `https://api.granularx.com/fiatons`
- **Chat**: `https://api.granularx.com/chat`
- **Authentication**: `https://api.granularx.com/auth`

---

## User Management System (UMS)

### **/auth/signin**

- **Method**: `POST`
- **Description**: Signs a user into their account.
- **Query Parameters**: 
  - `platform=web` or `platform=mobile`
  
- **Request Body**:
    ```json
    {
        "username": "<string>",
        "password": "<string>"
    }
    ```

- **Response**:
    ```json
    {
        "status": "success",
        "error": "",
        "data": "User successfully logged in"
    }
    ```
- **Status Code**: `200 OK`

---

### **/auth/signup**

- **Method**: `POST`
- **Description**: Signs up a new user.
  
- **Request Body**:
    ```json
    {
        "username": "<string>",
        "phone_number": "<string>",
        "password": "<string>"
    }
    ```

- **Response**:
    ```json
    {
        "status": "success",
        "error": "",
        "data": "User successfully created"
    }
    ```
- **Status Code**: `201 Created`

---

## Transactions

### **/transactions/outbound-transfer**

- **Method**: `POST`
- **Description**: Creates a transaction based on type for submission and approval on the blockchain.
  
- **Optional Query Parameter**:
  - `type=<transaction_type>`

- **Supported Transaction Types**: 
  - `peer`, `ref`, `root`, `re-root`, `glf`, `gxg`

- **Supported Currency Types**: 
  - `"USD"`, `"EUR"`, `"GBP"`, `"NGN"`, `"AED"`, `"AFN"`, `"ALL"`, `"ANG"`, `"AOA"`, `"ARS"`, `"AUD"`, `"BRL"`, `"CAD"`, and more.
  
- **Request Body**:
    ```json
    {
        "amount": 0.0,
        "receiver_id": "<string>",
        "base_currency": "<string>",
        "converted_currency": "<string>",
        "is_mitd": true,
        "pin": "<string>",
        "transaction_type": "<string>"
    }
    ```

- **Success Response**:
    ```json
    {
        "status": "success",
        "error": "",
        "data": "Transaction approved"
    }
    ```

- **Failure Response**:
    ```json
    {
        "status": "failed",
        "error": "Transaction failed due to server error or bad request",
        "data": "Transaction declined or failed"
    }
    ```
- **Status Codes**: `200 OK`, `500 Internal Server Error`, `404 Not Found`, `403 Forbidden`, `401 Unauthorized`

---

## Mailbox Management

### **/mailbox/create**

- **Method**: `POST`
- **Description**: Creates a new mailbox.

- **Request Body**:
    ```json
    {
        "owner_id": "<string>",
        "pin": "<string>"
    }
    ```

- **Response**:
    ```json
    {
        "status": "success",
        "error": "",
        "data": "Mailbox successfully created"
    }
    ```

- **Status Code**: `201 Created`

---

### **/mailbox/login**

- **Method**: `POST`
- **Description**: Logs in to a mailbox.

- **Request Body**:
    ```json
    {
        "owner_id": "<string>",
        "pin": "<string>"
    }
    ```

- **Response**:
    ```json
    {
        "status": "success",
        "error": "",
        "data": "Mailbox login successful"
    }
    ```
- **Status Code**: `200 OK`

---

## Wallet Top-up

### **/wallet/topup**

- **Method**: `POST`
- **Description**: Top up a wallet via external PSSP.

- **Request Body**:
    ```json
    {
        "amount": 1000,
        "email": "<string>",
        "uns": "<string>",
        "base_currency": "NGN",
        "transaction_type": "base",
        "pin": 1234
    }
    ```

- **Success Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": {
            "access_code": "eku5qwtqq496nja",
            "auth_url": "https://checkout.paystack.com/eku5qwtqq496nja",
            "reference": "2bb52u5ayo"
        }
    }
    ```

- **Status Code**: `200 OK`

### **/wallet/topup/verify/{reference}**

- **Method**: `GET`
- **Description**: Verifies if the top-up action was successful.

- **Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": {
            "reference": "<string>",
            "amount": 1000,
            "currency": "NGN",
            "gateway_response": "Successful"
        }
    }
    ```

- **Status Code**: `200 OK`

---

## In-Chat Payments

### **/fiatons/send/peer**

- **Method**: `POST`
- **Description**: Sends fiatons to a peer in chat.

- **Request Body**:
    ```json
    {
        "sender_wallet_id": "<string>",
        "receiver_wallet_id": "<string>",
        "amount": 100
    }
    ```

- **Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": "Transaction successful"
    }
    ```

- **Status Code**: `200 OK`

---

## Chat API

### **/chat/create**

- **Method**: `POST`
- **Description**: Creates a new chat session.

- **Request Body**:
    ```json
    {
        "p_1": "<string>",
        "p_2": "<string>"
    }
    ```

- **Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": "Chat session created successfully"
    }
    ```

- **Status Code**: `201 Created`

---

### **/chat/friends**

- **Method**: `POST`
- **Description**: Retrieves all friends of a user.

- **Request Body**:
    ```json
    {
        "uns": "<string>"
    }
    ```

- **Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": []
    }
    ```

- **Status Code**: `200 OK`

---

# GranularX API Documentation - Verse Endpoints

This section of the API documentation outlines the endpoints related to **Verses**, including content, product, and service management within a verse.

---

## Base URL

- **Verse API**: `https://api.granularx.com/verse`

### **Create a Verse**

- **Endpoint**: `/verse/create`
- **Method**: `POST`
- **Description**: Creates a new verse.
- **Request Body**:
    ```json
    {
        "uns": "<string>",
        "cta_title": "<string>",
        "header_banner_url": "<string>",
        "header_title": "<string>",
        "header_description": "<string>",
        "sector": "<string>",
        "type": "<string>"
    }
    ```
- **Success Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": "<verse_id>"
    }
    ```
- **Status Code**: `200 OK`

---

### **Get a Verse**

- **Endpoint**: `/verse/:uns`
- **Method**: `GET`
- **Description**: Retrieves the details of a verse by its UNS (Unique Name Space).
- **Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": {
            "id": "<string>",
            "uns": "<string>",
            "verse_header": {
                "cta_title": "<string>",
                "header_banner_url": "<string>",
                "header_title": "<string>",
                "header_description": "<string>"
            },
            "type": "<string>",
            "verse_products": [...],
            "verse_services": [...],
            "verse_content": [...],
            "has_softservant": true,
            "has_mailbox": true,
            "sector": "<string>"
        }
    }
    ```
- **Status Code**: `200 OK`

---

### **Delete a Verse**

- **Endpoint**: `/verse/:uns`
- **Method**: `DELETE`
- **Description**: Deletes a verse by its UNS.
- **Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": "Verse deleted successfully"
    }
    ```
- **Status Code**: `200 OK`

---

## Content Management

### **Add Content to Verse**

- **Endpoint**: `/verse/contents/add/:verse_id`
- **Method**: `POST`
- **Description**: Adds new content to a verse.
- **Request Body**:
    ```json
    {
        "title": "<string>",
        "description": "<string>",
        "price": "<float>"
    }
    ```
- **Success Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": "successfully added content to verse"
    }
    ```
- **Status Code**: `200 OK`

---

### **Get Content by ID**

- **Endpoint**: `/verse/contents/:verse_id/:content_id`
- **Method**: `GET`
- **Description**: Retrieves content by its ID within a specific verse.
- **Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": { ... } // Content details
    }
    ```
- **Status Code**: `200 OK`

---

### **Update Content**

- **Endpoint**: `/verse/contents/:verse_id`
- **Method**: `PUT`
- **Description**: Updates content within a verse by its ID.
- **Request Body**:
    ```json
    {
        "id": "<string>",
        "title": "<string>",
        "description": "<string>",
        "price": "<float>"
    }
    ```
- **Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": "Content updated successfully"
    }
    ```
- **Status Code**: `200 OK`

---

### **Delete Content**

- **Endpoint**: `/verse/contents/:verse_id/:content_id`
- **Method**: `DELETE`
- **Description**: Deletes content from a verse by its ID.
- **Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": "Content deleted successfully"
    }
    ```
- **Status Code**: `200 OK`

---

## Product Management

### **Add Product to Verse**

- **Endpoint**: `/verse/products/add/:verse_id`
- **Method**: `POST`
- **Description**: Adds a new product to a verse.
- **Request Body**:
    ```json
    {
        "title": "<string>",
        "description": "<string>",
        "price": "<float>",
        "quantity": "<int>"
    }
    ```
- **Success Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": "successfully added product to verse"
    }
    ```
- **Status Code**: `200 OK`

---

### **Get Product by ID**

- **Endpoint**: `/verse/products/:verse_id/:product_id`
- **Method**: `GET`
- **Description**: Retrieves a product by its ID within a specific verse.
- **Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": { ... } // Product details
    }
    ```
- **Status Code**: `200 OK`

---

### **Update Product**

- **Endpoint**: `/verse/products/:verse_id`
- **Method**: `PUT`
- **Description**: Updates a product within a verse by its ID.
- **Request Body**:
    ```json
    {
        "id": "<string>",
        "title": "<string>",
        "description": "<string>",
        "price": "<float>",
        "quantity": "<int>"
    }
    ```
- **Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": "Product updated successfully"
    }
    ```
- **Status Code**: `200 OK`

---

### **Delete Product**

- **Endpoint**: `/verse/products/:verse_id/:product_id`
- **Method**: `DELETE`
- **Description**: Deletes a product from a verse by its ID.
- **Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": "Product deleted successfully"
    }
    ```
- **Status Code**: `200 OK`

---

## Service Management

### **Add Service to Verse**

- **Endpoint**: `/verse/services/add/:verse_id`
- **Method**: `POST`
- **Description**: Adds a new service to a verse.
- **Request Body**:
    ```json
    {
        "title": "<string>",
        "description": "<string>",
        "price": "<float>"
    }
    ```
- **Success Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": "successfully added service to verse"
    }
    ```
- **Status Code**: `200 OK`

---

### **Get Service by ID**

- **Endpoint**: `/verse/services/:verse_id/:service_id`
- **Method**: `GET`
- **Description**: Retrieves a service by its ID within a specific verse.
- **Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": { ... } // Service details
    }
    ```
- **Status Code**: `200 OK`

---

### **Update Service**

- **Endpoint**: `/verse/services/:verse_id`
- **Method**: `PUT`
- **Description**: Updates a service within a verse by its ID.
- **Request Body**:
    ```json
    {
        "id": "<string>",
        "title": "<string>",
        "description": "<string>",
        "price": "<float>"
    }
    ```
- **Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": "Service updated successfully"
    }
    ```
- **Status Code**: `200 OK`

---

### **Delete Service**

- **Endpoint**: `/verse/services/:verse_id/:service_id`
- **Method**: `DELETE`
- **Description**: Deletes a service from a verse by its ID.
- **Response**:
    ```json
    {
        "status": "SUCCESS",
        "error": "",
        "data": "Service deleted successfully"
    }
    ```
- **Status Code**: `200 OK`


