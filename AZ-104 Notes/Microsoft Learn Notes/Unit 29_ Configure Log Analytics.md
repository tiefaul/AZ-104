# AZ-104 Notes
## Log Analytics
- Use this to edit and run log queries for the data collected in Azure Monitor Logs
- Supports the Kusto Query Language (KQL)
	- This can create simple and complex queries with KQL like:
		- Search and sort value, time, property state, and more
		- Join data from multiple tables
		- Aggregate large sets of data
		- Perform intricate operations with minimal code
<br/>
## Using KQL Queries
```
SecurityEvent # the table that KQL is targeting
| sort by TimeGenerated desc # sorts by timestamp and goes in descending order
| take 10 # Limits the output to only 10 records
```

```
SecurityEvent
| where Level == 8 and EventID != 4688 # Sets the critical event level to 8 and where the eventid is not 4688
| where TimeGenerated > ago(3d) # event happend in the last 3 days
| project TimeGenerated, Computer, Activity # sets specified fields for the table
| extend EventCode = substring(Activity, 0, 4) # adds event code to the columns listed in the project line, then grabs the first 4 strings to the activity column and adds it to the eventcode column
| summarize count() by Computer, EventCode # the query groups the events by Computer and EventCode, and then counts the number of events within each group using the count() function
| render piechart # displays a piechart of the data
```
```
Perf
| where TimeGenerated > ago(7d)
| where CounterName == "Available MBytes"
| summarize avg(CounterValue) by bin(TimeGenerated, 1h)# 
| render timechart
```
In the last instance (Perf) We're grouping data points into time intervals of 1 hour each. So, instead of having individual timestamps, we're organizing them into hourly intervals or buckets(bin).

For instance, if we have timestamps ranging from 12:00 PM to 4:00 PM, the data might be bucketized like this:

Bucket 1 (12:00 PM - 1:00 PM)
Bucket 2 (1:00 PM - 2:00 PM)
Bucket 3 (2:00 PM - 3:00 PM)
Bucket 4 (3:00 PM - 4:00 PM)
