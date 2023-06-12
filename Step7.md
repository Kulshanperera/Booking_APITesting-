**Chapter 07**

* Install Jenkins

should have requirnment Java 11 or 17

* Run Postman collections using Jenkins

Create a Freestyle project -> add project name (BookingAPI) -> select build as Execte Windows batch commands -> enter the batch file path
-> click Apply

Then select project and click build now(Console output in below)

![2023-06-10 18 26 16](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/699bfddd-3de1-4b9c-8f4c-56e74605d1bc)

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

![2023-06-10 18 28 23](https://github.com/Kulshanperera/Booking_APITesting-/assets/47887463/bdd133f3-798b-41a6-af80-af2e45093872)



