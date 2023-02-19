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

I am inserting data into a table based on partitions dynamically. But, I received an error – FAILED ERROR IN SEMANTIC ANALYSIS: Dynamic partition strict 
mode requires at least one static partition column. How will you remove this error?
```bash
SET hive.exec.dynamic.partition = true;
SET hive.exec.dynamic.partition.mode = nonstrict;
```



Suppose, I have a lot of small CSV files present in the input directory in HDFS and I want to create a single Hive table corresponding to these files. The data in these files are in the format: {id, name, e-mail, country}. Now, as we know, Hadoop performance degrades when we use lots of small files.
So, how will you solve this problem where we want to create a single Hive table for lots of small files without degrading the performance of the system?



```bash

Create a simple table:
CREATE TABLE table_to_use (id INT, name STRING, e-mail STRING, country STRING)

ROW FORMAT FIELDS DELIMITED TERMINATED BY ‘,’
STORED AS TEXTFILE;

Load the data into table_to_use:
load data inpath ‘/input’ into table table_to_use;

create a final table
create table full_data (id int, name string, e-mail string, country string)

ROW FORMAT FIELDS DELIMITED TERMINATED BY ‘,’ stored as full_data;


insert overwrite table full_data select * from simple_table;
```

Hive pratical

create table customers
```bash
    create table customers
     (
     id int
     age int,
     name string,
     adress string,
     salary int
     )
     ;
  ```
create table orders

```bash 
    create table orders
    (
    oid int,
    o_date date,
    customerid int,
    amount int
    );
```


Now perform different joins operations on top of these tables
(Inner JOIN, LEFT OUTER JOIN ,RIGHT OUTER JOIN ,FULL OUTER JOIN)

# inner join
```bash
select * from customers inner join orders on customers.id = orders.o_id;
```

# left outer join
```bash
select * from customers left outer join orders on customers.id = orders.o_id;
```
# right outer join
```bash
select * from customers right outer join orders on customers.id = orders.o_id;
```

# full outer join
```bash
select * from customers full outer join orders on customers.id = orders.o_id;
```

Download a data from the given location - 
https://archive.ics.uci.edu/ml/machine-learning-databases/00360/

1. Create a hive table as per given schema in your dataset 
2. ```
3. create table air(
    d_date date,
    d_time timestamp,
    d_co int,
    pt08 int,
    nmhc int,
    c6h6 int,
    pto8 int,
    nox int,
    pt08_s3 int,
    no2 int,
    pt08_s4 int,
    pt05_s5 int,
    t int,
    rh int,
    ah int
    )
    row format delimited
    fields terminated by ';';
    ```
    
    
    
    
    create table location
    ```bash
    ```
    try to place a data into table location
    ```bash
    load data local inpath 'file:///config/workspace/locations.csv' into table location;
     ```
     Perform a select operation . 
    ```bash
     select * from location;
    ```
    Fetch the result of the select operation in your local as a csv file .
    ```bash
    hadoop fs -cat /user/hive/warehouse/location/locations.csv > /config/workspace/sample.csv
    ```
    Perform group by operation . 
    ```bash
    select city from location group by city;
    ```
Perform filter operation at least 5 kinds of filter examples . 
```bash
select * from location where city='MAHARASHTRA';
select * from location;
select * from location order by city ;
    select * from location where id%2=0;
    select * from location where id%2!=0;
```

alter table operation 
```bash
alter table location rename to locations;
 ```
drop table operation
```bash
drop table locations;
```
order by operation .
```bash
select * from location order by city ;
```
where clause operations you have to perform . 
```bash
 select * from location where id%2=0;
 ```
 sorting operation you have to perform . 
```bash
select * from location order by city ;
```
distinct operation you have to perform . 
```bash
select distinct(city) from locations;
```
like an operation you have to perform . 
```bash
SELECT * FROM location
WHERE city LIKE 'a%';
```
union operation you have to perform . 
```bash
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
```
table view operation you have to perform . 
```bash
create view location_view as select * from locations where id%2=0;
```









