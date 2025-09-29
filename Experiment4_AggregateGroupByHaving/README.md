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
<img width="995" height="533" alt="Screenshot 2025-09-29 145324" src="https://github.com/user-attachments/assets/35a29eed-abb5-4df0-b30b-2ed9326834f7" />

```sql
SELECT 
PatientID,
COUNT(*) AS TotalRecords
FROM
MedicalRecords
GROUP BY
PatientID;
```

**Output:**
<img width="595" height="629" alt="Screenshot 2025-09-29 150858" src="https://github.com/user-attachments/assets/c04d5cce-ed30-4b19-adda-2925a2cda3be" />


**Question 2**
---
<img width="1010" height="463" alt="Screenshot 2025-09-29 145338" src="https://github.com/user-attachments/assets/a27231da-29fb-42b5-8de6-fd7cb5987e0a" />

```sql
select strftime('%Y-%m',Date)as Month,count(*) as TotalRecords
from MedicalRecords
group by Month
order by Month;
```

**Output:**
<img width="586" height="411" alt="Screenshot 2025-09-29 150910" src="https://github.com/user-attachments/assets/6c35ba8e-9baf-4c04-9ec5-f692e94782f2" />


**Question 3**
---
<img width="996" height="650" alt="Screenshot 2025-09-29 145421" src="https://github.com/user-attachments/assets/16e72cfa-3537-4999-8210-fdfbef8ce437" />

```sql
SELECT 
    InsuranceCompany,
    COUNT(PatientID) AS TotalExpiredPatients
FROM
    Insurance
GROUP BY
    InsuranceCompany;
```

**Output:**

<img width="889" height="720" alt="Screenshot 2025-09-29 150925" src="https://github.com/user-attachments/assets/52dc7583-1bc9-472a-9ca8-4e86d953aab8" />

**Question 4**
---

<img width="934" height="479" alt="Screenshot 2025-09-29 145434" src="https://github.com/user-attachments/assets/1fbb68f3-141c-4853-aaee-59dc4977cd61" />

```sql
SELECT count(id) as COUNT
FROM
    customer 
WHERE
    city <> 'Noida';
```

**Output:**
<img width="399" height="290" alt="Screenshot 2025-09-29 150937" src="https://github.com/user-attachments/assets/a5f7f1f3-0239-49fb-add8-f7c5b0ed4035" />

**Question 5**
---
<img width="551" height="444" alt="Screenshot 2025-09-29 145445" src="https://github.com/user-attachments/assets/1ddaa904-994f-480d-a2ec-59409359db20" />

```sql
SELECT 
    name,
    LENGTH(name) AS length
FROM
    customer 
ORDER BY
    length DESC
LIMIT 1;
```

**Output:**
<img width="666" height="287" alt="Screenshot 2025-09-29 150950" src="https://github.com/user-attachments/assets/1ac795dc-58b5-4a3c-b71f-e254717e0106" />

**Question 6**
---
<img width="957" height="480" alt="Screenshot 2025-09-29 145458" src="https://github.com/user-attachments/assets/26fdb579-056b-4877-8fea-81be675d5945" />

```sql
SELECT COUNT(customer_id) AS COUNT
FROM customer;
```

**Output:**

<img width="370" height="299" alt="Screenshot 2025-09-29 151004" src="https://github.com/user-attachments/assets/51658741-eeac-468d-af9e-cd24b4c46aab" />

**Question 7**
---
<img width="647" height="524" alt="Screenshot 2025-09-29 145514" src="https://github.com/user-attachments/assets/881f655e-ced4-4f92-8f4d-eba6af648dd0" />

```sql
SELECT 
    name AS fruit_name,
    inventory AS lowest_quantity
FROM
    fruits
ORDER BY
    inventory ASC 
LIMIT 1;
```

**Output:**
<img width="703" height="294" alt="Screenshot 2025-09-29 151012" src="https://github.com/user-attachments/assets/2d728f16-d0fe-4fde-8c9f-c31d8b0912ce" />

**Question 8**
---
<img width="1193" height="484" alt="Screenshot 2025-09-29 145527" src="https://github.com/user-attachments/assets/4228b895-1751-4f5b-94d4-4e29413b7419" />

```sql
SELECT 
    age,
    SUM(income)
FROM
    employee
GROUP BY
    age
HAVING
    SUM(income) > 1000000;
```

**Output:**
<img width="587" height="398" alt="Screenshot 2025-09-29 151021" src="https://github.com/user-attachments/assets/a81cd49a-c61a-4e0b-b00b-0de51260e78f" />

**Question 9**
---
<img width="850" height="575" alt="Screenshot 2025-09-29 145543" src="https://github.com/user-attachments/assets/e8b35ec7-a535-412e-ac75-d565b6c8b1eb" />

```sql
SELECT 
    address,
    AVG(salary)
FROM
    customer1
GROUP BY
    address
HAVING 
    AVG(salary) < 15000;
```

**Output:**
<img width="574" height="596" alt="Screenshot 2025-09-29 151037" src="https://github.com/user-attachments/assets/eb410300-2352-4101-944d-8cc8ab8c178f" />

**Question 10**
---
<img width="1221" height="528" alt="Screenshot 2025-09-29 145605" src="https://github.com/user-attachments/assets/c5fadc48-7397-4622-926d-798d26d23712" />

```sql
SELECT 
    category_id,
    SUM(price * category_id) AS Revenue 
FROM
    products
GROUP BY
    category_id
HAVING 
    SUM(price * category_id) > 25;
```

**Output:**
<img width="604" height="413" alt="Screenshot 2025-09-29 151053" src="https://github.com/user-attachments/assets/8eed3cbc-7014-43bf-baac-5465bd3534dd" />

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
<img width="1406" height="226" alt="Screenshot 2025-09-29 151653" src="https://github.com/user-attachments/assets/2215b2a8-8cc2-47ed-8223-8c902768b74f" />

