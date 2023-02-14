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
