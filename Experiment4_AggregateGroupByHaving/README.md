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
<img width="687" height="358" alt="image" src="https://github.com/user-attachments/assets/953667b9-32c1-4e75-9689-70028936da26" />

## code
```sql
select doctorid, count(*) as TotalAppointments from appointments group by doctorid;
```

**Output:**

<img width="462" height="407" alt="image" src="https://github.com/user-attachments/assets/62cff1c1-cbaf-484b-96fd-50824a7bc596" />


**Question 2**
---
-- Paste Question 2 here
## code
```sql
select insurancecompany, count(patientid) as TotalPatients from insurance group by insurancecompany;
```

**Output:**

<img width="476" height="407" alt="image" src="https://github.com/user-attachments/assets/821daee7-3114-4040-b019-f56eec3861b4" />


**Question 3**
---
<img width="677" height="342" alt="image" src="https://github.com/user-attachments/assets/5f067cfc-ece8-4699-bf54-1cb54c7dccd0" />

## code
```sql
select doctorid, count(recordid) as TotalRecords from medicalrecords group by doctorid;
```

**Output:**

<img width="390" height="376" alt="image" src="https://github.com/user-attachments/assets/227adb0d-3557-48d7-857b-b684ed953603" />


**Question 4**
---
<img width="382" height="325" alt="image" src="https://github.com/user-attachments/assets/8f8d1a86-0b5e-4dcb-8461-0d622fa496b5" />

## code
```sql
select max(purch_amt) as MAXIMUM from orders;
```

**Output:**

<img width="217" height="167" alt="image" src="https://github.com/user-attachments/assets/ba9c12e9-11c0-42bf-8a8f-d053b6481e36" />


**Question 5**
---
<img width="560" height="310" alt="image" src="https://github.com/user-attachments/assets/15a21b09-83a8-4ab6-a2f4-1a36b9f70fbb" />

## code
```sql
select name, max(income) from employee where city='california'
group by name having max(income)=(select max(income) from employee where city='california');
```

**Output:**

<img width="217" height="167" alt="image" src="https://github.com/user-attachments/assets/afe8ee78-0b84-4e57-8f8b-5d2a20395f6f" />


**Question 6**
---
<img width="501" height="325" alt="image" src="https://github.com/user-attachments/assets/b170b035-0f6b-4e40-b145-f989af9f79a7" />

## code
```sql
select COUNT(*) AS COUNT from customer;
```

**Output:**

<img width="230" height="187" alt="image" src="https://github.com/user-attachments/assets/591f2d20-28d2-432a-8d74-402ce60539e2" />


**Question 7**
---
<img width="585" height="297" alt="image" src="https://github.com/user-attachments/assets/a16b060d-7450-4cea-b7e0-e22a2b5784b8" />

## code
```sql
select sum(purch_amt) as TOTAL from orders;
```

**Output:**
<img width="212" height="162" alt="image" src="https://github.com/user-attachments/assets/e4a4a76f-426f-4220-a047-5b6cd00bbc47" />


**Question 8**
---
<img width="1282" height="312" alt="image" src="https://github.com/user-attachments/assets/82e48a12-1b56-46b2-b3e2-078c65ee4d30" />

## code
```sql
select category_id,product_name,price as Price from products 
where (category_id, price) IN (select category_id,max(price) from products group by category_id) and price>15;
```

**Output:**

<img width="547" height="242" alt="image" src="https://github.com/user-attachments/assets/08b76893-64bd-40ef-8ced-a2f3b61a8b6d" />


**Question 9**
---
<img width="1177" height="331" alt="image" src="https://github.com/user-attachments/assets/8e40b52d-b427-41e4-b739-2faec2c2bdbf" />

## code
```sql
select address, SUM(salary) from customer1 group by address having SUM(salary)>2000;
```

**Output:**

<img width="377" height="286" alt="image" src="https://github.com/user-attachments/assets/bc91d7c7-a0ae-4962-8896-b3d44ca66168" />


**Question 10**
---
<img width="1278" height="308" alt="image" src="https://github.com/user-attachments/assets/3090659c-ba02-498b-844e-7a3ec10f52c9" />

## code
```sql
Select (age/5)*5 as age_group, SUM(salary) from customer1 group by (age/5)*5 having SUM(salary)>5000;
```

**Output:**



<img width="371" height="223" alt="image" src="https://github.com/user-attachments/assets/2876360e-f330-4fec-adbf-79d8639558ae" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
