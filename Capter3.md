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

![2023-06-01 19 05 26](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/8aa882a5-8e21-4a48-a24d-bd051e9ccd14)


* Curl Command

Export API request into the CURL (</> button in Postman) command and export it to another API collection like the DEV environment
(Client URL enable the pass the data between the device and server through the command line interface)
when importing click the import button on top of the Postman, click row text, paste the command, click continue and click import
