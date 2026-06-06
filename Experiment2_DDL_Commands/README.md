# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
-- Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

EmployeeID  Name         Position
----------  -----------  ----------
4           Emily White  Analyst

Note: The Department and Salary columns will use their default values.    
For example:

Test	Result
SELECT EmployeeID, Name, Position 
FROM Employee;
EmployeeID  Name         Position
----------  -----------  ----------
4           Emily White  Analyst

```sql
-- INSERT INTO Employee(EmployeeID,Name,Position)
VALUES(4,'Emily White','Analyst');
```

**Output:**

<img width="892" height="427" alt="image" src="https://github.com/user-attachments/assets/4cae3f80-4144-415e-b9d8-29a7c8de249b" />

**Question 2**
---
-- Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

 

 

For example:

Test	Result
pragma table_info('Companies');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          int         0                       0
1           name        varchar(50  0                       0
2           address     text        0                       0
3           email       varchar(50  0                       0
4           phone       varchar(10  0                       0
5           designatio  varchar(50  0                       0
6           net_salary  number      0                       

```sql
-- ALTER TABLE Companies
ADD COLUMN designation varchar(50);
ALTER TABLE Companies
ADD COLUMN net_salary number;
```

**Output:**

<img width="1233" height="504" alt="image" src="https://github.com/user-attachments/assets/268b1ea3-1604-4ad5-bb62-2db6beeb3470" />



**Question 3**
---
-- Create a table named Orders with the following columns:

OrderID as INTEGER
OrderDate as TEXT
CustomerID as INTEGER
For example:

Test	Result
pragma table_info('Orders');
cid   name        type        notnull     dflt_value  pk
----  ----------  ----------  ----------  ----------  ----------
0     OrderID     INTEGER     0                       0
1     OrderDate   TEXT        0                       0
2     CustomerID  INTEGER     0                       0

```sql
-- CREATE TABLE Orders(OrderID INTEGER,OrderDate TEXT,CustomerID INTEGER);
```

**Output:**

<img width="1251" height="477" alt="image" src="https://github.com/user-attachments/assets/dfee8840-7e42-4cbf-91f6-02f5bb67f8ef" />


**Question 4**
---
-- Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.
For example:

Test	Result
INSERT INTO Invoices (InvoiceID, InvoiceDate)
VALUES (1, '2024-08-08'),(1,'2024-09-08');
Error: UNIQUE constraint failed: Invoices.InvoiceID


```sql
-- CREATE TABLE Invoices(InvoiceID INTEGER PRIMARY KEY,InvoiceDate DATE,DueDate DATE CHECK(DueDate>InvoiceDate),Amount REAL CHECK(Amount>0));
```

**Output:**
<img width="873" height="368" alt="image" src="https://github.com/user-attachments/assets/f1439391-d3e6-459e-820b-29d85000e762" />


**Question 5**
---
-- Create a table named Tasks with the following columns:

TaskID as INTEGER
TaskName as TEXT
DueDate as DATE
For example:

Test	Result
pragma table_info('Tasks');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           TaskID      INTEGER     0                       0
1           TaskName    TEXT        0                       0
2           DueDate     DATE        0                       0


```sql
-- CREATE TABLE Tasks(TaskID INTEGER,TaskName TEXT,DueDate DATE);
```

**Output:**

<img width="898" height="482" alt="image" src="https://github.com/user-attachments/assets/ebea2ace-bbff-4e6f-98f3-6d583f713aa4" />


**Question 6**
---
-- Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT
For example:

Test	Result
pragma table_info('Locations');
cid       name             type        notnull     dflt_value  pk
--------  ---------------  ----------  ----------  ----------  ----------
0         LocationID       INTEGER     0                       0
1         LocationName     TEXT        0                       0
2         Address          TEXT        0                       0


```sql
-- CREATE TABLE Locations(LocationID INTEGER,LocationName TEXT,Address TEXT);
```

**Output:**

<img width="895" height="474" alt="image" src="https://github.com/user-attachments/assets/001974b6-9241-44c1-b33d-b82895d18b84" />


**Question 7**
---
-- In the Cusomers table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

CustomerID  Name          Address      City        ZipCode
----------  ------------  ----------   ----------  ----------
306         Diana Prince  Themyscira
307         Bruce Wayne   Wayne Manor  Gotham      10007
308         Peter Parker  Queens                   11375
 

For example:

Test	Result
SELECT * FROM Customers;
CustomerID  Name          Address     City        ZipCode
----------  ------------  ----------  ----------  ----------
306         Diana Prince  Themyscira
307         Bruce Wayne   Wayne Mano  Gotham      10007
308         Peter Parker  Queens                  11375


```sql
-- INSERT INTO Customers(CustomerID,Name,Address,City,Zipcode)
VALUES(306, 'Diana Prince','Themyscira',NULL,NULL),
    (307,'Bruce Wayne','Wayne Mano','Gotham',10007),
    (308,'Peter Parker','Queens',NULL,11375);

     
```

**Output:**

<img width="874" height="379" alt="image" src="https://github.com/user-attachments/assets/345ff92f-a03b-4d4e-b2b2-3d69958aa6c6" />


**Question 8**
---
-- Create a table named Reviews with the following columns:

ReviewID as INTEGER
ProductID as INTEGER
Rating as REAL
ReviewText as TEXT
For example:

Test	Result
pragma table_info('Reviews');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           ReviewID    INTEGER     0                       0
1           ProductID   INTEGER     0                       0
2           Rating      REAL        0                       0
3           ReviewText  TEXT        0                       0


```sql
-- CREATE TABLE Reviews(ReviewID INTEGER,ProductID INTEGER,Rating REAL,ReviewText TEXT); 
```

**Output:**

<img width="871" height="481" alt="image" src="https://github.com/user-attachments/assets/4b4d645a-7b28-449f-8529-9d224f4b5e40" />


**Question 9**
---
-- Insert all students from Archived_students table into the Student_details table.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      INT           0                       1
1           Name        VARCHAR(100)  0                       0
2           Gender      VARCHAR(10)   0                       0
3           Subject     VARCHAR(50)   0                       0
4           MARKS       INT           0                       0
For example:

Test	Result
select * from student_details;
RollNo      Name           Gender      Subject     MARKS
----------  -------------  ----------  ----------  ----------
1           Alice Johnson  Female      Math        85
2           Bob Smith      Male        Science     90
3           Charlie Brown  Male        English     78


```sql
-- INSERT INTO student_details
SELECT* FROM Archived_students;
```

**Output:**

<img width="871" height="365" alt="image" src="https://github.com/user-attachments/assets/1e3b8915-ee2f-4214-b6a2-dd325ed4521f" />


**Question 10**
---
-- Write an SQL command can to add a column named email of type TEXT to the customers table

 

For example:

Test	Result
pragma table_info('Customers');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          integer     0                       0
1           name        text        0                       0
2           email       TEXT        0                      

```sql
-- ALTER TABLE Customers 
ADD COLUMN email TEXT;


```

**Output:**

<img width="899" height="389" alt="image" src="https://github.com/user-attachments/assets/52288cfd-130a-4252-994a-3d50ba780d59" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
