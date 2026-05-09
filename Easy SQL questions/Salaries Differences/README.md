# Salaries Differences


**[ENG]**

Calculates the difference between the highest salaries in the marketing and engineering departments. Output just the absolute difference in salaries.

**[ES]**

Calcula la diferencia entre los salarios mas altos de los departamentos de marketing e ingenieria. Muestra solo la diferencia absoluta de salarios.

# TABLAS

#### db_employee

| id    | first_name | last_name | salary | department_id |
| ----- | ---------- | --------- | ------ | ------------- |
| 10301 | Keith      | Morgan    | 27056  | 2             |
| 10302 | Tyler      | Booth     | 32199  | 3             |
| 10303 | Clifford   | Nguyen    | 32165  | 2             |
| 10304 | Mary       | Jones     | 49488  | 3             |
| 10305 | Melissa    | Lucero    | 27024  | 3             |
| 10306 | Ashley     | Li        | 28516  | 4             |
| 10307 | Joseph     | Solomon   | 19945  | 1             |
| 10308 | Anthony    | Sanchez   | 43801  | 3             |
| 10309 | Katherine  | Huffman   | 12984  | 4             |
| 10310 | Dawn       | Foley     | 28902  | 2             |

#### db_dept

| id  | department     |
| --- | -------------- |
| 1   | engineering    |
| 2   | human resource |
| 3   | operation      |
| 4   | marketing      |
| 5   | sales          |
| 6   | customer care  |


```sql

SELECT
    MAX(CASE
            WHEN d.department = 'marketing' THEN salary ELSE 0 END) - 
        
    MAX(CASE
            WHEN d.department = 'engineering' THEN salary ELSE 0 END) AS diferencia
FROM db_employee e
INNER JOIN db_dept d
    ON e.department_id = d.id


```

# EXPLICACION

Primero se unen empleados y departamentos para poder identificar a que departamento pertenece cada salario. Luego se usa agregacion condicional con `MAX(CASE WHEN ...)` para obtener el salario mas alto de marketing y el salario mas alto de engineering en la misma fila, y finalmente se resta un valor contra el otro para devolver la diferencia.

El truco esta en convertir dos grupos distintos en columnas comparables dentro de un mismo resultado. Asi la consulta entrega directamente la diferencia salarial entre ambos departamentos.
