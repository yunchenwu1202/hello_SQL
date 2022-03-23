Step 1: Inspect the fuel_type column
```
SELECT
  DISTINCT fuel_type
FROM
  cars.car_info;
 ``` 
Step 2: Inspect the length column
```
SELECT
  MIN(length) AS min_length,
  MAX(length) AS max_length
FROM
  cars.car_info;
```
Step 3: Fill the missing data
```
SELECT
  *
FROM
  cars.car_info 

WHERE 

  num_of_doors IS NULL;
 ``` 
  ---------------------------------------
  ```
  UPDATE
  cars.car_info
SET
  num_of_doors = "four"
WHERE
  make = "dodge"
  AND fuel_type = "gas"
  AND body_style = "sedan";
  ```
  ----------------------------------------
  ```
  SELECT
  *
FROM
  cars.car_info 

WHERE 

  num_of_doors IS NULL;
  ```
  
Step 4: Identify potential errors 
```
SELECT
  DISTINCT num_of_cylinders
FROM
  cars.car_info;
  ```
--------------------------------------------
```
UPDATE
  cars.car_info
SET
  num_of_cylinders = "two"
WHERE
  num_of_cylinders = "tow";
  ```
--------------------------------------------
```
SELECT
  DISTINCT num_of_cylinders
FROM
  cars.car_info;
  ```
---------------------------------------------
  ```
SELECT
  MIN(compression_ratio) AS min_compression_ratio,
  MAX(compression_ratio) AS max_compression_ratio
FROM
  cars.car_info;
  ```
---------------------------------------------
```
SELECT
  MIN(compression_ratio) AS min_compression_ratio,
  MAX(compression_ratio) AS max_compression_ratio
FROM
  cars.car_info

WHERE

  compression_ratio <> 70;
  ```
----------------------------------------------
```
DELETE cars.car_info

WHERE compression_ratio = 70;

Step 5: Ensure Constistency 

SELECT
  DISTINCT drive_wheels
FROM
  cars.car_info;
```
----------------------------------------------
```
SELECT
  DISTINCT drive_wheels,
  LENGTH(drive_wheels) AS string_length
FROM
  cars.car_info;
```
----------------------------------------------
```
UPDATE

  cars.car_info

SET

  drive_wheels = TRIM(drive_wheels)

WHERE TRUE;
  ```
-----------------------------------------------
```
 SELECT
  DISTINCT drive_wheels
FROM
  cars.car_info;
  ```

