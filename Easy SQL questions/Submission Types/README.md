# Submission Types

## PROBLEMA

**[ENG]**
Write a query that returns the user ID of all users that have created at least one `Refinance` submission and at least one `InSchool` submission.

**[ESP]**
Escribe una consulta que devuelva el `user_id` de todos los usuarios que hayan creado al menos una submission de tipo `Refinance` y al menos una de tipo `InSchool`.

---

### TABLA

`loans`

|id|user_id|created_at|status|type|
|---|---|---|---|---|
|1|100|2017-04-21|prequal_completd_offer|Refinance|
|2|100|2017-04-27|offer_accepted|Refinance|
|3|101|2017-04-22|prequal_completd_no_offer|Refinance|
|4|101|2017-04-23|offer_accepted|Refinance|
|5|101|2017-04-25|offer_accepted|Personal|
|6|102|2017-04-27|offer_accepted|InSchool|
|7|107|2017-04-27|prequal_response_received|Personal|
|8|108|2017-04-21|form_in_progress|Refinance|
|9|108|2017-04-27|offer_accepted|Refinance|
|10|108|2017-04-27|prequal_response_received|InSchool|
|11|100|2015-04-21|prequal_completd_offer|Refinance|

---

## RESPUESTA

```sql
WITH totals AS (
    SELECT
        user_id,
        SUM(CASE WHEN type = 'Refinance' THEN 1 ELSE 0 END) AS refinance_total,
        SUM(CASE WHEN type = 'InSchool' THEN 1 ELSE 0 END) AS inschool_total
    FROM loans
    GROUP BY user_id
)
SELECT
    user_id
FROM totals
WHERE refinance_total > 0
  AND inschool_total > 0;
```

---

## EXPLICACION

La CTE agrupa por `user_id` y cuenta por separado cuantas submissions tiene cada usuario de tipo `Refinance` y cuantas de tipo `InSchool`.

Despues la consulta principal filtra a los usuarios cuyos dos conteos son mayores que cero. Asi solo permanecen quienes tienen al menos una submission de cada tipo.
