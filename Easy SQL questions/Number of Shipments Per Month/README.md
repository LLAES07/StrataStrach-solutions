Write a query that will calculate the number of shipments per month. The unique key for one shipment is a combination of shipment_id and sub_id. Output the year_month in format YYYY-MM and the number of shipments in that month.

## amazon_shipment

| shipment_id | sub_id | weight | shipment_date |
| ----------- | ------ | ------ | ------------- |
| 101         | 1      | 10     | 2021-08-30    |
| 101         | 2      | 20     | 2021-09-01    |
| 101         | 3      | 10     | 2021-09-05    |
| 102         | 1      | 50     | 2021-09-02    |
| 103         | 1      | 25     | 2021-09-01    |
| 103         | 2      | 30     | 2021-09-02    |
| 104         | 1      | 30     | 2021-08-25    |
| 104         | 2      | 10     | 2021-08-26    |
| 105         | 1      | 20     | 2021-09-02    |


# RESPUESTA

```sql

SELECT
    TO_CHAR(shipment_date, 'YYYY-MM') AS Año_mes,
    COUNT( shipment_id + sub_id) AS total_shipments
FROM amazon_shipment
GROUP BY
    TO_CHAR(shipment_date, 'YYYY-MM')
    

```