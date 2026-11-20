# Experiment 8: PL/SQL Cursor Programs

## AIM
To write and execute PL/SQL programs using cursors and exception handling to manage runtime errors effectively and display appropriate messages.

## THEORY

In PL/SQL, cursors are used to handle query result sets row-by-row. 

There are two types of cursors:

- Implicit Cursors: Automatically created by PL/SQL for single-row queries.
- Explicit Cursors: Declared and controlled by the programmer for multi-row queries.

Types of Explicit Cursors:

1. Simple Cursor: Basic cursor to iterate over multiple rows.

2. Parameterized Cursor: Accepts parameters to filter the result dynamically.

3. Cursor FOR Loop: Simplifies cursor operations (open, fetch, close).

4. %ROWTYPE Cursor: Fetches entire row into a record using %ROWTYPE.

5. Cursor with FOR UPDATE: Used for row-level locking and updating the rows while looping.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:

- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

**Exception Handling**

PL/SQL provides a robust mechanism to handle runtime errors using exception handling blocks. When an error occurs during execution, control is passed to the EXCEPTION section, where specific or general errors can be handled gracefully.

### Components of Exception Handling:
- Predefined Exceptions: Automatically raised by PL/SQL for common errors (e.g., NO_DATA_FOUND, TOO_MANY_ROWS, ZERO_DIVIDE).
- User-defined Exceptions: Declared explicitly in the declaration section using the EXCEPTION keyword.
- WHEN OTHERS: A generic handler for all exceptions not handled explicitly.

```sql
BEGIN
   -- Statements
EXCEPTION
   WHEN exception_name THEN
      -- Handling code
   WHEN OTHERS THEN
      -- Handling for unknown errors
END;
```

### **Question 1: Simple Cursor with Exception Handling**

**Write a PL/SQL program using a simple cursor to fetch employee names and designations from the `employees` table. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: When no rows are fetched.
2. **OTHERS**: Any other unexpected errors during execution.

**Steps:**

- Create an `employees` table with fields `emp_id`, `emp_name`, and `designation`.
- Insert some sample data into the table.
- Use a simple cursor to fetch and display employee names and designations.
- Implement exception handling to catch the relevant exceptions and display appropriate messages.

**Program:**


```
CREATE TABLE employees (
    emp_id NUMBER PRIMARY KEY,
    emp_name VARCHAR2(50),
    designation VARCHAR2(50)
);

INSERT INTO employees VALUES (101, 'Alice', 'Manager');
INSERT INTO employees VALUES (102, 'Bob', 'Developer');
INSERT INTO employees VALUES (103, 'Charlie', 'Tester');

COMMIT;

SET SERVEROUTPUT ON;

DECLARE
    CURSOR emp_cursor IS
        SELECT emp_name, designation FROM employees;

    v_name employees.emp_name%TYPE;
    v_designation employees.designation%TYPE;

BEGIN
    OPEN emp_cursor;

    LOOP
        FETCH emp_cursor INTO v_name, v_designation;

        EXIT WHEN emp_cursor%NOTFOUND;

        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || v_name);
        DBMS_OUTPUT.PUT_LINE('Designation: ' || v_designation);
        DBMS_OUTPUT.PUT_LINE('-------------------------');
    END LOOP;

    CLOSE emp_cursor;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employee records found.');

    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred.');
        DBMS_OUTPUT.PUT_LINE(SQLERRM);
END;
```

**Output:**  
<img width="751" height="225" alt="image" src="https://github.com/user-attachments/assets/99eee8fa-ceaa-4845-b909-5a62fec7f3e2" />


---

### **Question 2: Parameterized Cursor with Exception Handling**

**Write a PL/SQL program using a parameterized cursor to retrieve and display employees with a salary in a given range. Implement exception handling for the following errors:**

1. **NO_DATA_FOUND**: When no employees meet the salary criteria.
2. **OTHERS**: For any unexpected errors during the execution.

**Steps:**

