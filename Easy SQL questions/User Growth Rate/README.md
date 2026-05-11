# User Growth Rate

## PROBLEMA

**[ENG]**
Find the growth rate of active users from Dec 2020 to Jan 2021 for each account. The growth rate is defined as the number of users in January 2021 divided by the number of users in Dec 2020. Output the `account_id` and growth rate.

**[ESP]**
Encuentra la tasa de crecimiento de usuarios activos de diciembre de 2020 a enero de 2021 para cada cuenta. La tasa de crecimiento se define como el numero de usuarios de enero de 2021 dividido por el numero de usuarios de diciembre de 2020. Muestra el `account_id` y la tasa de crecimiento.

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
    SUM(CASE WHEN record_date >= '2021-01-01' AND record_date <= '2021-01-31' THEN 1 ELSE 0 END) * 1.0 /
    SUM(CASE WHEN record_date >= '2020-12-01' AND record_date <= '2020-12-31' THEN 1 ELSE 0 END) AS growth_rate
FROM sf_events
GROUP BY account_id;
```

---

## EXPLICACION

La consulta separa los registros de enero de 2021 y diciembre de 2020 mediante expresiones `CASE`. Cada suma cuenta cuantas filas caen dentro de cada periodo para una misma cuenta.

Despues divide el total de enero entre el total de diciembre para obtener `growth_rate`. El resultado final se muestra por `account_id`.
