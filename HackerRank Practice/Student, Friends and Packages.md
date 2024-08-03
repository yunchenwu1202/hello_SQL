### Students, Friends and Packages

The Students table is described as follows:

|  Field | Type |
|---|---|
| ID | INTEGER   |
| NAME | STRING  |

The Friends table is described as follows:

|  Field | Type |
|---|---|
| ID | INTEGER   |
| FRIENDS_ID | STRING  |

The Packages table is described as follows:

|  Field | Type |
|---|---|
| ID | INTEGER   |
| SALARY | FLOAT  |

You are given three tables: Students, Friends and Packages. Students contains two columns: ID and Name. 
Friends contains two columns: ID and Friend_ID (ID of the ONLY best friend). 
Packages contains two columns: ID and Salary (offered salary in $ thousands per month).

1. Write a query to output the names of those students whose best friends got offered a higher salary than them.
   Names must be ordered by the salary amount offered to the best friends.
   It is guaranteed that no two students got same salary offer.

```SQL
SELECT S.Name
FROM Students S
INNER JOIN Friends F
ON S.id = F.id
INNER JOIN Packages P1
ON P1.id = S.id
INNER JOIN Packages P2
ON F.Friend_id = P2.id
WHERE P1.Salary < P2.Salary
ORDER BY P2.Salary;
```



