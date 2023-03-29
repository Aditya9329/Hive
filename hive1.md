# task to load data from hdfs to hive table it is about internal table
#### step -1 load the raw data into the hdfs
#### step -2 create table 
#### step -3 load data into the hive table from hdfs
##### step -1 (done)
step -2 create table
```bash
    (
    dept_id  int,
    dept_name string,
    manager_id int,
    salary int
    )
    row format delimited
    fields terminated by ',';
```
step-3

```bash
load data inpath '/tmp/depart_data.csv' into table data;
```

