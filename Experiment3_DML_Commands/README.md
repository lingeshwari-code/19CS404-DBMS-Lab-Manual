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
--<img width="1005" height="297" alt="Screenshot 2025-09-29 140625" src="https://github.com/user-attachments/assets/f141766a-8e3a-4335-8213-d02b5b4c7029" />


```sql
UPDATE products
SET sell_price=sell_price *1.10
WHERE category='Bakery';
```

**Output:**

<img width="988" height="432" alt="Screenshot 2025-09-29 140827" src="https://github.com/user-attachments/assets/86bab376-b807-4486-af23-10442309a330" />

**Question 2**
---
<img width="984" height="479" alt="Screenshot 2025-09-29 140657" src="https://github.com/user-attachments/assets/364df69e-3404-480b-a187-3f63b73beae6" />

```sql
UPDATE suppliers
SET address='58 Lakeview, Magnolia'
WHERE supplier_id=5;
```

**Output:**

<img width="1109" height="313" alt="Screenshot 2025-09-29 140953" src="https://github.com/user-attachments/assets/56b3b4c7-4a71-4add-83ca-e9ca385df9fc" />

**Question 3**
---
<img width="744" height="547" alt="Screenshot 2025-09-29 141057" src="https://github.com/user-attachments/assets/6fa83b9c-bee9-454e-93d1-11761028d216" />


```sql
DELETE FROM Doctors
WHERE specialization IS NULL;
```

**Output:**
<img width="527" height="338" alt="Screenshot 2025-09-29 141120" src="https://github.com/user-attachments/assets/e8454254-a3cc-4641-abb7-5eca5dc2beed" />


**Question 4**
---<img width="1196" height="458" alt="Screenshot 2025-09-29 141242" src="https://github.com/user-attachments/assets/9e3b43b8-5123-48ae-95a5-b229ee9a9ec5" />


```sql
DELETE FROM Customer
WHERE CUST_COUNTRY NOT IN ('India','USA');
```

**Output:**
<img width="1166" height="463" alt="Screenshot 2025-09-29 141304" src="https://github.com/user-attachments/assets/625a3bff-d2af-45bc-a0f2-373a9a89496e" />

**Question 5**
---
<img width="1173" height="472" alt="Screenshot 2025-09-29 141459" src="https://github.com/user-attachments/assets/c2177f5f-ca34-4f12-a596-37fde16737b9" />

```sql
SELECT customer_id,cust_name, city, grade,
salesman_id
FROM customer
WHERE grade>100;
```

**Output:**
<img width="1164" height="369" alt="Screenshot 2025-09-29 141528" src="https://github.com/user-attachments/assets/249037c4-9ca9-4385-9275-2490a1065b2c" />


**Question 6**
---
<img width="1086" height="533" alt="Screenshot 2025-09-29 141642" src="https://github.com/user-attachments/assets/5a5647f5-6a7b-4a53-a2a3-d4b925fbf045" />


```sql
SELECT salesman_id, name, city, commission
FROM salesman
WHERE commission BETWEEN 0.12 AND 0.14;
```

**Output:**
<img width="1012" height="430" alt="Screenshot 2025-09-29 141658" src="https://github.com/user-attachments/assets/64c86d21-1b88-4336-8497-1d11de3e72a8" />


**Question 7**
---
<img width="1175" height="597" alt="Screenshot 2025-09-29 141845" src="https://github.com/user-attachments/assets/b6bde6cc-3e5e-4671-8458-dc9f4c46e687" />

```sql
SELECT 
    id,
    value2,
    CASE
       WHEN value2 < 10 THEN 'Small'
       WHEN value2 BETWEEN 10 AND 50 THEN 'Medium'
       WHEN value2>50 THEN 'Large'
    END AS size_category
FROM
    calculations;
```

**Output:**
<img width="850" height="474" alt="Screenshot 2025-09-29 141857" src="https://github.com/user-attachments/assets/1dc4c832-435b-47bf-910b-0f44d795c731" />


**Question 8**
---
<img width="1141" height="466" alt="Screenshot 2025-09-29 142017" src="https://github.com/user-attachments/assets/2ee23b54-7102-475f-849c-ffe1e4d81bd2" />

```sql
SELECT customer_id,cust_name, city, grade,
salesman_id
FROM customer
WHERE city= 'New York' OR grade > 200;
```

**Output:**
<img width="1129" height="370" alt="Screenshot 2025-09-29 142033" src="https://github.com/user-attachments/assets/635d266f-66bf-41ce-aa7e-ae93f1052ee0" />

**Question 9**
---
<img width="1181" height="539" alt="Screenshot 2025-09-29 142148" src="https://github.com/user-attachments/assets/dbc0eb45-eaea-45dd-ae7c-f5f71c616395" />

```sql
SELECT ord_no, purch_amt, ord_date, customer_id,
salesman_id
FROM orders
WHERE purch_amt BETWEEN 500 AND 4000
AND purch_amt NOT IN(948.50, 1983.43);
```

**Output:**
<img width="1164" height="323" alt="Screenshot 2025-09-29 142205" src="https://github.com/user-attachments/assets/787e37fa-61fd-40ea-9a43-9c2e454fc534" />


**Question 10**
---
<img width="890" height="505" alt="Screenshot 2025-09-29 142433" src="https://github.com/user-attachments/assets/fe391a4e-892b-4c6d-83eb-be629b1d5f87" />

```sql
SELECT
   first_name,
   last_name,
   CAST(julianday(discharge_date)-
julianday(admission_date)AS INTEGER)+1.0 AS no_of_days
FROM
   patients
WHERE
   julianday(discharge_date) - julianday(admission_date)> 3;
```

**Output:**
<img width="776" height="326" alt="Screenshot 2025-09-29 142450" src="https://github.com/user-attachments/assets/583de075-b114-4d5f-9232-0f3e32f5c546" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
