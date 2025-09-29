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
<img width="1313" height="381" alt="Screenshot 2025-09-29 131819" src="https://github.com/user-attachments/assets/b84bda96-20f7-4b6a-afb8-8132d5914a6d" />

```sql
ALTER TABLE Employees
ADD COLUMN Date_of_joining Date;
ALTER TABLE Employees
RENAME COLUMN job_title TO Designation;
```

**Output:**

<img width="1195" height="256" alt="Screenshot 2025-09-29 133642" src="https://github.com/user-attachments/assets/def8e97b-afd3-4dd4-9c24-f7821519b2ca" />


**Question 2**
---
<img width="1261" height="444" alt="Screenshot 2025-09-29 131944" src="https://github.com/user-attachments/assets/0119c6f8-9943-4d7d-b824-1c6b02844de4" />

```sql
CREATE TABLE Employees(
EmployeeID PRIMARY KEY,
FirstName NOT NULL,
LastName NOT NULL,
Email UNIQUE,
Salary CHECK(salary >0),
DepartmentID INT,
FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**

<img width="1044" height="253" alt="Screenshot 2025-09-29 133740" src="https://github.com/user-attachments/assets/aef22d46-fa89-4e10-a464-10d359e264a6" />

**Question 3**
---
<img width="1203" height="417" alt="Screenshot 2025-09-29 132015" src="https://github.com/user-attachments/assets/4e00906b-5591-4a49-9c61-0a54b93453fd" />

```sql
INSERT INTO Products(Name, Category, Price, Stock)
VALUES
   ('Smartphone', 'Electronics', 800, 150),
   ('Headphones', 'Accessories', 200, 300);
```

**Output:**
<img width="919" height="260" alt="Screenshot 2025-09-29 133828" src="https://github.com/user-attachments/assets/206447ae-4c21-422f-9029-bf7335a1769b" />


**Question 4**
---
<img width="1413" height="463" alt="Screenshot 2025-09-29 132043" src="https://github.com/user-attachments/assets/f0231d07-a12d-490a-8e2e-fc754e206686" />

```sql
CREATE TABLE Invoices(
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
Amount REAL CHECK(Amount >0),
DueDate DATE,
OrderID INTEGER,
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID),
CHECK(DueDate > InvoiceDate)
);
```

**Output:**

<img width="1152" height="193" alt="Screenshot 2025-09-29 133943" src="https://github.com/user-attachments/assets/f4880ec3-982b-43b0-a36f-113459890365" />

**Question 5**
---
<img width="1188" height="501" alt="Screenshot 2025-09-29 132059" src="https://github.com/user-attachments/assets/e18cd408-2249-403b-a9c3-1e2f6fd5967b" />

```sql
INSERT INTO Books(ISBN, Title, Author)
VALUES('978-6655443321', 'Big Data Analytics', 'Karen Adams');
```

**Output:**

<img width="1063" height="247" alt="Screenshot 2025-09-29 134030" src="https://github.com/user-attachments/assets/b573bace-71f9-4d44-acd6-126c4264a5a8" />


**Question 6**
---
<img width="1384" height="412" alt="Screenshot 2025-09-29 132115" src="https://github.com/user-attachments/assets/70f6032a-4213-4cbc-970b-a95be5c4ac32" />

```sql
ALTER TABLE Student_details
ADD COLUMN ParentsNumber number;
ALTER TABLE Student_details
ADD COLUMN Adhar_Number number;
```

**Output:**

<img width="1195" height="304" alt="Screenshot 2025-09-29 134213" src="https://github.com/user-attachments/assets/1a8f68a6-c06f-4b13-9844-8265c4447740" />

**Question 7**
---
<img width="1123" height="508" alt="Screenshot 2025-09-29 132128" src="https://github.com/user-attachments/assets/7251166e-4231-40c0-bed3-867140edf4c1" />

```sql
INSERT INTO Student_details SELECT*FROM
Archived_Students;
```

**Output:**

<img width="1145" height="198" alt="Screenshot 2025-09-29 134252" src="https://github.com/user-attachments/assets/31de7e4d-4c21-44da-b013-6d796637bc6e" />

**Question 8**
---
<img width="962" height="374" alt="Screenshot 2025-09-29 132138" src="https://github.com/user-attachments/assets/6e3869cc-0bf3-415b-96db-4eb6d94d008b" />

```sql
CREATE TABLE Products(
ProductID PRIMARY KEY,
ProductName NOT NULL,
Price REAL CHECK(Price>0),
Stock INT CHECK(Stock >=0)
);
```

**Output:**
<img width="1085" height="186" alt="Screenshot 2025-09-29 134400" src="https://github.com/user-attachments/assets/8f8af746-47e4-411a-b1ee-589d48e542fd" />


**Question 9**
---
<img width="1241" height="436" alt="Screenshot 2025-09-29 132150" src="https://github.com/user-attachments/assets/720d468c-787a-461b-a202-6455eabc7103" />

```sql
CREATE TABLE Events(
EventID INTEGER,
EventName TEXT,
EventDate DATE
);
```

**Output:**

<img width="1196" height="298" alt="Screenshot 2025-09-29 132718" src="https://github.com/user-attachments/assets/781e978b-7cd3-43fd-ac55-0f3ddf3e5ffc" />

**Question 10**
---
<img width="1189" height="378" alt="Screenshot 2025-09-29 132202" src="https://github.com/user-attachments/assets/6da7d69c-7a2d-4520-988f-6894fa39936d" />


```sql
CREATE TABLE Invoices(
InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE,
DueDate DATE CHECK(DueDate>InvoiceDate),
Amount REAl CHECK(Amount>0)
);
```

**Output:**
<img width="1022" height="196" alt="Screenshot 2025-09-29 132522" src="https://github.com/user-attachments/assets/7041051a-db10-49a6-bd4e-2a4c965df615" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
