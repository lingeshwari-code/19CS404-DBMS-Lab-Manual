# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
<img width="1142" height="325" alt="Screenshot 2025-09-29 155727" src="https://github.com/user-attachments/assets/19bf6f57-16ab-42d0-884c-a03c02b76971" />

```sql
SELECT
    s.*
FROM
    salesman s
LEFT JOIN
    customer c ON s.salesman_id = c.salesman_id
WHERE
    c.cust_name = 'Fabian Johns';

```

**Output:**
<img width="1097" height="308" alt="Screenshot 2025-09-29 160135" src="https://github.com/user-attachments/assets/1b088f74-8b3f-4c89-97eb-91200b242e2c" />

**Question 2**
---
<img width="1088" height="767" alt="Screenshot 2025-09-29 155750" src="https://github.com/user-attachments/assets/e9992312-c091-4f75-9f34-b4abe980e71a" />

```sql
SELECT
    ord_no,
    purch_amt,
    cust_name,
    city
FROM
    orders
INNER JOIN
    customer ON orders.customer_id = customer.customer_id
WHERE
    purch_amt BETWEEN 500 AND 2000;
```

**Output:**
<img width="1092" height="366" alt="Screenshot 2025-09-29 160146" src="https://github.com/user-attachments/assets/f6f6f17f-5a5e-457f-98c6-022a98612614" />

**Question 3**
---
<img width="1301" height="586" alt="Screenshot 2025-09-29 155806" src="https://github.com/user-attachments/assets/727d8d0d-6ea9-4670-8f21-2fe8d8d60a19" />

```sql
SELECT
    p.first_name AS patient_name,
    a.*
FROM
    patients AS p
INNER JOIN
    appointments AS a
ON
    p.patient_id = a.patient_id;
```

**Output:**
<img width="686" height="398" alt="Screenshot 2025-09-29 160158" src="https://github.com/user-attachments/assets/c24e6c1b-18d5-49fb-a844-0f4308f8ba72" />

**Question 4**
---
<img width="1290" height="548" alt="Screenshot 2025-09-29 155820" src="https://github.com/user-attachments/assets/740890f9-f339-45ab-b8c7-564ff48bb0fc" />

```sql
SELECT
    p.*
FROM
    patients p
INNER JOIN
    test_results tr ON p.patient_id = tr.patient_id
WHERE
    tr.test_date BETWEEN '2024-03-01' AND '2024-03-31';
```

**Output:**
<img width="842" height="268" alt="Screenshot 2025-09-29 160212" src="https://github.com/user-attachments/assets/23ce8b93-9d6a-4ad9-98d2-7bdca6071ea3" />


**Question 5**
---
<img width="1289" height="734" alt="Screenshot 2025-09-29 155835" src="https://github.com/user-attachments/assets/35b6c315-8f60-44d7-8f84-da275ac5ff9b" />

```sql
SELECT
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission
FROM
    customer c
INNER JOIN
    salesman s ON c.salesman_id = s.salesman_id
WHERE
    c.city <> s.city
    AND s.commission > 0.12;
```

**Output:**

<img width="1271" height="499" alt="Screenshot 2025-09-29 160224" src="https://github.com/user-attachments/assets/8433c246-6eaf-4572-954f-824ac9a86d04" />

**Question 6**
---
<img width="1242" height="768" alt="Screenshot 2025-09-29 160000" src="https://github.com/user-attachments/assets/e3f63990-7403-4fa5-9bb0-6af86ee050a8" />

```sql
SELECT
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.commission
FROM
    customer c
INNER JOIN
    salesman s ON c.salesman_id = s.salesman_id
WHERE
    s.commission > 0.12;
```

**Output:**
<img width="1101" height="605" alt="Screenshot 2025-09-29 160235" src="https://github.com/user-attachments/assets/9d8dfe07-ba45-4a76-a2e9-f2e78303644a" />

**Question 7**
---
<img width="1215" height="473" alt="Screenshot 2025-09-29 160015" src="https://github.com/user-attachments/assets/5eb3fd91-6103-45de-9210-8ebc0431e279" />

```sql
SELECT
    c.cust_name
FROM
    customer c
LEFT JOIN
    orders o ON c.customer_id = o.customer_id;
```

**Output:**
<img width="313" height="330" alt="Screenshot 2025-09-29 160254" src="https://github.com/user-attachments/assets/09e5ca54-80c1-4c5f-9e58-ffcd3f39344d" />

**Question 8**
---
<img width="1300" height="562" alt="Screenshot 2025-09-29 160029" src="https://github.com/user-attachments/assets/5cca1501-2306-43ae-a524-63665d66551a" />

```sql
SELECT
    n.nurse_id,
    d.department_name
FROM
    nurses n
INNER JOIN
    departments d ON n.department_id = d.department_id
WHERE
    n.first_name = 'David'
    AND n.last_name = 'Moore';
```

**Output:**
<img width="594" height="308" alt="Screenshot 2025-09-29 160304" src="https://github.com/user-attachments/assets/b8ff31cf-1d63-4ff3-9df8-1728d072d52b" />

**Question 9**
---
<img width="1328" height="806" alt="Screenshot 2025-09-29 160055" src="https://github.com/user-attachments/assets/0801f179-aa1f-4d50-b32f-46c24ef977bf" />

```sql
SELECT
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount"
FROM
    customer c
LEFT JOIN
    orders o ON c.customer_id = o.customer_id
ORDER BY
    o.ord_date;
```

**Output:**
<img width="629" height="327" alt="Screenshot 2025-09-29 160318" src="https://github.com/user-attachments/assets/953ac5fe-8b11-4fd0-9085-11479317426d" />

**Question 10**
---
<img width="1059" height="776" alt="Screenshot 2025-09-29 160112" src="https://github.com/user-attachments/assets/687c31ff-8232-43f0-9b83-33dc7a83afdc" />

```sql
SELECT
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.commission
FROM
    customer c
INNER JOIN
    salesman s ON c.salesman_id = s.salesman_id;
```

**Output:**
<img width="522" height="253" alt="Screenshot 2025-09-29 160335" src="https://github.com/user-attachments/assets/5b694791-1ee0-4951-abeb-5b5bff89563b" />

## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
<img width="1456" height="248" alt="image" src="https://github.com/user-attachments/assets/b0d2a0dd-7a6c-41f9-80c3-5219dcd11e9d" />

