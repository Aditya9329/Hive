
## create csv table for sales data

create table sales_order_data_csv_v1 ( ORDERNUMBER int, QUANTITYORDERED int, PRICEEACH float, ORDERLINENUMBER int, SALES float, STATUS string, QTR_ID int, MONTH_ID int, YEAR_ID int, PRODUCTLINE string, MSRP int, PRODUCTCODE string, PHONE string, CITY string, STATE string, POSTALCODE string, COUNTRY string, TERRITORY string, CONTACTLASTNAME string, CONTACTFIRSTNAME string, DEALSIZE string ) row format delimited fields terminated by ',' tblproperties("skip.header.line.count"="1") ;

load data local inpath 'file:///home/hadoop/sales_order_data.csv' into table sales_order_data_csv_v1;


## load sales_order_data.csv data into above mentioned tables
create table sales_order_data_orc ( ORDERNUMBER int, QUANTITYORDERED int, PRICEEACH float, ORDERLINENUMBER int, SALES float, STATUS string, QTR_ID int, MONTH_ID int, YEAR_ID int, PRODUCTLINE string, MSRP int, PRODUCTCODE string, PHONE string, CITY string, STATE string, POSTALCODE string, COUNTRY string, TERRITORY string, CONTACTLASTNAME string, CONTACTFIRSTNAME string, DEALSIZE string ) stored as orc;

from sales_order_data_csv_v1 insert overwrite table sales_order_data_orc select *;
