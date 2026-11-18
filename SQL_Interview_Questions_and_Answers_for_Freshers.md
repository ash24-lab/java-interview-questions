# SQL Interview Questions and Answers for Freshers

These answers are written in a simple, interview-friendly style.
Understand the concepts and practise the example queries rather than
memorizing them word for word.

## 1. What is SQL?

**Answer:**

SQL stands for Structured Query Language. It is a standard language used
to communicate with relational databases.

We use SQL to: - Create databases and tables. - Insert records. -
Retrieve data. - Update existing records. - Delete records.

**Example:**

``` sql
SELECT * FROM employees;
```

This query retrieves all records from the `employees` table.

## 2. What is DBMS?

**Answer:**

DBMS stands for Database Management System. It is software used to
store, manage, retrieve, and organize data efficiently.

It acts as an interface between users and databases.

**Examples:** MySQL, Oracle, PostgreSQL, Microsoft SQL Server, and
MongoDB.

## 3. Difference between DBMS and RDBMS?

**Answer:**

DBMS is software used to manage databases, whereas RDBMS is a type of
DBMS that stores data in tables consisting of rows and columns and
establishes relationships between tables.

  -----------------------------------------------------------------------
  DBMS                                RDBMS
  ----------------------------------- -----------------------------------
  Manages databases                   Manages relational databases

  May not support relationships       Supports relationships between
  between tables                      tables

  May not enforce primary and foreign Supports primary and foreign keys
  key constraints                     

  Examples include some file-based    Examples: MySQL, Oracle, PostgreSQL
  database systems                    
  -----------------------------------------------------------------------

**Interview tip:** Every RDBMS is a DBMS, but not every DBMS is an
RDBMS.

## 4. What is a Primary Key?

**Answer:**

A primary key is a column or combination of columns that uniquely
identifies each record in a table.

Important points: - It must contain unique values. - It cannot contain
`NULL` values. - A table can have only one primary key constraint. - It
can consist of multiple columns (a composite primary key).

**Example:**

``` sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50),
    salary INT
);
```

Here, `emp_id` uniquely identifies each employee.

## 5. What is a Foreign Key?

**Answer:**

A foreign key is a column or combination of columns that establishes a
relationship between two tables. It references a primary key or a unique
key in another table (or the same table).

**Example:**

``` sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50),
    dept_id INT,
    FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);
```

Here, `dept_id` is a foreign key that references the `departments`
table.

## 6. What is a UNIQUE Constraint?

**Answer:**

A `UNIQUE` constraint ensures that values in a column or combination of
columns are unique. It prevents duplicate values.

**Example:**

``` sql
CREATE TABLE students (
    id INT PRIMARY KEY,
    email VARCHAR(100) UNIQUE,
    name VARCHAR(50)
);
```

Here, duplicate email addresses are not allowed.

**Difference between Primary Key and Unique Key:**

  -----------------------------------------------------------------------
  Primary Key                         Unique Key
  ----------------------------------- -----------------------------------
  Uniquely identifies records         Ensures unique values

  Does not allow `NULL`               `NULL` handling depends on the
                                      database

  Only one primary key constraint per Multiple unique constraints are
  table                               allowed
  -----------------------------------------------------------------------

## 7. What is Normalization?

**Answer:**

Normalization is the process of organizing data in database tables to
reduce data redundancy and improve data consistency.

Common normal forms:

**1NF (First Normal Form):** - Each column should contain atomic
(single) values. - No repeating groups.

**2NF (Second Normal Form):** - Must satisfy 1NF. - No partial
dependency of a non-key attribute on part of a candidate key.

**3NF (Third Normal Form):** - Must satisfy 2NF. - No transitive
dependency of non-key attributes on a candidate key.

**Example:** Instead of storing department information repeatedly in
every employee record, create a separate department table and reference
it using a foreign key.

## 8. What are the Different Types of Joins?

**Answer:**

Joins are used to retrieve data from multiple tables based on a related
column.

Main types of joins:

1.  **INNER JOIN:** Returns only matching records from both tables.
2.  **LEFT JOIN (LEFT OUTER JOIN):** Returns all records from the left
    table and matching records from the right table.
3.  **RIGHT JOIN (RIGHT OUTER JOIN):** Returns all records from the
    right table and matching records from the left table.
4.  **FULL OUTER JOIN:** Returns all records from both tables, matching
    where possible.
5.  **CROSS JOIN:** Returns the Cartesian product of both tables.
6.  **SELF JOIN:** Joins a table with itself.

## 9. Difference between INNER JOIN and LEFT JOIN?

**Answer:**

`INNER JOIN` returns only matching records from both tables, whereas
`LEFT JOIN` returns all records from the left table and matching records
from the right table.

**INNER JOIN example:**

``` sql
SELECT *
FROM employees e
INNER JOIN departments d
ON e.dept_id = d.dept_id;
```

This returns only employees who have matching departments.

**LEFT JOIN example:**

``` sql
SELECT *
FROM employees e
LEFT JOIN departments d
ON e.dept_id = d.dept_id;
```

This returns all employees, including those who do not have a matching
department. For unmatched records, department columns contain `NULL`.

