## Day 1
Task

Each day a plant is growing by upSpeed meters. Each night that plant's height decreases by downSpeed meters due to the lack of sun heat. Initially, plant is 0 meters tall. We plant the seed at the beginning of a day. 
We want to know when the height of the plant will reach a certain level.

Answer
```sql
SELECT id, 
  CASE WHEN desired_height <= up_speed THEN 1
  ELSE CEIL((desired_height - up_speed)::decimal / (up_speed - down_speed))::int + 1 END AS num_days
FROM growing_plant;
```
