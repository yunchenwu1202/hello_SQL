# Analyze Data to Answer Questions - Week 2 - Merging and Multiple Sources


## CONCAT Function- 
```SQL
SELECT
  usertpye, 
  CONCAT(start_station, "to", end_station_name) AS route, 
  COUNT(*) AS num_trips, 
  ROUDN(AVG(CAST(tripduration AS int64)/60, 2) AS duration

FROM
  `bigquery-public-data.new_york.citibike_trips`

GROUP BY
  start_station_name, end_station_name, usertype

ORDER BY
  num_trips DESC
 
LIMIT
  10
 ``` 
  
