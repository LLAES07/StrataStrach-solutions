# Find unique IATA codes


**[ENG]**

What are the unique airport codes for all origin airports in the dataset? (e.g., LAX, JFK, SFO)


**[ESP]**






### TABLA




# RESPUESTA

```sql
select DISTINCT dest from us_flights;

```