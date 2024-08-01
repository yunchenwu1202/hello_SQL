### Employee
Given a table STATION that holds data for five fields namely employee_id, name, months, salary.
|  Field | Type |
|---|---|
| EMPLOYEE_ID | INTEGER   |
| NAME  | STRING  |
| MONTHS |  INTEGER |
| SALARY | INTEGER |

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

3. We define an employee's total earnings to be their monthly  worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as 2 space-separated integers.