## 10. What is GROUP BY?

**Answer:**

`GROUP BY` is used to group rows that have the same values in specified
columns. It is commonly used with aggregate functions such as: -
`COUNT()` - `SUM()` - `AVG()` - `MAX()` - `MIN()`

**Example:**

``` sql
SELECT dept_id, AVG(salary)
FROM employees
GROUP BY dept_id;
```

This query calculates the average salary of each department.

## 11. What is HAVING?

**Answer:**

`HAVING` is used to filter grouped records based on a condition. It is
commonly used with `GROUP BY`.

**Example:**

``` sql
SELECT dept_id, AVG(salary)
FROM employees
GROUP BY dept_id
HAVING AVG(salary) > 30000;
```

This query displays departments whose average salary is greater than
30,000.

## 12. Difference between WHERE and HAVING?

**Answer:**

`WHERE` filters individual rows before grouping, whereas `HAVING`
filters groups after `GROUP BY`.

  -----------------------------------------------------------------------
  WHERE                               HAVING
  ----------------------------------- -----------------------------------
  Filters individual records          Filters grouped records

  Applied before `GROUP BY`           Applied after `GROUP BY`

  Cannot directly use aggregate       Can use aggregate functions
  functions in its condition          
  -----------------------------------------------------------------------

**Example:**

``` sql
SELECT dept_id, AVG(salary)
FROM employees
WHERE salary > 20000
GROUP BY dept_id
HAVING AVG(salary) > 30000;
```

Here: - `WHERE` filters employees whose salary is greater than 20,000. -
`GROUP BY` groups employees by department. - `HAVING` filters
departments whose average salary is greater than 30,000.

## 13. What is an Index?

**Answer:**

An index is a database object used to improve the speed of data
retrieval operations.

It works similarly to an index in a book. Instead of searching every
record, the database can use an index to find records faster.

**Example:**

``` sql
CREATE INDEX idx_emp_name
ON employees(emp_name);
```

This creates an index on the employee name column.

**Advantages:** - Improves `SELECT` query performance. - Helps with
searching and filtering records.

**Disadvantages:** - Requires additional storage. - Can slow down
`INSERT`, `UPDATE`, and `DELETE` operations because indexes may need to
be maintained.

## 14. What is a Subquery?

**Answer:**

A subquery is a query written inside another SQL query. It is also
called an inner query or nested query.

**Example:**

``` sql
SELECT *
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);
```

The inner query calculates the average salary. The outer query retrieves
employees whose salaries are greater than the average salary.

## 15. Difference between DELETE, TRUNCATE and DROP?

**Answer:**

These commands remove data or database objects, but they work
differently.

  -----------------------------------------------------------------------
  DELETE                  TRUNCATE                DROP
  ----------------------- ----------------------- -----------------------
  Deletes selected rows   Removes all rows        Removes the entire
  or all rows                                     table

  Supports `WHERE`        Does not support        Does not support
                          `WHERE`                 `WHERE`

  Table structure remains Table structure remains Table structure is
                                                  removed

  Commonly classified as  Commonly classified as  DDL
  DML                     DDL                     
  -----------------------------------------------------------------------

**DELETE example:**

``` sql
DELETE FROM employees
WHERE emp_id = 101;
```

**TRUNCATE example:**

``` sql
TRUNCATE TABLE employees;
```

**DROP example:**

``` sql
DROP TABLE employees;
```

**Interview tip:** Transaction and rollback behavior for these commands
depends on the database system. Do not assume `TRUNCATE` behaves
identically in every DBMS.

## 16. What is ACID?

**Answer:**

ACID properties ensure reliable and consistent database transactions.

ACID stands for:

1.  **Atomicity:** A transaction is completed entirely or not executed
    at all.
2.  **Consistency:** A transaction must maintain database rules and
    constraints.
3.  **Isolation:** Concurrent transactions should not interfere with
    each other in ways that violate the chosen isolation level.
4.  **Durability:** Once a transaction is committed, its changes remain
    saved even if a system failure occurs.

**Example:** Consider transferring ₹1,000 from Account A to Account B: -
₹1,000 must be deducted from Account A. - ₹1,000 must be added to
Account B.

Both operations should succeed together. If one fails, the transaction
should be rolled back.

## 17. What is a One-to-Many Relationship?

**Answer:**

A one-to-many relationship occurs when one record in a table is
associated with multiple records in another table.

**Example:** One department can have multiple employees, but each
employee belongs to one department.

**Departments table:**

  dept_id   dept_name
  --------- -----------
  1         Java
  2         Testing

**Employees table:**

  emp_id   emp_name   dept_id
  -------- ---------- ---------
  101      Rahul      1
  102      Arjun      1
  103      Ravi       2

Here, one department can have multiple employees. The `dept_id` in the
employees table acts as a foreign key.

## 18. Difference between CHAR and VARCHAR?

**Answer:**

