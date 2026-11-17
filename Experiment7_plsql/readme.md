# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

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

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

## code
```
DECLARE
a NUMBER :=80;
b NUMBER :=20;
BEGIN
    IF a>b THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || a);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || b);
    END IF;
END;
```

**Expected Output:**  
```
Greater number is: 80
```
## OUTPUT
<img width="733" height="348" alt="image" src="https://github.com/user-attachments/assets/8ecc2c1e-b0d3-48e6-99ba-52afc768d3bf" />




---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

## code
```
DECLARE
    n NUMBER := 10;
    total_sum NUMBER := 0;
    i NUMBER := 1;
BEGIN
    WHILE i <= n LOOP
        total_sum := total_sum + i;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || total_sum);
END;
```

**Expected Output:**  
```Sum of first 10 natural numbers is: 55```
## OUTPUT
<img width="732" height="355" alt="image" src="https://github.com/user-attachments/assets/757188a9-d12c-4fad-a21a-053030601f5c" />


---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

## code
```
DECLARE
    n NUMBER := 7;
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    output_str VARCHAR2(200);
BEGIN
    DBMS_OUTPUT.PUT_LINE('n = ' || n);
    
    output_str := a || ', ' || b;
    
    FOR i IN 3..n LOOP
        c := a + b;
        output_str := output_str || ', ' || c;
        a := b;
        b := c;
    END LOOP;
    
    DBMS_OUTPUT.PUT_LINE('Fibonacci sequence: ' || output_str);
END;
```


**Expected Output:**  
```n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8
```
## OUTPUT
<img width="732" height="362" alt="image" src="https://github.com/user-attachments/assets/7d0f87cd-b2d1-424a-a50c-9bb28a30917e" />


---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

## code
```
DECLARE
    n NUMBER := 1535;
    temp NUMBER;
    rev NUMBER := 0;
    rem NUMBER;
BEGIN
    temp := n;
    
    WHILE temp > 0 LOOP
        rem := MOD(temp, 10);
        rev := (rev * 10) + rem;
        temp := TRUNC(temp / 10);
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('n = ' || n);
    DBMS_OUTPUT.PUT_LINE('Reversed number is ' || rev);
END;
```

**Expected Output:**  
```n = 1535  
Reversed number is 5351
```
## OUTPUT
<img width="722" height="333" alt="image" src="https://github.com/user-attachments/assets/26785ae9-0ecd-4b3b-af43-99b813156a5b" />


---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

## code
```
DECLARE
a NUMBER :=10;
b NUMBER :=9;
c NUMBER :=15;
BEGIN
    IF a>b AND a>c THEN
        DBMS_OUTPUT.PUT_LINE('Largest of the three number is ' || a);
    ELSIF b>c AND b>a THEN
        DBMS_OUTPUT.PUT_LINE('Largest of the three number is ' || b);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Largest of the three number is ' || c);
    END IF;
END;
```

**Expected Output:**  
```a = 10, b = 9, c = 15  
Largest of three number is 15
```
## OUTPUT
<img width="735" height="357" alt="image" src="https://github.com/user-attachments/assets/7f01db59-0e92-4142-b331-ef5c5524e8ef" />


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
