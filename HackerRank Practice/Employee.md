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

```sql
SELECT MAX(salary*months), COUNT(*)
FROM Employee
WHERE (salary*months) = 
(
    SELECT MAX(salary*months)
    FROM Employee 
);
```

4. Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table but did not realize her keyboard's 0 key was broken until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeros removed), and the actual average salary.
Write a query calculating the amount of error (i.e.: ACTUAL - MISCALCULATED average monthly salaries), and round it up to the next integer.

```SQL
WITH ActualAvgSalary AS (
    SELECT AVG(Salary) AS avg_salary
    FROM EMPLOYEES
),
MiscalculatedAvgSalary AS (
    SELECT AVG(CONVERT(REPLACE(CONVERT(Salary, CHAR), '0', ''), UNSIGNED INTEGER)) AS avg_salary
    FROM EMPLOYEES
)
SELECT CEILING(ABS(ActualAvgSalary.avg_salary - MiscalculatedAvgSalary.avg_salary)) AS error_difference
FROM ActualAvgSalary, MiscalculatedAvgSalary;
```








