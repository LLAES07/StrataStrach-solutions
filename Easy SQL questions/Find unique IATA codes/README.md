# Find Unique IATA Codes

## PROBLEMA

**[ENG]**
What are the unique airport codes for all origin airports in the dataset? For example: `LAX`, `JFK`, `SFO`.

**[ESP]**
Cuales son los codigos IATA unicos de todos los aeropuertos de origen en el dataset. Por ejemplo: `LAX`, `JFK`, `SFO`.

---

### TABLA

`us_flights`

|flight_date|unique_carrier|flight_num|origin|dest|arr_delay|cancelled|distance|carier_delay|weather_delay|late_aircraft_delay|nas_delay|security_delay|actual_elapsed_time|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|2015-01-02|VX|231|ORD|LAX|33|0|1744|33|0|0|0|0|278|
|2015-01-02|EV|4736|CLE|EWR|-29|0|404|||||83|||
|2015-01-09|US|2195|LGA|DCA|-7|0|214|||||82|||
|2015-01-05|EV|5586|ATL|FAY|-9|0|331|||||72|||
|2015-01-02|B6|1022|PBI|BOS|-23|0|1197|||||162|||
|2015-01-06|DL|2270|MSP|PIT|-12|0|726|||||111|||
|2015-01-11|B6|161|JFK|SMF|2|0|2521|||||374|||
|2015-01-06|B6|1016|FLL|JAX|-15|0|319|||||71|||
|2015-01-02|AA|272|SFO|MIA|14|0|2585|||||333|||
|2015-01-08|DL|2226|FLL|ATL|-2|0|581|||||120|||
|2015-01-03|AA|1151|DEN|DFW|174|0|641|43|0|4|127|0|247|
|2015-01-02|B6|1459|BDL|FLL|-4|0|1173|||||190|||
|2015-01-08|HA|42|OGG|SFO|-14|0|2338|||||278|||
|2015-01-02|US|607|LAS|PHL|-27|0|2176|||||249|||
|2015-01-04|UA|1205|KOA|LAX|7|0|2504|||||320|||
|2015-01-15|AA|999|SEA|JFK|0|0|2176|||||||| 

---

## RESPUESTA

```sql
SELECT DISTINCT
    origin
FROM us_flights;
```

---

## EXPLICACION

La columna que contiene los aeropuertos de origen es `origin`, asi que solo necesitamos consultarla directamente.

`DISTINCT` elimina repetidos y deja una lista unica de codigos IATA de salida.
