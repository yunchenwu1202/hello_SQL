### The Report

You are given two tables: Students and Grades. Students contains three columns ID, Name and Marks.

Students: 
|  Field | Type |
|---|---|
| ID | INTEGER   |
| Name | STRING  |
| Marks | INTEGER   |

Grades: 
|  Field | Type |
|---|---|
| Grade | STRING   |
| Min_Mark | INTEGER  |
| Max_Mark | INTEGER  |


Ketty gives Eve a task to generate a report containing three columns: Name, Grade and Mark. 
Ketty doesn't want the NAMES of those students who received a grade lower than 8. 
The report must be in descending order by grade -- i.e. higher grades are entered first. 
If there is more than one student with the same grade (8-10) assigned to them, order those particular students by their name alphabetically. 
Finally, if the grade is lower than 8, use "NULL" as their name and list them by their grades in descending order. 
If there is more than one student with the same grade (1-7) assigned to them, order those particular students by their marks in ascending order.
Write a query to help Eve.

```sql
WITH 'Grades' AS
(SELECT 
 CASE WHEN Marks BETWEEN 0 AND 9 THEN 1
            WHEN Marks BETWEEN 10 AND 19 THEN 2
            WHEN Marks BETWEEN 20 AND 29 THEN 3
            WHEN Marks BETWEEN 30 AND 39 THEN 4
            WHEN Marks BETWEEN 40 AND 49 THEN 5
            WHEN Marks BETWEEN 50 AND 59 THEN 6
            WHEN Marks BETWEEN 60 AND 69 THEN 7
            WHEN Marks BETWEEN 70 AND 79 THEN 8
            WHEN Marks BETWEEN 80 AND 89 THEN 9
            WHEN Marks BETWEEN 90 AND 100 THEN 10
 END
)


SELECT
CASE WHEN 'Grade'
FROM 
JOIN
ON
WHERE
ORDER BY
```



