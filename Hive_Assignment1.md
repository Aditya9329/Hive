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
5. Create an internal hive table which will store data in ORC format "sales_order_orc"

```bash

create table sales_order_data_orc 
(
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
COUNTRY string, 
TERRITORY string, 
CONTACTLASTNAME string, 
CONTACTFIRSTNAME string, 
DEALSIZE string 
) 
stored as orc;
```

6. Load data from "sales_order_csv" into "sales_order_orc"

```bash
from sales_order_csv insert overwrite table sales_order_orc select *;
```


a. Calculatye total sales per year
```bash
```

b. Find a product for which maximum orders were placed
```bash
```

c. Calculate the total sales for each quarter
```bash
```

d. In which quarter sales was minimum
```bash
```

e. In which country sales was maximum and in which country sales was minimum
```bash
```

f. Calculate quartelry sales for each city
```bash
```

h. Find a month for each year in which maximum number of quantities were sold
```bash
```

