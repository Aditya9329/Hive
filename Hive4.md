# Bucketing in Hive


# diff. in partitioning and bucketing?
#### partitioning
```Apache Hive allows us to organize the table into multiple partitions where we can group the same kind of data together. It is used for distributing the load horizontally. ```
#### When to use partitioning
```bash
When the column with a high search query has low cardinality.
For example, if you create a partition by the country name then a maximum of 195 partitions will be made and these number
of directories are manageable by the hive.
On the other hand, do not create partitions on the columns with very high cardinality. 
For example- product IDs, timestamp, and price because will create millions of directories which will be impossible for the hive to manage.
```
