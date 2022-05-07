## CREATE Function
1. Creating two tables PETSALE and PET
```sql 
CREATE TABLE PETSALE(
  ID INTEGAR NOT NULL,
  PET CHAR(20),
  SALEPRICE DECIMAL(6,2),
  PROFIT DECIMAL(6,2),
  SALEDATE DATE
);

CREATE TABLE PET(
  ID INTEGAR NOT NULL,
  ANIMAL VARCHAR(20),
  QUANTITY INTEGAR
  );
```

2. Insert records into the two newly created tables and show all records of two tables
```sql
INSERT INTO PETSALE VALUES
    (1,'Cat',450.09,100.47,'2018-05-29'),
    (2,'Dog',666.66,150.76,'2018-06-01'),
    (3,'Parrot',50.00,8.9,'2018-06-04'),
    (4,'Hamster',60.60,12,'2018-06-11'),
    (5,'Goldfish',48.48,3.5,'2018-06-14');
    
INSERT INTO PET VALUES
    (1,'Cat',3),
    (2,'Dog',4),
    (3,'Hamster',2);
    
SELECT * FROM PETSALE;
SELECT * FROM PET;
```

## ALTER Function
TASK A. ALTER with ADD COLUMN
1. Add new QUANTITY column to PETSALE table and show the altered table.
```sql
ALTER TABLE PETSALE
ADD COLUMN QUANTITY INTEGER;

SELECT * FROM PETSALE;
```
2. Update the newly added QUANTITY column of PETSLAE with some values. 
```sql
UPDATE PETSALE SET QUANTITY = 9 WHERE ID = 1;
UPDATE PETSALE SET QUANTITY = 3 WHERE ID = 2;
UPDATE PETSALE SET QUANTITY = 2 WHERE ID = 3;
UPDATE PETSALE SET QUANTITY = 6 WHERE ID = 4;
UPDATE PETSALE SET QUANTITY = 24 WHERE ID = 5;

SELECT * FROM PETSALE;
```
TASK B. ALTER using DROP COLUMN
1. Delete PROFIT from PETSALE and show the altered table.
```sql
ALTER TABLE PETSALE
DROP COLUMN PROFIT;

SELECT * FROM PETSALE;
```

TASK C. ALTER using ALTER COLUMN
1. Change data type to VARCHAR(20) of PET of the table PETSALE.
```sql
ALTER TABLE PETSALE
ALTER COLUMN PET SET DATA TYPE VARCHAR(20);

SELECT * FROM PETSALE;
```

TASK D. ALER using RENAME COLUMN
```SQL
ALTER TABLE PETSALE
RENAME COLUMN PET TO ANIMAL;

SELECT * FROM PETSALE;
```

## TRUNCATE Function
1. Remove all rows from PET.
```sql
TRUNCATE TABLE PET IMMEDIATE;

SELECT * FROM PET;
```

## DROP Function
1. Delete the PET table and verify if the table still exist.
```sql
DROP TABLE PET;

SELECT * FROM PET;
```
