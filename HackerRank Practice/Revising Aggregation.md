### Revising Aggregation

The CITY table is described as follows:

|  Field | Type |
|---|---|
| ID | NUMBER   |
| NAME | VARCHAR2(17)  |
| COUNTRYCODE |  VARCHAR2(3) |
| DISTRICT | VARCHAR2(20) |
| POPULATION | NUMBER |

The COUNTRY table is described as follows:

|  Field | Type |
|---|---|
| CODE | VARCHAR2(3)   |
| NAME | VARCHAR2(44)  |
| CONTINENT |  VARCHAR2(13) |
| REGION | VARCHAR2(25) |
| SURFACEAREA | NUMBER |
| INDEPYEAR | VARCHAR2(5)   |
| POPULATION | NUMBER  |
| LIFEEXPECTANCY |  VARCHAR2(4) |
| GNP | NUMBER |
| GNPOLD | VARCHAR2(9) |
| LOCALNAME | VARCHAR2(44)  |
| GOVERNMENTFORM | VARCHAR2(44) |
| HEADOFSTATE |  VARCHAR2(32) |
| CAPITAL | VARCHAR2(4) |
| CODE2 | VARCHAR2(2) |

1. Query the total population of all cities in CITY where District is California.
   
```sql
SELECT SUM(POPULATION)
FROM CITY
WHERE DISTRICT = 'California';
```

2. Query a count of the number of cities in CITY having a Population larger than 100000 .

```SQL
SELECT COUNT(ID)
FROM CITY
WHERE POPULATION > 100000 ;
```

3. Query the average population of all cities in CITY where District is California.

```SQL
SELECT AVG(POPULATION)
FROM CITY
WHERE DISTRICT = 'California' ;
```

4. Query the average population for all cities in CITY, rounded down to the nearest integer.

```SQL
SELECT ROUND(AVG(POPULATION),0)
FROM CITY;
```

5. Query the difference between the maximum and minimum populations in CITY.

```SQL
SELECT MAX(POPULATION) - MIN(POPULATION)
FROM CITY ; 
```
6. Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.
Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

```SQL
SELECT SUM(CITY.POPULATION)
FROM CITY
JOIN COUNTRY
ON CITY.CountryCode = COUNTRY.Code
WHERE CONTINENT = 'Asia' ; 
```

7. Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.
Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

```SQL
SELECT COUNTRY.CONTINENT, FLOOR(AVG(CITY.POPULATION))
FROM CITY
INNER JOIN COUNTRY
ON CITY.CountryCode = COUNTRY.Code 
GROUP BY COUNTRY.CONTINENT;
```









