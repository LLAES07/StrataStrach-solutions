# Host Popularity Rental Prices

**[ENG]**


You are given a table named `airbnb_host_searches` that contains listings shown to users during Airbnb property searches. Each record represents a property listing (not the user's search query). Determine the minimum, average, and maximum rental prices for each host popularity rating based on the property's `number_of_reviews`.

The host’s popularity rating is defined as below: • 0 reviews: "New" • 1 to 5 reviews: "Rising" • 6 to 15 reviews: "Trending Up" • 16 to 40 reviews: "Popular" • More than 40 reviews: "Hot"

Tip: The `id` column in the table refers to the listing ID.

Output host popularity rating and their minimum, average and maximum rental prices. Order the solution by the minimum price.


**[ESP]**


Se te da una tabla llamada `airbnb_host_searches' que contiene listas mostrada a los usuarios durante las búsquedas de Airbnb de propiedades. Cada registro representa una lista de propiedades (no la consulta del usuario). Determina el minimo, promedio y maximos precios de renta para cada nivel de popularidad de los hots basado en el numero de reviews de la propiedad.

El score de popularidad es definido como • 0 reviews: "New" • 1 to 5 reviews: "Rising" • 6 to 15 reviews: "Trending Up" • 16 to 40 reviews: "Popular" • More than 40 reviews: "Hot"

Pista: La columna id en la tabla se refiere a las ids listadas.

Muestra el rating de popularidad del host y su minimo, promedio y maximas precios de rente. Ordena la solución por el precio menor.

### Table


|id|price|property_type|room_type|amenities|accommodates|bathrooms|bed_type|cancellation_policy|cleaning_fee|city|host_identity_verified|host_response_rate|host_since|neighbourhood|number_of_reviews|review_scores_rating|zipcode|bedrooms|beds|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|8284881|621.46|House|Entire home/apt|{TV,"Cable TV",Internet,"Wireless Internet","Air conditioning",Pool,Kitchen,"Free parking on premises",Gym,"Hot tub","Indoor fireplace",Heating,"Family/kid friendly",Washer,Dryer,"Smoke detector","Carbon monoxide detector","First aid kit","Safety card","Fire extinguisher",Essentials,Shampoo,"24-hour check-in",Hangers,"Hair dryer",Iron,"Laptop friendly workspace"}|8|3|Real Bed|strict|TRUE|LA|f|100%|2016-11-01|Pacific Palisades|1||90272|4|6|
|8284882|621.46|House|Entire home/apt|{TV,"Cable TV",Internet,"Wireless Internet","Air conditioning",Pool,Kitchen,"Free parking on premises",Gym,"Hot tub","Indoor fireplace",Heating,"Family/kid friendly",Washer,Dryer,"Smoke detector","Carbon monoxide detector","First aid kit","Safety card","Fire extinguisher",Essentials,Shampoo,"24-hour check-in",Hangers,"Hair dryer",Iron,"Laptop friendly workspace"}|8|3|Real Bed|strict|TRUE|LA|f|100%|2016-11-01|Pacific Palisades|1||90272|4|6|
|9479348|598.9|Apartment|Entire home/apt|{"Wireless Internet","Air conditioning",Kitchen,Heating,"Smoke detector","Carbon monoxide detector",Essentials,Shampoo,Hangers,Iron,"translation missing: en.hosting_amenity_49","translation missing: en.hosting_amenity_50"}|7|2|Real Bed|strict|FALSE|NYC|f|100%|2017-07-03|Hell's Kitchen|1|60|10036|3|4|
|8596057|420.47|House|Private room|{"Wireless Internet","Air conditioning",Pool,Kitchen,"Free parking on premises",Breakfast,"Family/kid friendly",Washer,Dryer,Essentials,Shampoo,Hangers,"Hair dryer","Self Check-In","Doorman Entry"}|1|2|Real Bed|flexible|FALSE|LA|f|100%|2016-04-20||0||91748|1|1|
|11525500|478.75|Apartment|Entire home/apt|{"Wireless Internet","Air conditioning",Heating,Washer,Dryer,Essentials,"Laptop friendly workspace",Microwave,Refrigerator,Dishwasher,"Dishes and silverware","Cooking basics",Oven,Stove,"Host greets you"}|2|1|Real Bed|flexible|TRUE|NYC|f|100%|2017-10-07|Williamsburg|2|100|11206|1|1|
|533884|662.01|Apartment|Entire home/apt|{TV,Internet,"Wireless Internet","Air conditioning",Kitchen,"Pets allowed",Heating,"Family/kid friendly",Washer,Dryer,Shampoo,"24-hour check-in",Hangers,"Hair dryer","Laptop friendly workspace"}|6|1|Real Bed|flexible|FALSE|SF|f||2016-01-20|Cow Hollow|0||94123|3|3|
|1404510|534.71|Townhouse|Entire home/apt|{TV,"Wireless Internet",Kitchen,"Free parking on premises","Indoor fireplace",Heating,"Family/kid friendly",Washer,Dryer,"Smoke detector","First aid kit","Fire extinguisher",Essentials,Shampoo,Hangers,"Hair dryer",Iron,"Laptop friendly workspace"}|6|2|Real Bed|moderate|TRUE|LA|t|100%|2015-09-02|West Los Angeles|10|95|90025|3|3|
|4691130|444.27|House|Private room|{TV,"Wireless Internet","Air conditioning",Pool,Kitchen,"Free parking on premises",Breakfast,Heating,"Family/kid friendly",Washer,Dryer,"Smoke detector","Carbon monoxide detector","First aid kit",Essentials,Shampoo,"Lock on bedroom door",Hangers,"Hair dryer",Iron,"Laptop friendly workspace"}|2|1|Real Bed|flexible|TRUE|LA|t|0%|2013-10-28||0||91324|1|1|
|16449480|468.21|Apartment|Private room|{TV,"Cable TV",Internet,"Wireless Internet","Air conditioning",Kitchen,"Smoking allowed","Pets allowed",Doorman,Elevator,Heating,Washer,Dryer,"Smoke detector","Fire extinguisher",Essentials,Shampoo}|2|1|Real Bed|moderate|TRUE|NYC|f|100%|2012-03-26|East Harlem|4|90|10029|1|1|
|12513361|555.68|Apartment|Entire home/apt|{TV,"Wireless Internet","Air conditioning","Smoke detector","Carbon monoxide detector",Essentials,"Lock on bedroom door",Hangers,Iron}|2|1|Real Bed|flexible|FALSE|NYC|t|89%|2015-11-18|East Harlem|3|87|10029|0|1|
|15149374|444.27|Bungalow|Private room|{"Wireless Internet",Kitchen,"Pets allowed","Indoor fireplace",Heating,Washer,Dryer,"Smoke detector","Carbon monoxide detector","First aid kit","Fire extinguisher",Essentials,Shampoo,"Lock on bedroom door",Hangers,"Hair dryer",Iron,"Laptop friendly workspace"}|3|1|Real Bed|strict|TRUE|LA|t|97%|2012-08-17|Venice|3|100|90291|0|1|

# RESPUESTA

```sql
WITH data AS (
    SELECT
        *,
        CASE
            WHEN number_of_reviews = 0 THEN 'New'
            WHEN number_of_reviews BETWEEN 1 AND 5 THEN 'Rising'
            WHEN number_of_reviews BETWEEN 6 AND 15 THEN 'Trending Up'
            WHEN number_of_reviews BETWEEN 16 AND 40 THEN 'Popular'
            WHEN number_of_reviews > 40 THEN 'Hot'
            ELSE 'Unknown' 
        END AS review_category
    FROM airbnb_host_searches
)

SELECT
    review_category,
    MIN(price) AS min_price,
    AVG(price) AS avg_price,
    MAX(price) AS max_price
FROM data
GROUP BY
    review_category
ORDER BY
    min_price

```

# EXPLICACION

La consulta cruza la popularidad del host con el precio de sus anuncios para evaluar ambas variables en conjunto. Despues se agrupa por la dimension pedida y se calcula el promedio o total correspondiente. Con eso se puede comparar el comportamiento de los hosts mas populares frente a los precios de renta.
