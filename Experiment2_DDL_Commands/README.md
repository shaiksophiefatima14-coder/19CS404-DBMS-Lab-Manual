
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
<img width="676" height="252" alt="image" src="https://github.com/user-attachments/assets/da7adeb3-b4fa-47ea-b89a-d91cbe828a63" />

## CODE
```
INSERT INTO Customers
SELECT * FROM Old_customers;
```

**Output:**

<img width="1187" height="190" alt="image" src="https://github.com/user-attachments/assets/3ec3adfb-2746-4e15-bfc9-74f7684d0fc0" />


**Question 2**
---
<img width="1276" height="351" alt="image" src="https://github.com/user-attachments/assets/e1622f5e-e1ca-47b1-849f-53839b8d2dfa" />

## CODE
```
INSERT INTO Student_details VALUES
(205,'Olivia Green', 'F', NULL, NULL),
(207, 'Liam Smith','M','Mathematics','85'),
(208, 'Sophia Johns','F','Science',NULL);
```

**Output:**

<img width="1143" height="197" alt="image" src="https://github.com/user-attachments/assets/2e0da72e-104f-4000-bd37-ea3c283ffb08" />


**Question 3**
---
<img width="733" height="287" alt="image" src="https://github.com/user-attachments/assets/4bba5aea-ab28-417b-91fd-cc2a10bbe415" />

## CODE
```
CREATE TABLE Orders(
OrderID INTEGER,
OrderDate TEXT,
CustomerID INTEGER);
```

**Output:**

<img width="1270" height="230" alt="image" src="https://github.com/user-attachments/assets/70e2fee2-c99d-4c9c-988f-ad534f384d76" />


**Question 4**
---
<img width="785" height="337" alt="image" src="https://github.com/user-attachments/assets/7047b097-2443-4871-98bc-23f8453a13cd" />

## CODE
```
CREATE TABLE item(
item_id TEXT PRIMARY KEY,
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT CHECK(LENGTH(icom_id)==4),
FOREIGN KEY(icom_id) REFERENCES company(com_id) ON UPDATE CASCADE ON DELETE CASCADE
);
```

**Output:**

<img width="1161" height="197" alt="image" src="https://github.com/user-attachments/assets/a02a434c-cb40-4dd2-8f5f-9814438fab53" />


**Question 5**
---
<img width="1103" height="242" alt="image" src="https://github.com/user-attachments/assets/53579932-a4f3-4259-ba3e-8a0a1e7ad28a" />

## CODE
```sql
CREATE TABLE Orders(
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY(CustomerID) REFERENCES Customers(CustomerID));
```

**Output:**

<img width="1295" height="135" alt="image" src="https://github.com/user-attachments/assets/5ce2de81-963c-4368-b22d-35e9095aa7d8" />


**Question 6**
---
<img width="1240" height="173" alt="image" src="https://github.com/user-attachments/assets/da6987fa-044a-495a-8f1f-dffefe0cf03d" />



## CODE
```sql
CREATE TABLE jobs(
job_id INTEGER,
job_title TEXT,
min_salary INTEGER DEFAULT '8000',
max_salary INTEGER NULL);
```

**Output:**

<img width="1826" height="211" alt="image" src="https://github.com/user-attachments/assets/ae3e1c9b-5990-4ca1-9e4e-ae779bfd2fa4" />


**Question 7**
---
<img width="1793" height="282" alt="image" src="https://github.com/user-attachments/assets/a5566b55-7e2b-48f7-a8f8-58fa870ca79a" />

## CODE
```sql
ALTER TABLE Student_details ADD Email VARCHAR(50);
ALTER TABLE Student_details ADD COLUMN MARKS INTEGER DEFAULT 0;
```

**Output:**

<img width="1680" height="135" alt="image" src="https://github.com/user-attachments/assets/dd0620d9-d52d-4c7c-ab19-efbaa46533c2" />


**Question 8**
---
<img width="918" height="158" alt="image" src="https://github.com/user-attachments/assets/6694433a-bb8a-41f2-bf36-a2ca33c6d7ba" />

## CODE
```sql
INSERT INTO Products VALUES(104,'Tablet','Electronics',100,50);
```

**Output:**

<img width="1251" height="123" alt="image" src="https://github.com/user-attachments/assets/4cd7919b-83f3-4619-85cd-c64fbd725ff0" />


**Question 9**
---
<img width="877" height="431" alt="image" src="https://github.com/user-attachments/assets/3803dd87-eda1-4d50-8dc7-7a6e4bc564c9" />

## CODE
```sql
ALTER TABLE Customer ADD discount DECIMAL(5,2);
```

**Output:**

<img width="1595" height="210" alt="image" src="https://github.com/user-attachments/assets/97702c4d-4cf2-402b-8dca-16d2d009581c" />


**Question 10**
---
<img width="602" height="255" alt="image" src="https://github.com/user-attachments/assets/546a5c9d-85e9-41bc-94c0-9aab5ffb0332" />

## CODE
```sql
CREATE TABLE Products(
ProductID INTEGER PRIMARY KEY,
ProductName INTEGER NOT NULL,
Price REAL CHECK(Price > 0),
Stock INTEGER CHECK (Stock >=0));
```

**Output:**
<img width="1171" height="147" alt="image" src="https://github.com/user-attachments/assets/10195688-44f3-47de-8bd4-b88a88a5ceb0" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
