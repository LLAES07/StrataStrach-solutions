# Monthly Active Users

## PROBLEMA

**[ENG]**
Find the monthly active users for January 2021 for each account. Your output should have `account_id` and the monthly count for that account.

**[ESP]**
Encuentra los usuarios activos mensuales de enero de 2021 para cada cuenta. Muestra el `account_id` y el conteo mensual correspondiente.

---

### TABLA

`sf_events`

|record_date|account_id|user_id|
|---|---|---|
|2021-01-01|A1|U1|
|2021-01-01|A1|U2|
|2021-01-06|A1|U3|
|2021-01-02|A1|U1|
|2020-12-24|A1|U2|
|2020-12-08|A1|U1|
|2020-12-09|A1|U1|
|2021-01-10|A2|U4|
|2021-01-11|A2|U4|
|2021-01-12|A2|U4|
|2021-01-15|A2|U5|
|2020-12-17|A2|U4|
|2020-12-25|A3|U6|
|2020-12-25|A3|U6|
|2020-12-25|A3|U6|
|2020-12-06|A3|U7|
|2020-12-06|A3|U6|
|2021-01-14|A3|U6|
|2021-02-07|A1|U1|
|2021-02-10|A1|U2|
|2021-02-01|A2|U4|
|2021-02-01|A2|U5|
|2020-12-05|A1|U8|

---

## RESPUESTA

```sql
SELECT
    account_id,
    COUNT(DISTINCT user_id) AS monthly_active_users
FROM sf_events
WHERE EXTRACT(YEAR FROM record_date) = 2021
  AND EXTRACT(MONTH FROM record_date) = 1
GROUP BY account_id;
```

---

## EXPLICACION

La consulta filtra primero los registros de enero de 2021 usando `EXTRACT` sobre `record_date`. Asi solo se consideran los eventos del periodo pedido.

Luego agrupa por `account_id` y aplica `COUNT(DISTINCT user_id)` para contar usuarios unicos por cuenta. Eso evita duplicar usuarios que tuvieron mas de un evento durante el mes.
