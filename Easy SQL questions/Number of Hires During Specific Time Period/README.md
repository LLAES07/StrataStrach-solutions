# Number of Hires During Specific Time Period


You have been asked to find the number of employees hired between the months of January and July in the year 2022 **inclusive**.

Your output should contain the number of employees hired in this given time frame.

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