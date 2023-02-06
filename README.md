# create table for sales data
suppose you have a table and table have some data in it,and someone wants you to drop the data but making sure that there must be a backup of it.
table name is sales_data OK.
create table sales_data
(item string,
total_sales int
)
row format delimited
fields terminated by ',';


# Load data into the hdfs of table
load data local inpath 'file:///config/workspace/sales_data_raw.csv' into table sales_data;
select * from sales_data;

# create a backup table
create table sales_data_bkup as select * from sales_data;


