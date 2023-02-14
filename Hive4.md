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
