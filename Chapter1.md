
* API, Request types, Collections and Folders.

API -  is an application programming interface, it enables 2 software components to communicate with each other using a set of definitions and protocol

this API uses the following URL to do the CRUD operations - https://restful-booker.herokuapp.com/booking 
and blow are the REST API request types

Below the interface is the request types, collection name and folders used for the API Test

![2023-05-27 20 44 22](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/c0a20aae-bdcf-4f7f-abb1-24e3c964b0ed)



Step 1 : Get - Select booking data using id

![2023-05-28 16 50 56](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/61d89cf9-8ccc-4020-bea5-f44c079e970c)


Step 2: Post - Create a new booking in the database and generate an id

fname and name getting from the environment variable

![2023-05-28 16 52 38](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/40eacbd1-d070-4f34-992b-d73d9f13c187)

Step 3 : Get- Get Booking details created in above step 2
Access id environmental variable using {{b_Id}}

```
//Script for b_Id varable creation
var jsonData = pm.response.json();
pm.environment.set("b_Id", jsonData.bookingid);//assign bookingid response value to b_Id as environment varable

```

![2023-05-28 16 55 12](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/e906feec-9fc5-4a1a-93c1-acebd6fba98f)


Step 4: Post/token Generator - to generate a token and update or delete data using the token (token identifies the resource user URL - https://restful-booker.herokuapp.com/auth)

```
//script to create token as a enviromental variable and add it as an header value in the reuest 

var tokenData = pm.response.json();
pm.environment.set("Token", tokenData.token);
```

![2023-05-28 18 02 37](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/0fea7968-fa3f-4770-a128-1a64bcc77b46)

Step 5 : Put - Use the token as an authenticator to access and update the data
//Header values - **key**   Cookie   | **value** token = {{Token}}  
![2023-05-28 18 04 17](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/64d0e7b9-853d-4ec5-8dd2-b6de7b56b6ea)

Step 6: Delete - Delete data using id (authenticate delete operation using a token)
//Header values - **key**   Cookie   | **value** token = {{Token}} 
![2023-05-28 18 06 07](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/a458fb3b-189c-47b3-91fc-b2c9163a6396)


* Web Services and types

Web service is a software package that enables the communication between two devices or web entities over the internet.

Types

* SOAP web services
* REST web services
