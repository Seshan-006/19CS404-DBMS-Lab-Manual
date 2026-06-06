# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Write a SQL statement to double the availability of the product with product_id 1.

products table

---------------
product_id
product_name
category_id
availability

```sql
-- update products
set availability = availability * 2
where product_id = 1;
```

**Output:**

<img width="1200" height="229" alt="438644100-22995305-5814-41ba-a545-d2410f3789bb" src="https://github.com/user-attachments/assets/6c962a91-c5dc-4856-9e2b-b1c652103e36" />


**Question 2**
---
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'


Employees table
---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id


```sql
-- update Employees 
set SALARY = SALARY * 2 
where job_id like "%MAN"
```

**Output:**

<img width="1186" height="339" alt="438644761-e66fb081-fc98-4845-870e-4e213068948f" src="https://github.com/user-attachments/assets/ff775e73-ce7f-4466-a6e2-e50d335887c0" />


**Question 3**
---
-- Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

```sql
-- update Suppliers
set address = '58 Lakeview, Magnolia'
where supplier_id=5
```

**Output:**
<img width="1191" height="384" alt="438645044-47556b01-6642-46e8-90e0-d47dc429b5e8" src="https://github.com/user-attachments/assets/2e92fc8d-f12f-4b6b-ac4f-738ed5018a18" />




**Question 4**
---
-- Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
-- update Employees 
set EMAIL = 'Unavailable'
```

**Output:**

<img width="1177" height="445" alt="438645302-06e2e3cd-3308-4e05-a3e9-d174d180b16d" src="https://github.com/user-attachments/assets/80c0ed28-5a81-4436-a9be-e57542ccc8b0" />


**Question 5**
---
-- Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
-- UPDATE  PRODUCTS 
set reorder_lvl = reorder_lvl * 0.7
where product_name like '%cream%' and quantity > reorder_lvl;
```

**Output:**

<img width="1185" height="483" alt="438645590-0dac1f67-600d-4e7b-a9e2-b30506b15e22" src="https://github.com/user-attachments/assets/c1646f59-6c21-41f7-a64a-79d588c0f0fb" />


**Question 6**
---
-- Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 |BBBBSBB      | A008       

```sql
-- delete FROM Customer
where CUST_CITY <>'New York' and OUTSTANDING_AMT > 5000;
```

**Output:**

<img width="1179" height="560" alt="438645975-78864722-0448-4e14-81d5-e8622fad2ced" src="https://github.com/user-attachments/assets/d2cde7ed-f355-4496-9dac-37a4257a5725" />


**Question 7**
---
-- Write a SQL query to Delete customers from 'customer' table where 'GRADE' is odd.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008     


```sql
-- delete from Customer
where grade%2=1;
```

**Output:**

<img width="1193" height="417" alt="438646398-8a2ed82a-77c6-45ad-ba68-86ad9bf18f3a" src="https://github.com/user-attachments/assets/cde23d11-b12c-4952-a86e-3315fac2cc92" />


**Question 8**
---
-- Write a SQL query to Delete All Doctors with a NULL Specialization

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
-- delete from Doctors
where specialization is null;
```

**Output:**

<img width="985" height="753" alt="438647740-4d4af6a2-6a17-4d4c-974d-74d7586510e2" src="https://github.com/user-attachments/assets/b66bc7ce-dc4c-4113-8184-ac512c5198d2" />


**Question 9**
---
-- Show the categoryName and description from the categories table sorted by categoryName.

name                     type
---------------       ---------------
CategoryID           INTEGER
CategoryName     VARCHAR(25)
Description          VARCHAR(255)

```sql
-- select CategoryName,Description from categories
order by CategoryName ASC;
```

**Output:**

<img width="931" height="379" alt="438648192-d4041812-1932-4172-b8e1-e60c30d00330" src="https://github.com/user-attachments/assets/10bb852a-e62d-4435-8c79-8ada3adee553" />


**Question 10**
---
-- Write a SQL query to categorize value1 in the Calculations table as 'High' if it is greater than 50, otherwise 'Low'.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0

```sql
-- select id,value1,
    case
        when value1 > 50 then 'High'
        else 'Low'
    end as value_category
from Calculations;
```

**Output:**
<img width="623" height="197" alt="438648425-9d7ee5a6-d8af-433b-aa93-4911bcc16c4e" src="https://github.com/user-attachments/assets/a374ff89-1c68-4bd4-83ba-1cb4d5b796aa" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
