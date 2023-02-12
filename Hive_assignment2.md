# Hive Assignment2
Will the reducer work or not if you use “Limit 1” in any HiveQL query?
```bash
No , the reducer will not work because we know that the reducer work only if there is any group by or join or agg. function exists in the query.
```

Suppose I have installed Apache Hive on top of my Hadoop cluster using default metastore configuration. Then, what will happen if we have multiple clients trying to access Hive at the same time? 
```bash
The default metastore of hive allows only one session at a time so if we have multiple clients trying to access the hive they will get an error.
```
Suppose, I create a table that contains details of all the transactions done by the customers: CREATE TABLE transaction_details (cust_id INT, amount FLOAT, month STRING, country STRING) ROW FORMAT DELIMITED FIELDS TERMINATED BY ‘,’ ;
Now, after inserting 50,000 records in this table, I want to know the total revenue generated for each month. But, Hive is taking too much time in processing this query. How will you solve this problem and list the steps that I will be taking in order to do so?

```bash
step -1 : create a bucket and store data in it based on some column.
step -2 : use bucketMapJoin.
```



How can you add a new partition for the month December in the above partitioned table?
```bash
ALTER TABLE table_name ADD PARTITION (month=’December’) LOCATION  ‘/table_name’;
```
