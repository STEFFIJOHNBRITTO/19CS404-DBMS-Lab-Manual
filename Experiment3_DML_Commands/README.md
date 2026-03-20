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
Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.

```sql
UPDATE Products
SET category = 'Household'
WHERE product_name LIKE '%Detergent%';
```

**Output:**

<img width="1382" height="295" alt="image" src="https://github.com/user-attachments/assets/e1feacdd-96bd-4f8e-b9fe-32f9fdba5160" />


**Question 2**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

```sql
UPDATE Products
SET product_name = 'Premium Bread'
WHERE product_id = 5;

```

**Output:**

<img width="1308" height="264" alt="image" src="https://github.com/user-attachments/assets/551872eb-74a3-4c69-af1f-edd58174541e" />


**Question 3**
---
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'

```sql
UPDATE Employees
SET salary = salary * 2
WHERE department_id = 20
  AND job_id LIKE '%MAN';
```

**Output:**

<img width="998" height="207" alt="image" src="https://github.com/user-attachments/assets/78bd16cb-07a0-4b2a-bcf6-2022e4c686f4" />


**Question 4**
---
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

```sql
UPDATE Products
SET sell_price = sell_price * 1.10
WHERE category = 'Bakery';
```

**Output:**

<img width="1318" height="301" alt="image" src="https://github.com/user-attachments/assets/e32f7962-c9e7-4541-9970-0377bccb8c30" />


**Question 5**
---
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

```sql
UPDATE Suppliers
SET address = '58 Lakeview, Magnolia'
WHERE supplier_id = 5;
```

**Output:**

<img width="1374" height="241" alt="image" src="https://github.com/user-attachments/assets/e226bb77-6f90-4e70-8ed6-b970adb8328a" />


**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' has exactly 6 characters.

```sql
DELETE FROM customer
WHERE LENGTH(CUST_NAME) = 6;
```

**Output:**

<img width="1403" height="429" alt="image" src="https://github.com/user-attachments/assets/cf28f751-be81-47fb-8da1-15ea2df13b8d" />


**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_COUNTRY' is neither 'India' nor 'USA'.

```sql
DELETE FROM customer
WHERE CUST_COUNTRY NOT IN ('India', 'USA');

```

**Output:**

<img width="1393" height="342" alt="image" src="https://github.com/user-attachments/assets/9aa26e59-a4cf-44ce-bab0-968528811f7e" />


**Question 8**
---
Write a SQL query to Delete All Doctors with a NULL Last Name

```sql
DELETE FROM Doctors
WHERE last_name IS NULL;
```

**Output:**

<img width="945" height="537" alt="image" src="https://github.com/user-attachments/assets/e619c127-c100-4bfb-a66f-67b7c4612c91" />


**Question 9**
---
Write a SQL query to Delete a Specific Surgery which was made on 28th Feb 2024.

```sql
DELETE FROM Surgeries
WHERE surgery_date = '2024-02-28';

```

**Output:**

<img width="901" height="312" alt="image" src="https://github.com/user-attachments/assets/77435862-63ff-4d0c-a695-995e46577a2b" />


**Question 10**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is exactly 2.

```sql
DELETE FROM customer
WHERE GRADE = 2;
```

**Output:**

<img width="569" height="464" alt="image" src="https://github.com/user-attachments/assets/2a9311d5-7438-445b-8f23-2e6443b7eab8" />

## COMPLETION STATUS 

<img width="1047" height="358" alt="image" src="https://github.com/user-attachments/assets/1569f317-f8e2-4011-95b4-e38d8a39ef4d" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
