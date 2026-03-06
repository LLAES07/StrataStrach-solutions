# Find business types present in the dataset



**[ENG]**

Find business types present in the dataset.




**[ESP]**


Encuentra los tipos de negocios presentes en el conjunto de datos.









### TABLA

google_adwords_earnings

|business_type|business_name|n_employees|year|adwords_earnings|
|---|---|---|---|---|
|handyman|Golden Solutions|2|2018|81|
|handyman|Red Enterprises|10|2018|110|
|media|Sunny Services|10000|2018|123456789|
|handyman|Golden Hub|5000|2018|1001001|
|handyman|Golden Group|2|2018|150|
|handyman|Lucky Solutions|10|2018|87|
|handyman|Blue Ventures|1500|2018|5040032|
|transport|Sunny Enterprises|3200|2018|7865490|
|handyman|Bright Group|10|2018|55|
|handyman|Blue Hub|2|2018|130|
|handyman|Sunny Hub|10|2019|80|
|handyman|Lucky Enterprises|2|2020|16|
|handyman|Happy Group|5|2018|130|
|handyman|Red Solutions|10|2019|55|
|handyman|Swift Labs|7|2020|182|


# RESPUESTA

```sql


select DISTINCT business_type from google_adwords_earnings;



```