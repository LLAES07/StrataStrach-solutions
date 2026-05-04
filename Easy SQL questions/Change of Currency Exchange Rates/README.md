# Change of Currency Exchange Rates

## 馃搶 PROBLEMA

**[ENG]**

You are given a list of exchange rates from various currencies to US Dollars (USD) in different months. Show how the exchange rate of all the currencies changed in the first half of 2020. Output the currency code and the difference between values of the exchange rate between July 1, 2020 and January 1, 2020.

**[ES]**


Te han dado una lista de tasas de cambio de diferentes monedas a d贸lares estadounidenses (USD) en diferentes meses. Muestra c贸mo cambi贸 la tasa de cambio de todas las monedas en la primera mitad de 2020. Muestra el c贸digo de moneda y la diferencia entre los valores de la tasa de cambio entre julio 1, 2020 y enero 1, 2020.

---

### Table

sf_exchange_rate



|source_currency|target_currency|exchange_rate|date|
|---|---|---|---|
|USD|USD|1|2020-01-01|
|EUR|USD|1.12|2020-01-01|
|GBP|USD|1.33|2020-01-01|
|INR|USD|0.01|2020-01-01|
|AUD|USD|0.7|2020-01-01|
|CAD|USD|0.77|2020-01-01|
|CHF|USD|1.03|2020-01-01|
|AED|USD|0.27|2020-01-01|
|SEK|USD|0.11|2020-01-01|
|EGP|USD|0.06|2020-01-01|
|KWD|USD|3.3|2020-01-01|
|PLN|USD|0.26|2020-01-01|
|UAH|USD|0.04|2020-01-01|
|USD|USD|1|2020-02-01|
|EUR|USD|1.11|2020-02-01|
|GBP|USD|1.32|2020-02-01|
|INR|USD|0.01|2020-02-01|
|AUD|USD|0.67|2020-02-01|
|CAD|USD|0.76|2020-02-01|
|CHF|USD|1.04|2020-02-01|
|AED|USD|0.27|2020-02-01|
|SEK|USD|0.1|2020-02-01|
|EGP|USD|0.06|2020-02-01|
|KWD|USD|3.29|2020-02-01|
|PLN|USD|0.26|2020-02-01|
|UAH|USD|0.04|2020-02-01|
|USD|USD|1|2020-03-01|
|EUR|USD|1.1|2020-03-01|
|GBP|USD|1.28|2020-03-01|
|INR|USD|0.01|2020-03-01|
|AUD|USD|0.65|2020-03-01|
|CAD|USD|0.75|2020-03-01|
|CHF|USD|1.04|2020-03-01|
|AED|USD|0.27|2020-03-01|
|SEK|USD|0.1|2020-03-01|
|EGP|USD|0.06|2020-03-01|
|KWD|USD|3.26|2020-03-01|
|PLN|USD|0.25|2020-03-01|
|UAH|USD|0.04|2020-03-01|
|USD|USD|1|2020-04-01|
|EUR|USD|1.09|2020-04-01|
|GBP|USD|1.24|2020-04-01|
|INR|USD|0.01|2020-04-01|
|AUD|USD|0.61|2020-04-01|

# 馃捇 RESPUESTA

```sql

SELECT 
    a1.source_currency,
    (a2.exchange_rate - a1.exchange_rate) AS diferencia
FROM sf_exchange_rate a1
JOIN sf_exchange_rate a2 
    ON a1.source_currency = a2.source_currency
# ?? Explicaci髇

Para calcular la diferencia en la tasa de cambio, unimos la tabla sf_exchange_rate consigo misma (JOIN). La primera instancia (1) filtra los datos del 1 de enero de 2020, mientras que la segunda (2) filtra los del 1 de julio de 2020. Al unir ambas por el c骴igo de moneda (source_currency), podemos restar directamente el valor inicial del valor final para obtener la variaci髇 exacta en la primera mitad del a駉.
