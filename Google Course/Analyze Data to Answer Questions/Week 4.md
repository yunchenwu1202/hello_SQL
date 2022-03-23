# Analyze Data to Answer Questions - Week 4 - Common Calculation Formulas

## SUM Function - 
``` 
SELECT
    Date, 
    small_bags,
    large_bags, 
    xlarge_bags, 
    small_bags + large_bags + xlarge_bags AS total_bags_calc
FROM
    avocado_data.avocado_prices
```
```
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
```
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
