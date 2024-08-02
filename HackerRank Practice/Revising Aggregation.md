### Revising Aggregation

The CITY table is described as follows:

|  Field | Type |
|---|---|
| ID | NUMBER   |
| NAME | VARCHAR2(17)  |
| COUNTRYCODE |  VARCHAR2(3) |
| DISTRICT | VARCHAR2(20) |
| POPULATION | NUMBER |

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

