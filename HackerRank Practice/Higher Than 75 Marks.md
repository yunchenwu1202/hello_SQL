### Higher Than 75 Marks
The STUDENTS table is described as follows: 

|  Field | Type |
|---|---|
| ID  | INTEGER |
| NAME | STRING   |
| MARKS  | INTEGER |

The Name column only contains uppercase (A-Z) and lowercase (a-z) 

```sql
SELECT Name
FROM STUDENTS
WHERE Marks > 75 
ORDER BY RIGHT(NAME, 3), ID ASC;
```
