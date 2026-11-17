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
<img width="745" height="432" alt="image" src="https://github.com/user-attachments/assets/b809484a-499a-4333-85f3-318fa9fdec87" />

## code
```sql
SELECT * 
FROM Employee 
WHERE age < (
    SELECT AVG(age) 
    FROM Employee 
    WHERE income > 250000
);
```

**Output:**

<img width="922" height="327" alt="image" src="https://github.com/user-attachments/assets/a343f48d-d76b-4207-8f3d-40b6518f7f5d" />


**Question 2**
---
<img width="852" height="302" alt="image" src="https://github.com/user-attachments/assets/cca682a8-c86e-4649-bb95-86e6aaa3828c" />

## code
```sql
SELECT grade, COUNT(*) 
FROM customer 
GROUP BY grade 
HAVING grade > (SELECT AVG(grade) FROM customer WHERE city = 'New York');
```

**Output:**

<img width="363" height="203" alt="image" src="https://github.com/user-attachments/assets/be7fa714-179f-48b2-ba16-d07b5cdd02d9" />


**Question 3**
---
<img width="646" height="330" alt="image" src="https://github.com/user-attachments/assets/047afbe6-f8f2-4201-95c0-371edade34c7" />

## code
```sql
SELECT * 
FROM Medications 
WHERE dosage = (SELECT MAX(dosage) FROM Medications);
```

**Output:**

<img width="587" height="253" alt="image" src="https://github.com/user-attachments/assets/f1c8d89a-9957-4e2e-90bf-f6790d0f6ac4" />


**Question 4**
---
<img width="702" height="367" alt="image" src="https://github.com/user-attachments/assets/b62ea90d-5297-4063-9bbf-cb23df259971" />

## code
```sql
SELECT name 
FROM customer 
WHERE phone IN (
    SELECT phone 
    FROM customer 
    GROUP BY phone 
    HAVING COUNT(*) = 1
);
```

**Output:**

<img width="275" height="291" alt="image" src="https://github.com/user-attachments/assets/fa1aef34-e0f6-4d77-8b9f-4a1268706f16" />


**Question 5**
---
<img width="651" height="437" alt="image" src="https://github.com/user-attachments/assets/28831178-4eb7-4d9e-b706-c2be97a7edfa" />

## code
```sql
SELECT * 
FROM CUSTOMERS 
WHERE salary > 4500;
```

**Output:**

<img width="790" height="266" alt="image" src="https://github.com/user-attachments/assets/eaad58e2-4148-4019-8d18-300fdb50a2e9" />


**Question 6**
---
<img width="901" height="412" alt="image" src="https://github.com/user-attachments/assets/8b266a09-b281-4601-b880-b99ea89cc1f1" />

## code
```sql
SELECT student_name, grade 
FROM GRADES g 
WHERE grade = (
    SELECT MIN(grade) 
    FROM GRADES 
    WHERE subject = g.subject
);
```

**Output:**

<img width="482" height="266" alt="image" src="https://github.com/user-attachments/assets/6f149800-e803-413b-9ae6-d4b7b4ab34b6" />


**Question 7**
---
<img width="740" height="348" alt="image" src="https://github.com/user-attachments/assets/b677cbf5-0b28-4d41-b54d-cbb683dd1eae" />

## code
```sql
SELECT name, city 
FROM customer 
WHERE city IN (
    SELECT city 
    FROM customer 
    WHERE id IN (3, 7)
);
```

**Output:**

<img width="368" height="287" alt="image" src="https://github.com/user-attachments/assets/bc40c9b8-aff2-4af7-9bbf-26cff565c665" />


**Question 8**
---
<img width="967" height="515" alt="image" src="https://github.com/user-attachments/assets/595d665e-d5e4-46c8-96a5-030a66ccd98d" />

## code
```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id 
FROM orders 
WHERE salesman_id IN (
    SELECT salesman_id 
    FROM salesman 
    WHERE city = 'New York'
);
```

**Output:**

<img width="817" height="305" alt="image" src="https://github.com/user-attachments/assets/a6c6cab0-998b-407d-8931-04e072b641b1" />


**Question 9**
---
<img width="857" height="413" alt="image" src="https://github.com/user-attachments/assets/9b79c56b-b6a3-45a2-bf17-e7c9c8562ad5" />

## code
```sql
SELECT * 
FROM Grades g 
WHERE grade = (
    SELECT MAX(grade) 
    FROM Grades 
    WHERE subject = g.subject
);
```

**Output:**

<img width="897" height="245" alt="image" src="https://github.com/user-attachments/assets/c0eff98f-1858-4e84-be16-c67e5c1655ec" />


**Question 10**
---
<img width="638" height="335" alt="image" src="https://github.com/user-attachments/assets/7e38393a-ab6e-4f61-8864-1ff6f9b6fa6a" />

## code
```sql
SELECT * 
FROM Medications 
WHERE dosage = (SELECT MIN(dosage) FROM Medications);
```

**Output:**

<img width="602" height="250" alt="image" src="https://github.com/user-attachments/assets/f50dff96-03d4-4284-8966-78d6b9e363b7" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
