---
title: Blog sample for database product
---

Technical blog post for database company

The client has been anonymized in this 750-word piece. 

## How DatabaseCo Handles Data Deduplication 

“There are two major problems with distributed data systems. The second is out of order messages. The first is duplicate messages. The third is off-by-one errors… And the first is duplicate messages.”  Yes, this is a vintage example of database humor.  But it also illustrates the inspiration for DatabaseCo to solve the data duplication issue, which we call deduplication.  This blog post is a high-level overview of how DatabaseCo solves deduplication through field transformations. 

### The Deduplication Problem 

In distributed systems, messages get passed back and forth between many locations, and it’s common for messages to be generated two or more times.  A system may create a duplicate message because:
- A confirmation was not sent.
- A message was replicated before it was sent.  
- Messages were delivered out-of-order. 

A message can be received multiple times with the same information by the time it gets to a database management system. Therefore, your system needs to ensure that data received multiple times doesn’t create duplicate records.  These duplicated messages must be consolidated into a single message.  

### Deduplication Solutions

Before DatabaseCo, there were 3 general ways you could deduplicate: 
- Before duplication happens.
- During ETL jobs.
- At query time. 

### Stop Duplication Before it Happens

You can attempt to stop deduplication before it happens.  This would be ideal, but requires difficult and costly work to identify the location and causes of the duplication. 

The problem can be caused by any of the following:
- A switch or router.
- A failing consumer or worker.
- A problem with GRPC connections.
- Too much traffic.
- A window size that is too small for packets.  

And these are not the only causes. This solution to deduplication requires an in-depth knowledge and understanding of the system network, as well as the hardware and framework(s). This approach offers the greatest reward, however the cost and expertise requirements are very high.

### Stop Duplication During ETL Jobs

Stream-processing ETL jobs is another deduplication option. This method involves deduplication during data stream consumption. These include:
- Introducing an ETL job with KSQL.
- Creating a compacted topic.
- Performing a SQL transformation.
- Performing a Spark job that would work across the streams. 

In order for deduplication to be effective using the stream-processing ETL jobs method, you must ensure the ETL jobs run throughout your system.

### Stop Duplication at Query Time

Attempting to solve the deduplication problem at query time is another method.  However, this involves adding complexity to your query. This is risky because query errors could occur.  For example, if your solution is based on time, but the duplicate messages are delayed by one second instead of 50 milliseconds, the timestamp on the duplicate messages will be beyond your query syntax setup.  

### How DatabaseCo Solves Deduplication

DatabaseCo solves the deduplication problem through unique SQL transformations.  When you bring data into DatabaseCo, you can create SQL transformations that enable you to: 
- Identify a single key.
- Identify a composite key.
- Extract data from multiple keys.

This enables you to build your own complex key, called _ID.  

_ID acts like a primary key in a NOSQL database, which allows updates or duplicate messages to be merged into a single message within DatabaseCo.  DatabaseCo is fully mutable without an active window.  As long as you specify messages with _ID, or identify _ID within the document you are updating or inserting, incoming duplicate messages will be deduplicated and merged together to form a single document. 

### A DatabaseCo Customer Win

Here is an example of how DatabaseCo achieves significant query time savings for one of our customers.  

One of DatabaseCo’s customers has massive amounts of change data, and utilizes an _ID field map. When a field in a database changes, a new record is created. The customer only cares about the latest data state. However, because all the change data is stored, multiple events are created.

If the customer wants to put this data into a data warehouse that cannot map _ID, the customer would have to cycle through the multiple events stored in their database. This means they would need to run a base query followed by additional event queries to get to the latest value state.  This process is extremely computationally expensive and time consuming. 

DatabaseCo eliminates this problem and provides a more efficient solution. If DatabaseCo maps _ID, only the latest state of all records are stored, and all incoming events are deduplicated. Therefore the customer only needs to query the latest state. DatabaseCo enables customers to reduce their query processing time from minutes, down to milliseconds. 
