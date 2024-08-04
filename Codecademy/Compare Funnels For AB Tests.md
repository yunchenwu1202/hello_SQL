### Compare Funnels For A/B Tests
Mattresses and More has an onboarding workflow for new users of their website. It uses modal pop-ups to welcome users and show them important features of the site like:

1. Welcome to Mattresses and More!
2. Browse our bedding selection
3. Select items to add to your cart
4. View your cart by clicking on the icon
5. Press ‘Buy Now!’ when you’re ready to checkout

The Product team at Mattresses and More has created a new design for the pop-ups that they believe will lead more users to complete the workflow.

They’ve set up an A/B test where:

50% of users view the original control version of the pop-ups
50% of users view the new variant version of the pop-ups

Eventually, we’ll want to answer the question:

How is the funnel different between the two groups?

We will be using a table called onboarding_modals with the following columns:

user_id - the user identifier
modal_text - the modal step
user_action - the user response (Close Modal or Continue)
ab_group - the version (control or variant)

1.
Start by getting a feel for the onboarding_modals table.
Select all columns for the first 10 records from onboarding_modals.

```sql
SELECT *
FROM onboarding_modals
LIMIT 10;
```

2. Try using a GROUP BY statement to calculate COUNT(DISTINCT user_id) for each modal_text.

And don’t forget ORDER BY to sort.

```sql
SELECT modal_text, 
       COUNT(DISTINCT user_id)
FROM onboarding_modals
GROUP BY 1
ORDER BY 1;
```

3. The previous query combined both the control and variant groups.

We can use a CASE statement within our COUNT() aggregate so that we only count user_ids whose ab_group is equal to ‘control’:

```sql
SELECT modal_text,
COUNT(DISTINCT CASE
    WHEN ab_group = 'control' THEN user_id
    END) AS 'control_clicks'
FROM onboarding_modals
GROUP BY 1
ORDER BY 1;
```










