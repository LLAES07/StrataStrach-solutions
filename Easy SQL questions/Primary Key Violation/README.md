# Primary Key Violation


**[ENG]**

Write a query to return all Customers (cust_id) who are violating primary key constraints in the Customer Dimension (dim_customer) i.e. those Customers who are present more than once in the Customer Dimension.
For example if cust_id 'C123' is present thrice then the query should return two columns, value in first should be 'C123', while value in second should be 3

**[ES]**

Escriba una consulta para devolver todos los Clientes (cust_id) que violan las restricciones de clave principal en la Dimensión del Cliente (dim_customer), es decir, aquellos Clientes que están presentes más de una vez en la Dimensión del Cliente.
Por ejemplo, si cust_id 'C123' está presente tres veces, la consulta debería devolver dos columnas, el valor de la primera debería ser 'C123', mientras que el valor de la segunda debería ser 3.


### TABLA

dim_customer

| cust_id | cust_name             | cust_city     | cust_dob   | cust_pin_code |
| ------- | --------------------- | ------------- | ---------- | ------------- |
| C273    | Stephen V. Cooke      | New York      | 1996-11-28 | 8235          |
| C274    | Peter P. Mankin       | Mount Upton   | 1984-06-25 | 6050          |
| C274    | Juan C. Parker        | Mertzon       | 1989-07-07 | 6867          |
| C274    | Eve E. McClure        | Southfield    | 1995-05-18 | 7791          |
| C275    | Charles J. Stevens    | Oakland       | 1975-12-02 | 5930          |
| C276    | Roger V. Malveaux     | Fresno        | 1970-10-13 | 4370          |
| C276    | Susan D. Kramer       | Cleveland     | 1975-09-12 | 5447          |
| C277    | Pearl P. West         | San Francisco | 1996-12-03 | 9097          |
| C278    | Christina C. Hudson   | Houston       | 1993-02-11 | 7418          |
| C279    | Melissa C. Greenblatt | Austin        | 1994-05-03 | 7678          |
| C280    | Johnny M. Johnson     | Peoria        | 1960-03-10 | 2641          |
| C281    | Sonia W. Watts        | Bloomington   | 1968-03-11 | 3915          |
| C281    | Jack R. Kerr          | Newark        | 1999-04-28 | 9770          |
| C282    | Dominic N. Ramey      | Aurora        | 1985-11-27 | 6516          |
| C283    | Richard I. Taylor     | Wheeling      | 1992-06-03 | 7070          |
| C284    | Michael B. Brooks     | Conyers       | 1987-11-11 | 6745          |
| C285    | Gary B. Jordan        | Duluth        | 1986-10-15 | 6597          |
| C286    | Tina E. Ward          | Brooklyn      | 1966-07-27 | 2671          |
| C287    | Beth C. Hollomon      | Westbury      | 1974-06-20 | 4796          |


# RESPUESTA

```sql


```