# Workers With The Highest Salaries

## PROBLEMA

**[ENG]**
Management wants to analyze only employees with official job titles. Find the job titles of the employees with the highest salary. If multiple employees have the same highest salary, include all their job titles.

**[ESP]**
Management quiere analizar solo a los empleados con titulos oficiales. Encuentra el titulo del puesto de los empleados con el salario mas alto. Si varios empleados comparten el salario maximo, incluye todos sus titulos.

---

### TABLA

`worker`

|worker_id|first_name|last_name|salary|joining_date|department|
|---|---|---|---|---|---|
|1|Monika|Arora|100000|2014-02-20|HR|
|2|Niharika|Verma|80000|2014-06-11|Admin|
|3|Vishal|Singhal|300000|2014-02-20|HR|
|4|Amitah|Singh|500000|2014-02-20|Admin|
|5|Vivek|Bhati|500000|2014-06-11|Admin|
|6|Vipul|Diwan|200000|2014-06-11|Account|
|7|Satish|Kumar|75000|2014-01-20|Account|
|8|Geetika|Chauhan|90000|2014-04-11|Admin|

`title`

|worker_ref_id|worker_title|affected_from|
|---|---|---|
|1|Manager|2016-02-20|
|2|Executive|2016-06-11|
|8|Executive|2016-06-11|
|5|Manager|2016-06-11|
|4|Asst. Manager|2016-06-11|
|7|Executive|2016-06-11|
|6|Lead|2016-06-11|

---

## RESPUESTA

```sql
WITH ct1 AS (
    SELECT
        *,
        DENSE_RANK() OVER (ORDER BY salary DESC) AS rk
    FROM worker w
    INNER JOIN title t
        ON w.worker_id = t.worker_ref_id
)
SELECT DISTINCT
    worker_title
FROM ct1
WHERE rk = 1;
```

---

## EXPLICACION

Primero se unen `worker` y `title` para tener en una misma fila el salario y el titulo de cada empleado.

Luego `DENSE_RANK()` ordena por `salary` de mayor a menor y asigna el rango `1` a quienes tienen el salario maximo. Finalmente se filtra por `rk = 1` y se devuelven los titulos sin duplicados.
