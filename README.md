# create table for sales data
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


# Load data into the hdfs of table
```bash
load data local inpath 'file:///config/workspace/sales_data_raw.csv' into table sales_data;
select * from sales_data;
```

# create a backup table
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
