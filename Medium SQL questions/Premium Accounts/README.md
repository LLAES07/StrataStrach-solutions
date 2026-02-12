# Premium Accounts

**[ENG]**


You have a dataset that records daily active users for each premium account. A premium account appears in the data every day as long as it remains premium. However, some premium accounts may be temporarily discounted, meaning they are not actively paying — this is indicated by a final_price of 0.


For each date, count the number of premium accounts that were actively paying on that day. Then, track how many of those same accounts are still premium and actively paying exactly 7 days later, if that later date exists in the dataset. Return results for the first 7 dates in the dataset.


Output three columns:
•   The date of initial calculation.
•   The number of premium accounts that were actively paying on that day.
•   The number of those accounts that remain premium and are still paying after 7 days.


**[ESP]**


Tiene un conjunto de datos que registra los usuarios activos diarios para cada cuenta premium. Una cuenta premium aparece en los datos todos los días mientras siga siendo premium. Sin embargo, algunas cuentas premium pueden tener un descuento temporal, lo que significa que no están pagando activamente; esto se indica con un precio_final de 0.


Para cada fecha, cuente la cantidad de cuentas premium que estaban pagando activamente ese día. Luego, realice un seguimiento de cuántas de esas mismas cuentas siguen siendo premium y pagan activamente exactamente 7 días después, si esa fecha posterior existe en el conjunto de datos. Devuelve resultados para las primeras 7 fechas del conjunto de datos.


Salida de tres columnas:
• La fecha del cálculo inicial.
• La cantidad de cuentas premium que estaban pagando activamente ese día.
• El número de aquellas cuentas que siguen siendo premium y siguen pagando después de 7 días.

# TABLA

### premium_accounts_by_day


| entry_date | premium_paid_accounts | premium_paid_accounts_after_7d |
| ---------- | --------------------- | ------------------------------ |
| 2022-02-07 | 2                     | 2                              |
| 2022-02-08 | 3                     | 2                              |
| 2022-02-09 | 3                     | 2                              |
| 2022-02-10 | 4                     | 3                              |
| 2022-02-11 | 4                     | 1                              |

# RESPUESTA

```SQL

SELECT
    a.
    entry_date,
    COUNT(a.account_id) premium_paid_accounts,
    COUNT(b.account_id) premium_paid_accounts_after_7d
FROM premium_accounts_by_day a
LEFT JOIN premium_accounts_by_day b ON a.account_id = b.account_id
AND (b.entry_date - a.entry_date) = 7 AND b.final_price > 0
WHERE a.final_price > 0
GROUP BY a.entry_date
ORDER BY a.entry_date
LIMIT 7

```