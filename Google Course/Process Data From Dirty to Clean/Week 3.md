# Process Data from Dirty to Clean - Week 3 - Cleaning String Variables using SQL

SELECT 
  customer_id 
FROM
  customer_data.customer_address
  
  
## DISTINCT Function- Prevent duplicates
  
SELECT 
  DISTINCT customer_id 
FROM
  customer_data.customer_address
  
## LENGTH (LEN) Function- Double-check if string variables are consistent

SELECT
  LENGTH(country) AS letters_in_country
FROM
  customer_data.customer_address
  
SELECT
    country
FROM
    customer_data.customer_address
WHERE
  LENGTH(country)>2
  
  SUBSTR Function- 
SELECT
  customer_id
FROM
  customer_data.customer_address
WHERE
  SUBSTR(country,1,2)='US'
  
  
## Getting rid of duplicates

SELECT
  DISTINCT customer_id
FROM
  customer_data.customer_address
WHERE
  SUBSTR(country,1,2)='US'

Double-check 

SELECT
 state
FROM
  customer_data.customer_address
WHERE
  LENGTH(state)>2
  
## TRIM Function- 

SELECT
  DISTINCT customer_id
FROM 
  customer_data.customer_address
WHERE
  TRIM(state) = 'OH'
  
  
SELECT customer_id, 
  SUBSTR(country, 1, 3) AS new_country 
FROM 
  customer 
ORDER BY 
  country
  
  
## CAST function- converting anything from one data type to another 

SELECT
  CAST(purchase_price AS FLOAT64)
FROM
  customer_data.customer_purchase
ORDER BY
  CAST(purchase_price AS FLOAT64 DESC
  
  
SELECT
  CAST(date AS date) AS date_only 
FROM
  customer_data.customer_purchase
WHERE
  date BETWEEN '2020-12-01' AND '2020-12-31'
  
  
## CONCAT Function- Adding strings together to create new text strings that can be used as unique keys 

SELECT
  CONCAT(product_code, prodcut_color) AS new_product_code
FROM
  customer_data.customer_purchase
WHERE
  product = 'couch'

## COALESCE Function- Return non-null values in a list

SELECT
  COALESCE(product, product_code) AS product_info
FROM 
  customer_data.customer_purchase


## CASE Function- 

SELECT
  customer_id, 
  CASE 
   WHEN first_name= 'Tnoy' THEN 'Tony'
   WHEN first_name= 'Rahcel'THEN 'Rachel' 
   ELSE first_name
   END AS cleaned_name
FROM 
    customer_data.customer_name
    

## Changelog ##
Query history 






