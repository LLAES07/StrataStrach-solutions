# Salary by Education

**[ENG]**

Given the education levels and salaries of a group of individuals, find what is the average salary for each level of education.

**[ES]**

Dado los niveles de educacion y salarios de un grupo de individuos, encuentra cual es el salario promedio para cada nivel de educacion.

### TABLA

google_salaries

|id|first_name|last_name|department|education|salary|
|---|---|---|---|---|---|
|376|Gary|Stokes|Accounting|Master|56760|
|377|Lorenzo|Cortez|Accounting|Doctorate|74127|
|378|Roberta|Mcgee|Administration|Primary|23987|
|379|Myrtle|Munoz|Administration|Primary|31079|
|380|Molly|Walker|Administration|Primary|20725|
|381|Maria|Simmons|Administration|Secondary|39723|
|382|Muriel|Hernandez|Administration|Bachelor|58555|
|383|Andres|Watson|BI|Bachelor|56834|
|384|Wayne|Leonard|BI|Master|65180|
|385|Julius|Poole|BI|Master|55842|
|386|Louis|Baker|Facilities|Primary|31158|
|387|Sandra|Wright|HR|Primary|24082|
|388|Jenny|Peterson|HR|Secondary|31098|
|389|Ellis|Hodges|HR|Secondary|38128|
|390|Larry|Jacobs|IT|Secondary|33544|
|391|Milton|Pratt|IT|Secondary|35476|
|392|Marvin|Gilbert|IT|Bachelor|41147|
|393|Geoffrey|Montgomery|IT|Bachelor|47757|
|394|Anne|Mann|IT|Master|54863|
|395|Marjorie|Malone|Legal|Bachelor|45149|
|396|Erika|Fuller|Legal|Master|53391|
|397|Guadalupe|Shaw|Legal|Doctorate|62994|

# RESPUESTA

```sql
SELECT
    department,
    AVG(salary) as salario_promedio
FROM google_salaries
GROUP BY education;
```

# EXPLICACION

El objetivo del ejercicio es comparar salarios promedio segun el nivel educativo, asi que la logica correcta consiste en formar grupos por `education`. Una vez creados esos grupos, `AVG(salary)` calcula el salario medio dentro de cada nivel de estudios.

En otras palabras, todas las filas con `Bachelor` se promedian juntas, las de `Master` en otro grupo, y asi con cada categoria educativa. El resultado final permite ver como varia el ingreso promedio dependiendo de la formacion academica registrada en la tabla.
