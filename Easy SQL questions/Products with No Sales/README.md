# Products with No Sales

**[ENG]**

Write a query to get a list of products that have not had any sales. Output the ID and market name of these products.

**[ESP]**

Escribe una consulta para obtener la lista de producto que no tiene alguna benta. Muestra la ID y el nombre del mercado de estos productos.



### Tables
fct_customer_sales
|cust_id|prod_sku_id|order_date|order_value|order_id|
|---|---|---|---|---|
|C274|P474|2021-06-28|1500|O110|
|C285|P472|2021-06-28|899|O118|
|C282|P487|2021-06-30|500|O125|
|C282|P476|2021-07-02|999|O146|
|C284|P487|2021-07-07|500|O149|
|C285|P478|2021-07-12|700|O150|
|C287|P489|2021-07-13|189|O151|
|C284|P482|2021-07-15|725|O156|
|C281|P482|2021-07-19|725|O164|
|C282|P480|2021-07-22|300|O172|
|C281|P477|2021-07-23|1400|O174|
|C273|P487|2021-07-26|500|O181|
|C287|P482|2021-07-27|725|O186|
|C280|P482|2021-07-30|725|O190|

dim_product


| prod_sku_id | prod_sku_name    | prod_brand | market_name                   |
| ----------- | ---------------- | ---------- | ----------------------------- |
| P472        | iphone-13        | Apple      | Apple IPhone 13               |
| P473        | iphone-13-promax | Apple      | Apply IPhone 13 Pro Max       |
| P474        | macbook-pro-13   | Apple      | Apple Macbook Pro 13''        |
| P475        | macbook-air-13   | Apple      | Apple Makbook Air 13''        |
| P476        | ipad             | Apple      | Apple IPad                    |
| P477        | ipad-pro         | Apple      | Apple IPad Pro                |
| P478        | galaxy-s21       | Samsung    | Samsung Galaxy S21            |
| P479        | galaxy-s22plus   | Samsung    | Samsung Galaxy S22+           |
| P480        | galaxy-watch4    | Samsung    | Samsung Galaxy Watch4         |
| P481        | galaxy-tab-a     | Samsung    | Samsung Galaxy Tab A          |
| P482        | galaxy-tab-s8    | Samsung    | Samsung Galaxy Tab 8          |
| P483        | xps-13           | Dell       | Dell XPS13                    |
| P484        | inspiron-13      | Dell       | Dell Inspiron 13              |
| P485        | powershot-g7     | Canon      | Canon PowerShot G7 X Mark III |
| P486        | hero-10          | GoPro      | GoPro Hero 10                 |
| P487        | max              | GoPro      | GoPro Max                     |
| P488        | charge-5         | JBL        | JBL Charge 5                  |
| P489        | tuner-xl         | JBL        | JBL Tuner XL                  |

# RESPUESTA

```sql



SELECT
    prod_sku_id,
    prod_sku_name
FROM dim_product

WHERE prod_sku_id NOT IN (
    -- Subquery genera las id de los productos vendidos
    select
        DISTINCT prod_sku_id
    from fct_customer_sales
)



```