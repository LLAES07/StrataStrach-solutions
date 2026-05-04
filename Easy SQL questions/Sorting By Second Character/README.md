# Sorting By Second Character

**[ENG]**

You've been asked to arrange a column of random IDs in ascending alphabetical order based on their second character.

**[ESP]**

Te han solicitado arreglar una columna de ids aleatoreos en orden alfabeitco basado en su segundo caracter.

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

# 📊 Explicación

Para ordenar los IDs basándonos únicamente en su segundo carácter, utilizamos la función `substring(id, 2, 1)`. Esta función extrae una cadena de longitud 1 empezando desde la posición 2. Luego, aplicamos `ORDER BY` sobre este resultado en orden ascendente (`ASC`) para organizar la lista según el abecedario basándonos en ese carácter específico.

La clave de este ejercicio es que no se ordena por el valor completo de id, sino solo por su segundo caracter. Para extraer exactamente esa posicion se usa substring(id, 2, 1), que toma un caracter comenzando en la segunda posicion de cada cadena.

Una vez obtenido ese valor auxiliar, ORDER BY lo usa como criterio de ordenamiento ascendente. De esa forma los ids quedan acomodados alfabeticamente segun su segundo caracter, incluso si el primero o el resto del texto son diferentes.
