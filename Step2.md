
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
