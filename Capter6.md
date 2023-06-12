**Step 06**

* Data-driven testing using JSON file

Getting firstname and lastname from the external data(JSON) file. it is able to pass multiple booking creations through the post request(CreateBookingWithFile), in here only uses first name and last name fields.

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

![2023-06-10 15 49 08](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/88a853e8-26cf-4eac-b8be-2fe705203978)

```
//Test script for validate results

var fname = pm.variables.get("fname");
var lname  = pm.variables.get("lname");//reading the data variable from external file

var d = pm.response.json();
pm.test("Validate Firstname from external file", function(){
    pm.expect(d.booking.firstname).to.eql(fname);
});

pm.test("Validate Lastname from external file", function(){
    pm.expect(d.booking.lastname).to.eql(lname);
});

```
* Data-driven testing using CSV file 

Followed the same steps this have done entering the data to an Excel file and then saving it as a CSV data file
