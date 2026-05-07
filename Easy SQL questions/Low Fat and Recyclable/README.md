# Low Fat and Recyclable

## 📌 PROBLEMA

**[ENG]**
What percentage of all products are both low fat and recyclable?

**[ESP]**
Que porcentaje del total de productos son tanto bajos en grasa como reciclables?

### TABLA

facebook_products

|product_id|product_class|brand_name|is_low_fat|is_recyclable|product_category|product_family|
|---|---|---|---|---|---|---|
|1|ACCESSORIES|Fort West|N|N|3|GADGET|
|2|DRINK|Fort West|N|Y|2|CONSUMABLE|
|3|FOOD|Fort West|Y|N|1|CONSUMABLE|
|4|DRINK|Golden|Y|Y|3|CONSUMABLE|
|5|FOOD|Golden|Y|N|2|CONSUMABLE|
|6|FOOD|Lucky Joe|N|Y|3|CONSUMABLE|
|7|ELECTRONICS|Lucky Joe|N|Y|2|GADGET|
|8|FURNITURE|Lucky Joe|N|Y|3|GADGET|
|9|ELECTRONICS|Lucky Joe|N|Y|2|GADGET|
|10|FURNITURE|American Home|N|Y|2|GADGET|
|11|FURNITURE|American Home|N|Y|3|GADGET|
|12|ELECTRONICS|American Home|N|Y|3|ACCESSORY|

# 💻 RESPUESTA

```sql
SELECT
    COUNT(*) * 100.0 / (SELECT COUNT(*) FROM facebook_products) AS pct_total
FROM facebook_products
WHERE is_low_fat = 'Y'
  AND is_recyclable = 'Y';
```

# 📊 Explicación

La consulta compara dos cantidades: el numero de productos que cumplen ambas condiciones y el total de productos de la tabla. El `WHERE` deja solo las filas donde `is_low_fat = 'Y'` y `is_recyclable = 'Y'`.

Despues, `COUNT(*)` cuenta esas filas filtradas y las divide por otro `COUNT(*)` calculado sobre toda la tabla mediante la subconsulta. Multiplicar por `100.0` convierte el resultado en porcentaje y evita una division entera.
