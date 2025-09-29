# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="1238" height="816" alt="Screenshot 2025-09-29 152504" src="https://github.com/user-attachments/assets/854dbd5d-ad21-4b9d-88c2-b6fce17749a8" />

```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.salesman_id
FROM orders o
JOIN salesman s ON o.salesman_id = s.salesman_id
WHERE s.commission = (SELECT MAX(commission) FROM salesman);
```

**Output:**
<img width="1009" height="463" alt="Screenshot 2025-09-29 152734" src="https://github.com/user-attachments/assets/c6b49b20-ff91-43ea-a692-6119f3c5b149" />

**Question 2**
---
<img width="1133" height="458" alt="Screenshot 2025-09-29 152517" src="https://github.com/user-attachments/assets/9820428e-4dfb-405a-b8bd-ff12884accd0" />

```sql
SELECT
  department_id,
  department_name
FROM
  Departments
WHERE
 
  LENGTH(department_name) > (
    
    SELECT
      AVG(LENGTH(department_name))
    FROM
      Departments
  );
```

**Output:**
<img width="560" height="405" alt="Screenshot 2025-09-29 152747" src="https://github.com/user-attachments/assets/0b9e78d0-04fb-472d-89ce-622fd0e419d4" />

**Question 3**
---
<img width="930" height="498" alt="Screenshot 2025-09-29 152530" src="https://github.com/user-attachments/assets/49dc7080-cdc1-4427-99b7-0411fd62456b" />

```sql
SELECT
  medication_id,
  medication_name,
  dosage
FROM
  Medications

WHERE
  dosage = (
    
    SELECT
      MIN(dosage)
    FROM
      Medications
  );
```

**Output:**
<img width="893" height="386" alt="Screenshot 2025-09-29 152758" src="https://github.com/user-attachments/assets/a76908b5-b79d-4304-8dc6-f9739e6eb458" />

**Question 4**
---
<img width="1055" height="547" alt="Screenshot 2025-09-29 152542" src="https://github.com/user-attachments/assets/84d60dc1-a7df-47a6-97fc-7f4a80eeddb3" />

```sql
SELECT
  name
FROM
  customer

WHERE

  phone IN (

    SELECT
      phone
    FROM
      customer

    GROUP BY
      phone
  
    HAVING
      COUNT(*) = 1
  );
```

**Output:**

<img width="488" height="431" alt="Screenshot 2025-09-29 152806" src="https://github.com/user-attachments/assets/9ff3b020-388e-420d-a3a5-165992dc450a" />

**Question 5**
---
<img width="1079" height="516" alt="Screenshot 2025-09-29 152558" src="https://github.com/user-attachments/assets/8572478d-bd23-48d2-a01f-eb4558b73343" />

```sql
SELECT
  name,
  city
FROM
  customer

WHERE
 
  city IN (

    SELECT
      city
    FROM
      customer
    WHERE
      id IN (3, 7)
  );
```

**Output:**

<img width="576" height="454" alt="Screenshot 2025-09-29 152818" src="https://github.com/user-attachments/assets/a2e64a13-7e08-4eaf-b085-c29be76f5d98" />

**Question 6**
---
<img width="1013" height="725" alt="Screenshot 2025-09-29 152610" src="https://github.com/user-attachments/assets/f0672836-f5c7-43b8-9ca0-40c16c08055a" />

```sql
SELECT
  customer_id,
  cust_name,
  city,
  grade,
  salesman_id
FROM
  customer

WHERE
  customer_id = (
 
    SELECT
      salesman_id
    FROM
      salesman
    WHERE
      name = 'Mc Lyon'
  ) - 2001; 
```

**Output:**

<img width="1229" height="299" alt="Screenshot 2025-09-29 152828" src="https://github.com/user-attachments/assets/146556ab-7c33-4c94-a867-574d36c3fc5d" />

**Question 7**
---
<img width="930" height="739" alt="Screenshot 2025-09-29 152623" src="https://github.com/user-attachments/assets/8276e312-c150-4d55-9edb-6c88e2b07edc" />

```sql
SELECT
  *
FROM
  CUSTOMERS

WHERE
 
  AGE < 30;
```

**Output:**

<img width="1195" height="564" alt="Screenshot 2025-09-29 152841" src="https://github.com/user-attachments/assets/abe3c730-3bb9-43ef-b369-d216ae43724a" />


**Question 8**
---
<img width="886" height="619" alt="Screenshot 2025-09-29 152636" src="https://github.com/user-attachments/assets/2c3583db-c52d-4c51-8067-8ef4d4c6106a" />

```sql
SELECT
  *
FROM
  CUSTOMERS

WHERE
  
  ADDRESS = 'Delhi';
```

**Output:**

<img width="1295" height="328" alt="Screenshot 2025-09-29 152852" src="https://github.com/user-attachments/assets/384a6d82-11f7-4f91-9c9e-9aa1fc915b0f" />

**Question 9**
---
<img width="1027" height="673" alt="Screenshot 2025-09-29 152700" src="https://github.com/user-attachments/assets/7cef3850-dd80-4d77-8088-61061e520c61" />

```sql
select commission from salesman
where salesman_id in (select (salesman_id)
from customer
where city='Paris'
);
```

**Output:**
<img width="332" height="310" alt="Screenshot 2025-09-29 152904" src="https://github.com/user-attachments/assets/5d5b30a7-d833-4217-a1b3-3fbd03e59219" />


**Question 10**
---
<img width="1236" height="568" alt="Screenshot 2025-09-29 152715" src="https://github.com/user-attachments/assets/30ab7c18-4bee-4f12-b34a-0c43e5cfede8" />

```sql
select *
from orders
where salesman_id in (
select salesman_id 
from orders
where customer_id=3007);
```

**Output:**

<img width="1226" height="417" alt="Screenshot 2025-09-29 152914" src="https://github.com/user-attachments/assets/9b99c568-b596-4f72-8aaa-dbd824027587" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
<img width="1460" height="217" alt="Screenshot 2025-09-29 154131" src="https://github.com/user-attachments/assets/64e66963-6a55-4cd6-9db5-2a3a89585eb9" />

