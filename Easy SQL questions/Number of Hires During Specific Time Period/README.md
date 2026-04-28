# Number of Hires During Specific Time Period

**[ENG]**

You have been asked to find the number of employees hired between the months of January and July in the year 2022 **inclusive**.

Your output should contain the number of employees hired in this given time frame.

**[ES]**

Te han pedido encontrar el numero de empleados contratados entre los meses de enero y julio inclusive en el año 2022. 
Tu output debe contar con el número de empleados contratados en este tiempo.



### Table

employees

# RESPUESTA

```sql

SELECT
    COUNT(id) AS total_employees_hired
FROM employees
WHERE
    joining_date >= '2022-06-01' AND
    joining_date >= '2022-07-31'

```

# EXPLICACION

La consulta cuenta los empleados que cumplen con el rango de fechas indicado en el `WHERE`. La idea es filtrar la tabla `employees` para quedarse solo con las contrataciones dentro del periodo solicitado y luego usar `COUNT(id)` para devolver un unico total con la cantidad de empleados contratados.
