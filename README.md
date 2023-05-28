# Booking_APITesting-
Here is the workflow for booking API Testing

**Chapter 01**

* API, Request types, Collections and Folders.

API - is an application programming interface, it enables 2 software components to communication with each other using set of definitions and protocol

this API uses following URL to do the CRUD operations - https://restful-booker.herokuapp.com/booking 
and blow are the REST API request types

Below the interface is the request types, collection name and folders used for the API Test

![2023-05-27 20 44 22](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/bd944184-de24-4f01-85b7-d69cd717f5fc)

Get - Select booking data using id

![2023-05-28 16 50 56](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/5d9a069d-4e1c-4023-90cf-fe89d7ad81df)

Post - Create a new booking in the database and generate id

fname and name getting from environment variable

![2023-05-28 16 52 38](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/40eacbd1-d070-4f34-992b-d73d9f13c187)

Enviromental variables
fname,lname and last create booking id

code to create dynamic varible id and assing it to b_Id

var jsonData = pm.response.json();//pm access response and request data and set it to the variable
pm.environment.set("b_Id", jsonData.bookingid);//assign booking id to an environment variable(b_Id) and create it


![2023-05-28 16 57 15](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/13bd6e72-c66e-4731-9085-b1dda4ed5892)


Get- Get Booking details created in above step 

![2023-05-28 16 55 12](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/e3ebde4c-36b0-47e1-b56a-4b9dddf6260d)


Post/token Generator - access login and generate a token to update it

Put - Use the token as an authenticator to access and update the required data

Delete - Delete data using id (authenticate delete operation using a token)


* Web Services and types



**Chapter 02**

* Negative Scenarios
* Create and use of envirnment variable
* Postman console
* Assertions - status code,response body, response header, response time

**Chaper 03**

* JSON Assertions
* Curl Command
* execute collection
* Excule tests script from execution
* export collection

**Chapter 04**

* Install Newman
* Execute postman collection using newman
* generate standard html report using newman
* generate detail report using newman

**Chapter 05**

* Patch API
* Difference between patch and put
* Verify Json Schema

**Chapter 06**

* Data dirven testing using JSON file
* Data dirven testing using CSV file

**Chapter 07**

* Install Jenkins
* Run postman collections using Jenkins
* CRON pattern 
* Run newman and generate html report using Jenkins
