# Find all searches for San Francisco with a flexible cancellation policy and a review score rating


Find all searches for San Francisco with a flexible cancellation policy and a review score rating. Sort the results by the review score in the descending order.
	
### Table
	
airbnb_search_details

| id       | price  | property_type | room_type       | amenities                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| -------- | ------ | ------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 12513361 | 555.68 | Apartment     | Entire home/apt | {TV,"Wireless Internet","Air conditioning","Smoke detector","Carbon monoxide detector",Essentials,"Lock on bedroom door",Hangers,Iron}                                                                                                                                                                                                                                                                                                                                                             |
| 7196412  | 366.36 | Cabin         | Private room    | {"Wireless Internet",Kitchen,Washer,Dryer,"Smoke detector","First aid kit","Fire extinguisher",Essentials,"Hair dryer","translation missing: en.hosting_amenity_49","translation missing: en.hosting_amenity_50"}                                                                                                                                                                                                                                                                                  |
| 16333776 | 482.83 | House         | Private room    | {TV,"Cable TV",Internet,"Wireless Internet",Kitchen,"Free parking on premises","Pets live on this property",Dog(s),"Indoor fireplace","Buzzer/wireless intercom",Heating,Washer,Dryer,"Smoke detector","Carbon monoxide detector","First aid kit","Safety card","Fire extinguisher",Essentials,Shampoo,"24-hour check-in",Hangers,"Hair dryer",Iron,"Laptop friendly workspace","translation missing: en.hosting_amenity_49","translation missing: en.hosting_amenity_50","Self Check-In",Lockbox} |
| 1786412  | 448.86 | Apartment     | Private room    | {"Wireless Internet","Air conditioning",Kitchen,Heating,"Suitable for events","Smoke detector","Carbon monoxide detector","First aid kit","Fire extinguisher",Essentials,Shampoo,"Lock on bedroom door",Hangers,"translation missing: en.hosting_amenity_49","translation missing: en.hosting_amenity_50"}                                                                                                                                                                                         |
| 14575777 | 506.89 | Villa         | Private room    | {TV,Internet,"Wireless Internet","Air conditioning",Kitchen,"Free parking on premises",Essentials,Shampoo,"translation missing: en.hosting_amenity_49","translation missing: en.hosting_amenity_50"}                                                                                                                                                                                                                                                                                               |
| 20515889 | 720.79 | Villa         | Entire home/apt | {TV,"Cable TV",Internet,"Wireless Internet",Kitchen,"Free parking on premises","Pets allowed","Elevator in building","Hot tub","Indoor fireplace",Heating,"Family/kid friendly","Suitable for events",Washer,Dryer,"Smoke detector","Carbon monoxide detector","First aid kit","Safety card","Fire extinguisher",Essentials,Shampoo}                                                                                                                                                               |
| 13783491 | 516.48 | Villa         | Private room    | {TV,"Cable TV",Internet,"Wireless Internet","Air conditioning",Pool,Kitchen,"Free parking on premises","Pets allowed","Hot tub","Indoor fireplace",Heating,"Family/kid friendly",Washer,Dryer,"Smoke detector","Carbon monoxide detector","Fire extinguisher",Essentials,Shampoo,"Lock on bedroom door","24-hour check-in",Hangers,"Hair dryer",Iron,"Laptop friendly workspace"}                                                                                                                  |
| 6591755  | 529.33 | Villa         | Entire home/apt | {TV,"Cable TV",Internet,"Wireless Internet",Kitchen,"Pets allowed","Pets live on this property","Buzzer/wireless intercom",Heating,"Family/kid friendly",Washer,Dryer,"Smoke detector","Carbon monoxide detector","Fire extinguisher",Essentials,Hangers,"Hair dryer",Iron,"Laptop friendly workspace"}                                                                                                                                                                                            |

# RESPUESTA

```sql

SELECT
    city,
    review_scores_rating
FROM airbnb_search_details
WHERE
    cancellation_policy = 'flexible'
    AND LOWER(city) LIKE 'sf'
ORDER BY
    review_scores_rating DESC NULLS LAST;

```