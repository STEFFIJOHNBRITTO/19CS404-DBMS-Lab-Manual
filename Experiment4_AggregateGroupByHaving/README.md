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
How many patients have expired insurance coverage for each insurance company?

Sample table:Insurance Table

```sql
SELECT
    InsuranceCompany,
    COUNT(*) AS TotalExpiredPatients FROM Insurance
WHERE DATE(substr(ValidityPeriod,-10))< DATE('now')
GROUP BY InsuranceCompany;
```

**Output:**

<img width="1204" height="925" alt="image" src="https://github.com/user-attachments/assets/2a75fad3-5402-4d39-94cc-c493c07edc9f" />


**Question 2**
---
How many patients are covered by each insurance company?

Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
ValidityPeriod     TEXT

```sql
SELECT
    InsuranceCompany,
    COUNT(DISTINCT PatientID) AS TotalPatients
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**

<img width="1215" height="847" alt="image" src="https://github.com/user-attachments/assets/b695473a-83a6-4aaf-97b7-7cea2201b11e" />


**Question 3**
---
How many male and female doctors are there in each medical specialty?

Sample table:Doctors Table

```sql
SELECT
    Specialty,
    Gender,
    Count(*) AS TotalDoctors
FROM Doctors
GROUP BY Specialty,Gender;
```

**Output:**

<img width="1205" height="818" alt="image" src="https://github.com/user-attachments/assets/3fbfad12-ffcd-4ae4-ad32-748a1bd52ec4" />


**Question 4**
---
Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
SELECT MAX(age)-MIN(age) AS age_difference
FROM employee;
```

**Output:**

<img width="1210" height="437" alt="image" src="https://github.com/user-attachments/assets/2d2eb3a5-b9e9-4ba7-8a6a-d18ba815b710" />


**Question 5**
---
Write a SQL query to calculate total available amount of fruits that has a price greater than 0.5 . Return total Count. 

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL

```sql
SELECT
    SUM(inventory)AS total_available_amount
FROM fruits
WHERE price>0.5;
```

**Output:**

<img width="1207" height="430" alt="image" src="https://github.com/user-attachments/assets/6bbd3625-fe56-4a13-974a-10ecff09f5ce" />


**Question 6**
---
Write a SQL query to Calculate the average income of the employees with names starting with 'A': 

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
SELECT AVG(income) AS avg_income
FROM employee
WHERE name LIKE 'A%';
```

**Output:**

<img width="1201" height="434" alt="image" src="https://github.com/user-attachments/assets/5e275448-53e3-4b49-acf7-56151fc782b9" />


**Question 7**
---
Write a SQL query to find the shortest email address in the customer table?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER

```sql
SELECT
    name,
    email,
    LENGTH(email) AS
min_email_length
FROM customer
ORDER BY min_email_length
LIMIT 1;
```

**Output:**

<img width="1210" height="438" alt="image" src="https://github.com/user-attachments/assets/b7a47bfb-d30d-4f28-946d-0dcafe77d409" />


**Question 8**
---
Write the SQL query that achieves the selection of product names and the maximum price for each category from the "products" table, and includes only those products where the maximum price is greater than 15.

Sample table: products

```sql
SELECT
    t1.category_id,
    t1.product_name,
    t2.max_price AS Price
FROM products AS t1
INNER JOIN(SELECT category_id,MAX(price)AS max_price
FROM products
GROUP BY category_id
HAVING MAX(price)>15)
AS t2 ON t1.category_id=t2.category_id AND t1.price=t2.max_price;
```

**Output:**

<img width="1211" height="512" alt="image" src="https://github.com/user-attachments/assets/d8f886d7-a48d-4a36-a179-e581a9c39664" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000.

Sample table: employee

```sql
SELECT
    city,
    AVG(income) AS "AVG(income)"
FROM employee
GROUP BY city
HAVING AVG(income)>500000;
```

**Output:**

<img width="1204" height="570" alt="image" src="https://github.com/user-attachments/assets/a23c518f-c553-4b87-b5aa-766f4deefe87" />


**Question 10**
---
Write the SQL query that achieves the selection of category and calculates the sum of the product of price and category ID as Revenue for each category from the "products" table, and includes only those products where the total revenue is greater than 25.

Sample table: products

```sql
SELECT 
    category_id,
    SUM(price*category_id) AS Revenue
FROM products
GROUP BY category_id
HAVING SUM(price*category_id)>25;
```

**Output:**

<img width="1206" height="577" alt="image" src="https://github.com/user-attachments/assets/a18d0063-2029-464a-8dad-0560091100ce" />

## COMPLETION STATUS

<img width="1287" height="290" alt="image" src="https://github.com/user-attachments/assets/0b75eb85-a882-48aa-ad50-c7612ce0b25a" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
