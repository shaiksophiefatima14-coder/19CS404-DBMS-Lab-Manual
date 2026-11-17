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
--
<img width="680" height="210" alt="image" src="https://github.com/user-attachments/assets/dec3f520-4933-4d35-a9d0-b0ac8d69fa1d" />


## CODE
```sql
update products set product_name='Premium Bread' where product_id=5;
```

**Output:**

<img width="1800" height="245" alt="image" src="https://github.com/user-attachments/assets/7f181922-a381-4934-b6bc-0ec6545a2940" />


**Question 2**
---
<img width="787" height="232" alt="image" src="https://github.com/user-attachments/assets/58222932-085a-4f01-b000-f6995aea8fca" />

## CODE
```sql
update products set sell_price = sell_price*1.10 where category = 'Bakery';
```

**Output:**

<img width="1650" height="296" alt="image" src="https://github.com/user-attachments/assets/1fb7969e-e30f-4ecd-9e58-7432c0fbbbac" />


**Question 3**
---
<img width="1187" height="288" alt="image" src="https://github.com/user-attachments/assets/97277386-4c98-4bca-ac83-06d7e3480b29" />

## CODE
```sql
update Employees set first_name='John' where department_id = 80;
```

**Output:**

<img width="1842" height="247" alt="image" src="https://github.com/user-attachments/assets/5975c425-7c99-4103-9477-5ab282179309" />


**Question 4**
---
<img width="1107" height="447" alt="image" src="https://github.com/user-attachments/assets/cc0fd7d1-0ceb-4871-bcdd-3ff54df9abaf" />

## CODE
```sql
update employees set salary=8000 where employee_id = 105;
```

**Output:**

<img width="1525" height="133" alt="image" src="https://github.com/user-attachments/assets/2b5be3db-c133-4523-a1aa-c3d93f2a9868" />


**Question 5**
---
<img width="1265" height="462" alt="image" src="https://github.com/user-attachments/assets/b40bd5e5-63ae-49d3-83eb-9c6692a0828f" />

## CODE
```sql
update employees set email='not available';
update employees set commission_pct='not available';
update employees set commission_pct=0.55 where department_id=110;
```

**Output:**

<img width="1372" height="235" alt="image" src="https://github.com/user-attachments/assets/3309d804-78f3-4005-9237-9805ab7b2321" />


**Question 6**
---
<img width="1253" height="507" alt="image" src="https://github.com/user-attachments/assets/b6781ca3-0c53-41c6-a3df-a09a3300fb33" />

## CODE
```sql
delete from customer where length(cust_name)==6;
```

**Output:**

<img width="1167" height="743" alt="image" src="https://github.com/user-attachments/assets/225f23c9-978a-4c7e-9795-07ccedd379b2" />


**Question 7**
---
<img width="648" height="358" alt="image" src="https://github.com/user-attachments/assets/15a8da3c-41e6-45a6-8987-ecc8e0ec6971" />

## CODE
```sql
delete from Doctors where doctor_id between 2 and 4;
```

**Output:**

<img width="682" height="446" alt="image" src="https://github.com/user-attachments/assets/f30267a9-546f-496c-ba06-b0aa32c3455c" />


**Question 8**
---
<img width="1232" height="477" alt="image" src="https://github.com/user-attachments/assets/77aacd14-36bd-439a-8201-47d9e8e0294c" />

## CODE
```sql
delete from Customer where grade!=3;
```

**Output:**

<img width="1862" height="392" alt="image" src="https://github.com/user-attachments/assets/b91bdfd2-150b-4f9b-8e00-76e6e71bad10" />


**Question 9**
---
<img width="1217" height="345" alt="image" src="https://github.com/user-attachments/assets/5c0ab7c6-c0ae-43e8-92ca-c3c8b4eaa658" />

## CODE
```sql
delete from Customer where grade==2 and cust_name like 'M%' and payment_amt <3000;
```

**Output:**
<img width="1881" height="202" alt="image" src="https://github.com/user-attachments/assets/913b8127-2a59-4535-b45f-02730def5a72" />


**Question 10**
---
<img width="1227" height="350" alt="image" src="https://github.com/user-attachments/assets/747b9a72-6d4b-4f07-9dd3-9254faf87afe" />

## CODE
```sql
delete from Customer where cust_country=='UK' and working_area=='London' and grade <3;
```

**Output:**

<img width="1917" height="242" alt="image" src="https://github.com/user-attachments/assets/232f865e-3adb-453b-9abe-b32d99f08122" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
