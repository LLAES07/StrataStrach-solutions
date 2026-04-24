# Sorting By Second Character


**[ENG]**

You've been asked to arrange a column of random IDs in ascending alphabetical order based on their second character.


**[ESP]**

Te han solicitado arreglar una columna de ids aleatoreos en orden alfabeitco basado en su segúndo carácter.


### tabla
random_id


|id|
|---|
|2DQS4|
|2ABS5|
|2CBS6|
|2DYS7|
|2SUI8|
|2POI9|
|2PTY1|
|3DUU1|
|3ASD1|
|3TQS1|
|3CYS1|
|3CGY1|
|3CUY1|
|3NOS8|
|4DSS1|
|4AOS9|
|5TLS2|
|5NES1|
|5MQS2|
|5ZQS3|


# RESPUESTA

```sql

SELECT
  id
FROM random_id
ORDER BY substring(id,2,1)  ASC

```

# EXPLICACION

La logica consiste en extraer el segundo caracter de cada cadena y usarlo como criterio de ordenamiento. Una vez aplicada esa transformacion, las filas se ordenan alfabéticamente segun ese valor. Esto permite comparar palabras que comparten el mismo primer caracter.
