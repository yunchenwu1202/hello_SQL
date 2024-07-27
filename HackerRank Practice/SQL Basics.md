
Given a table CITY that holds data for five fields namely ID, NAME, COUNTRY CODE, DISTRICT and POPULATION.

|  Field | Type |
|---|---|
| ID  | NUMBER |
| NAME | VARCHAR2(17)   |
| COUNTRY CODE| VARCHAR2(2)  |
| DISTRICT | VARCHAR2(20) |
| POPULATION | NUMBER |

### Select All
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

### Revising the Select Query
 
1. Write a query all columns for all American cities in CITY with populations larger than 100000. The CountryCode for America is USA.

```SQL
SELECT *
FROM CITY
WHERE CountryCode = 'USA'
AND population > 100000;
```

2. Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.

```sql
SELECT NAME
FROM CITY
WHERE CountryCode = 'USA'
AND population > 120000;
```
