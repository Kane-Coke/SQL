#  Calculate The Difference Between The Highest Salaries In Two Departments

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
### Notes
  
###### Table shows department ID "4" = marketing

###### Table shows department ID "1" = engineering


   ```sql
select max(salary) as engineersalary from db_employee where department_id = 4
```
> shows the max salary for the engineering department




###### The same query above but replacing "engineersalary" with "marketingsalary" and changing the department_id to = 1 will provide the max salary for the marketing department

###### engineersalary & marketingsalary is something we've renamed so could be named as anything we'd like.
```sql  
select (e.engineersalary - b.marketingsalary) as salaryDIFF
```
> the main query
```sql  
( 
 select max(salary) as engineersalary from db_employee where department_id = 4
)as e,

(
  select max(salary) as marketingsalary from db_employee where department_id = 1
)as b
  ```
>
> These are the two subqueries used for the main query so that we could calculate the difference between the two salaries

# Calculate The Number Of Shipments per Month

https://platform.stratascratch.com/coding/2056-number-of-shipments-per-month?code_type=3
## Solution
```sql
select count(shipment_id), date_format (shipment_date, '%Y-%m') as month_year 
from amazon_shipment
group by month_year;
```
### Notes
```sql
date_format (shipment_date, '%Y-%m') as month_year
```
>this changed the date format  of ‘shipment_date’ 

###### “%Y” = Year as a numeric, 4-Digit Value 
###### “%m” = Month name as a numeric value (00 to 12)
###### “as month_year” = was used to rename the column

```sql
Select count(shipment_id)
```
>Returned the number of records in the shipment_id column

```sql
Group by month_year
```
>Was used to group the row of values into a summary row

