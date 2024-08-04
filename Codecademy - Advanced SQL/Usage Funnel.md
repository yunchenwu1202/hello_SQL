
### Build a Funnel From a Single Table

Mattresses and More users were asked to answer a five-question survey:

“How likely are you to recommend Mattresses and More to a friend?”
“Which Mattresses and More location do you shop at?”
“How old are you?”
“What is your gender?”
“What is your annual household income?”
However, not every user finished the survey!

We want to build a funnel to analyze if certain questions prompted users to stop working on the survey.

We will be using a table called survey_responses with the following columns:

question_text - the survey question
user_id - the user identifier
response - the user answer

1. Start by getting a feel for the survey_responses table.
Select all columns for the first 10 records from survey_responses.

```sql
SELECT *
 FROM survey_responses
 LIMIT 10
```

2. What is the number of responses for each question?

```sql
 SELECT *
 FROM survey_responses
 LIMIT 10;

 SELECT question_text, COUNT(DISTINCT user_id)
 FROM survey_responses
 GROUP BY 1;
```

