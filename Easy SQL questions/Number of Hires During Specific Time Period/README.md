# Number of Hires During Specific Time Period

**[ENG]**

You have been asked to find the number of employees hired between the months of January and July in the year 2022 **inclusive**.

Your output should contain the number of employees hired in this given time frame.

**[ES]**

Te han pedido encontrar el numero de empleados contratados entre los meses de enero y julio inclusive en el ano 2022. 
Tu output debe contar con el numero de empleados contratados en este tiempo.

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

La idea general de la consulta es filtrar las contrataciones que caen dentro del periodo pedido y, sobre ese subconjunto, contar cuantas filas existen. `COUNT(id)` devuelve un unico valor con la cantidad total de empleados contratados en el rango seleccionado.

El papel del `WHERE` es delimitar el intervalo de fechas para que solo entren las incorporaciones del ano 2022 entre enero y julio inclusive. Despues de aplicar ese filtro, ya no hace falta agrupar nada porque el ejercicio solo solicita un total final.
