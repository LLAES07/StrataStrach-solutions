# Products Report Summary

**[ENG]**

Find the number of unique transactions and total sales for each of the product categories in 2017. Output the product categories, number of transactions, and total sales in descending order. The sales column represents the total cost the customer paid for the product so no additional calculations need to be done on the column. Only include product categories that have products sold.


**[ESP]**

Encuentre la cantidad de transacciones únicas y las ventas totales para cada una de las categorías de productos en 2017. Genere las categorías de productos, la cantidad de transacciones y las ventas totales en orden descendente. La columna de ventas representa el costo total que el cliente pagó por el producto, por lo que no es necesario realizar cálculos adicionales en la columna. Incluya únicamente categorías de productos que tengan productos vendidos.

### Tables

wfm_transactions


|customer_id|store_id|transaction_date|transaction_id|product_id|sales|
|---|---|---|---|---|---|
|1|1|2017-01-06|1|101|13|
|1|1|2017-01-06|1|102|5|
|1|1|2017-01-06|1|103|1|
|2|4|2017-05-06|2|105|20|
|5|4|2017-05-06|5|104|12|
|6|6|2016-02-03|6|106|3|
|7|6|2018-09-09|7|108|5|
|8|10|2017-06-11|8|107|2|
|8|10|2017-06-11|8|109|9|
|8|10|2017-06-11|8|110|10|
|11|11|2017-12-01|11|501|16|
|12|12|2017-12-01|12|502|15|
|13|13|2017-05-05|13|503|13|
|14|14|2017-08-10|14|505|15|
|14|14|2017-08-10|14|506|5|
|14|14|2017-08-10|14|507|500|
|14|14|2017-08-10|14|509|300|
|18|18|2020-01-01|18|510|30|
|19|19|2017-01-07|19|504|50|
|19|20|2017-02-07|20|508|22|
|1|1|2017-01-01|21|401|10|
|2|2|2017-02-02|22|402|16|
|3|3|2017-03-06|23|403|15|
|4|4|2017-04-07|24|404|13|
|5|5|2017-05-09|25|405|15|
|6|6|2017-06-10|26|406|5|
|7|7|2017-07-12|27|407|500|
|8|8|2017-08-13|28|408|300|
|9|9|2017-09-14|29|409|9|
|10|10|2017-10-16|30|410|10|
|11|10|2017-11-17|31|301|16|
|12|11|2017-12-19|32|302|15|
|13|12|2017-01-01|33|303|13|
|14|13|2017-02-02|34|304|15|
|15|14|2017-03-06|35|305|5|
|16|15|2017-04-07|36|306|500|
|17|16|2017-05-09|37|307|300|
|18|15|2017-06-10|38|308|30|
|19|16|2017-07-12|39|309|50|
|20|17|2017-08-13|40|310|22|
|1|18|2017-09-14|41|201|100|
|2|2|2017-10-16|42|202|36|
|3|3|2017-11-17|43|203|78|
|4|4|2017-12-19|44|204|99|
|5|5|2017-01-01|45|205|26|
|6|6|2017-02-02|46|206|265|
|7|7|2017-03-06|47|207|215|
|8|8|2017-04-07|48|208|98|
|9|9|2017-05-09|49|209|66|
|10|10|2017-06-10|50|210|34|
|11|10|2017-07-12|51|601|31|
|12|11|2017-08-13|52|602|89|
|13|12|2017-09-14|53|603|59|
|14|13|2017-10-16|54|604|70|
|15|14|2017-11-17|55|605|9|
|16|15|2017-12-19|56|606|13|
|17|16|2017-10-16|57|607|5|
|18|15|2017-11-17|58|608|1|
|19|16|2017-12-19|59|609|20|
|20|17|2017-01-01|60|610|12|
|21|18|2017-02-02|61|701|3|
|22|15|2017-03-06|62|702|5|
|23|16|2017-04-07|63|703|2|
|24|15|2017-05-09|64|704|9|
|25|16|2017-06-10|65|705|10|
|26|17|2017-07-12|66|706|16|
|23|18|2017-08-13|67|707|15|
|28|14|2017-09-14|68|708|13|
|29|15|2017-10-16|69|709|15|
|40|16|2017-11-17|70|710|5|
|46|15|2017-12-19|71|801|500|
|78|16|2017-06-10|72|802|300|
|33|17|2017-07-12|73|803|30|
|66|18|2017-08-13|74|804|50|
|1|15|2017-09-14|75|805|22|
|1|16|2017-10-16|76|806|10|
|1|15|2017-11-17|77|807|16|
|2|16|2017-12-19|78|808|15|

wfm_products

|roduct_id|product_description|product_brand|product_category|
|---|---|---|---|
|101|101 sold by Brand1|Brand1|Seafood|
|102|102 sold by Brand1|Brand1|Seafood|
|103|103 sold by Brand1|Brand1|Seafood|
|105|105 sold by Brand1|Brand1|Seafood|
|104|104 sold by Brand1|Brand1|Seafood|
|106|106 sold by Brand1|Brand1|Seafood|
|108|108 sold by Brand1|Brand1|Seafood|
|107|107 sold by Brand1|Brand1|Seafood|
|109|109 sold by Brand1|Brand1|Seafood|
|110|110 sold by Brand1|Brand1|Seafood|
|501|501 sold by Brand9|Brand9|OTS|
|502|502 sold by Brand9|Brand9|OTS|
|503|503 sold by Brand9|Brand9|OTS|
|505|505 sold by Brand9|Brand9|OTS|
|506|506 sold by Brand9|Brand9|OTS|
|507|507 sold by Brand9|Brand9|OTS|
|509|509 sold by Brand9|Brand9|OTS|
|510|510 sold by Brand9|Brand9|OTS|
|504|504 sold by Brand9|Brand9|OTS|
|508|508 sold by Brand9|Brand9|OTS|
|401|401 sold by Brand2|Brand2|Dairy|
|402|402 sold by Brand2|Brand2|Dairy|
|403|403 sold by Brand2|Brand2|Dairy|
|404|404 sold by Brand2|Brand2|Dairy|
|405|405 sold by Brand2|Brand2|Dairy|
|406|406 sold by Brand2|Brand2|Dairy|
|407|407 sold by Brand2|Brand2|Dairy|
|408|408 sold by Brand2|Brand2|Dairy|
|409|409 sold by Brand2|Brand2|Dairy|
|410|410 sold by Brand2|Brand2|Dairy|

# RESPUESTA



```sql
SELECT
    p.product_category,
    COUNT(DISTINCT t.transaction_id) AS num_transactions,
    SUM(t.sales) AS total_sales
FROM wfm_transactions t
JOIN wfm_products p ON t.product_id = p.product_id
WHERE EXTRACT(YEAR FROM t.transaction_date) = 2017
GROUP BY p.product_category
ORDER BY total_sales DESC;
```

# 📊 Explicación

El objetivo es resumir las transacciones del año 2017 por categoría de producto. Para ello, unimos las tablas `wfm_transactions` (donde están las ventas) y `wfm_products` (donde están las categorías). Filtramos los registros del año 2017 y agrupamos por `product_category`. En la salida, calculamos el total de transacciones únicas usando `COUNT(DISTINCT transaction_id)` y el total de ventas sumando la columna `sales`. Finalmente, ordenamos los resultados de mayor a menor según el volumen de ventas.

