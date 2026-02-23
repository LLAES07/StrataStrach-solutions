# Sales with Valid Promotion


**[ENG]**

The marketing manager wants you to evaluate how well the previously ran advertising campaigns are working.

Particularly, they are interested in the promotion IDs from the `online_promotions` table.

Calculate the percentage of orders in the `online_orders`table that used a promotion from the `online_promotions` table.

### Tables

online_promotions


| promotion_id |
| ------------ |
| 1            |
| 2            |


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

# REPSUESTA

```sql
-- propuesta 1
SELECT
    COUNT(*)*100.0 / (SELECT COUNT(*) FROM online_orders) AS pct
FROM online_orders o
INNER JOIN online_promotions p
    ON o.promotion_id = p.promotion_id;
    
    
-- propuesta 2
SELECT
    AVG( CASE WHEN p.promotion_id IS NOT NULL THEN 100.0 ELSE 0 END) AS pct
FROM online_orders o
LEFT JOIN online_promotions p
    ON o.promotion_id = p.promotion_id;


```
