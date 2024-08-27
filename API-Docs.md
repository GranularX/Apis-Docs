# Apis-Docs
documentation for service APIs


# ums
Source for User Management System
# base uril for UMS - https://ums.granularx.com


## /auth/signin

- **Method:** POST 
- **Description:** Used for sigining in a user into their account
- **Query String:** platform=web or platform=mobile
- **JSON Request Format/Params:**
    ```json
    {
        "username":"",
        "password": ""
    }
    ```
- **JSON Response:**
    ```json
    {
        "status":"success",
        "error":"",
        "data":"user successfully logged in"
    }
    ```
- **Status Code: 200**

## /auth/signup

- **Method:** POST 
- **Description:** Used for signing up a user into a new account
- **JSON Request Format/Params:**
    ```json
    {
        "username":"",
        "phone_number":"",
        "password": ""
    }
    ```
- **JSON Response:**
    ```json
    {
        "status":"success",
        "error":"",
        "data":"user successfully created"
    }
    ```
- **Status Code: 201**

## /transactions/outbound-transfer

- **Method:** POST 
- **Description:** Used for creating transaction based on type, for submission and approval on the blockchain
- **Query Parameters:** ?type= (optional)
- **Supported Transaction Types**: ["peer","ref","root","re-root","glf","gxg"] 
- **Supported Currency Types**: ["AED", "AFN", "ALL", "ANG", "AOA", "ARS", "AUD", "AWG", "AZN", "BAM",
	"BBD", "BDT", "BGN", "BHD", "BIF", "BMD", "BOB", "BRL", "BSD", "BTN",
	"BWP", "BYN", "BZD", "CAD", "CDF", "CHF", "CLP", "CNY", "COP", "CRC",
	"CVE", "CYP", "CZK", "DJF", "DKK", "DOP", "EGP", "ERN", "ETB", "EUR",
	"FJD", "FKP", "GBP", "GEL", "GHS", "GIP", "GMD", "GNF", "GTQ", "GYD",
	"HKD", "HNL", "HRK", "HTG", "HUF", "IDR", "ILS", "IMP", "INR", "IQD",
	"IRR", "ISK", "JEP", "JMD", "JOD", "JPY", "KES", "KGS", "KHR", "KMF",
	"KPW", "KRW", "KWD", "KYD", "LAK", "LBP", "LRD", "LYD", "MAD", "MDL",
	"MGA", "MKD", "MMK", "MNT", "MOP", "MRU", "MUR", "MVR", "MWK", "MXN",
	"MYR", "NAD", "NGN", "NIO", "NOK", "NPR", "NZD", "OMR", "PAB", "PEN",
	"PGK", "PHP", "PKR", "PLN", "PYG", "QAR", "RON", "RUB", "RWF", "SAR",]
- **JSON Request Format/Params:**
    ```json
    {
       "amount<Float64>":0.0,
       "receiver_id<String>":"",
       "base_currency<String>":"",
       "converted_currency<String>":"",
       "is_mitd<Bool>":true,
       "pin<String>":"",
       "transaction_type<String>":""
    }
    ```
- **JSON Response (success):**
    ```json
    {
        "status":"success",
        "error":"",
        "data":"transaction approved"
    }
    ```
- **Status Code: 200**

- **JSON Response (failed):**
    ```json
    {
        "status":"failed",
        "error":"transaction failed due to server error, bad request, or is unauthorized",
        "data":"transaction declined or failed"
    }
    ```
- **Status Code: 500/404/403/401**

<!-- ## /signout

- **Method:** GET 
- **Description:** Used for signing out of account
- **JSON Request Format/Params:**
    ```json
    {
     Not implemented yet
    }
    ```


## /mailbox

- **Method:** PUT
- **Description:** Used for updating a mailbox with new message
- **JSON Request Format/Params:**
    ```json
    {
        "owner_id":"",
        "mail_id":"",
        "message_header":"",
        "message_body":"",
        "message_type":""
    }
    ```
## /message

- **Method:** POST
- **Description:** Used for creating a new message
- **JSON Request Format/Params:**
    ```json
    {
        "owner_id": "",
        "mail_id": "",
        "message_header":"",
        "message_body":"",
        "message_type":""
    }
    ```

## /events?stream=<user_id>

- **Method:** GET
- **Description:** Used for creating a stream for events notification per client
- **JSON Request Format/Params:**
    ```

    ```

## /trigger/:id

- **Method:** GET
- **Description:** Used to trigger a notification on a client stream
- **JSON Request Format/Params:**
    ```
    ```

TODO: Add Service passwords to endpoints that are not accessible to clients but other services  -->


# Mailbox End
Backend for Mailbox, <baseUrl = bmailbox.granularx.com>


## /create

- **Method:** POST 
- **Description:** Used for creating a new mailbox
- **JSON Request Format/Params:**
    ```json
    {
        "owner_id":"",
        "pin": ""
    }
    ```


## /login

- **Method:** POST 
- **Description:** Used for logging in to a new mailbox
- **JSON Request Format/Params:**
    ```json
    {
        "owner_id":"",
        "pin": ""
    }
    ```

## /mailbox

- **Method:** GET 
- **Description:** Used for getting a mailbox
- **JSON Request Format/Params:**
    ```json
    {
        "owner_id":"",
        "mail_id":"",
        "pin": ""
    }
    ```


## /mailbox

- **Method:** PUT
- **Description:** Used for updating a mailbox with new message
- **JSON Request Format/Params:**
    ```json
    {
        "owner_id":"",
        "mail_id":"",
        "message_header":"",
        "message_body":"",
        "message_type":""
    }
    ```
## /message

- **Method:** POST
- **Description:** Used for creating a new message
- **JSON Request Format/Params:**
    ```json
    {
        "owner_id": "",
        "mail_id": "",
        "message_header":"",
        "message_body":"",
        "message_type":""
    }
    ```

## /events?stream=<user_id>

- **Method:** GET
- **Description:** Used for creating a stream for events notification per client
- **JSON Request Format/Params:**
    ```

    ```

## /trigger/:id

- **Method:** GET
- **Description:** Used to trigger a notification on a client stream
- **JSON Request Format/Params:**
    ```
    ```

TODO: Add Service passwords to endpoints that are not accessible to clients but other services 

# New Auth
Recent API for authentication on Gx Finance, <baseUrl = www.granularx.com/auth>


## /signup

- **Method:** POST 
- **Description:** Used for creating a new user
- **JSON Request Format/Params:**
    ```json
    {
        "username":""<string>,
        "position": ""<string>,
    	"identifier":""<string>,
	"phone_number":""<string>,
    	"password":""<string>,
    	"pin": <int>,


    }
    ```
- **JSON Response Success:** 
	 ```json
    {
       "status": "SUCCESS",
    "error": "",
    "data": "user successfully created"


    }
    ```

**JSON Response Failed (user already exists):** 
	 ```json
    {
       "status": "FAILED",
    "error": "user already exists",
    "data": [
        "Jason.XL.frantic",
        "Jason.XLVII.awesome",
        "Jason.XVI.gorgeous"
    ],


    }
    ```

 
