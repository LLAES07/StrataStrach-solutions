
# Processed Ticket Rate By Type

**[ENG]**

Find the processed rate of tickets for each `type`. The processed rate is defined as the number of processed tickets divided by the total number of tickets for that type. Round this result to two decimal places.

**[ESP]**

Encuentra la tasa procesada de tickets para cada `type`. La tasa procesada se define como el número de tickets procesados dividido por el total de tickets para ese tipo. Redondea este resultado a dos decimales.


### Table

facebook_complaints

|complaint_id|type|processed|
|---|---|---|
|0|0|TRUE|
|1|0|TRUE|
|2|0|FALSE|
|3|1|TRUE|
|4|1|TRUE|
|5|1|FALSE|
## RESPUESTA

```sql
SELECT
    type,
    ROUND(SUM(CASE WHEN processed = TRUE THEN 1 ELSE 0 END)::NUMERIC / COUNT(*), 2) AS processed_rate
FROM facebook_complaints
GROUP BY type
ORDER BY type;
```

## EXPLICACION

Primero contamos cuantas filas procesadas hay por `type` y luego lo dividimos entre el total de tickets de ese mismo tipo. `ROUND(..., 2)` deja el resultado con dos decimales.
