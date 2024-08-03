### Occupation

The OCCUPATIONS table is described as follows:

|  Field | Type |
|---|---|
| NAME  | STRING  |
| Occupation | STRING |

1. Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation.
   The output column headers should be Doctor, Professor, Singer, and Actor, respectively.

Note: Print NULL when there are no more names corresponding to an occupation.

```SQL
-- Step 1: Assign row numbers to each name within its occupation
WITH OrderedNames AS (
    SELECT 
        Name,
        Occupation,
        ROW_NUMBER() OVER (PARTITION BY Occupation ORDER BY Name) AS RowNumber
    FROM OCCUPATIONS
)

-- Step 2: Pivot the table
SELECT 
    MAX(CASE WHEN Occupation = 'Doctor' THEN Name ELSE NULL END) AS Doctor,
    MAX(CASE WHEN Occupation = 'Professor' THEN Name ELSE NULL END) AS Professor,
    MAX(CASE WHEN Occupation = 'Singer' THEN Name ELSE NULL END) AS Singer,
    MAX(CASE WHEN Occupation = 'Actor' THEN Name ELSE NULL END) AS Actor
FROM OrderedNames
GROUP BY RowNumber
ORDER BY RowNumber;
```


