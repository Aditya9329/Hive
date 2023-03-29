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

# Dealing with different typeof data in fields
create table
```bash
create table employee
    (
    emp_id int,
    name string,
    skills array<string>
    )
    row format delimited
    fields terminated by ','
    collection items terminated by ':';
 ```
 load data file
 ```bash
 load data local inpath 'file:///config/workspace/array_data.csv' into table employee;
 ```
 query-1
 ```bash
 select name,
    skills[0] as primary_skills 
   from employee;
   ```
  
  query-2
  ```bash
  select emp_id,
    name,
    size(skills) as total_skills,
    array_contains(skills,"HADOOP") as known_Hadoop
    from employee;
   ```
  
