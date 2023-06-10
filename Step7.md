**Chapter 07**

* Install Jenkins

should have requirnment Java 11 or 17

* Run Postman collections using Jenkins

Create a Freestyle project -> add project name (BookingAPI) -> select build as Execte Windows batch commands -> enter the batch file path
-> click Apply

Then select project and click build now(Console output in below)

![image](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/b5a7724d-1c1c-4c4b-b96a-6ded394b0f4c)


* CRON pattern 

Use cron pattern to schedule the jobs in jenkings

*- Single Star - minitues (0,59)

** - Double - hours (1,23)

*** - Thirple - days of a month (1-31)

**** - Quadruple - Month (1- 12)

***** - Quintuple - Day of the week (1-7/Monday to Sunday)

Jenkings - > configure - > Build triggers -> Build Periodically -> schedule -> */1 * * * * 
//including space /1 is indicate to build it every minite 


* Run Newman and generate html report using Jenkins

should have configure node path as a system varable to access to Newman commad in jenkings
run api collection and generate report using newman in jenkings

Create a Windows batfile using below command

newman run "CollectionfilePath\\FileName.json" -e "environmentFilePath\\FileName.json" --reporters=cli,htmlextra

Output Files in workspace

![image](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/a2a4715a-4c55-47ba-98dc-1536557fb610)



