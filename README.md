# Booking_APITesting-
Here is the workflow for booking API Testing

**Chapter 01**

* API, Request types, Collections and Folders. below one is the interface of postman, that have the request types,collection name and folders used for API Test

API - is a application programming interface, it enbles 2 software components to communication with each other using set of dedinition and protocol

this API uses foolowing URL to do the CRUD operations - https://restful-booker.herokuapp.com/ 
and blow are the REST API request types

Get - Select booking data using id

Post - Create a new booking in the database and generate id

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
