# Salaries Differences

https://platform.stratascratch.com/coding/10308-salaries-differences?code_type=3
## Solution
```sql
 select (e.engineersalary - b.marketingsalary) as salaryDIFF

 from

 ( 
 select max(salary) as engineersalary from db_employee where department_id = 4
 )as e,
 
 (
  select max(salary) as marketingsalary from db_employee where department_id = 1
  )as b
  ```
## Notes
  ```
Table shows department ID "4" = marketing
Table shows department ID "1" = engineering
  
select max(salary) as engineersalary from db_employee where department_id = 4
"shows the max salary for the marketing department"

the same query above but replacing "engineersalary" with "marketingsalary" and changing the department_id to = 1
will provide the max salary for the engineering department

engineersalary & marketingsalary is something we've renamed so could be named as anything we'd like.
  
select (e.engineersalary - b.marketingsalary) as salaryDIFF is the MAIN QUERY
  
select max(salary) as engineersalary from db_employee where department_id = 4
 )as e,
 
 (
  select max(salary) as marketingsalary from db_employee where department_id = 1
  )as b
  
These are the two subqueries used for the main query so that we could calculate the difference between the two salaries
