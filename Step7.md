**Chapter 07**

* Install Jenkins

should have requirnment Java 11 or 17

* Run Postman collections using Jenkins


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

Create a windown batfile using below command
newman run "CollectionfilePath\\FileName.json" -e "environmentFilePath\\FileName.json" --reporters=cli,htmlextra

