# Analyze Data to Answer Questions - Week 4 - Common Calculation Formulas

## SUM Function - 
``` SQL
SELECT
    Date, 
    small_bags,
    large_bags, 
    xlarge_bags, 
    small_bags + large_bags + xlarge_bags AS total_bags_calc
FROM
    avocado_data.avocado_prices
```
```SQL
SELECT 
    date, region, 
    total_bags, 
    small_bags,
    (small_bags/total_bags) *100 AS small_bags_percent
 FROM
    avocado_data.avocado_prices
 WHERE
    total_bags <> 0
```

## EXTRACT Function - 
```SQL
SELECT
    Extract(YEAR FROM STARTTIME) AS year, 
    COUNT(*) AS number_of_rides
FROM
    bigquery-public-data.new_york.citibike_trips
GROUP BY
    year
ORDER BY 
    year
```
## Teporary Table -
Like a sticky note. 

### WITH Function - 

```SQL
WITH 
    trips_over_1_hr AS (
  SELECT *
  FROM
    bigquery-public-data.new_york.citibike_trips
  WHERE 
    tripduration >=60
   )
## Count how many trips are 60+ minutes long

SELECT
    COUNT(*) AS cnt
 FROM
    trips_over_1_hr
```

### CREATE TABLE Function - 
```SQL

```
### SELECT INTO Function - 
```SQL
SELECT 
    *
INTO
    AfricaSales
FROM 
    GlobalSales
WHERE
    Region = Africa
```

### CREATE TEMP TABLE Function - 
```SQL

```