- Modify the `employees` table by adding a `salary` column.
- Insert sample salary values for the employees.
- Use a parameterized cursor to accept a salary range as input and fetch employees within that range.
- Implement exception handling to catch and display relevant error messages.

**Program:**


```
-- Add salary column to employees table
ALTER TABLE employees ADD salary NUMBER;

-- Insert salary values
UPDATE employees SET salary = 50000 WHERE emp_id = 101;
UPDATE employees SET salary = 30000 WHERE emp_id = 102;
UPDATE employees SET salary = 25000 WHERE emp_id = 103;

COMMIT;

-- PL/SQL program using parameterized cursor
DECLARE
    CURSOR emp_cursor (min_sal NUMBER, max_sal NUMBER) IS
        SELECT emp_id, emp_name, designation, salary
        FROM employees
        WHERE salary BETWEEN min_sal AND max_sal;

    v_id employees.emp_id%TYPE;
    v_name employees.emp_name%TYPE;
    v_designation employees.designation%TYPE;
    v_salary employees.salary%TYPE;

BEGIN
    OPEN emp_cursor(25000, 50000);

    LOOP
        FETCH emp_cursor INTO v_id, v_name, v_designation, v_salary;

        EXIT WHEN emp_cursor%NOTFOUND;

        DBMS_OUTPUT.PUT_LINE('Employee ID: ' || v_id);
        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || v_name);
        DBMS_OUTPUT.PUT_LINE('Designation: ' || v_designation);
        DBMS_OUTPUT.PUT_LINE('Salary: ' || v_salary);
        DBMS_OUTPUT.PUT_LINE('-------------------------');
    END LOOP;

    CLOSE emp_cursor;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in the given salary range.');

    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred.');
        DBMS_OUTPUT.PUT_LINE(SQLERRM);
END;
```
**Output:**  
<img width="932" height="525" alt="image" src="https://github.com/user-attachments/assets/0cc9121f-76e0-4cfd-aa4b-3b8a0d876d95" />


---

### **Question 3: Cursor FOR Loop with Exception Handling**

**Write a PL/SQL program using a cursor FOR loop to retrieve and display all employee names and their department numbers from the `employees` table. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: If no employees are found in the database.
2. **OTHERS**: For any other unexpected errors.

**Steps:**

- Modify the `employees` table by adding a `dept_no` column.
- Insert sample department numbers for employees.
- Use a cursor FOR loop to fetch and display employee names along with their department numbers.
- Implement exception handling to catch the relevant exceptions.

**Program:**


```
-- Add department number column
ALTER TABLE employees ADD dept_no NUMBER;

-- Insert department numbers
UPDATE employees SET dept_no = 10 WHERE emp_id = 101;
UPDATE employees SET dept_no = 20 WHERE emp_id = 102;
UPDATE employees SET dept_no = 30 WHERE emp_id = 103;

COMMIT;

-- PL/SQL program using Cursor FOR Loop
DECLARE
BEGIN
    FOR emp_rec IN (SELECT emp_name, dept_no FROM employees)
    LOOP
        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || emp_rec.emp_name);
        DBMS_OUTPUT.PUT_LINE('Department Number: ' || emp_rec.dept_no);
        DBMS_OUTPUT.PUT_LINE('-------------------------');
    END LOOP;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in the database.');

    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred.');
        DBMS_OUTPUT.PUT_LINE(SQLERRM);
END;
```

**Output:**  
<img width="940" height="400" alt="image" src="https://github.com/user-attachments/assets/56b0bdcc-6129-4b46-93dd-b3587d26b902" />


---

### **Question 4: Cursor with `%ROWTYPE` and Exception Handling**

**Write a PL/SQL program that uses a cursor with `%ROWTYPE` to fetch and display complete employee records (emp_id, emp_name, designation, salary). Implement exception handling for the following errors:**

1. **NO_DATA_FOUND**: When no employees are found in the database.
2. **OTHERS**: For any other errors that occur.

**Steps:**

