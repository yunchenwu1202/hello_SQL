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

1. Query all columns (attributes) for every row in the CITY table.

```sql
SELECT *
FROM CITY;
```

2. Query all columns for a city in CITY with the ID 1661.
   
```SQL
SELECT *
FROM CITY
WHERE ID = 1661;
```
 
3. Write a query all columns for all American cities in CITY with populations larger than 100000. The CountryCode for America is USA.

```SQL
SELECT *
FROM CITY
WHERE CountryCode = 'USA'
AND population > 100000;
```

4. Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.

```sql
SELECT NAME
FROM CITY
WHERE CountryCode = 'USA'
AND population > 120000;
```

5. Query the total population of all cities in CITY where District is California.
   
```sql
SELECT SUM(POPULATION)
FROM CITY
WHERE DISTRICT = 'California';
```

6. Query a count of the number of cities in CITY having a Population larger than 100000 .

```SQL
SELECT COUNT(ID)
FROM CITY
WHERE POPULATION > 100000 ;
```

7. Query the average population of all cities in CITY where District is California.

```SQL
SELECT AVG(POPULATION)
FROM CITY
WHERE DISTRICT = 'California' ;
```

8. Query the average population for all cities in CITY, rounded down to the nearest integer.

```SQL
SELECT ROUND(AVG(POPULATION),0)
FROM CITY;
```

9. Query the difference between the maximum and minimum populations in CITY.

```SQL
SELECT MAX(POPULATION) - MIN(POPULATION)
FROM CITY ; 
```
10. Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.
Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

```SQL
SELECT SUM(CITY.POPULATION)
FROM CITY
JOIN COUNTRY
ON CITY.CountryCode = COUNTRY.Code
WHERE CONTINENT = 'Asia' ; 
```

11. Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.
Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

```SQL
SELECT COUNTRY.CONTINENT, FLOOR(AVG(CITY.POPULATION))
FROM CITY
INNER JOIN COUNTRY
ON CITY.CountryCode = COUNTRY.Code 
GROUP BY COUNTRY.CONTINENT;
```

12. Query the sum of the populations for all Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

```SQL
SELECT SUM(POPULATION)
FROM CITY
WHERE COUNTRYCODE = 'JPN';
```









