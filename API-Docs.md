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
Recent API for authentication on Gx Finance, <baseUrl = api.granularx.com/auth>


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
    	"email": ""<string>,
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

- **JSON Response Failed (user already exists):** 
	 ```json
    {
       "status": "FAILED",
       "error": "user already exists",
       "data": [
        "Jason.XL.frantic",
        "Jason.XLVII.awesome",
        "Jason.XVI.gorgeous",
    }
    ```

 
## /signin?

- **Method:** POST 
- **Description:** Used for signing in a user via uns or email
- **Query Parameter:** platform =  web | mobile
- **JSON Request Format/Params:**
    ```json
    {
        "uns":""<string>,
    	OR
    	"email":""<string>,
    	"password":""<string>,
    }
    ```
- **JSON Response Success:** 
	 ```json
    {
     	"status": "SUCCESS",
    	"error": "",
    	"data": "user signed in successfully"
    }
    ```

- **JSON Response Failed (user not signed in):** 
	 ```json
    {
         "status": "FAILED",
   	 "error": "not found",
    	 "data": "oops, it appears you are not signed up yet"
    }
    ```
## /verify-email

- **Method:** POST 
- **Description:** Used for verifying user email
- **JSON Request Format/Params:**
    ```json
    {
        "email":""<string>,
    	"otp":""<string>,
    }
    ```
- **JSON Response Success:** 
	 ```json
    {
     	"status": "SUCCESS",
    	"error": "",
    	"data": "user email verified successfully"
    }
    ```

 
# Wallet Topup	
For Wallet topup , <baseUrl = api.granularx.com/wallet>

 
## /topup

- **Method:** POST 
- **Description:** Used for topup-ing wallet via external pssp
- **Query Parameter:** type =  base | peer
- **JSON Request Format/Params:**
    ```json
    {
       "amount":<int>
    	"email":""<string>,
       "uns":<string>,
    	"base_currency":e.g "NGN" <string>,
    	"transaction_type":e.g "base" <string>,
    	"pin":1234
    }
    ```
- **JSON Response Success:** 
	 ```json
    {
     	 "status": "SUCCESS" <string>,
   	 "error": "" <string>,
    	"data": {
        	"access_code": e.g "eku5qwtqq496nja" <string>,
        	"auth_url": "https://checkout.paystack.com/eku5qwtqq496nja" <string> ,
        	"reference": "2bb52u5ayo" <string>
  	}
    }
    ```
## /topup/verfiy/:reference

- **Method:** GET
- **Description:** Used for verify that topup action was successful
- **JSON Response Success:** 
	 ```json
    {
     	{
    "status": "SUCCESS",
    "error": "",
    "data": {
        "id": 4127098325,
        "domain": "test",
        "status": "success",
        "reference": "api8yn6no5",
        "receipt_number": null,
        "amount": 23333,
        "message": null,
        "gateway_response": "Successful",
        "paid_at": "2024-08-30T11:00:43.000Z",
        "created_at": "2024-08-30T11:00:07.000Z",
        "channel": "card",
        "currency": "NGN",
        "ip_address": "102.88.68.165",
        "metadata": "",
        "log": {
            "start_time": 1725015637,
            "time_spent": 6,
            "attempts": 1,
            "errors": 0,
            "success": true,
            "mobile": false,
            "input": [],
            "history": [
                {
                    "type": "action",
                    "message": "Attempted to pay with card",
                    "time": 3
                },
                {
                    "type": "success",
                    "message": "Successfully paid with card",
                    "time": 6
                }
            ]
        },
        "fees": 350,
        "fees_split": null,
        "authorization": {
            "authorization_code": "AUTH_ry3o1myjqp",
            "bin": "408408",
            "last4": "4081",
            "exp_month": "12",
            "exp_year": "2030",
            "channel": "card",
            "card_type": "visa ",
            "bank": "TEST BANK",
            "country_code": "NG",
            "brand": "visa",
            "reusable": true,
            "signature": "SIG_U63UIVzALNsppiMUbvVc",
            "account_name": null
        },
        "customer": {
            "id": 183585503,
            "first_name": null,
            "last_name": null,
            "email": "jason@gmail.com",
            "customer_code": "CUS_yunmbk7a5fqayx1",
            "phone": null,
            "metadata": null,
            "risk_action": "default",
            "international_format_phone": null
        },
        "plan": null,
        "split": {},
        "order_id": null,
        "requested_amount": 23333,
        "pos_transaction_data": null,
        "source": null,
        "fees_breakdown": null,
        "connect": null,
        "transaction_date": "2024-08-30T11:00:07.000Z",
        "plan_object": {},
        "subaccount": {}
    }
}
    }
    ```


