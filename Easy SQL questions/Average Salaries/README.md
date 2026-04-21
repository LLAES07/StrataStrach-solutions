# Average Salaries


## 📌 PROBLEMA

**[ENG]**
Compare each employee's salary with the average salary of the corresponding department.
Output the department, first name, and salary of employees along with the average salary of that department.

**[ESP]**

Compara el salario de cada empleado con el salario promedio correspondiente a su departamento. Muestra el departamento, el nombre del empleado y el salario junto con el salario promedio de cada departamento.

# TABLA

### employee


| id  | first_name | last_name | age | sex | employee_title | department | salary | target | bonus | email                | city       | address              | manager_id |
| --- | ---------- | --------- | --- | --- | -------------- | ---------- | ------ | ------ | ----- | -------------------- | ---------- | -------------------- | ---------- |
| 5   | Max        | George    | 26  | M   | Sales          | Sales      | 1300   | 200    | 150   | Max@company.com      | California | 2638 Richards Avenue | 1          |
| 13  | Katty      | Bond      | 56  | F   | Manager        | Management | 150000 | 0      | 300   | Katty@company.com    | Arizona    |                      | 1          |
| 11  | Richerd    | Gear      | 57  | M   | Manager        | Management | 250000 | 0      | 300   | Richerd@company.com  | Alabama    |                      | 1          |
| 10  | Jennifer   | Dion      | 34  | F   | Sales          | Sales      | 1000   | 200    | 150   | Jennifer@company.com | Alabama    |                      | 13         |
| 19  | George     | Joe       | 50  | M   | Manager        | Management | 100000 | 0      | 300   | George@company.com   | Florida    | 1003 Wyatt Street    | 1          |
| 18  | Laila      | Mark      | 26  | F   | Sales          | Sales      | 1000   | 200    | 150   | Laila@company.com    | Florida    | 3655 Spirit Drive    | 11         |
| 20  | Sarrah     | Bicky     | 31  | F   | Senior Sales   | Sales      | 2000   | 200    | 150   | Sarrah@company.com   | Florida    | 1176 Tyler Avenue    | 19         |

#  💻 REPSUESTA

```sql

SELECT
    department,
    first_name,
    salary,
    AVG(salary) OVER(partition by department) AS avg_salary

FROM 
    employee;

```

# 📊 Explicación

Para comparar cada salario de un empleado con el promedio de su departamento necesitamos por un lado tener los salarios promedio de cada departamento por cada fila correspondiente a cada persona que este en ese departamento. Que quiere decir eso que primero generamos una tabla con `department`, `first_name` y `salary` logrando con esto cada persona junto a su departamento con su salario e incluimos una ultima columna donde utilizamos una window function para poder calcular el promedio de los salarios del departamento tomando la columna de departamento. De esta forma podemos comparar cada sueldo de cada empleado ordenado con su departamento con su correspondiente promedio de departamento.


