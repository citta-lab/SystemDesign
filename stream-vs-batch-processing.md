# Stream vs Batch 

## Which one to Pick ?
### Batch Processing 
- Processing files once a day ( end of the day )
- Not in real time, Reporting using Tableau etc 
- Can use Hadoop / Spark to normalize the and feed into the database 
- Huge files and need to maintain the history 

### Stream Processing 
- Parsing log for 200, 400, 500 errors 
- Monitoring applications to monitor logs at real time 
- Kafka topic is feed with logs from all the applications ( POINT OF ENTRY )
- subscribers of kafka topics can process the data, we can scale it horizontally when needed 

