# Low Fat and Recyclable

## PROBLEMA

**[ENG]**
What percentage of all products are both low fat and recyclable?

**[ESP]**
Que porcentaje del total de productos es a la vez bajo en grasa y reciclable.

---

### TABLA

`facebook_products`

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

---

## RESPUESTA

```sql
SELECT
    COUNT(*) * 100.0 / (SELECT COUNT(*) FROM facebook_products) AS pct_total
FROM facebook_products
WHERE is_low_fat = 'Y'
  AND is_recyclable = 'Y';
```

---

## EXPLICACION

La consulta cuenta primero cuantas filas cumplen simultaneamente `is_low_fat = 'Y'` e `is_recyclable = 'Y'`.

Despues divide ese total por la cantidad completa de productos obtenida en la subconsulta. Multiplicar por `100.0` convierte el valor en porcentaje.
