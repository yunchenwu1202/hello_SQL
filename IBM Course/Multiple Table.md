## Exercise 1: Accessing Multiple Tables with Sub-Queries
1. Problem: Retrieve only the EMPLOYEES records that correspond to jobs in the JOBS table.
```sql
 select * 
 from employees 
 where JOB_ID IN (select JOB_IDENT from jobs);
```
2. Problem: Retrieve only the list of employees whose JOB_TITLE is Jr. Designer.
```sql
 select * 
 from employees 
 where JOB_ID IN (select JOB_IDENT from jobs where JOB_TITLE= 'Jr. Designer');
```
3. Problem: Retrieve JOB information and who earn more than $70,000.
```sql
 select JOB_TITLE, MIN_SALARY,MAX_SALARY,JOB_IDENT 
 from jobs 
 where JOB_IDENT IN (select JOB_ID from employees where SALARY > 70000 );
```
4. Problem: Retrieve JOB information and whose birth year is after 1976.
```sql
 select JOB_TITLE, MIN_SALARY,MAX_SALARY,JOB_IDENT 
 from jobs 
 where JOB_IDENT IN (select JOB_ID from employees where YEAR(B_DATE)>1976 );
```
5. Problem: Retrieve JOB information for female employees whose birth year is after 1976.
```sql
 select JOB_TITLE, MIN_SALARY,MAX_SALARY,JOB_IDENT 
 from jobs 
 where JOB_IDENT IN (select JOB_ID from employees where YEAR(B_DATE)>1976 and SEX='F' );
```

## Exercise 2: Accessing Multiple Tables with Implicit Joins
1. Problem: Perform an implicit cartesian/cross join between EMPLOYEES and JOBS tables.
```sql
 select * 
 from employees, jobs;
```
2. Problem: Retrieve only the EMPLOYEES records that correspond to jobs in the JOBS table.
```sql
 select * 
 from employees, jobs 
 where employees.JOB_ID = jobs.JOB_IDENT;
```
3. Problem: Redo the previous query, using shorter aliases for table names.
```sql
 select * 
 from employees E, jobs J 
 where E.JOB_ID = J.JOB_IDENT;
```
4. Problem: Redo the previous query, but retrieve only the Employee ID, Employee Name and Job Title.
```sql
 select EMP_ID,F_NAME,L_NAME, JOB_TITLE 
 from employees E, jobs J 
 where E.JOB_ID = J.JOB_IDENT;
```
5. Problem: Redo the previous query, but specify the fully qualified column names with aliases in the SELECT clause.
```sql
 select E.EMP_ID,E.F_NAME,E.L_NAME, J.JOB_TITLE 
 from employees E, jobs J 
 where E.JOB_ID = J.JOB_IDENT;
```
