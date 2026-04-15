# Employees' Without Annual Review

**[ENG]**

Return all employees who have never had an annual review. Your output should include the employee's first name, last name, hiring date, and termination date. List the most recently hired employees first.

**[ESP]**

Devuelve todos los empleados que nunca han tenido una revisión anual. Tu salida debe incluir el nombre y apellido del empleado, la fecha de contratación y la fecha de terminación. Lista a los empleados más recientemente contratados primero.

### TABLA

uber_employees

|first_name|last_name|id|hire_date|termination_date|salary|
|---|---|---|---|---|---|
|Bob|Smith|1|2009-02-03|2016-01-01|10000|
|Joe|Jarrod|2|2009-02-03||20000|
|Nancy|Soley|3|2009-02-03||30000|
|Keith|Widjaja|4|2009-04-15|2014-01-01|20000|
|Kelly|Smalls|5|2009-02-03||20000|
|Frank|Nguyen|6|2009-06-20|2015-05-01|60000|
|Moe|Down|7|2009-07-20|2017-04-15|83668|
|Joe|Carlos|8|2009-08-13||24133|
|Karen|Adam|9|2009-09-25||73794|
|Smith|John|10|2009-10-09||40658|
|Nataly|Joe|11|2009-11-22||62930|
|Suzan|Power|12|2009-12-23|2017-05-22|32565|
|Bob|Marely|13|2010-01-20|2017-07-20|88355|
|Mike|Tayson|14|2010-02-03|2017-09-25|65915|
|Zuo|Yang|15|2010-02-12|2017-09-25|66808|
|Armin|Roberson|16|2010-03-20|2017-09-25|97364|
|Kale|Matteo|17|2010-04-15|2017-11-22|99235|
|Rahul|Thomas|18|2010-05-22|2018-04-15|72014|
|Kumar|Joshua|19|2010-07-20|2018-05-20|97559|
|Joseph|Charles|20|2010-08-13|2018-05-22|11732|
|Patil|Keera|21|2010-09-25|2018-08-13|33185|



uber_annual_review


|id|emp_id|review_date|
|---|---|---|
|1|1|2013-01-20|
|2|1|2015-01-20|
|3|2|2013-02-03|
|4|2|2015-02-03|
|5|2|2017-02-03|
|6|2|2019-02-03|
|7|2|2021-02-03|
|8|3|2013-03-20|
|9|3|2015-03-20|
|10|3|2017-03-20|
|11|3|2017-03-20|
|12|3|2019-03-20|
|13|4|2013-04-15|
|14|5|2013-05-22|
|15|5|2015-05-22|
|16|5|2017-05-22|
|17|5|2019-05-22|
|18|6|2013-06-20|
|19|7|2013-07-20|


# RESPUESTA

```sql

SELECT 
    e.first_name, 
    e.last_name, 
    e.hire_date, 
    e.termination_date
FROM uber_employees e
LEFT JOIN uber_annual_review r ON e.id = r.emp_id
WHERE r.emp_id IS NULL
ORDER BY e.hire_date DESC;


```

# 📊 Explicación

Para entender esta consulta de forma sencilla, imagina que tienes dos listas. En una están absolutamente todos los empleados de la empresa (`uber_employees`) y en la otra está el registro de todas las revisiones anuales que se han hecho (`uber_annual_review`).

1. **El `LEFT JOIN`**: Lo que hacemos aquí es decirle a la base de datos "tráeme a todos los empleados de la primera lista y, si encuentras su nombre en la segunda, pégales al lado su revisión". Como estamos usando un `LEFT JOIN`, nos va a traer a todos los empleados sin excepción. Si un empleado no tiene ninguna revisión registrada, la base de datos no lo borra, simplemente deja esos espacios en blanco (les pone un valor `NULL`).
2. **El `WHERE r.emp_id IS NULL`**: Aquí está el verdadero truco. Con esta línea filtramos toda la información y le decimos que nos deje únicamente a los empleados que se quedaron con esos "espacios en blanco", es decir, aquellos que *nunca* aparecieron en la lista de revisiones anuales.
3. **El `ORDER BY e.hire_date DESC`**: Ya por último, la instrucción nos pide listar a los empleados contratados más recientemente primero. Para esto simplemente ordenamos la lista por la fecha de contratación (`hire_date`) de mayor a menor usando `DESC`, para que los más nuevos salgan hasta arriba.
old_string:
ORDER BY e.hire_date DESC;