# In Chat payment	
For In Chat payment , <baseUrl = api.granularx.com/wallet>

 
## /transfer

- **Method:** POST 
- **Description:** Used for sending fiatons to a peer in chat
- **JSON Request Format/Params:**
    ```json
    {
      "sender_wallet_id":"use UNS here <string>",
      "receiver_wallet_id":"use UNS here <string>",
      "amount":"e.g 100 <int>"
    }
    ```
- **JSON Response Success:** 
	 ```json
    {
     	 "status": "SUCCESS" <string>,
   	 "error": "" <string>,
    	"data": "success"
    }
    ```


# In Chat payment using Fiaton service	
For In Chat payment , <baseUrl = api.granularx.com/fiatons>
## /send/peer

- **Method:** POST 
- **Description:** Used for sending fiatons to a peer in chat
- **JSON Request Format/Params:**
    ```json
    {
      "sender_wallet_id":"use UNS here <string>",
      "receiver_wallet_id":"use UNS here <string>",
      "amount":"e.g 100 <int>"
    }
    ```
- **JSON Response Success:** 
	 ```json
    {
     	 "status": "SUCCESS" <string>,
   	 "error": "" <string>,
    	"data": "success"
    }
    ```

## /view/<uns>

- **Method:** GET
- **Description:** Used for getting the fiatons from a user walet
- **JSON Request Format/Params:**

- **JSON Response Success:** 
	 ```json
    {
     	 "status": "SUCCESS" <string>,
   	 "error": "" <string>,
    	"data": []
    }
    ```




  # Chat REST endpoints	
For Chat Rest endpoints , <baseUrl = api.granularx.com/chat>
## /create

- **Method:** POST 
- **Description:** Used for creating a new chat session
- **JSON Request Format/Params:**
    ```json
    {
      "p_1":"use UNS here <string>",
      "p_2":"use UNS here <string>",
    }
    ```
- **JSON Response Success:** 
	 ```json
    {
     	 "status": "SUCCESS" <string>,
   	 "error": "" <string>,
    	"data": "success"
    }
    ```


## /friends

- **Method:** POST 
- **Description:** Used get all friends of a user
- **JSON Request Format/Params:**
    ```json
    {
      "uns":"use UNS here <string>",
      
    }
    ```
- **JSON Response Success:** 
	 ```json
    {
     	 "status": "SUCCESS" <string>,
   	 "error": "" <string>,
    	"data": []
    }
    ```

## /add

- **Method:** POST 
- **Description:** Used for adding a new friend by uns
- **JSON Request Format/Params:**
    ```json
    {
      "uns":"use UNS here <string>",
      "friend_uns":"use UNS here <string>",
    }
    ```
- **JSON Response Success:** 
	 ```json
    {
     	 "status": "SUCCESS" <string>,
   	 "error": "" <string>,
    	"data": "success"
    }
    ```

## /?id=<string>

- **Method:** GET
- **Description:** Used for fetching a chat
- **JSON Request Format/Params:**
    ```json
    {
     
    }
    ```
- **JSON Response Success:** 
	 ```json
    {
     	 "status": "SUCCESS",
    "error": "",
    "data": {
  	// example response data
        "id": "64939e38-841f-4ac5-87bb-02b13401b1ca",
        "p_1": "Chuks.III.King",
        "p_2": "Fem.I.Cool",
        "message": []
    }
    }
    ```







