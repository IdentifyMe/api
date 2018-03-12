[![Missed call based phone verification](https://identifyme.net/image/logo_gray.svg "Missed call based phone verification")](https://identifyme.net)

# Send a missed call for verification
*Sends a missed call to the specified phone with a number, the last 6 digits of which form the OTP*

* **URL:**  https://identifyme.net/api/missedcall/send

* **Method:** `POST`

* **Data Params**

  **Required:**
 
  ```javascript
    {
    	client: {
    		id, // Your client ID
    		secret // Your secret token
    	},
    	timestamp, // Request timestamp in millis
    	phone // User's full phone number with country code
    }
  ```
    
  **Optional:**
 
  ```javascript
    {
    	eventPushUrl // Endpoint where IdentifyMe may send events like "RING", "HANGUP"
    }
  ```
  
  Sample push: `POST`: `{"status":"HANGUP","phone":"918967896789","timestamp":"1520789802968"}`
  
  Check [requestb](https://requestb.in) for easy development

* **Success Response:**

    * **Code:** `201`
  
      **Content:** `{"message":"call fired","callerPrefix":"900000"}`
 
* **Error Response:**

    * **Code:** 400 BAD REQUEST
  
    * **Code:** 401 UNAUTHORIZED
  
    * **Code:** 402 PAYMENT REQUIRED
  
  
  
  
# Verify OTP in response to a missed call
*Verify if the OTP supplied by user, in response to a missed call, is valid*

* **URL:**  https://identifyme.net/api/missedcall/verify

* **Method:** `POST`

* **Data Params**

  **Required:**
 
  ```javascript
    {
    	client: {
    		id, // Your client ID
    		secret // Your secret token
    	},
    	timestamp, // Call request timestamp in millis
    	phone, // User's full phone number with country code
    	otp // 6 digit OTP supplied by user
    }
  ```
* **Success Response:**

    * **Code:** `200`
  
      **Content:** `{"isValid":[boolean]}`
 
* **Error Response:**

    * **Code:** 401 UNAUTHORIZED
