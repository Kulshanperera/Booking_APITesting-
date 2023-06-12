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
![2023-06-01 20 16 11](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/e024d679-03b5-4c0c-b6b1-9b6a2d99f513)

