# Stream vs Batch 

## Which one to Pick ?
### Batch Processing 
- Processing files once a day ( end of the day )
- Not in real time, Reporting using Tableau etc 
- Can use Hadoop / Spark to normalize the and feed into the database 
- Huge files and need to maintain the history 

### Stream Processing ( Kafka, Amazon Kenisis )
- Used in Monitoring Applications, Data Analytics application ( google analytics )
- Parsing log for 200, 400, 500 errors 
- Monitoring applications to monitor logs at real time 
- Kafka topic is feed with logs from all the applications ( POINT OF ENTRY )
- subscribers of kafka topics can process the data, we can scale it horizontally when needed 

## Data Analytics Design 

![Screen Shot 2022-02-04 at 12 50 05 PM](https://user-images.githubusercontent.com/16902666/152578260-d909bd31-4ae2-46b7-b622-be021909c4ae.png)
