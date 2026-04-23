# Top Businesses With Most Reviews

**[ENG]**


Find the top 5 businesses with most reviews. Assume that each row has a unique business_id such that the total reviews for each business is listed on each row. Output the business name along with the total number of reviews and order your results by the total reviews in descending order.

If there are ties in review counts, businesses with the same number of reviews receive the same rank, and subsequent ranks are skipped accordingly (e.g., if two businesses tie for rank 4, the next business receives rank 6, skipping rank 5).


**[ESP]**

Encuentra los 5 negocios principales con la mayor cantidad de reseñas. Supón que cada fila tiene un business_id único, de modo que el total de reseñas de cada negocio aparece en cada fila.

Muestra el nombre del negocio junto con el número total de reseñas y ordena los resultados por el total de reseñas de forma descendente.


### Table

yelp_business


|business_id|name|neighborhood|address|city|state|postal_code|latitude|longitude|stars|review_count|is_open|categories|
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|G5ERFWvPfHy7IDAUYlWL2A|All Colors Mobile Bumper Repair||7137 N 28th Ave|Phoenix|AZ|85051|33.45|-112.07|1|4|1|Auto Detailing;Automotive|
|0jDvRJS-z9zdMgOUXgr6rA|Sunfare||811 W Deer Valley Rd|Phoenix|AZ|85027|33.68|-112.08|5|27|1|Personal Chefs;Food;Gluten-Free;Food Delivery Services;Event Planning & Services;Restaurants|
|6HmDqeNNZtHMK0t2glF_gg|Dry Clean Vegas|Southeast|2550 Windmill Ln, Ste 100|Las Vegas|NV|89123|36.04|-115.12|1|4|1|Dry Cleaning & Laundry;Laundry Services;Local Services;Dry Cleaning|
|pbt3SBcEmxCfZPdnmU9tNA|The Cuyahoga Room||740 Munroe Falls Ave|Cuyahoga Falls|OH|44221|41.14|-81.47|1|3|0|Wedding Planning;Caterers;Event Planning & Services;Venues & Event Spaces|
|CX8pfLn7Bk9o2-8yDMp_2w|The UPS Store||4815 E Carefree Hwy, Ste 108|Cave Creek|AZ|85331|33.8|-111.98|1.5|5|1|Notaries;Printing Services;Local Services;Shipping Centers|
|yzAB_pRwk8FJl3aILiiySA|CenturyLink|Spring Valley|4850 S Fort Apache Rd, Ste 100|Las Vegas|NV|89147|36.1|-115.3|1.5|35|0|Home Services;Television Service Providers;Professional Services;Internet Service Providers;Utilities|
|p8keQs0xw0TzP0JjYPiZPQ|The Enfield Fox||285 Enfield Place|Mississauga|ON|L5B 3Y6|43.59|-79.64|1.5|3|0|Bars;Restaurants;Pubs;British;Nightlife|
|lbxfIXUNUdSRO2t7z2PxPA|Budget Car Rental||7125 E Shea Blvd, Ste 101|Scottsdale|AZ|85254|33.58|-111.93|2|6|1|Hotels & Travel;Car Rental|
|xxCrRqqICzQyR0Q-iqCrNw|Subway|Plaza Midwood|1300 The Plz|Charlotte|NC|28205|35.22|-80.81|2|13|1|Fast Food;Sandwiches;Restaurants|
|WdQP8kl9SzcOdubWz0Rs5g|Red Beard Bodywork And Structural Integration|Capitol|301 S Bedford St|Madison|WI|53703|43.07|-89.39|5|10|1|Rolfing;Health & Medical;Beauty & Spas;Massage|

# RESPUESTA

```sql
-- OBJ: TOP 5 BUSINESSES  >> reviews
-- EACH ROW 1 business_id
-- SELECT buisiness name, # rewiees
-- ORDER total_reviews DESC
WITH CT1 AS (
        -- Usando rank para ajustarse al requisito de saltarse valores
    SELECT 
        name,
        review_count,
        RANK() OVER(ORDER BY review_count DESC)
    FROM yelp_business
)
-- Consulta final ordenada por el ranking
SELECT
    name, 
    review_count
FROM ct1
ORDER BY rank ASC
LIMIT 5;


```

# EXPLICACION

Primero se toma la cantidad de reviews por negocio, porque ese es el valor que define el ranking. Luego se ordenan los negocios de mayor a menor para identificar los que concentran mas opiniones. Si hay empates, la logica de ranking o el ordenamiento permite devolver todos los negocios que comparten la misma posicion.
