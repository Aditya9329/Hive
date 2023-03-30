# Create table for sales data
suppose you have a table and table have some data in it,and someone wants you to drop the data but making sure that there must be a backup of it.
```bash
table name is sales_data OK.
create table sales_data
(item string,
total_sales int
)
row format delimited
fields terminated by ',';
```


# Load data into the hive table from local machine
```bash
load data local inpath 'file:///config/workspace/sales_data_raw.csv' into table sales_data;
select * from sales_data;
```

# Create a backup table
```bash
create table sales_data_bkup as select * from sales_data;
```

# Table as CSV Serde
```bash
create table csv_table
    (
    name string,
    location string
    )
    row format serde 'org.apache.hadoop.hive.serde2.OpenCSVSerde'
    with serdeproperties(
    "separatorChar" = ",",
    "quoteChar" = "\"",
    "escapeChar" = "\\"
    )
    stored as textfile
    tblproperties ("skip.header.line.count" = "1");
```
------ load data local inpath 'file:///config/workspace/csv_file.csv' into table csv_table;--------


# JSON Serde 

create table json_table
    (
    name string,
    id int,
    skills array<string>
    )
    row format serde 'org.apache.hive.hcatalog.data.JsonSerDe'
    stored as textfile;
 
    load data local inpath 'file:///config/workspace/json_file.json' into table json_table;
    
    select skills[0] as primary_skills from json_table; 
    
    
    
    
    
# Jar
  
    
# How to add file in other format like parquet ,ORC(Optimize Row Columnar),etc in HDFS.
    - ORC file format works well in Hive.
    - PARQUET file format works well with Spark.
    
    Steps to store data a parquet file format.
     - store data a csv then
     - from csv store as parquet
# Create table for parquet
    ```bash
    (
    item string,
    total_sales int
    )
    stored as parquet;
    - cmd:-from sales insert overwrite table data_as_parquet_file select *;
    ```
# InterviewQuestion
    -Ques1. I loaded the file by mentioning as stored as parquet it load with no error in HDFS but at the time of retrival itis throwing an error while running cmd as
    "select * from parquest_table;" why error.
    - Ques2. What is schema on read?
    - Ques3. What is schema on write?