Both `CHAR` and `VARCHAR` are used to store strings, but they differ in
how they handle storage.

  -----------------------------------------------------------------------
  CHAR                                VARCHAR
  ----------------------------------- -----------------------------------
  Fixed-length string type            Variable-length string type

  Uses the declared fixed length      Stores the value's length plus
                                      database-specific overhead

  Shorter values may be padded with   Does not normally pad values to the
  spaces                              declared length

  Suitable for fixed-length data      Suitable for variable-length data
  -----------------------------------------------------------------------

**Example:**

``` sql
CREATE TABLE students (
    gender CHAR(1),
    name VARCHAR(50)
);
```

Here: - `CHAR(1)` stores a fixed-length character. - `VARCHAR(50)`
stores names with variable lengths up to 50 characters.

## 19. How do you find the second-highest salary?

**Answer:**

We can find the second-highest distinct salary using a subquery.

**Method 1: Using MAX() and a subquery**

``` sql
SELECT MAX(salary)
FROM employees
WHERE salary < (
    SELECT MAX(salary)
    FROM employees
);
```

**Explanation:** 1. The inner query finds the highest salary. 2. The
outer query finds the maximum salary that is less than the highest
salary. 3. Therefore, we get the second-highest distinct salary.

**Method 2: Using DISTINCT and LIMIT (MySQL)**

``` sql
SELECT DISTINCT salary
FROM employees
ORDER BY salary DESC
LIMIT 1 OFFSET 1;
```

**Explanation:** - `DISTINCT` removes duplicate salaries. - `ORDER BY`
sorts salaries in descending order. - `LIMIT 1 OFFSET 1` skips the
highest salary and returns the second-highest.

## 20. Write a query to find duplicate records.

**Answer:**

We can use `GROUP BY` and `HAVING COUNT()` to identify duplicate values.

**Example:** Find employees having duplicate names.

``` sql
SELECT emp_name, COUNT(*)
FROM employees
GROUP BY emp_name
HAVING COUNT(*) > 1;
```

**Explanation:** 1. `GROUP BY` groups employees with the same name. 2.
`COUNT(*)` counts the number of occurrences. 3. `HAVING COUNT(*) > 1`
returns only duplicate names.

To find duplicate email addresses:

``` sql
SELECT email, COUNT(*)
FROM employees
GROUP BY email
HAVING COUNT(*) > 1;
```

------------------------------------------------------------------------

# Additional SQL Queries to Practise

These are useful practical questions frequently asked in fresher
interviews.

  No.   Question                                  SQL concept
  ----- ----------------------------------------- ---------------------
  1     Find the highest salary                   `MAX()`
  2     Find the lowest salary                    `MIN()`
  3     Find the average salary                   `AVG()`
  4     Count total employees                     `COUNT()`
  5     Find employees earning more than 30,000   `WHERE`
  6     Sort employees by salary                  `ORDER BY`
  7     Find the second-highest salary            Subquery
  8     Find the top 3 salaries                   `ORDER BY`, `LIMIT`
  9     Find employees whose names start with A   `LIKE`
  10    Find employees without a department       `IS NULL`

# SQL Mock Interview Quiz

Try answering these questions without looking at the explanations.

## Questions

1.  Which key uniquely identifies each record in a table?
    -   A. Foreign Key
    -   B. Primary Key
    -   C. Unique Key
    -   D. Index
2.  Which SQL clause filters grouped records?
    -   A. WHERE
    -   B. ORDER BY
    -   C. HAVING
    -   D. SELECT
3.  Which JOIN returns all records from the left table?
    -   A. INNER JOIN
    -   B. LEFT JOIN
    -   C. CROSS JOIN
    -   D. SELF JOIN
4.  Which command removes the complete table structure?
    -   A. DELETE
    -   B. TRUNCATE
    -   C. DROP
    -   D. UPDATE
5.  Which approach can be used to find duplicate values?
    -   A. ORDER BY
    -   B. GROUP BY with HAVING
    -   C. UPDATE
    -   D. INSERT
6.  What does ACID stand for?
    -   A. Atomicity, Consistency, Isolation, Durability
    -   B. Accuracy, Consistency, Index, Data
    -   C. Atomicity, Control, Isolation, Database
    -   D. None of these
7.  Which function calculates the average?
    -   A. SUM()
    -   B. COUNT()
    -   C. AVG()
    -   D. MAX()
8.  Which command retrieves data from a table?
    -   A. INSERT
    -   B. SELECT
    -   C. UPDATE
    -   D. DELETE

## Answer Key

  Question   Correct answer
  ---------- --------------------------------------------------
  1          B. Primary Key
  2          C. HAVING
  3          B. LEFT JOIN
  4          C. DROP
  5          B. GROUP BY with HAVING
  6          A. Atomicity, Consistency, Isolation, Durability
  7          C. AVG()
  8          B. SELECT

------------------------------------------------------------------------

# Interview Preparation Tips

As a fresher:

1.  Understand each definition instead of memorizing it word for word.
2.  Practise writing SQL queries yourself.
3.  Learn the difference between similar concepts such as `WHERE` and
    `HAVING`, and `DELETE`, `TRUNCATE`, and `DROP`.
4.  Practise joins using two sample tables.
5.  Explain your query step by step when the interviewer asks you to
    solve a problem.
6.  If you do not know an answer, be honest and explain what you do
    know.
