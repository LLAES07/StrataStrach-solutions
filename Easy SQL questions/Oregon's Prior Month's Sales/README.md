# Oregon's Prior Month's Sales



**[ENG]**

The sales division is investigating their sales for the past month in Oregon.


Calculate the total revenue generated from Oregon-based customers for April 2022.

**[ESP]**

La division de ventas está investigando sus ventas en el mes de abril de 2022 en Oregon.

Calcula el total generado de los clientes de la base oregon para abril de 2022.


# TABLA


online_orders

|product_id|promotion_id|cost_in_dollars|customer_id|date_sold|units_sold|
|---|---|---|---|---|---|
|1|1|2|1|2022-04-01|4|
|3|3|6|3|2022-05-24|6|
|1|2|2|10|2022-05-01|3|
|1|2|3|2|2022-05-01|9|
|2|2|10|2|2022-05-01|1|
|9|3|1|2|2022-05-31|5|
|6|1|4|1|2022-04-07|8|
|6|2|2|1|2022-05-01|12|
|3|3|5|1|2022-05-25|4|
|3|3|6|2|2022-05-25|6|
|3|3|7|3|2022-05-25|7|
|2|2|12|3|2022-05-01|1|
|8|2|4|3|2022-05-01|4|
|9|1|1|10|2022-04-07|2|
|10|1|3|2|2022-04-07|4|
|10|1|3|1|2022-04-01|5|
|3|1|6|1|2022-04-02|10|
|2|1|10|10|2022-04-04|8|
|2|1|11|3|2022-04-05|6|
|4|2|2|2|2022-05-02|7|
|5|2|8|1|2022-05-02|7|
|2|3|13|1|2022-05-30|3|
|1|1|2|2|2022-04-07|3|
|10|2|2|3|2022-05-02|9|
|11|1|5|1|2022-04-03|9|



online_customers


|id|first_name|last_name|age|email|state|address|
|---|---|---|---|---|---|---|
|1|Max|George|26|Max@company.com|Oregon|2638 Richards Avenue|
|2|George|Joe|50|George@company.com|California|1003 Wyatt Street|
|3|Laila|Mark|26|Laila@company.com|Oregon|3655 Spirit Drive|
|4|Sarrah|Bicky|31|Sarrah@company.com|California|1176 Tyler Avenue|
|5|Suzan|Lee|34|Suzan@company.com|Washington|1275 Monroe Avenue|
|6|Mandy|John|31|Mandy@company.com|Washington|2510 Maryland Avenue|
|7|Britney|Berry|45|Britney@company.com|Washington|3946 Steve Hunt Road|
|8|Jack|Mick|29|Jack@company.com|Arizona|3762 Stratford Drive|
|9|Ben|Ten|43|Ben@company.com|Oregon|3055 Indiana Avenue|
|10|Tom|Fridy|32|Tom@company.com|Arizona|801 Stratford Drive|
|11|Antoney|Adam|34|Antoney@company.com|Montana|3533 Randall Drive|
|12|Morgan|Matt|25|Morgan@company.com|Montana|2641 Randall Drive|
|13|Molly|Sam|28|Molly@company.com|Arizona|3632 Polk Street|
|14|Adam|Morris|30|Adam@company.com|Oregon|4541 Ferry Street|
|15|Mark|Jon|28|Mark@company.com|Oregon|2522 George Avenue|


# RESPUESTA

```sql


SELECT 
    SUM(units_sold * cost_in_dollars) AS total_revenue_dollars
FROM online_orders
WHERE date_sold >= '2022-04-01'
  AND date_sold <  '2022-05-01'
  AND customer_id IN (
      SELECT id 
      FROM online_customers 
      WHERE state = 'Oregon'
  );


```