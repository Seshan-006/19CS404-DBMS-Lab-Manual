# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
-- What is the average dosage prescribed for each medication?

Sample tablePrescriptions Table

Medication     AvgDosage
-------------  ----------
Ciprofloxacin  500.0
Doxorubicin    60.0
Ibuprofen      400.0
Levothyroxine  50.0
Lisinopril     10.0
MMR            0.5
Pending        0.0
Prenatal vita  1.0
Sertraline     50.0
Topiramate     25.0

```sql
-- SELECT
  Medication,
  AVG(Dosage) AS AvgDosage
FROM
  Prescriptions
GROUP BY
  Medication;

```

**Output:**

<img width="697" height="745" alt="438733614-cbf06455-04ba-4d64-899c-19b9f6285e48" src="https://github.com/user-attachments/assets/aea5fc88-9a55-485c-af18-6a81a9bd97a1" />


**Question 2**
---
-- How many patients are there in each city?

Sample table: Patients Table

Address     TotalPatients
----------  -------------
Berlin      3
Chicago     4
Mexico      3

```sql
-- select Address,count(*)
as TotalPatients
from Patients
group by Address 
```

**Output:**

<img width="661" height="396" alt="438736526-8d4957fe-fb4f-4c02-a28e-1f6c65c3430c" src="https://github.com/user-attachments/assets/0e7f9a58-4692-4968-8d82-a30d2997eea1" />


**Question 3**
---
-- Write a SQL Query to find how many medications are prescribed for each patient?

Sample table:MedicalRecords Table

PatientID   AvgMedications
----------  --------------
4           5
6           1
7           1
8           3


```sql
--SELECT PatientID,COUNT(*) AS 
AvgMedications
FROM MedicalRecords
GROUP BY PatientID;
```

**Output:**

<img width="679" height="614" alt="438736832-03cd9d50-06b5-4812-9c53-729d7557944f" src="https://github.com/user-attachments/assets/aa211016-36be-489a-816b-aace3c0fbd79" />

**Question 4**

-- Write a SQL query to find the maximum purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001


```sql
-- SELECT
  MAX(purch_amt) AS MAXIMUM
FROM
  orders;
```
**Output:**
<img width="408" height="298" alt="438737116-3b0552ba-cb0f-47b2-a14f-4f41e3f13b8a" src="https://github.com/user-attachments/assets/9f4ecb3c-5058-4abd-8279-3c9da1b13470" />

**Question 5**

-- Write a SQL query to find the total income of employees aged 40 or above.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
-- SELECT
  SUM(income) AS total_income
FROM
  employee
WHERE
  age >= 40;
```

**Output:**

<img width="442" height="308" alt="438737389-7dd0627c-5b47-45cd-9da2-b4c8b2308c33" src="https://github.com/user-attachments/assets/e9edddbe-9f4f-4d23-b58f-d2e0de9adb8d" />

**Question 6**
---
-- Write a SQL query to find the number of employees whose age is greater than 32.

Sample table: employee

SELECT
  COUNT(*) AS COUNT
FROM
  employee
WHERE
  age > 32;

```sql
-- SELECT
  COUNT(*) AS COUNT
FROM
  employee
WHERE
  age > 32; 
```

**Output:**

<img width="439" height="321" alt="438737785-facbdbb0-4fdf-4680-a2f2-05496c32ebde" src="https://github.com/user-attachments/assets/aafcb1bc-14d8-4f1e-afc7-9e7644641992" />


**Question 7**
---
-- Write a SQL query to find the average length of names for people living in Chennai?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER

```sql
-- SELECT
  AVG(LENGTH(name)) AS avg_name_length
FROM
  customer
WHERE
  city = 'Chennai';
```

**Output:**

<img width="445" height="296" alt="438738011-d162dc9e-2f89-4e8d-ace5-ffa4b385b7bb" src="https://github.com/user-attachments/assets/c6a6cc7d-d223-43a6-a246-05d8fa564d52" />


**Question 8**
---
-- Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the maximum work hours for each date, and excludes dates where the maximum work hour is not greater than 12.

Sample table: employee1

jdate       MAX(workhour)
----------  -------------
2004.0      15
2006.0      15

```sql
-- SELECT
  jdate,
  MAX(workhour) AS "MAX(workhour)"
FROM
  employee1
GROUP BY
  jdate
HAVING
  MAX(workhour) > 12;
```

**Output:**
<img width="673" height="376" alt="438738394-4f18be9a-1667-4bc1-825b-115d62e6f1c9" src="https://github.com/user-attachments/assets/2f48d794-e876-4907-a807-815cd46c0fcb" />




**Question 9**
---
-- Write the SQL query that achieves the grouping of data by occupation, calculates the total work hours for each occupation, and excludes occupations where the total work hour sum is not greater than 20.

Sample table: employee1

occupation  SUM(workhour)
----------  -------------
Business    30
Doctor      30
Engineer    24
Teacher     27

```sql
-- SELECT
  occupation,
  SUM(workhour) AS "SUM(workhour)"
FROM
  employee1
GROUP BY
  occupation
HAVING
  SUM(workhour) > 20;
```

**Output:**

<img width="619" height="432" alt="438738762-ed11db98-a58b-4cb2-934b-49a26899d26b" src="https://github.com/user-attachments/assets/5afffc8b-13e1-41eb-b012-638799c3b160" />


**Question 10**
---
-- Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1

occupation  AVG(workhour)
----------  -------------
Business    10.0
Engineer    12.0

```sql
-- SELECT
  occupation,
  AVG(workhour) AS "AVG(workhour)"
FROM
  employee1
GROUP BY
  occupation
HAVING
  AVG(workhour) BETWEEN 10 AND 12;
```

**Output:**

<img width="757" height="392" alt="438739091-2feda0d6-0e59-4af8-a0b6-15ea0c411c22" src="https://github.com/user-attachments/assets/1dbb0295-89c6-46e9-87ff-69556b21d0ca" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
