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
<img width="1301" height="217" alt="image" src="https://github.com/user-attachments/assets/156d1de3-6826-4eba-8e35-06ccba136c9e" />

## code
```sql
SELECT s.name 
FROM salesman s 
LEFT JOIN customer c ON s.salesman_id = c.salesman_id 
WHERE c.city = 'London';
```

**Output:**

<img width="282" height="305" alt="image" src="https://github.com/user-attachments/assets/7df01241-e35e-46fb-be24-ba234eeb0f33" />


**Question 2**
---
<img width="1357" height="526" alt="image" src="https://github.com/user-attachments/assets/9554f0b0-c384-4699-a354-64c5fa52f8cd" />

## code

```sql
SELECT patients.*, doctors.specialization AS doctor_specialization 
FROM patients 
INNER JOIN doctors ON patients.doctor_id = doctors.doctor_id;
```

**Output:**

<img width="1717" height="323" alt="image" src="https://github.com/user-attachments/assets/6a178819-ea26-42fc-b11e-b783fc33f947" />


**Question 3**
---
<img width="900" height="982" alt="image" src="https://github.com/user-attachments/assets/e2f0e420-ce1d-4224-8fda-b03d86806eb3" />

## code

```sql
SELECT a.ord_no, a.ord_date, a.purch_amt, b.cust_name AS "Customer Name", b.grade, c.name AS "Salesman", c.commission 
FROM orders a 
JOIN customer b ON a.customer_id = b.customer_id 
JOIN salesman c ON a.salesman_id = c.salesman_id;
```

**Output:**

<img width="1381" height="776" alt="image" src="https://github.com/user-attachments/assets/51294654-e472-49fa-aaf9-137732c4fae4" />


**Question 4**
---
<img width="1656" height="975" alt="image" src="https://github.com/user-attachments/assets/da422e22-0316-4eaa-a658-4dea6f12bf9f" />

## code

```sql
SELECT a.cust_name, a.city, b.ord_no, b.ord_date, b.purch_amt AS "Order Amount", c.name, c.commission 
FROM customer a 
LEFT JOIN orders b ON a.customer_id = b.customer_id 
LEFT JOIN salesman c ON b.salesman_id = c.salesman_id;
```

**Output:**

<img width="1452" height="785" alt="image" src="https://github.com/user-attachments/assets/54d8bdd3-bdeb-41c2-9718-520555ca24ab" />



**Question 5**
---
<img width="1330" height="210" alt="image" src="https://github.com/user-attachments/assets/9abe7020-5dc4-4967-abc8-f47bd7188f6e" />


## code

```sql
SELECT c.* 
FROM customer c 
LEFT JOIN salesman s ON c.salesman_id = s.salesman_id 
WHERE s.name = 'Mc Lyon';
```

**Output:**
<img width="1082" height="228" alt="image" src="https://github.com/user-attachments/assets/8d6e3fcf-ecd1-4ff8-aca2-04e021241a64" />


**Question 6**
---
<img width="1560" height="593" alt="image" src="https://github.com/user-attachments/assets/31e13c07-5e37-464c-ba6a-812ec31971b1" />

## code

```sql
SELECT a.cust_name AS "Customer Name", a.city, b.name AS "Salesman", b.city, b.commission 
FROM customer a 
JOIN salesman b ON a.salesman_id = b.salesman_id 
WHERE a.city <> b.city AND b.commission > 0.12;
```

**Output:**

<img width="1266" height="480" alt="image" src="https://github.com/user-attachments/assets/4d74db99-75b0-49d0-897f-a88a0126a31e" />


**Question 7**
---
<img width="1411" height="787" alt="image" src="https://github.com/user-attachments/assets/fdb415b2-f521-4f0e-b3e9-d47c22eb0fcc" />


## code

```sql
SELECT a.cust_name, a.city, b.ord_no, b.ord_date, b.purch_amt AS "Order Amount" 
FROM customer a 
LEFT JOIN orders b ON a.customer_id = b.customer_id 
ORDER BY b.ord_date ASC;
```

**Output:**

<img width="1098" height="781" alt="image" src="https://github.com/user-attachments/assets/ef46f129-83a5-4f01-bf6c-2523ca1acca1" />



**Question 8**
---
<img width="1376" height="477" alt="image" src="https://github.com/user-attachments/assets/3e67b3fe-4609-4a83-ac08-bca30bf56e35" />




## code

```sql
SELECT p.first_name AS patient_name, t.test_name 
FROM patients p 
JOIN test_results t ON p.patient_id = t.patient_id;
```

**Output:**
<img width="642" height="426" alt="image" src="https://github.com/user-attachments/assets/303bd7d7-1306-4ee4-ac13-44334d6f1b77" />



**Question 9**
---
<img width="1056" height="527" alt="image" src="https://github.com/user-attachments/assets/790e780a-0169-4d52-bf00-db8d051fffab" />

## code

```sql
SELECT a.cust_name, a.city, a.grade, b.name AS "Salesman", b.city AS "city" 
FROM customer a 
JOIN salesman b ON a.salesman_id = b.salesman_id 
WHERE a.grade < 300 
ORDER BY a.customer_id ASC;
```

**Output:**


<img width="918" height="437" alt="image" src="https://github.com/user-attachments/assets/2539ddae-3923-4e6c-8fee-755d8de64c38" />


**Question 10**
---
<img width="1501" height="387" alt="image" src="https://github.com/user-attachments/assets/140458c5-0635-4cab-907e-443003b64c8b" />

## code

```sql
SELECT p.* 
FROM patients p 
JOIN test_results t ON p.patient_id = t.patient_id 
WHERE t.test_name IN ('Blood Test', 'Blood Pressure') 
  AND t.result NOT LIKE '%Normal%';
```

**Output:**


<img width="1641" height="258" alt="image" src="https://github.com/user-attachments/assets/404e630d-c603-48e4-846e-0c5483eba112" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
