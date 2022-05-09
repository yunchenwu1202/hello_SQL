## Exercise 2: Aggregate Functions
Query A1: Enter a function that calculates the total cost of all animal rescues in the PETRESCUE table.

```sql
select SUM(COST) 
from PETRESCUE;
```

Query A2: Enter a function that displays the total cost of all animal rescues in the PETRESCUE table in a column called SUM_OF_COST.

```sql
select SUM(COST) AS SUM_OF_COST 
from PETRESCUE;
```

Query A3: Enter a function that displays the maximum quantity of animals rescued.

```sql
select MAX(QUANTITY) 
from PETRESCUE;
```

Query A4: Enter a function that displays the average cost of animals rescued.

```sql
select AVG(COST) 
from PETRESCUE;
```

Query A5: Enter a function that displays the average cost of rescuing a dog. Hint - Bear in my the cost of rescuing one dog on day, is different from another day. So you will have to use and average of averages.

```sql
select AVG(COST/QUANTITY) 
from PETRESCUE where ANIMAL = 'Dog';
```
## Exercise 3: Scalar and String Functions
Query B1: Enter a function that displays the rounded cost of each rescue.

```sql
select ROUND(COST) 
from PETRESCUE;
```

Query B2: Enter a function that displays the length of each animal name.

```sql
select LENGTH(ANIMAL) 
from PETRESCUE;
```

Query B3: Enter a function that displays the animal name in each rescue in uppercase.

```sql
select UCASE(ANIMAL) 
from PETRESCUE;
```

Query B4: Enter a function that displays the animal name in each rescue in uppercase without duplications.

```sql
select DISTINCT(UCASE(ANIMAL)) 
from PETRESCUE;
```

Query B5: Enter a query that displays all the columns from the PETRESCUE table, where the animal(s) rescued are cats. Use cat in lower case in the query.

```sql
select * 
from PETRESCUE 
where LCASE(ANIMAL) = 'cat';
```

## Exercise 4: Date and Time Functions
Query C1: Enter a function that displays the day of the month when cats have been rescued.

```sql
select DAY(RESCUEDATE) 
from PETRESCUE 
where ANIMAL = 'Cat';
```

Query C2: Enter a function that displays the number of rescues on the 5th month.

```sql
select SUM(QUANTITY) 
from PETRESCUE 
where MONTH(RESCUEDATE)='05';
```

Query C3: Enter a function that displays the number of rescues on the 14th day of the month.

```sql
select SUM(QUANTITY) 
from PETRESCUE 
where DAY(RESCUEDATE)='14';
```

Query C4: Animals rescued should see the vet within three days of arrivals. Enter a function that displays the third day from each rescue.

```sql
select (RESCUEDATE + 3 DAYS) 
from PETRESCUE;
```

Query C5: Enter a function that displays the length of time the animals have been rescued; the difference between today’s date and the recue date.

```sql
select (CURRENT DATE - RESCUEDATE) 
from PETRESCUE;
```

