# Titanic Survivors and Non-Survivors


**[ENG]**

Make a report showing the number of survivors and non-survivors by passenger class. Classes are categorized based on the `pclass` value as:

• First class: `pclass = 1` • Second class: `pclass = 2` • Third class: `pclass = 3`

Output the number of survivors and non-survivors by each class.

**[ESP]**

Haz un reporte mostrando el numero de sobrevivientes y no sobrevivientes según la clase de cada pasajero. Las clases estan categorizadas segun el valor de `pclass` como:

• Primera clase: `pclass = 1` • Segunda clase: `pclass = 2` • Tercera clase: `pclass = 3`

Muestra el numero de sobrevivientes y no sobrevivientes por cada clase.




### Table

titanic

# RESPUESTA

```sql
SELECT
    survived, 

    -- Case para las condiciones indicadas
    SUM(CASE
            WHEN pclass = 1 THEN 1  END) 
    AS first_class,
    SUM(CASE
            WHEN pclass = 2 THEN 1  END) 
    AS second_class,
    SUM(CASE
            WHEN pclass = 3 THEN 1  END) 
    AS third_class
FROM 
    titanic
GROUP BY
    survived

```