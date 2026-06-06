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

**Expected Output:**  
Greater number is: 80

## program:
  ```
DECLARE
      num1 NUMBER := 50;
      num2 NUMBER := 80;
  BEGIN
      IF num1 > num2 THEN
          DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num1);
      ELSE
          DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num2);
      END IF;
  END;
  /
```
## Output:
<img width="729" height="788" alt="596024901-159cadeb-31ed-4823-8687-54b06135f9c3" src="https://github.com/user-attachments/assets/3e60fcd1-c88e-4764-b60e-cc7a9567c83a" />




---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Sum of first 10 natural numbers is: 55

## program:
 ```
 DECLARE
      n NUMBER := 10;      -- Number of natural numbers
      i NUMBER := 1;       -- Loop counter
      sum NUMBER := 0;     -- Variable to store sum
  BEGIN
      WHILE i <= n LOOP
          sum := sum + i;  -- Add current number to sum
          i := i + 1;      -- Increment counter
      END LOOP;
  
      DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || 
                           ' natural numbers is: ' || sum);
  END;
  /
```
## Output:
<img width="641" height="845" alt="596026238-e3bfa43f-213e-4a48-82e5-2d9377896736" src="https://github.com/user-attachments/assets/32288233-a431-4b61-a166-1dd946ed4bd3" />


---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

## program:
  ```
DECLARE
      n NUMBER := 7;        -- Number of terms
      a NUMBER := 0;       -- First term
      b NUMBER := 1;       -- Second term
      c NUMBER;            -- Next term
      i NUMBER := 1;       -- Loop counter
  BEGIN
      DBMS_OUTPUT.PUT('Fibonacci sequence: ');
  
      WHILE i <= n LOOP
          DBMS_OUTPUT.PUT(a);
  
          IF i < n THEN
              DBMS_OUTPUT.PUT(', ');
          END IF;
  
          c := a + b;   -- Next Fibonacci number
          a := b;       -- Update a
          b := c;       -- Update b
  
          i := i + 1;
      END LOOP;
  
      DBMS_OUTPUT.NEW_LINE;
  END;
  /
```
## Output:

<img width="616" height="914" alt="596026803-81aa248f-3ba8-44be-b4db-f3ccdb8499f4" src="https://github.com/user-attachments/assets/d7c9e6f9-af26-478d-9e32-0c2f2b21fb1d" />

  

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**Expected Output:**  
n = 1535  
Reversed number is 5351

## Program:
```
DECLARE
      n NUMBER := 1535;     -- Original number
      rev NUMBER := 0;      -- Reversed number
      rem NUMBER;           -- Remainder (digit)
      temp NUMBER := n;     -- Temporary variable
  BEGIN
      WHILE temp > 0 LOOP
          rem := MOD(temp, 10);                 -- Extract last digit
          rev := (rev * 10) + rem;              -- Build reversed number
          temp := FLOOR(temp / 10);             -- Remove last digit
      END LOOP;

      DBMS_OUTPUT.PUT_LINE('n = ' || n);
      DBMS_OUTPUT.PUT_LINE('Reversed number is ' || rev);
  END;
  /
  ```
## Output:


<img width="633" height="891" alt="596027244-5ed6e1e5-197a-4783-8a0e-bc65c3446e06" src="https://github.com/user-attachments/assets/fbcc9d96-356e-424e-98d9-5e8dfb4708c0" />

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15



## Program:
```
DECLARE
      a NUMBER := 10;
      b NUMBER := 9;
      c NUMBER := 15;
      largest NUMBER;
  BEGIN
      IF a >= b AND a >= c THEN
          largest := a;
      ELSIF b >= a AND b >= c THEN
          largest := b;
      ELSE
          largest := c;
      END IF;
  
      DBMS_OUTPUT.PUT_LINE('a = ' || a || ', b = ' || b || ', c = ' || c);
      DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || largest);
  END;
  /
  ```
## Output:




<img width="639" height="883" alt="596027641-fd7947b4-9811-454f-a3e6-382b98e17dd6" src="https://github.com/user-attachments/assets/fc86e658-9931-4006-a422-bb8abe351d65" />

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
