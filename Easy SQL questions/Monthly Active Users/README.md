# Monthly Active Users

**[ENG]**
Find the monthly active users for January 2021 for each account. Your output should have account_id and the monthly count for that account.

**[ESP]**

Encuentra los usuarios activos mensualmente para enero del 2021 para cada cuenta. Muestra el account_id y el recuento mensual para esa cuenta.

---

### TABLA

sf_events

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

# RESPUESTA

```sql
SELECT 
    account_id,
    COUNT(DISTINCT user_id) AS monthly_active_users
FROM sf_events
WHERE EXTRACT(YEAR FROM record_date) = 2021 AND EXTRACT(MONTH FROM record_date) = 1
GROUP BY account_id;
```

# EXPLICACION

El primer paso es filtrar la tabla para conservar solamente los eventos de enero de 2021. Eso se logra con EXTRACT(YEAR FROM record_date) y EXTRACT(MONTH FROM record_date), que separan el ano y el mes de cada fecha y permiten quedarnos exactamente con el periodo solicitado.

Despues la consulta agrupa por ccount_id porque el resultado debe mostrarse por cuenta. Dentro de cada grupo se usa COUNT(DISTINCT user_id) para contar usuarios activos sin duplicar a quienes hayan tenido varios eventos durante el mismo mes.

Asi se obtiene el numero real de usuarios activos mensuales por cuenta y se evita inflar el total con acciones repetidas del mismo usuario.
