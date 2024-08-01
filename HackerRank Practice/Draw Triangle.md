
### P(R) represents a pattern drawn by Julia in R rows. The following pattern represents P(5):

```
* * * * * 
* * * * 
* * * 
* * 
*
```

Write a query to print the pattern P(20).

```sql
WITH RECURSIVE Pattern AS (
    SELECT 20 AS n
    UNION ALL
    SELECT n - 1
    FROM Pattern
    WHERE n > 1
)

SELECT REPEAT('* ', n)
FROM Pattern;
```

### P(R) represents a pattern drawn by Julia in R rows. The following pattern represents P(5):

```
* 
* * 
* * * 
* * * * 
* * * * *
```

Write a query to print the pattern P(20).

```sql
WITH RECURSIVE Pattern AS (
    SELECT 1 AS n
    UNION ALL
    SELECT n + 1
    FROM Pattern
    WHERE n < 20
)

SELECT REPEAT('* ', n)
FROM Pattern;
```

### Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:
Equilateral: It's a triangle with 3 sides of equal length.
Isosceles: It's a triangle with 2 sides of equal length.
Scalene: It's a triangle with 3 sides of differing lengths.
Not A Triangle: The given values of A, B, and C don't form a triangle.

```SQL
SELECT 
    CASE WHEN  A+B <= C THEN 'Not A Triangle'
              WHEN  B+C <= A THEN 'Not A Triangle'
              WHEN  C+A <= B THEN 'Not A Triangle'
              WHEN A=B THEN CASE WHEN B = C THEN 'Equilateral' ELSE 'Isosceles'  
              END
              WHEN B=C THEN 'Isosceles'
              WHEN A=C THEN 'Isosceles'
              ELSE 'Scalene' END
FROM TRIANGLES
```







