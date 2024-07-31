
1. Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.

```sql
SELECT name
FROM Employee
ORDER BY name ASC;
```

2. Write a query that prints a list of employee names (i.e.: the name attribute) for employees in Employee having a salary greater than $2000 per month who have been employees for less than 10 months. Sort your result by ascending employee_id.

```sql
SELECT name
FROM Employee
WHERE months < 10
AND salary > 2000
ORDER BY employee_id ASC;
```


