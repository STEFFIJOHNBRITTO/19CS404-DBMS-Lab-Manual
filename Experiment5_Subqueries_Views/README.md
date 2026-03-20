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
Write a SQL query that retrieves the all the columns from the Table Grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)

```sql
SELECT *
FROM Grades g
WHERE grade = (
    SELECT MIN(grade)
    FROM Grades
    WHERE subject = g.subject
);

```

**Output:**

<img width="1316" height="466" alt="image" src="https://github.com/user-attachments/assets/b6c92462-bb69-4f45-86ca-e698ff599b0b" />


**Question 2**
---
From the following tables, write a SQL query to find all the orders generated in New York city. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

SALESMAN TABLE

name               type
-----------        ----------
salesman_id  numeric(5)
name             varchar(30)
city                 varchar(15)
commission   decimal(5,2)

ORDERS TABLE

name            type
----------      ----------
ord_no          int
purch_amt    real
ord_date       text
customer_id  int
salesman_id  int

```sql
SELECT
    T1.ord_no,
    T1.purch_amt,
    T1.ord_date,
    T1.customer_id,
    T1.salesman_id
FROM
    orders AS T1 
INNER JOIN
    salesman AS T2
ON
    T1.salesman_id = T2.salesman_id
WHERE
    T2.city = 'New York';
```

**Output:**

<img width="1305" height="519" alt="image" src="https://github.com/user-attachments/assets/9eec777e-271c-4cfa-9e65-133d876c1c73" />


**Question 3**
---
From the following tables, write a SQL query to find those salespeople who earned the maximum commission. Return ord_no, purch_amt, ord_date, and salesman_id.

salesman table

name             type
---------------  ---------------
salesman_id      numeric(5)
name                 varchar(30)
city                    varchar(15)
commission       decimal(5,2)

orders table

name             type
---------------  --------
order_no         int
purch_amt        real
order_date       text
customer_id      int
salesman_id      int
 

```sql
SELECT
    T2.ord_no,
    T2.purch_amt,
    T2.ord_date,
    T2.salesman_id
FROM
    salesman AS T1
INNER JOIN
    orders AS T2
ON
    T1.salesman_id = T2.salesman_id
WHERE
    T1.commission = (
        SELECT
            MAX(commission)
        FROM
            salesman
    );
```

**Output:**

<img width="1314" height="500" alt="image" src="https://github.com/user-attachments/assets/44803df5-2316-419e-9e84-9777e7323c00" />


**Question 4**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000



```sql
SELECT
    *
FROM
    CUSTOMERS
WHERE
    ADDRESS = 'Delhi';
```

**Output:**

<img width="1310" height="371" alt="image" src="https://github.com/user-attachments/assets/fd0a5684-e620-4ce7-8ef4-1cc5668d0840" />


**Question 5**
---
Write a SQL query to Retrieve the names and cities of customers who have the same city as customers with IDs 3 and 7

SAMPLE TABLE: customer

name             type
---------------  ---------------
id               INTEGER
name             TEXT
city             TEXT
email            TEXT
phone            INTEGER

```sql
SELECT
    name,
    city
FROM
    customer
WHERE
    city IN (
        SELECT
            city
        FROM
            customer
        WHERE
            id IN (3, 7)
    );
```

**Output:**

<img width="1309" height="488" alt="image" src="https://github.com/user-attachments/assets/ce07dd50-ca2e-42fe-9b3b-fad89a3cf2f9" />


**Question 6**
---
Write a SQL query to Retrieve the medications with dosages equal to the highest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)

```sql
SELECT
    medication_id,
    medication_name,
    dosage
FROM
    Medications
WHERE
    dosage = (
        SELECT
            MAX(dosage)
        FROM
            Medications
    );
```

**Output:**

<img width="1310" height="435" alt="image" src="https://github.com/user-attachments/assets/44707878-98c3-4208-83b1-0172c291e532" />


**Question 7**
---
From the following tables write a SQL query to find the order values greater than the average order value of 10th October 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

Note: date should be yyyy-mm-dd format

ORDERS TABLE

name            type
----------     ----------
ord_no          int
purch_amt    real
ord_date       text
customer_id  int
salesman_id  int

```sql
SELECT
    ord_no,
    purch_amt,
    ord_date,
    customer_id,
    salesman_id
FROM
    orders
WHERE
    purch_amt > (
        SELECT
            AVG(purch_amt)
        FROM
            orders
        WHERE
            ord_date = '2012-10-10'
    );
```

**Output:**

<img width="1312" height="488" alt="image" src="https://github.com/user-attachments/assets/9cae30f1-7964-4aca-b267-6a0a97eef13c" />


**Question 8**
---
Write a SQL query to Retrieve the names of customers who have a phone number that is not shared with any other customer.

SAMPLE TABLE: customer

name             type
---------------  ---------------
id               INTEGER
name             TEXT
city             TEXT
email            TEXT
phone            INTEGER

```sql
SELECT
    name
FROM
    customer
WHERE
    phone IN (
        SELECT
            phone
        FROM
            customer
        GROUP BY
            phone
        HAVING
            COUNT(phone) = 1
    );
```

**Output:**

<img width="1310" height="491" alt="image" src="https://github.com/user-attachments/assets/d032c744-f25d-4034-a4bd-710e5d8dfcbc" />


**Question 9**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $4500.

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

```sql
SELECT
    *
FROM
    CUSTOMERS
WHERE
    SALARY > 4500;
```

**Output:**

<img width="1307" height="461" alt="image" src="https://github.com/user-attachments/assets/da7a74a2-ec1d-4e7f-8123-3fd2249cd1a4" />


**Question 10**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $1500.

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

```sql
SELECT
    *
FROM
    CUSTOMERS
WHERE
    SALARY > 1500;
```

**Output:**

<img width="1310" height="622" alt="image" src="https://github.com/user-attachments/assets/b0dabbe3-3716-414b-844d-5137c5fa69e1" />

## COMPLETION STATUS

<img width="1080" height="425" alt="image" src="https://github.com/user-attachments/assets/1287fa45-d266-4052-a455-d6da2843f797" />




## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
