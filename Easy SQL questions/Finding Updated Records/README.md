# Finding Updated Records

## PROBLEMA

**[ENG]**
We have a table with employees and their salaries, however, some of the records are old and contain outdated salary information. Find the current salary of each employee assuming that salaries increase each year. Output their id, first name, last name, department ID, and current salary. Order your list by employee ID in ascending order.

**[ESP]**
Tenemos una tabla con empleados y sus salarios, pero algunos registros son antiguos y contienen informacion salarial desactualizada. Encuentra el salario actual de cada empleado asumiendo que el salario aumenta cada ano. Muestra su id, `first_name`, `last_name`, `department_id` y salario actual. Ordena la lista por `id` en orden ascendente.

---

### TABLA

`ms_employee_salary`

|id|first_name|last_name|salary|department_id|
|---|---|---|---|---|
|1|Todd|Wilson|110000|1006|
|1|Todd|Wilson|106119|1006|
|2|Justin|Simon|128922|1005|
|2|Justin|Simon|130000|1005|
|3|Kelly|Rosario|42689|1002|
|4|Patricia|Powell|162825|1004|
|4|Patricia|Powell|170000|1004|
|5|Sherry|Golden|44101|1002|
|6|Natasha|Swanson|79632|1005|
|6|Natasha|Swanson|90000|1005|

---

## RESPUESTA

```sql
SELECT
    a.id,
    a.first_name,
    a.last_name,
    a.department_id,
    (
        SELECT MAX(b.salary)
        FROM ms_employee_salary b
        WHERE a.id = b.id
    ) AS current_salary
FROM ms_employee_salary a
GROUP BY a.id, a.first_name, a.last_name, a.department_id
ORDER BY id ASC;
```

---

## EXPLICACION

La consulta agrupa los registros por empleado usando sus datos identificatorios. Asi se obtiene una sola fila por cada persona.

Dentro del `SELECT`, una subconsulta busca el `MAX(salary)` para el mismo `id`. Como el enunciado indica que el salario aumenta con el tiempo, el valor maximo representa el salario actual del empleado.
