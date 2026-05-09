# Total Employees in Each Department



# ðŸ“Œ PROBLEMA

**[ENG]**

Find the number of employees in each department.


Output the department name along with the corresponding number of employees.

**[ESP]**

Encuentra el numero de empleados por cada departamento.

Muestra el nombre del departamento junto con el numero de empleados.




# TABLA

**worker**

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
|9|Agepi|Argon|90000|2015-04-10|Admin|
|10|Moe|Acharya|65000|2015-04-11|HR|
|11|Nayah|Laghari|75000|2014-03-20|Account|
|12|Jai|Patel|85000|2014-03-21|HR|
|13|Jura|Jomun|980000|2013-05-20|HR|

# ðŸ’» REPSUESTA

```sql

SELECT
    department,
    SUM(worker_id) AS total_workers
FROM worker
GROUP BY department

```

# ðŸ§  EXPLICACIÃ“N


Nos solicitan por cada departamento el numero total de empleados. Primero agrupamos por departamento y sumamos todos los registros que cada departamento tenga.
## EXPLICACION

`GROUP BY department` crea un grupo por cada departamento y `COUNT(employee_id)` devuelve cuantos empleados hay en cada uno.

Con esto la consulta resume la tabla completa en una sola fila por area. Es una forma simple de obtener el tamanio de cada departamento sin perder la relacion entre empleado y departamento.
