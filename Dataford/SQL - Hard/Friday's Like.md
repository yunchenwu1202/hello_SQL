### Friday's Likes
Company: Meta
Level: Hard
You have access to Facebook's database, containing tables related to user posts, friendships, and likes. Your goal is to calculate the total number of likes made on posts by friends specifically on Fridays.

user_posts table:
|  Column Name | Description |
|---|---|
| post_id | Indentifer of post   |
| user_name | Username  |
| date_posted | Date posted  |


friendships table:
| Column Name |	Description |
|---|---|
|user_name1 |	Friend 1 |
|user_name2 |	Friend 2 |

likes table:
|Column Name	| Description |
|---|---|
|user_name | Username |
|post_id |	Identifier of post |
|date_liked	| Date liked |

Example output:
|date_liked	| likes |
|---|---|
|2024-01-05	| 3 |
|2024-01-12	| 1 |

```sql
WITH friends_likes AS (
    SELECT 
        l.user_name,
        l.post_id,
        l.date_liked
    FROM 
        likes l
    JOIN 
        friendships f 
    ON 
        (l.user_name = f.user_name1 AND l.post_id IN (SELECT post_id FROM user_posts WHERE user_name = f.user_name2))
        OR 
        (l.user_name = f.user_name2 AND l.post_id IN (SELECT post_id FROM user_posts WHERE user_name = f.user_name1))
    WHERE 
        EXTRACT(DOW FROM l.date_liked) = 5 -- 5 indicates Friday
)
SELECT 
    date_liked, 
    COUNT(*) AS likes
FROM 
    friends_likes
GROUP BY 
    date_liked
ORDER BY 
    date_liked;
```
