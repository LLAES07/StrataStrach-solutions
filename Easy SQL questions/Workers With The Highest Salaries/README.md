Management wants to analyze only employees with official job titles. Find the job titles of the employees with the highest salary. If multiple employees have the same highest salary, include all their job titles.

## Tablas


### worker
| worker_id | first_name | last_name | salary | joining_date | department |
| --------- | ---------- | --------- | ------ | ------------ | ---------- |
| 1         | Monika     | Arora     | 100000 | 2014-02-20   | HR         |
| 2         | Niharika   | Verma     | 80000  | 2014-06-11   | Admin      |
| 3         | Vishal     | Singhal   | 300000 | 2014-02-20   | HR         |
| 4         | Amitah     | Singh     | 500000 | 2014-02-20   | Admin      |
| 5         | Vivek      | Bhati     | 500000 | 2014-06-11   | Admin      |
| 6         | Vipul      | Diwan     | 200000 | 2014-06-11   | Account    |
| 7         | Satish     | Kumar     | 75000  | 2014-01-20   | Account    |
| 8         | Geetika    | Chauhan   | 90000  | 2014-04-11   | Admin      |

### title


| worker_ref_id | worker_title  | affected_from |
| ------------- | ------------- | ------------- |
| 1             | Manager       | 2016-02-20    |
| 2             | Executive     | 2016-06-11    |
| 8             | Executive     | 2016-06-11    |
| 5             | Manager       | 2016-06-11    |
| 4             | Asst. Manager | 2016-06-11    |
| 7             | Executive     | 2016-06-11    |
| 6             | Lead          | 2016-06-11    |



# RESPUESTA


```sql
WITH ct1 AS (
    -- Une ambas tablas y usa dense rank para rankear por salaria si hay salarios con el mismo valor comparten el mismo ranking
    SELECT
        *,
        DENSE_RANK() OVER(ORDER BY salary DESC) AS rk
    FROM worker w
    INNER JOIN title t
        ON w.worker_id = t.worker_ref_id
)

-- Query final que filtra por el ranking 1
SELECT
    DISTINCT worker_title
FROM ct1
WHERE
    rk =1
```