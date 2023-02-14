# Bucketing in Hive

creating table for users
```bash
create table users
    (
    id int,
    name string,
    salary int,
    unit int
    )
    row format delimited
    fields terminated by ',';
```
loading data into users table
```bash
load data local inpath 'file:///config/workspace/users.csv' into table users;
```

create table locations
```bash
create table locations
    (
    id int,
    location string
    )
    row format delimited
    fields terminated by ',';
```
loading data into locations table
```bash
load data local inpath'file:///config/workspace/locations.csv' into table locations;
```
create bucket table for users
```bash
 create table bucketed_users
    (
    id int,
    name string,
    salary  int,
    unit string
    )
    clustered by (id)
    sorted by (id)
    into 3 buckets;
```
load data into bucketeduser table from users table;
```bash
insert overwrite table bucketed_users select * from users;
```
create bucketed locations table 
```bash
create table bucketed_locations
    (
    id int,
    location string
    )
    clustered by(id)
    sorted by (id)
    into 3 buckets;
  ```

load data into the bucketed location table from table locations;
```bash
 insert overwrite table bucketed_locations select * from locations;
```


# important types of join
# broadcast join
<img src="https://www.clairvoyant.ai/hubfs/img2.png" width="350" >

