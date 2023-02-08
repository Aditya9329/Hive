# Hive Assignment

data download done
```bash
 https://github.com/shashank-mishra219/Hive-Class/blob/main/sales_order_data.csv
 ```
 
 
2. Store raw data into hdfs location
 ```bash
  hadoop fs -put sales_order_data.csv /data_dir
  ```

3. Create a internal hive table "sales_order_csv" which will store csv data sales_order_csv .. make sure to skip header row while creating table
```bash
 create table sales_order_csv( 
 ORDERNUMBER int,
 QUANTITYORDERED int,
 PRICEEACH float,
 ORDERLINENUMBER int, 
 SALES float, 
 STATUS string, 
 QTR_ID int, 
 MONTH_ID int, 
 YEAR_ID int, 
 PRODUCTLINE string, 
 MSRP int, 
 PRODUCTCODE string, 
 PHONE string, 
 CITY string, 
 STATE string, 
 POSTALCODE string, 
 COUNTRY string, TERRITORY string,
 CONTACTLASTNAME string, 
 CONTACTFIRSTNAME string, 
 DEALSIZE string 
 ) 
 row format delimited
 fields terminated by ',' 
 tblproperties("skip.header.line.count"="1") ;
```
4. Load data from hdfs path into "sales_order_csv" 
```bash
load data inpath '/data_dir/sales_order_data.csv' into table sales_order_csv;
```