- Modify the `employees` table by adding `emp_id`, `emp_name`, `designation`, and `salary` fields.
- Insert sample data into the `employees` table.
- Declare a cursor using `%ROWTYPE` to fetch complete rows from the `employees` table.
- Implement exception handling to catch the relevant exceptions and display appropriate messages.

**Program:**


```
-- Create employees table (if not already created)
CREATE TABLE employees (
    emp_id NUMBER PRIMARY KEY,
    emp_name VARCHAR2(50),
    designation VARCHAR2(50),
    salary NUMBER
);

-- Insert sample data
INSERT INTO employees VALUES (101, 'Alice', 'Manager', 50000);
INSERT INTO employees VALUES (102, 'Bob', 'Developer', 30000);
INSERT INTO employees VALUES (103, 'Charlie', 'Tester', 25000);

COMMIT;

-- PL/SQL program using cursor with %ROWTYPE
DECLARE
    CURSOR emp_cursor IS
        SELECT emp_id, emp_name, designation, salary FROM employees;

    emp_rec emp_cursor%ROWTYPE;

BEGIN
    OPEN emp_cursor;

    LOOP
        FETCH emp_cursor INTO emp_rec;

        EXIT WHEN emp_cursor%NOTFOUND;

        DBMS_OUTPUT.PUT_LINE('Employee ID: ' || emp_rec.emp_id);
        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || emp_rec.emp_name);
        DBMS_OUTPUT.PUT_LINE('Designation: ' || emp_rec.designation);
        DBMS_OUTPUT.PUT_LINE('Salary: ' || emp_rec.salary);
        DBMS_OUTPUT.PUT_LINE('-------------------------');
    END LOOP;

    CLOSE emp_cursor;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in the database.');

    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred.');
        DBMS_OUTPUT.PUT_LINE(SQLERRM);
END;
```

**Output:**  
<img width="920" height="437" alt="image" src="https://github.com/user-attachments/assets/aad24a49-5fc0-4a36-bb68-de0bbf5a252f" />



---

### **Question 5: Cursor with FOR UPDATE Clause and Exception Handling**

**Write a PL/SQL program using a cursor with the `FOR UPDATE` clause to update the salary of employees in a specific department. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: If no rows are affected by the update.
2. **OTHERS**: For any unexpected errors during execution.

**Steps:**

- Modify the `employees` table to include a `dept_no` and `salary` field.
- Insert sample data into the `employees` table with different department numbers.
- Use a cursor with the `FOR UPDATE` clause to lock the rows of employees in a specific department and update their salary.
- Implement exception handling to handle `NO_DATA_FOUND` or other errors that may occur.

**Program:**

```
-- PL/SQL program using cursor with FOR UPDATE
DECLARE
    CURSOR emp_cursor IS
        SELECT emp_id, emp_name, salary
        FROM employees
        WHERE dept_no = 10
        FOR UPDATE;

    v_count NUMBER := 0;

BEGIN
    FOR emp_rec IN emp_cursor
    LOOP
        UPDATE employees
        SET salary = salary + 5000
        WHERE CURRENT OF emp_cursor;

        v_count := v_count + 1;

        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || emp_rec.emp_name);
        DBMS_OUTPUT.PUT_LINE('Updated Salary: ' || (emp_rec.salary + 5000));
        DBMS_OUTPUT.PUT_LINE('-------------------------');
    END LOOP;

    IF v_count = 0 THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in the specified department.');
    ELSE
        DBMS_OUTPUT.PUT_LINE('Salary updated successfully.');
    END IF;

    COMMIT;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in the specified department.');

    WHEN OTHERS THEN
        ROLLBACK;
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred.');
        DBMS_OUTPUT.PUT_LINE(SQLERRM);
END;
```

**Output:**  
<img width="945" height="313" alt="image" src="https://github.com/user-attachments/assets/2024e7ce-38a6-44bd-b1d1-811ec2b8b8fb" />


---

## RESULT
Thus, the program successfully executed and displayed employee details using a cursor. 

