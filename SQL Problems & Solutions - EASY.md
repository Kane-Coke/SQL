#  Calculate The Difference Between The Highest Salaries In Two Departments

https://platform.stratascratch.com/coding/10308-salaries-differences?code_type=3
## Solution
```sql
SELECT (e.engineersalary - b.marketingsalary) AS salaryDIFF

FROM

( 
 SELECT max(salary) AS engineersalary FROM db_employee WHERE department_id = 4
)AS e,

(
  SELECT max(salary) AS marketingsalary FROM db_employee WHERE department_id = 1
)AS b
  ```
### Notes
  
###### Table shows department ID "4" = marketing

###### Table shows department ID "1" = engineering


   ```sql
SELECT max(salary) AS engineersalary FROM db_employee WHERE department_id = 4
```
> shows the max salary for the engineering department




###### The same query above but replacing "engineersalary" with "marketingsalary" and changing the department_id to = 1 will provide the max salary for the marketing department

###### engineersalary & marketingsalary is something we've renamed so could be named as anything we'd like.
```sql  
SELECT (e.engineersalary - b.marketingsalary) AS salaryDIFF
```
> the main query
```sql  
( 
 SELECT max(salary) AS engineersalary FROM db_employee WHERE department_id = 4
)AS e,

(
  SELECT max(salary) AS marketingsalary FROM db_employee WHERE department_id = 1
)AS b
  ```
>
> These are the two subqueries used for the main query so that we could calculate the difference between the two salaries

# Calculate The Number Of Shipments Per Month

https://platform.stratascratch.com/coding/2056-number-of-shipments-per-month?code_type=3
## Solution
```sql
SELECT count(shipment_id), date_format (shipment_date, '%Y-%m') AS month_year 
FROM amazon_shipment
GROUP BY month_year;
```
### Notes
```sql
SELECT COUNT(shipment_id)
```
>Returned the number of records in the 'shipment_id' column

```sql
DATE_FORMAT (shipment_date, '%Y-%m') AS month_year
```
>this changed the date format  of ‘shipment_date’ 

###### “%Y” = Year as a numeric, 4-Digit Value 
###### “%m” = Month name as a numeric value (00 to 12)
###### “as month_year” = was used to rename the column

```sql
GROUP BY month_year
```
>Was used to group the row of values into a summary row

# Calculate The Total Revenue Of Each Customer (Specific Time-Frame) - MEDIUM -

https://platform.stratascratch.com/coding/9782-customer-revenue-in-march?code_type=3

## Solution
```sql
SELECT cust_id, SUM(total_order_cost) AS revenue FROM orders
WHERE order_date BETWEEN '2019-03-01' AND '2019-03-31' 
GROUP BY cust_id
ORDER BY revenue desc;
```

### Notes

```sql
SELECT cust_id
```
>cust_id was representative of each customer 

```sql
SUM(total_order_cost) AS revenue FROM orders
```
>returned the total sum of the 'total_order_cost' numeric column

```sql
AS revenue
```
>revenue is what we’ve named the column for the sum of 'total_order_cost'

```sql
WHERE order_date BETWEEN '2019-03-01' AND '2019-03-31'
```
>we used ‘between’ to only provide values from the 'order_date' column that was within the specific month

```sql
GROUP BY cust_id
```
>used rather than DISTINCT seeing as we grouped row based on specific column and also used aggregate functions
```sql
ORDER BY revenue desc;
```
>sorted into a descending order based on the revenue



