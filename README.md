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

Step 3 : Get- Get Booking details created in above step 2
Access id environmental variable using {{b_Id}}

![2023-05-28 16 55 12](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/e3ebde4c-36b0-47e1-b56a-4b9dddf6260d)


Step 4: Post/token Generator - to generate a token and update or delete data using the token (token identifies the resource user URL - https://restful-booker.herokuapp.com/auth)

```
//script to create token as a enviromental variable and add it as an aheader value in the reuest 

var tokenData = pm.response.json();
pm.environment.set("Token", tokenData.token);
```

![2023-05-28 18 02 37](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/d324fb5d-6f0c-45c4-a816-bd57828ca327)


Step 5 : Put - Use the token as an authenticator to access and update the data
//Header values - **key**   Cookie   | **value** token = {{Token}}  
![2023-05-28 18 04 17](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/ad4df7a6-001f-48bf-bfbd-990d85460e7b)


Step 6: Delete - Delete data using id (authenticate delete operation using a token)
//Header values - **key**   Cookie   | **value** token = {{Token}} 
![2023-05-28 18 06 07](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/4e652336-658f-4eb1-9055-2f09ceaa3b2f)



* Web Services and types



**Chapter 02**

* Negative Scenarios

here in the negative scenario tring to validate data and iD that not avalable in the database 
URI for get request - https://restful-booker.herokuapp.com/booking/70100
expected result - 404 not found message
actual result - 404 not found 

URI for Post request - https://restful-booker.herokuapp.com/booking
Post body
```
{
    "firstname": "Thilith",
    "lastname": "Perera",
    "totalprice": 11trrt1,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2018-01-01",
        "checkout": "2019-01-01"
    },
    "additionalneeds": "Breakfast"
```
expected result - status code - 400 (Bad request )
actual result - status code - 400

* Create and use of environmental variable

environment variable(test environment,dev environment), global variable(can access it through the workspace), 
collection (within only the same collection), request level (only access inside the requests)

Environmental variables
fname,lname and last create booking id

code to create dynamic varible b_Id and store it(Created test scripts in Post Request)

```
var jsonData = pm.response.json();//pm access response and request data and set it to the variable
pm.environment.set("b_Id", jsonData.bookingid);//assign booking id to an environment variable(b_Id) and create it
```

![2023-05-28 16 57 15](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/13bd6e72-c66e-4731-9085-b1dda4ed5892)

* Assertions - status code, response body, response header, response time
```
//Assert the response code 
  pm.test("Status code is 400", function () {
    pm.response.to.have.status(400);
});
```

**Chapter 03**

* JSON Assertions

```
pm.test("status code is 200", function (){
    pm.response.to.have.status(200);
});
```
```
varv = pm.response.json(); //reading the api response and store in variable as a json object 
pm.test("Verfy the response",function(){
    pm.expect(v.firstname).to.eql("Thilith"); //assert the results
});
```
```
var p = pm.response.json();
pm.test("Verify the total price",function(){
    pm.expect(p.totalprice).to.eql(1000); 
});
```
```
var c =pm.response.json();
pm.test("Verify checking date",function() {
    pm.expect(c.bookingdates.checkin).to.eql("2018-01-01");//access json object inside the another json oject 
});
```
Test Results

![image](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/b24f5b37-c5d3-403c-9eca-cb83a6a6d34c)


* Curl Command

Export API request into the CURL (</> button in Postman) command and export it to another API collection like the DEV environment
(Client URL enable the pass the data between the device and server through the command line interface)
when importing click the import button on top of the Postman, click row text, paste the command, click continue and click import


**Chapter 04**

* Install Newman

_installation_

**$ npm install -g newman //newman --version - check Version**

* Execute postman collection using Newman

**$ newman run collectionFileName.json -e environmenrVariableFileName.json  //run collection using CMD -e including an environment file**

* generate standard html report using Newman

Reporters with Newman Install the reporter package

$ npm install -g newman-reporter-html //simple report

_Run_

**$ newman run /path/to/collection.json -r cli,html**

Reporters with Newman Install the reporter package

**$ npm install -g newman-reporter-html //simple report**

_Run_

**$ newman run /path/to/collection.json -r cli,html**

* generate detailed report using Newman

Interactive Example report

To globally install the htmlextra package:

**$ npm install -g newman-reporter-htmlextra**

excute collection using advance HTML report

**$ newman run collectionName.json -r htmlextra --reporters-cli,htmlextra**

**Chapter 05**

* Patch Request

Patch request modify the data in the applicaiton server 

* Difference between patch and put

Patch request modify the data in the applicaiton server 

it request to update partial data in the server

//for PUT request when updating the firstname and lastname we sending request body as a blow data
```
{
    "firstname": "Thilith",
    "lastname": "Perera",
    "totalprice": 1000,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2018-01-01",
        "checkout": "2023-05-15"
    },
    "additionalneeds": "Breakfast"
}
```
//for PATCH request when updating the firstname and lastname we sending request body as a blow data only specific data fields
and it saving more data intead to sending whole data as a request.
```
{
    "firstname": "AB",
    "lastname": "CD"

}
```

* Verify JSON Schema

Validate field getting correct data type when getting the response when request get method

```
//below is Postman response from get method 
{
    "firstname": "Thilith",
    "lastname": "Perera",
    "totalprice": 1000,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2018-01-01",
        "checkout": "2019-01-01"
    },
    "additionalneeds": "Breakfast"
}
```

```
//blow Json schema validaion with Json Oject (response by server/above response)
const expectedJSONSchema =
{
  "type": "object",
  "properties": {
    "firstname": {
      "type": "string"
    },
    "lastname": {
      "type": "string"
    },
    "totalprice": {
      "type": "integer"
    },
    "depositpaid": {
      "type": "boolean"
    },
    "bookingdates": {
      "type": "object",
      "properties": {
        "checkin": {
          "type": "string"
        },
        "checkout": {
          "type": "string"
        }
      },
      "required": [
        "checkin",
        "checkout"
      ]
    },
    "additionalneeds": {
      "type": "string"
    }
  },
  "required": [
    "firstname",
    "lastname",
    "totalprice",
    "depositpaid",
    "bookingdates",
    "additionalneeds"
  ]
};

```
```
pm.test("Json Schema Validation", function(){
    pm.response.to.have.jsonSchema(expectedJSONSchema);//pm.response.to.have.jsonSchema - this part covert the response to jsonSchema

});

```

Test result 

![image](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/08592a14-9a5d-409c-b049-7ca38ccd2948)

**Chapter 06**

* Data-driven testing using JSON file

Getting firstname and lastname from the external data(Json) file. it able to pass multiple booking creation post request(CreateBookingWithFile), in here only use first name and last name fields.

below is json file data (3 json objects/File Name - PostManDataDrivenTestingFile.json) 

```
[
	{
		"fname":"Postman1",
		"lname":"PostRequest1"
	},
	{
		"fname":"Postman2",
		"lname":"PostRequest2"
	},

	{
		"fname":"Postman3",
		"lname":"PostRequest3"
	}
]

```

```
//created varable as bleow ({{fanme}}) and pass it in above data as a json file
{
    "firstname": "{{fname}}",
    "lastname": "{{lname}}",
    "totalprice": 1000,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2018-01-01",
        "checkout": "2019-01-01"
    },
    "additionalneeds": "Breakfast"
}
```
steps - click 3 dots near to the collection name -> run collection -> select CreateBookingWithFile(postrequest) ->select data file -> 
Click run Booking Api.

Below the success results

![image](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/2f41a433-9e36-4e63-a7da-c64901c4609a)

```
//Test script for validate results

var fname = pm.variables.get("fname");
var lname  = pm.variables.get("lname");//reading the data variable from externak file

var d = pm.response.json();
pm.test("Validate Firstname from external file", function(){
    pm.expect(d.booking.firstname).to.eql(fname);
});

pm.test("Validate Lastname from external file", function(){
    pm.expect(d.booking.lastname).to.eql(lname);
});

```
* Data-driven testing using CSV file - same way entering the data to an excel file then saving it as a CSV data file

**Chapter 07**

* Install Jenkins
* 
should have requirnment Java 11 or 17

* Run Postman collections using Jenkins


* CRON pattern 

Use cron pattern to schedule the jobs in jenkings

* - Single Star - minitues (0,59)
** - Double - hours (1,23)
*** - Thirple - days of a month (1-31)
**** - Quadruple - Month (1- 12)
***** - Quintuple - Day of the week (1-7/Monday to Sunday)

Jenkings - > configure - > Build triggers -> Build Periodically -> schedule -> */1 * * * * 
//including space /1 is indicate to build it every minite 


* Run Newman and generate html report using Jenkins

should have configure node path as a system varable to access to Newman commad in jenkings
run api collection and generate report using newman in jenkings

Create a windown batfile using below command
newman run "CollectionfilePath\\FileName.json" -e "environmentFilePath\\FileName.json" --reporters=cli,htmlextra

