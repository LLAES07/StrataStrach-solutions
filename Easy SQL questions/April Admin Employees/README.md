Find the number of employees working in the Admin department that joined in April or later, in any year.

# Tabla

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
| 9         | Agepi      | Argon     | 90000  | 2015-04-10   | Admin      |
| 10        | Moe        | Acharya   | 65000  | 2015-04-11   | HR         |
| 11        | Nayah      | Laghari   | 75000  | 2014-03-20   | Account    |


# RESPUESTA

```sql

SELECT 
    COUNT(DISTINCT worker_id) AS total_admin_workers
FROM worker
WHERE
    EXTRACT(MONTH FROM joining_date) >= 4 AND
    department LIKE 'Admin';
```