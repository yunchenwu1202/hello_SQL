## Case Study Questions

Q1. What is the total amount each customer spent at the restaurant
```sql
SELECT customer_id , SUM(price) AS total_spent
FROM dannys_diner.sales s
JOIN dannys_diner.menu m 
ON s.product_id = m.product_id
GROUP BY customer_id;
```

Q2. How many days has each customer visited the restaurant?
```sql
SELECT customer_id , COUNT(order_date) AS date
FROM dannys_diner.sales s
JOIN dannys_diner.menu m 
ON s.product_id = m.product_id
GROUP BY customer_id;
```

Q3. What was the first item from the menu purchased by each customer?
```sql
SELECT customer_id , MIN(order_date)
FROM dannys_diner.sales 
GROUP BY customer_id;
```

Q4. What is the most purchased item on the menu and how many times was it purchased by all customers?
```sql
SELECT m.product_name, COUNT(order_date)
FROM dannys_diner.sales s
JOIN dannys_diner.menu m 
ON s.product_id = m.product_id
GROUP BY product_name
ORDER BY COUNT(order_date) DESC
LIMIT 1;
```

Q5. Which item was the most popular for each customer?
Q6. Which item was the most popular for each customer?
Q7. Which item was purchased first by the customer after they became a member?
Q8. Which item was purchased just before the customer became a member?
Q9. What is the total items and amount spent for each member before they became a member?
Q10.If each $1 spent equates to 10 points and sushi has a 2x points multiplier - how many points would each customer have?
Q11.In the first week after a customer joins the program (including their join date) they earn 2x points on all items, not just sushi - how many points do customer A and B have at the end of January?
