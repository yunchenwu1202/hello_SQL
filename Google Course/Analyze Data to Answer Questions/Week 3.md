# Analyze Data to Answer Questions - Week 3 - COUNT & COUNTD

## JOIN Function - 

```SQL
SELECT 
  orders.*, 
  warehouse.warehouse_alias,
  warehouse.state
FROM 
  warehouse_orders.Orders orders
JOIN 
  warehouse_orders.wareohuse warehouse ON orders.warehouse_id = warehouse.warehouse_id
```

## COUNT DISTINCT Function - 
  
```SQL
SELECT 
  warehouse.state as state
  COUNT (DISTINCT order_id) as num_orders
FROM 
  warehouse_orders.Orders orders
JOIN 
  warehouse_orders.wareohuse warehouse ON orders.warehouse_id = warehouse.warehouse_id
GOURP BY 
  warehouse.state
 ``` 
  
  
  
## Subqueries
```SQL
SELECT 
  station_id, 
  num_bike_available,
  (SELECT
    AVG(num_bikes_available)
    FROM bigquery-public-data.new_york.citibike_stations ) AS avg_num_bikes_available
FROM bigquery-public-data.new_york.citibike_stations
```
``` SQL
SELECT
  station_id, name, number_of_rides AS number_of_rides_starting_at_station
FROM
  (
  SELECT start_station_id, 
    COUNT(*) number_of_rides
  FROM 
    bigquery-public-data.new_york.citibike_trips
  GROUP BY
    start_station_id
    )
 AS station_num_trips
 
INNER JOIN
 bigquery-public-data.new_york.citibike_stations ON station_id = start_station_id
 
ORDER BY
  number_of_rides DESC
```
 ```SQL
SELECT
  station_id,
  name
FROM
  bigquery-public-data.new_york.citibike_stations
WHERE
  station_id IN
  (
    SELECT
      start_station_id
    FROM
      bigquery-public-data.new_york.citibike_trips
    WHERE
      usertype = 'Subscriber'
    )
```
  
## HAVING Fuction - 
Allows you to add filter to your query instead of the underlying table that can only be used with aggregate functions
```SQL
SELECT
  warehouse.warehouse_id, 
  CONCAT (warehouse.state, ':', warehouse_alias) AS warehouse_name,
  COUNT (orders.order_id) AS number_of_orders, 
  (
  SELECT
    COUNT(*)
  FROM
    warehouse_orders.orders order
    ) AS total_orders,
  
  CASE
    WHEN 
      COUNT(orders.order_id)/(SELECT COUNT(*) FROM warehouse_orders.orders orders) <= 0.20
    THEN 
      "fulfilled 0-20% of orders"
    WHEN 
      COUNT(orders.order_id)/(SELECT COUNT(*) FROM warehouse_orders.orders orders) > 0.20
      AND
       COUNT(orders.order_id)/(SELECT COUNT(*) FROM warehouse_orders.orders orders) <= 0.60
    THEN 
      "fulfilled 21-60% of orders"
    ELSE
      "fulfilled more than 60% of orders"
    END AS fulfillment_summary
  
FROM 
  warehouse_order.warehouse warehouse

LEFT JOIN
  warehouse_orders.orders orders
   ON 
    orders.warehouse_id = warehouse.warehouse_id

GROUP BY
  warehouse.warehouse_id, 
  warehouse_name

HAVING 
  COUNT(orders.order_id)>0
   ``` 
    
    
    
    
    
    
    
    
    
    
    
    
 
 
 
 
 
 
 
 
 
 
 
 
 
  
