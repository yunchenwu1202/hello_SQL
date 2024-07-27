### Weather Observation Station
The STATION table is described as follows:

|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

where LAT_N is the northern latitude and LONG_W is the western longitude.

1. Query a list of CITY and STATE from the STATION table.

```sql
SELECT CITY, STATE
FROM STATION ; 
```

3. Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE ID % 2 = 0;
```

4. Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table.

For example, if there are three records in the table with CITY values 'New York', 'New York', 'Bengalaru', there are 2 different city names: 'New York' and 'Bengalaru'. 

```sql
SELECT COUNT(CITY) - COUNT(DISTINCT City)
FROM STATION;
```

5. Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.

```sql
SELECT CITY, LENGTH(CITY) AS CITY_LENGTH
FROM STATION
ORDER BY CITY_LENGTH DESC, CITY ASC
LIMIT 1;

SELECT CITY, LENGTH(CITY) AS CITY_LENGTH
FROM STATION
ORDER BY CITY_LENGTH ASC, CITY ASC
LIMIT 1;
```

6. Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.

```sql
SELECT CITY
FROM STATION
WHERE CITY RLIKE '^[aeiouAEIOU]';
```

7. Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.
   
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE CITY RLIKE '[aeiouAEIOU]$'
```

8. Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.
   
```sql
SELECT CITY
FROM STATION
WHERE CITY RLIKE '^[aeiouAEIOU]'
AND CITY RLIKE '[aeiouAEIOU]$';
```

9. Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE LOWER(SUBSTR(CITY,1,1)) NOT IN ('a','e','i','o','u');
```

10. Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE LOWER(SUBSTR(CITY,LENGTH(CITY),1)) NOT IN ('a','e','i','o','u');
```

11. Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE LOWER(SUBSTR(CITY,1,1)) NOT IN ('a','e','i','o','u') OR LOWER(SUBSTR(CITY, LENGTH(CITY),1)) NOT IN ('a','e','i','o','u');   
```

12. Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE LOWER(SUBSTR(CITY,1,1)) NOT IN ('a','e','i','o','u') AND LOWER(SUBSTR(CITY,LENGTH(CITY),1)) NOT IN ('a','e','i','o','u');
```

