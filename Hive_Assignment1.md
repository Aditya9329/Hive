# Hive Assignment

data download done
```bash
 https://github.com/shashank-mishra219/Hive-Class/blob/main/sales_order_data.csv
 ```

3. Create a internal hive table "sales_order_csv" which will store csv data sales_order_csv .. make sure to skip header row while creating table
4. ```bash
5. create table sales_order_csv( 
6.  ORDERNUMBER int,
7.  QUANTITYORDERED int,
8.   PRICEEACH float,
9.   ORDERLINENUMBER int, 
10.  SALES float, 
11.  STATUS string, 
12.  QTR_ID int, 
13.  MONTH_ID int, 
14.  YEAR_ID int, 
15.  PRODUCTLINE string, 
16.  MSRP int, 
17.  PRODUCTCODE string, 
18.  PHONE string, 
19.  CITY string, 
20.  STATE string, 
21.  POSTALCODE string, 
22.  COUNTRY string, TERRITORY string,
23.  CONTACTLASTNAME string, 
24.  CONTACTFIRSTNAME string, 
25.  DEALSIZE string 
26.  ) 
27.  row format delimited
28.  fields terminated by ',' 
29.  tblproperties("skip.header.line.count"="1") ;
30.  ```
31.  
