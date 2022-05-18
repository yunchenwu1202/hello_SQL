## Exercise 1, Question 1. 
Write and execute a SQL query to list the school names, community names and average attendance for communities with a hardship index of 98. 
```sql
SELECT 
ps.NAME_OF_SCHOOL, ps.AVERAGE_STUDENT_ATTENDANCE, cd.COMMUNITY_AREA_NAME, cd.HARDSHIP_INDEX
FROM `ferrous-destiny-344108.ibm.chicago_public_schools` AS ps
RIGHT JOIN `ferrous-destiny-344108.ibm.census_data` AS cd
ON ps.COMMUNITY_AREA_NUMBER = cd.COMMUNITY_AREA_NUMBER
```

## Exercise 1, Question 2. 
Write and execute a SQL query to list all crimes that took place at a school. Include case number, crime type and community name.
```sql
SELECT 
cd.COMMUNITY_AREA_NAME, ccd.CASE_NUMBER, ccd.PRIMARY_TYPE, ccd.LOCATION_DESCRIPTION
FROM 
`ferrous-destiny-344108.ibm.chicago_crime_data` AS ccd
RIGHT JOIN 
`ferrous-destiny-344108.ibm.census_data` AS cd
ON 
ccd.COMMUNITY_AREA_NUMBER = cd.COMMUNITY_AREA_NUMBER
WHERE 
ccd.LOCATION_DESCRIPTION LIKE '%SCHOOL%'
```

## Exercise 2, Question 1. 
Write and execute a SQL statement that returns just the school name and leaders’ icon from the view. 
```SQL
CREATE OR REPLACE VIEW school_data ("school_name","leader_icon")
AS SELECT 
NAME_OF_SCHOOL, Leaders_Icon
FROM
`ferrous-destiny-344108.ibm.chicago_public_schools`

SELECT *
FROM school_data
```

## Exercise 3, Question 1.
Write the structure of a query to create or replace a stored procedure called UPDATE_LEADERS_SCORE that takes a in_School_ID parameter as an integer and a in_Leader_Score parameter as an integer. Don't forget to use the #SET TERMINATOR statement to use the @ for the CREATE statement terminator. 
```SQL
#SET TERMINATOR@
CREATE OR REPLACE PROCEDURE update_leaders_score
(IN in_School_ID INTEGER, IN in_Leader_Sore INTEGER)
  BEGIN
 
  END@
```

## Exercise 3, Question 2.
Inside your stored procedure, write a SQL statement to update the Leaders_Score field in the CHICAGO_PUBLIC_SCHOOLS table for the school identified by in_School_ID to the value in the in_Leader_Score parameter. 
```sql
#SET TERMINATOR @

CREATE OR REPLACE PROCEDURE UPDATE_LEADERS_SCORE (IN in_School_ID INTEGER, IN in_Leader_Score INTEGER)
  LANGUAGE SQL
  
	BEGIN 
	
		UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
		SET "Leaders_Score" = in_Leader_Score
			WHERE "School_ID" = in_School_ID;
			
	END@
```

## Exercise 3, Question 3.
Inside your stored procedure, write a SQL IF statement to update the Leaders_Icon field in the CHICAGO_PUBLIC_SCHOOLS table for the school identified by in_School_ID using the following information. 
```sql
CREATE OR REPLACE PROCEDURE UPDATE_LEADERS_SCORE 
(IN in_School_ID INTEGER, IN in_Leader_Score INTEGER)
LANGUAGE SQL
  
	BEGIN 

		UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
		SET "Leaders_Score" = in_Leader_Score
			WHERE "School_ID" = in_School_ID;
			
		IF in_Leader_Score > 0 AND in_Leader_Score < 20 THEN
	      	UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
				SET "Leaders_Icon" = 'Very Weak';
	    ELSEIF in_Leader_Score < 40 THEN
	       	UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
				SET "Leaders_Icon" = 'Weak';	
	    ELSEIF in_Leader_Score < 60 THEN
	       	UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
				SET "Leaders_Icon" = 'Average';
	    ELSEIF in_Leader_Score < 80 THEN
	       	UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
				SET "Leaders_Icon" = 'Strong';
	    ELSEIF in_Leader_Score < 100 THEN
	       	UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
				SET "Leaders_Icon" = 'Very Strong';
	   	END IF;
		
	END@
```

## Exercise 3, Question 4.
Run your code to create the stored procedure.


## Exercise 4, Question 1.
Update your stored procedure definition. Add a generic ELSE clause to the IF statement that rolls back the current work if the score did not fit any of the preceding categories. 
```sql
CREATE OR REPLACE PROCEDURE UPDATE_LEADERS_SCORE 
(IN in_School_ID INTEGER, IN in_Leader_Score INTEGER)
  
	BEGIN 

		UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
		SET "Leaders_Score" = in_Leader_Score
			WHERE "School_ID" = in_School_ID;
			
		IF in_Leader_Score > 0 AND in_Leader_Score < 20 THEN
	      	UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
				SET "Leaders_Icon" = 'Very Weak';
	    ELSEIF in_Leader_Score < 40 THEN
	       	UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
				SET "Leaders_Icon" = 'Weak';	
	    ELSEIF in_Leader_Score < 60 THEN
	       	UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
				SET "Leaders_Icon" = 'Average';
	    ELSEIF in_Leader_Score < 80 THEN
	       	UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
				SET "Leaders_Icon" = 'Strong';
	    ELSEIF in_Leader_Score < 100 THEN
	       	UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
				SET "Leaders_Icon" = 'Very Strong';
      ELSE 
          ROLLBACK WORK 
	   	END IF;
		
	END@
```

## Exercise 4, Question 2.
Update your stored procedure definition again. Add a statement to commit the current unit of work at the end of the procedure. 
```sql
#SET TERMINATOR@
CREATE OR REPLACE PROCEDURE UPDATE_LEADERS_SCORE 
(IN in_School_ID INTEGER, IN in_Leader_Score INTEGER)
  
	BEGIN 

		UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
		SET "Leaders_Score" = in_Leader_Score
			WHERE "School_ID" = in_School_ID;
			
		IF in_Leader_Score > 0 AND in_Leader_Score < 20 THEN
	      	UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
				SET "Leaders_Icon" = 'Very Weak';
	    ELSEIF in_Leader_Score < 40 THEN
	       	UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
				SET "Leaders_Icon" = 'Weak';	
	    ELSEIF in_Leader_Score < 60 THEN
	       	UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
				SET "Leaders_Icon" = 'Average';
	    ELSEIF in_Leader_Score < 80 THEN
	       	UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
				SET "Leaders_Icon" = 'Strong';
	    ELSEIF in_Leader_Score < 100 THEN
	       	UPDATE `ferrous-destiny-344108.ibm.chicago_public_schools`
				SET "Leaders_Icon" = 'Very Strong';
      ELSE 
          ROLLBACK WORK 
	   	END IF;
          COMMIT WORK
		
	END@
```










