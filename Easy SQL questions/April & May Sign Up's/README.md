# April & May Sign Up's

## 📌 PROBLEMA


**[ENG]**
You have been asked to get a list of all the sign up IDs with transaction start dates in either April or May.

Since a sign up ID can be used for multiple transactions only output the unique ID.

Your output should contain a list of non duplicated sign-up IDs.

**[ESP]**

Se te ha solicitado obtener una lista de todos los ID de registro (sign-up IDs) cuyas fechas de inicio de transacción sean en abril o mayo.

Dado que un mismo ID de registro puede utilizarse para múltiples transacciones, solo debes mostrar el ID único.

Tu resultado debe contener una lista de IDs de registro sin duplicados.

### Table

transactions

| transaction_id | signup_id | transaction_start_date | amt   |
| -------------- | --------- | ---------------------- | ----- |
| 1              | 100       | 2020-04-30             | 24.9  |
| 2              | 101       | 2020-04-16             | 24.9  |
| 3              | 102       | 2020-04-28             | 9.9   |
| 4              | 102       | 2020-05-28             | 9.9   |
| 5              | 102       | 2020-06-27             | 9.9   |
| 6              | 102       | 2020-07-27             | 9.9   |
| 7              | 102       | 2020-08-26             | 9.9   |
| 8              | 102       | 2020-09-25             | 9.9   |
| 9              | 103       | 2020-04-11             | 24.9  |
| 10             | 104       | 2020-05-01             | 24.9  |
| 11             | 105       | 2020-04-21             | 9.9   |
| 12             | 105       | 2020-05-21             | 9.9   |
| 13             | 105       | 2020-06-20             | 9.9   |
| 14             | 106       | 2020-04-17             | 109.9 |
| 15             | 107       | 2020-04-14             | 109.9 |
| 16             | 108       | 2020-04-28             | 9.9   |
| 17             | 108       | 2020-05-28             | 9.9   |
| 18             | 109       | 2020-04-18             | 24.9  |
| 19             | 109       | 2020-07-17             | 24.9  |

# 💻 RESPUESTA

```sql
select 
    -- Deja solo los valores únicos
    DISTINCT
        signup_id
from transactions
WHERE
    -- Filtra por las transacciones entre abril y mayo
    EXTRACT(MONTH FROM transaction_start_date) IN (4,5)

```
# 📊 Explicación

El primer paso es filtrar nuestra tabla por abril y mayo paraa que solo tengamos como target estos registros. Una vez realizado el filtro dejamos solo las `singup_id` únicas.
