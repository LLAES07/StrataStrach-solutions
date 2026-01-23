You are given a dataset of health inspections that includes details about violations. Each row represents an inspection, and if an inspection resulted in a violation, the `violation_id` column will contain a value.

Count the total number of violations that occurred at **'Roxanne Cafe'** for each year, based on the inspection date. Output the year and the corresponding number of violations in ascending order of the year.

### Table
sf_restaurant_health_violations

| business_id | business_name               | business_address | business_city | business_state | business_postal_code | business_latitude | business_longitude | business_location                                                                                                                               | business_phone_number |
| ----------- | --------------------------- | ---------------- | ------------- | -------------- | -------------------- | ----------------- | ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- | --------------------- |
| 5800        | John Chin Elementary School | 350 Broadway St  | San Francisco | CA             | 94133                | 37.8              | -122.4             | {'longitude': '-122.403154', 'needs_recoding': False, 'latitude': '37.798358', 'human_address': '{"address":"","city":"","state":"","zip":""}'} |                       |
| 64236       | Sutter Pub and Restaurant   | 700 Sutter St    | San Francisco | CA             | 94102                | 37.79             | -122.41            | {'longitude': '-122.41188', 'needs_recoding': False, 'latitude': '37.78881', 'human_address': '{"address":"","city":"","state":"","zip":""}'}   |                       |


# RESPUESTA

```sql

-- if violation_id IS NOT NULL = violation



SELECT
    EXTRACT(YEAR FROM inspection_date) AS year,
    COUNT(inspection_id)
FROM sf_restaurant_health_violations
WHERE
    business_name = 'Roxanne Cafe'
GROUP BY
    EXTRACT(YEAR FROM inspection_date)
ORDER BY 1 ASC 

```