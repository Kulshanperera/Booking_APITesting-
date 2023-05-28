# Booking_APITesting-
Here is the workflow for booking API Testing

**Chapter 01**

* API, Request types, Collections and Folders.

API -  is an application programming interface, it enables 2 software components to communicate with each other using a set of definitions and protocol

this API uses the following URL to do the CRUD operations - https://restful-booker.herokuapp.com/booking 
and blow are the REST API request types

Below the interface is the request types, collection name and folders used for the API Test

![2023-05-27 20 44 22](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/bd944184-de24-4f01-85b7-d69cd717f5fc)

Step 1 : Get - Select booking data using id

![2023-05-28 16 50 56](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/5d9a069d-4e1c-4023-90cf-fe89d7ad81df)


Step 2: Post - Create a new booking in the database and generate an id

fname and name getting from the environment variable

![2023-05-28 16 52 38](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/40eacbd1-d070-4f34-992b-d73d9f13c187)

Environmental variables
fname,lname and last create booking id

code to create dynamic varible b_Id and store it(Created test scripts in Post Request)

```
var jsonData = pm.response.json();//pm access response and request data and set it to the variable
pm.environment.set("b_Id", jsonData.bookingid);//assign booking id to an environment variable(b_Id) and create it
```

![2023-05-28 16 57 15](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/13bd6e72-c66e-4731-9085-b1dda4ed5892)



Step 3 : Get- Get Booking details created in above step 2
Access id environmental variable using {{b_Id}}

![2023-05-28 16 55 12](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/e3ebde4c-36b0-47e1-b56a-4b9dddf6260d)


Step 4: Post/token Generator - to generate a token and update or delete data using the token (token identifies the resource user URL - https://restful-booker.herokuapp.com/auth)

```
//script to create token as a enviromental variable tokenData and add it as an header value 

var tokenData = pm.response.json();
pm.environment.set("Token", tokenData.token);
```

![2023-05-28 18 02 37](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/d324fb5d-6f0c-45c4-a816-bd57828ca327)


Step 5 : Put - Use the token as an authenticator to access and update the required data
//Headers **key**   Cookie   | **value** token = {{Token}}  
![2023-05-28 18 04 17](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/ad4df7a6-001f-48bf-bfbd-990d85460e7b)


Step 6: Delete - Delete data using id (authenticate delete operation using a token)
//Headers **key**   Cookie   | **value** token = {{Token}} 
![2023-05-28 18 06 07](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/4e652336-658f-4eb1-9055-2f09ceaa3b2f)



* Web Services and types



**Chapter 02**

* Negative Scenarios
* Create and use of environmental variable
* Postman console
* Assertions - status code, response body, response header, response time

**Chapter 03**

* JSON Assertions
* Curl Command
* execute collection
* Excule tests script from execution
* export collection

**Chapter 04**

* Install Newman
* Execute postman collection using Newman
* generate standard html report using Newman
* generate detailed report using Newman

**Chapter 05**

* Patch API
* Difference between patch and put
* Verify JSON Schema

**Chapter 06**

* Data-driven testing using JSON file
* Data-driven testing using CSV file

**Chapter 07**

* Install Jenkins
* Run Postman collections using Jenkins
* CRON pattern 
* Run Newman and generate html report using Jenkins
