# 📘 DBMS & SQL — Complete Placement Interview Guide
# PostgreSQL / Oracle Database Edition

> **Purpose:** Complete DBMS + SQL preparation for placement drives & interview rounds (Bizom, TCS, Infosys, Wipro, Accenture, etc.)  
> **Level:** Beginner to Advanced | Written in Simple Words  
> **Includes:** Theory + SQL Code (PostgreSQL/Oracle) + Interview Questions with Answers

---

## 📑 Table of Contents

| Chapter | Topic |
|---------|-------|
| 1 | [Introduction to DBMS](#chapter-1--introduction-to-dbms) |
| 2 | [Relational Model & Keys](#chapter-2--relational-model--keys) |
| 3 | [ER Model (Entity-Relationship)](#chapter-3--er-model-entity-relationship) |
| 4 | [SQL Basics — DDL, DML, DCL, TCL](#chapter-4--sql-basics--ddl-dml-dcl-tcl) |
| 5 | [SQL Queries — SELECT, WHERE, ORDER BY](#chapter-5--sql-queries--select-where-order-by) |
| 6 | [SQL Joins](#chapter-6--sql-joins) |
| 7 | [SQL Aggregate Functions & GROUP BY](#chapter-7--sql-aggregate-functions--group-by) |
| 8 | [Subqueries (Nested Queries)](#chapter-8--subqueries-nested-queries) |
| 9 | [SQL Views, Indexes & Sequences](#chapter-9--sql-views-indexes--sequences) |
| 10 | [SQL Constraints](#chapter-10--sql-constraints) |
| 11 | [Normalization](#chapter-11--normalization) |
| 12 | [Transactions & ACID Properties](#chapter-12--transactions--acid-properties) |
| 13 | [Concurrency Control](#chapter-13--concurrency-control) |
| 14 | [Deadlock in DBMS](#chapter-14--deadlock-in-dbms) |
| 15 | [Indexing & Hashing](#chapter-15--indexing--hashing) |
| 16 | [Stored Procedures, Functions & Triggers](#chapter-16--stored-procedures-functions--triggers) |
| 17 | [Relational Algebra](#chapter-17--relational-algebra) |
| 18 | [NoSQL vs SQL](#chapter-18--nosql-vs-sql) |
| 19 | [PostgreSQL & Oracle Specific Features](#chapter-19--postgresql--oracle-specific-features) |
| 20 | [Top 100 Most Asked Interview Questions](#chapter-20--top-100-most-asked-interview-questions) |

---

---

# Chapter 1 — Introduction to DBMS

## 1.1 What is a Database?

A **database** is an **organized collection of data** that can be easily accessed, managed, and updated.

**Example:** A school database stores students, teachers, courses, and grades.

## 1.2 What is DBMS?

**DBMS (Database Management System)** is **software** that allows users to create, manage, and access databases.

**Simple Analogy:** If a database is a **library**, then the DBMS is the **librarian** who organizes books, helps you find them, and ensures no one steals them.

```
User/Application → DBMS → Database (stored on disk)
```

**Examples of DBMS:**
| DBMS | Type |
|------|------|
| **PostgreSQL** | Open-source Relational DBMS |
| **Oracle Database** | Commercial Relational DBMS |
| **MySQL** | Open-source Relational DBMS |
| **SQL Server** | Microsoft's Relational DBMS |
| **MongoDB** | NoSQL (Document-based) |

## 1.3 File System vs DBMS

| Feature | File System | DBMS |
|---------|-----------|------|
| **Data Redundancy** | High (same data in multiple files) | Low (normalized, single source) |
| **Data Inconsistency** | High (updating one file misses others) | Low (centralized control) |
| **Data Access** | Difficult (write custom programs) | Easy (SQL queries) |
| **Data Security** | Poor | Strong (authentication, authorization) |
| **Concurrent Access** | Not supported well | Fully supported (locking, transactions) |
| **Backup & Recovery** | Manual | Automatic |
| **Data Integrity** | No constraints | Constraints enforced |

## 1.4 Advantages of DBMS

1. **Reduced Data Redundancy** — Data stored once, referenced everywhere.
2. **Data Consistency** — Single update reflects everywhere.
3. **Data Security** — Access control (who can see/edit what).
4. **Data Integrity** — Constraints ensure valid data.
5. **Concurrent Access** — Multiple users can access simultaneously.
6. **Backup & Recovery** — Automatic backup and crash recovery.
7. **Data Independence** — Change storage without changing applications.

## 1.5 DBMS Architecture — 3-Level (ANSI-SPARC)

```
┌─────────────────────────────────┐
│        External Level            │  ← User Views (what users see)
│     (View 1, View 2, View 3)    │
├─────────────────────────────────┤
│       Conceptual Level           │  ← Logical Structure (tables, relationships)
│    (Schema: tables, columns)     │
├─────────────────────────────────┤
│        Internal Level            │  ← Physical Storage (how data is stored on disk)
│   (Files, indexes, blocks)       │
└─────────────────────────────────┘
```

| Level | What it Shows | Who Uses It |
|-------|-------------|-------------|
| **External** | User-specific views | End users, applications |
| **Conceptual** | Entire logical database structure | Database designers |
| **Internal** | Physical storage details | Database administrators |

### Data Independence

| Type | Meaning |
|------|---------|
| **Logical Data Independence** | Change conceptual schema without changing external views |
| **Physical Data Independence** | Change internal schema (storage) without changing conceptual schema |

## 1.6 Types of DBMS

| Type | Description | Example |
|------|------------|---------|
| **Relational (RDBMS)** | Data stored in tables with rows and columns | PostgreSQL, Oracle, MySQL |
| **Hierarchical** | Data organized in tree structure | IBM IMS |
| **Network** | Data in graph structure (many-to-many) | IDMS |
| **Object-Oriented** | Data stored as objects | db4o, ObjectDB |
| **NoSQL** | Non-relational (documents, key-value, graphs) | MongoDB, Redis, Cassandra |

## 1.7 Schema vs Instance

| Term | Meaning |
|------|---------|
| **Schema** | The **structure** (blueprint) of the database — doesn't change frequently |
| **Instance** | The **actual data** in the database at a particular moment — changes frequently |

**Analogy:** Schema = Building blueprint, Instance = People currently inside the building.

---

### 🎯 Chapter 1 — Interview Questions

**Q1. What is DBMS? Why do we need it?**  
> **Ans:** DBMS is software that manages databases. We need it to reduce data redundancy, ensure consistency, provide security, support concurrent access, enforce integrity, and enable backup/recovery — things that file systems can't do well.

**Q2. What is the difference between File System and DBMS?**  
> **Ans:** File system has high redundancy, no data integrity, poor security, and no concurrent access control. DBMS has low redundancy, enforces integrity constraints, provides security, and supports concurrent access with transactions.

**Q3. Explain the 3-level architecture of DBMS.**  
> **Ans:** External level (user views), Conceptual level (logical schema — tables, relationships), Internal level (physical storage). This separation provides data independence — changing one level doesn't affect others.

**Q4. What is Data Independence?**  
> **Ans:** The ability to change one level of the database without affecting the other levels. Logical data independence: change conceptual schema without changing views. Physical data independence: change storage without changing logical schema.

**Q5. What is the difference between Schema and Instance?**  
> **Ans:** Schema is the design/structure of the database (table definitions, constraints) — rarely changes. Instance is the actual data at a given point in time — changes frequently with every insert/update/delete.

---

---

# Chapter 2 — Relational Model & Keys

## 2.1 Relational Model

- Data is stored in **tables** (called **relations**).
- Each table has **rows** (called **tuples**) and **columns** (called **attributes**).

```
Table: Students (Relation)
┌─────┬──────────┬─────┬────────┐
│ ID  │  Name    │ Age │ Dept   │  ← Attributes (columns)
├─────┼──────────┼─────┼────────┤
│ 101 │ Rahul    │ 21  │ CSE    │  ← Tuple (row)
│ 102 │ Priya    │ 22  │ ECE    │
│ 103 │ Amit     │ 20  │ CSE    │
└─────┴──────────┴─────┴────────┘
```

| Term | Relational Model | Common Name |
|------|-----------------|-------------|
| **Relation** | A table | Table |
| **Tuple** | A row in the table | Row / Record |
| **Attribute** | A column in the table | Column / Field |
| **Domain** | Set of allowed values for an attribute | Data type |
| **Degree** | Number of columns | — |
| **Cardinality** | Number of rows | — |

## 2.2 Properties of a Relation

1. Each column has a **unique name**.
2. All values in a column are of the **same data type** (domain).
3. Each row is **unique** (no duplicate tuples).
4. **Order of rows doesn't matter**.
5. **Order of columns doesn't matter**.
6. Each cell contains a **single (atomic) value** (no multi-valued attributes).

## 2.3 Keys in DBMS

Keys are used to **uniquely identify** rows and **establish relationships** between tables.

### 2.3.1 Super Key
- Any set of attributes that can **uniquely identify** a tuple.
- May contain extra (unnecessary) attributes.
- **Example:** `{ID}`, `{ID, Name}`, `{ID, Name, Age}` are all super keys if ID is unique.

### 2.3.2 Candidate Key
- A **minimal super key** — no extra attributes.
- Removing any attribute from it would lose uniqueness.
- A table can have **multiple** candidate keys.
- **Example:** `{ID}` and `{Email}` can both be candidate keys.

### 2.3.3 Primary Key
- **One chosen candidate key** used to uniquely identify rows.
- **Cannot be NULL**.
- **Only one** primary key per table.
- **Example:** `ID` is chosen as primary key.

```sql
-- PostgreSQL / Oracle
CREATE TABLE students (
    id       INT PRIMARY KEY,
    name     VARCHAR(100) NOT NULL,
    email    VARCHAR(100) UNIQUE,
    age      INT,
    dept     VARCHAR(50)
);
```

### 2.3.4 Alternate Key
- Candidate keys that are **NOT chosen** as primary key.
- **Example:** If `ID` is PK, then `Email` is an alternate key.

### 2.3.5 Foreign Key
- An attribute in one table that **references the primary key** of another table.
- Creates a **relationship** between tables.
- Ensures **referential integrity**.

```sql
CREATE TABLE departments (
    dept_id    INT PRIMARY KEY,
    dept_name  VARCHAR(100)
);

CREATE TABLE students (
    id        INT PRIMARY KEY,
    name      VARCHAR(100),
    dept_id   INT,
    FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);
```

```
departments                     students
┌─────────┬──────────┐         ┌────┬───────┬─────────┐
│ dept_id │dept_name │         │ id │ name  │ dept_id │
├─────────┼──────────┤         ├────┼───────┼─────────┤
│    1    │  CSE     │ ←───────│101 │ Rahul │    1    │
│    2    │  ECE     │ ←───────│102 │ Priya │    2    │
│    3    │  MECH    │         │103 │ Amit  │    1    │
└─────────┴──────────┘         └────┴───────┴─────────┘
                               FK references PK of departments
```

### 2.3.6 Composite Key
- A primary key made of **two or more columns**.
- **Example:** In an `enrollments` table, `(student_id, course_id)` together form the primary key.

```sql
CREATE TABLE enrollments (
    student_id  INT,
    course_id   INT,
    grade       CHAR(2),
    PRIMARY KEY (student_id, course_id),
    FOREIGN KEY (student_id) REFERENCES students(id),
    FOREIGN KEY (course_id) REFERENCES courses(course_id)
);
```

### 2.3.7 Unique Key
- Like primary key but **allows one NULL value**.
- A table can have **multiple** unique keys.

### Summary of Keys

| Key | Uniqueness | NULLs Allowed | How Many Per Table |
|-----|:-:|:-:|:-:|
| Super Key | ✅ | Depends | Many |
| Candidate Key | ✅ | Depends | Multiple |
| Primary Key | ✅ | ❌ | Only 1 |
| Alternate Key | ✅ | Depends | Multiple |
| Foreign Key | ❌ (can repeat) | ✅ | Multiple |
| Composite Key | ✅ (combination) | ❌ (if PK) | Depends |
| Unique Key | ✅ | ✅ (one NULL) | Multiple |

---

### 🎯 Chapter 2 — Interview Questions

**Q1. What is a Primary Key?**  
> **Ans:** A primary key is an attribute (or set of attributes) that uniquely identifies each row in a table. It cannot be NULL and each table can have only one primary key.

**Q2. What is a Foreign Key?**  
> **Ans:** A foreign key is an attribute in one table that references the primary key of another table. It creates a relationship between tables and ensures referential integrity (no orphan records).

**Q3. Difference between Primary Key and Unique Key?**  
> **Ans:** Primary Key: only one per table, cannot be NULL. Unique Key: multiple per table, allows one NULL value. Both enforce uniqueness.

**Q4. What is a Composite Key?**  
> **Ans:** A composite key is a primary key made up of two or more columns. The combination of these columns uniquely identifies each row, though individual columns may not be unique alone.

**Q5. What is a Candidate Key?**  
> **Ans:** A candidate key is a minimal set of attributes that can uniquely identify a tuple. A table can have multiple candidate keys. One is chosen as the primary key; the rest become alternate keys.

**Q6. What is Referential Integrity?**  
> **Ans:** Referential integrity ensures that a foreign key value in one table must either match a primary key value in the referenced table or be NULL. It prevents orphan records — you can't reference a row that doesn't exist.

---

---

# Chapter 3 — ER Model (Entity-Relationship)

## 3.1 What is an ER Model?

The **ER Model** is a **high-level design** tool used to represent the logical structure of a database before creating tables.

It shows:
- **Entities** (things/objects)
- **Attributes** (properties)
- **Relationships** (how entities are connected)

## 3.2 Components of ER Diagram

### Entity
An object that exists and is distinguishable. Represented as a **rectangle**.

```
┌──────────┐
│ STUDENT  │
└──────────┘
```

**Types:**
- **Strong Entity:** Has its own primary key. Example: Student, Course.
- **Weak Entity:** Depends on another entity for identification (no PK of its own). Represented as **double rectangle**. Example: Dependent (depends on Employee).

### Attribute
A property of an entity. Represented as an **ellipse/oval**.

| Attribute Type | Description | Symbol |
|---------------|------------|--------|
| **Simple** | Cannot be divided further (e.g., Age) | Oval |
| **Composite** | Can be divided (e.g., Name → First, Last) | Oval with sub-ovals |
| **Derived** | Computed from other attributes (e.g., Age from DOB) | Dashed oval |
| **Multi-valued** | Can have multiple values (e.g., Phone numbers) | Double oval |
| **Key Attribute** | Primary key — uniquely identifies entity | Underlined oval |

### Relationship
An association between entities. Represented as a **diamond**.

```
┌──────────┐         ┌──────────┐
│ STUDENT  │───◇───│  COURSE  │
└──────────┘  Enrolls └──────────┘
```

## 3.3 Cardinality (Mapping Constraints)

| Cardinality | Meaning | Example |
|------------|---------|---------|
| **One-to-One (1:1)** | One entity → one related entity | Person → Passport |
| **One-to-Many (1:M)** | One entity → many related entities | Department → Employees |
| **Many-to-One (M:1)** | Many entities → one related entity | Students → Department |
| **Many-to-Many (M:N)** | Many entities → many related entities | Students → Courses |

```
1:1 →  A ──── B          (One A maps to One B)
1:M →  A ──┬─ B1         (One A maps to Many B)
            ├─ B2
            └─ B3
M:N →  A1 ──┬─ B1        (Many A map to Many B)
       A2 ──┤  B2
       A3 ──┘
```

## 3.4 Participation Constraints

| Type | Meaning |
|------|---------|
| **Total Participation** | Every entity MUST participate in the relationship. Shown as **double line**. |
| **Partial Participation** | Some entities MAY participate. Shown as **single line**. |

**Example:** Every employee MUST belong to a department (total). A department MAY have a manager (partial).

## 3.5 Converting ER Diagram to Tables

| ER Element | How to Convert |
|-----------|---------------|
| **Strong Entity** | Create a table with all attributes. PK = key attribute. |
| **Weak Entity** | Create a table. PK = partial key + FK from strong entity. |
| **1:1 Relationship** | Add FK in either table (preferably the one with total participation). |
| **1:M Relationship** | Add FK in the "many" side table. |
| **M:N Relationship** | Create a **new junction table** with FKs from both entities. |
| **Multi-valued Attribute** | Create a separate table with FK back to the entity. |

**Example — M:N Relationship:**
```
Students ──── Enrolls ──── Courses (M:N)

Tables:
1. students (id, name, ...)
2. courses (course_id, title, ...)
3. enrollments (student_id FK, course_id FK, grade)  ← Junction table
```

---

### 🎯 Chapter 3 — Interview Questions

**Q1. What is an ER Model?**  
> **Ans:** The ER (Entity-Relationship) Model is a high-level conceptual model used to design databases. It represents data as entities (objects), attributes (properties), and relationships (connections between entities). It's converted into tables before implementation.

**Q2. What is a Weak Entity?**  
> **Ans:** A weak entity cannot be uniquely identified by its own attributes alone. It depends on a strong (owner) entity. It uses a partial key + the owner's PK to form its primary key. Example: "Dependent" depends on "Employee."

**Q3. What is Cardinality?**  
> **Ans:** Cardinality defines the number of instances of one entity that can be associated with instances of another entity. Types: One-to-One (1:1), One-to-Many (1:M), Many-to-One (M:1), Many-to-Many (M:N).

**Q4. How do you convert a Many-to-Many relationship into tables?**  
> **Ans:** Create a separate junction table (bridge table) that contains the foreign keys from both entities as its composite primary key. Example: Students-Courses (M:N) → Create an "Enrollments" table with student_id and course_id as FK+PK.

**Q5. What is Total vs Partial Participation?**  
> **Ans:** Total participation means every entity MUST participate in the relationship (double line in ER diagram). Partial participation means entities MAY or MAY NOT participate (single line). Example: Every employee must belong to a department (total), but not every department must have a manager (partial).

---

---

# Chapter 4 — SQL Basics — DDL, DML, DCL, TCL

## 4.1 What is SQL?

**SQL (Structured Query Language)** is the **standard language** used to interact with relational databases.

SQL is divided into **5 categories:**

| Category | Full Form | Commands | Purpose |
|----------|-----------|----------|---------|
| **DDL** | Data Definition Language | CREATE, ALTER, DROP, TRUNCATE, RENAME | Define/modify structure |
| **DML** | Data Manipulation Language | INSERT, UPDATE, DELETE, SELECT | Manipulate data |
| **DCL** | Data Control Language | GRANT, REVOKE | Control access/permissions |
| **TCL** | Transaction Control Language | COMMIT, ROLLBACK, SAVEPOINT | Manage transactions |
| **DQL** | Data Query Language | SELECT | Query/retrieve data |

## 4.2 DDL — Data Definition Language

### CREATE — Create objects (tables, databases, indexes)

```sql
-- Create a database (PostgreSQL)
CREATE DATABASE placement_db;

-- Create table
CREATE TABLE employees (
    emp_id      SERIAL PRIMARY KEY,          -- PostgreSQL auto-increment
    -- emp_id   NUMBER GENERATED ALWAYS AS IDENTITY PRIMARY KEY, -- Oracle
    first_name  VARCHAR(50) NOT NULL,
    last_name   VARCHAR(50) NOT NULL,
    email       VARCHAR(100) UNIQUE,
    salary      DECIMAL(10, 2) DEFAULT 0.00,
    dept_id     INT,
    hire_date   DATE DEFAULT CURRENT_DATE,
    is_active   BOOLEAN DEFAULT TRUE         -- PostgreSQL
    -- is_active NUMBER(1) DEFAULT 1         -- Oracle (no BOOLEAN)
);

CREATE TABLE departments (
    dept_id     SERIAL PRIMARY KEY,
    dept_name   VARCHAR(100) NOT NULL UNIQUE,
    location    VARCHAR(100)
);

-- Add foreign key
ALTER TABLE employees
    ADD CONSTRAINT fk_dept
    FOREIGN KEY (dept_id) REFERENCES departments(dept_id);
```

### ALTER — Modify table structure

```sql
-- Add a column
ALTER TABLE employees ADD COLUMN phone VARCHAR(15);
-- Oracle: ALTER TABLE employees ADD (phone VARCHAR2(15));

-- Modify column data type
ALTER TABLE employees ALTER COLUMN phone TYPE VARCHAR(20);
-- Oracle: ALTER TABLE employees MODIFY (phone VARCHAR2(20));

-- Drop a column
ALTER TABLE employees DROP COLUMN phone;

-- Rename a column
ALTER TABLE employees RENAME COLUMN first_name TO fname;

-- Rename a table
ALTER TABLE employees RENAME TO staff;

-- Add a constraint
ALTER TABLE employees ADD CONSTRAINT chk_salary CHECK (salary >= 0);
```

### DROP — Delete objects permanently

```sql
-- Drop table (permanently removes table + data)
DROP TABLE employees;

-- Drop table if it exists
DROP TABLE IF EXISTS employees;        -- PostgreSQL
-- DROP TABLE employees;                -- Oracle (no IF EXISTS, use PL/SQL block)

-- Drop database
DROP DATABASE placement_db;
```

### TRUNCATE — Remove all rows (keep structure)

```sql
-- Remove all data but keep table structure
TRUNCATE TABLE employees;

-- With restart identity (reset auto-increment) — PostgreSQL
TRUNCATE TABLE employees RESTART IDENTITY;
```

### DROP vs TRUNCATE vs DELETE

| Feature | DROP | TRUNCATE | DELETE |
|---------|------|----------|--------|
| **What it removes** | Table + data + structure | All rows (keeps structure) | Specific rows (or all) |
| **WHERE clause** | ❌ | ❌ | ✅ |
| **Rollback** | ❌ | ❌ (DDL, auto-commit) | ✅ (can rollback) |
| **Speed** | Fast | Fast | Slow (row by row) |
| **Triggers fired** | ❌ | ❌ | ✅ |
| **Resets identity** | Yes (table gone) | Yes (optionally) | No |

## 4.3 DML — Data Manipulation Language

### INSERT — Add new rows

```sql
-- Insert single row
INSERT INTO departments (dept_id, dept_name, location)
VALUES (1, 'Engineering', 'Bangalore');

-- Insert multiple rows (PostgreSQL)
INSERT INTO departments (dept_id, dept_name, location) VALUES
    (2, 'Marketing', 'Mumbai'),
    (3, 'HR', 'Delhi'),
    (4, 'Finance', 'Chennai');

-- Oracle: Use INSERT ALL
-- INSERT ALL
--     INTO departments VALUES (2, 'Marketing', 'Mumbai')
--     INTO departments VALUES (3, 'HR', 'Delhi')
--     INTO departments VALUES (4, 'Finance', 'Chennai')
-- SELECT 1 FROM DUAL;

-- Insert from another table
INSERT INTO dept_backup
SELECT * FROM departments WHERE location = 'Bangalore';
```

### UPDATE — Modify existing rows

```sql
-- Update specific rows
UPDATE employees
SET salary = salary * 1.10
WHERE dept_id = 1;

-- Update multiple columns
UPDATE employees
SET salary = 75000,
    dept_id = 2,
    is_active = TRUE
WHERE emp_id = 101;

-- Update all rows (careful!)
UPDATE employees SET salary = salary + 5000;
```

### DELETE — Remove specific rows

```sql
-- Delete specific rows
DELETE FROM employees WHERE emp_id = 105;

-- Delete with condition
DELETE FROM employees WHERE dept_id = 4 AND is_active = FALSE;

-- Delete all rows (can be rolled back, unlike TRUNCATE)
DELETE FROM employees;
```

## 4.4 DCL — Data Control Language

```sql
-- GRANT: Give permissions to a user
GRANT SELECT, INSERT ON employees TO user1;
GRANT ALL PRIVILEGES ON employees TO admin_user;
GRANT SELECT ON employees TO PUBLIC;  -- everyone can read

-- REVOKE: Remove permissions
REVOKE INSERT ON employees FROM user1;
REVOKE ALL PRIVILEGES ON employees FROM user1;
```

## 4.5 TCL — Transaction Control Language

```sql
-- Start a transaction (PostgreSQL)
BEGIN;
-- Oracle: transactions start automatically

    UPDATE accounts SET balance = balance - 5000 WHERE id = 1;
    UPDATE accounts SET balance = balance + 5000 WHERE id = 2;

-- Save the changes permanently
COMMIT;

-- OR undo the changes
ROLLBACK;

-- SAVEPOINT: Create a checkpoint within a transaction
BEGIN;
    INSERT INTO orders VALUES (1, 'Laptop', 50000);
    SAVEPOINT sp1;
    INSERT INTO orders VALUES (2, 'Phone', 20000);
    -- Oops, undo only the second insert
    ROLLBACK TO sp1;
COMMIT;
-- Result: Only order 1 is saved
```

---

### 🎯 Chapter 4 — Interview Questions

**Q1. What are the different types of SQL commands?**  
> **Ans:** DDL (CREATE, ALTER, DROP, TRUNCATE — define structure), DML (INSERT, UPDATE, DELETE — manipulate data), DQL (SELECT — query data), DCL (GRANT, REVOKE — control access), TCL (COMMIT, ROLLBACK, SAVEPOINT — manage transactions).

**Q2. Difference between DROP, TRUNCATE, and DELETE?**  
> **Ans:** DROP removes the entire table (structure + data). TRUNCATE removes all rows but keeps structure (cannot use WHERE, faster, cannot rollback). DELETE removes specific rows (can use WHERE, slower, can rollback, fires triggers).

**Q3. What is the difference between DDL and DML?**  
> **Ans:** DDL defines/modifies the structure of database objects (tables, columns). It auto-commits. DML manipulates the data (insert, update, delete rows). DML can be rolled back within a transaction.

**Q4. What is a SAVEPOINT?**  
> **Ans:** A savepoint is a marker within a transaction that allows you to rollback to a specific point instead of rolling back the entire transaction. Useful for partial undo within a complex transaction.

**Q5. What is the difference between GRANT and REVOKE?**  
> **Ans:** GRANT gives permissions (SELECT, INSERT, UPDATE, DELETE, etc.) to users. REVOKE removes previously granted permissions from users.

---

---

# Chapter 5 — SQL Queries — SELECT, WHERE, ORDER BY

## 5.1 Sample Data Setup

```sql
-- Let's create sample tables for all examples
CREATE TABLE employees (
    emp_id      SERIAL PRIMARY KEY,
    first_name  VARCHAR(50),
    last_name   VARCHAR(50),
    email       VARCHAR(100) UNIQUE,
    salary      DECIMAL(10, 2),
    dept_id     INT,
    manager_id  INT,
    hire_date   DATE
);

CREATE TABLE departments (
    dept_id     SERIAL PRIMARY KEY,
    dept_name   VARCHAR(100),
    location    VARCHAR(100)
);

-- Insert sample data
INSERT INTO departments VALUES (1, 'Engineering', 'Bangalore');
INSERT INTO departments VALUES (2, 'Marketing', 'Mumbai');
INSERT INTO departments VALUES (3, 'HR', 'Delhi');
INSERT INTO departments VALUES (4, 'Finance', 'Chennai');

INSERT INTO employees VALUES (101, 'Rahul', 'Sharma', 'rahul@mail.com', 75000, 1, NULL, '2022-01-15');
INSERT INTO employees VALUES (102, 'Priya', 'Patel', 'priya@mail.com', 82000, 1, 101, '2022-03-20');
INSERT INTO employees VALUES (103, 'Amit', 'Kumar', 'amit@mail.com', 65000, 2, NULL, '2021-06-10');
INSERT INTO employees VALUES (104, 'Sneha', 'Reddy', 'sneha@mail.com', 90000, 1, 101, '2020-11-05');
INSERT INTO employees VALUES (105, 'Vikram', 'Singh', 'vikram@mail.com', 55000, 3, NULL, '2023-02-28');
INSERT INTO employees VALUES (106, 'Neha', 'Gupta', 'neha@mail.com', 70000, 2, 103, '2022-08-14');
INSERT INTO employees VALUES (107, 'Arjun', 'Nair', 'arjun@mail.com', 95000, 4, NULL, '2019-04-01');
INSERT INTO employees VALUES (108, 'Kavita', 'Joshi', 'kavita@mail.com', 60000, 3, 105, '2023-07-22');
```

## 5.2 SELECT — Retrieve Data

```sql
-- Select all columns
SELECT * FROM employees;

-- Select specific columns
SELECT first_name, last_name, salary FROM employees;

-- Aliases (rename columns in output)
SELECT first_name AS "First Name", salary AS "Monthly Pay"
FROM employees;

-- Calculated columns
SELECT first_name, salary, salary * 12 AS annual_salary
FROM employees;

-- Distinct values (remove duplicates)
SELECT DISTINCT dept_id FROM employees;

-- Concatenation
SELECT first_name || ' ' || last_name AS full_name FROM employees;  -- PostgreSQL/Oracle
```

## 5.3 WHERE — Filter Rows

```sql
-- Basic comparison
SELECT * FROM employees WHERE salary > 70000;
SELECT * FROM employees WHERE dept_id = 1;
SELECT * FROM employees WHERE first_name = 'Rahul';

-- Multiple conditions (AND, OR, NOT)
SELECT * FROM employees WHERE dept_id = 1 AND salary > 80000;
SELECT * FROM employees WHERE dept_id = 1 OR dept_id = 2;
SELECT * FROM employees WHERE NOT dept_id = 3;

-- BETWEEN (inclusive range)
SELECT * FROM employees WHERE salary BETWEEN 60000 AND 80000;
-- Equivalent to: salary >= 60000 AND salary <= 80000

-- IN (match any value in list)
SELECT * FROM employees WHERE dept_id IN (1, 2, 4);
-- Equivalent to: dept_id = 1 OR dept_id = 2 OR dept_id = 4

-- LIKE (pattern matching)
SELECT * FROM employees WHERE first_name LIKE 'A%';    -- Starts with A
SELECT * FROM employees WHERE last_name LIKE '%ar%';   -- Contains "ar"
SELECT * FROM employees WHERE first_name LIKE '_a%';   -- Second char is 'a'
SELECT * FROM employees WHERE email LIKE '%@mail.com'; -- Ends with @mail.com

-- Wildcards:  % = any number of characters,  _ = exactly one character

-- IS NULL / IS NOT NULL
SELECT * FROM employees WHERE manager_id IS NULL;      -- No manager
SELECT * FROM employees WHERE manager_id IS NOT NULL;   -- Has a manager

-- NOT IN
SELECT * FROM employees WHERE dept_id NOT IN (3, 4);
```

## 5.4 ORDER BY — Sort Results

```sql
-- Sort ascending (default)
SELECT * FROM employees ORDER BY salary;
SELECT * FROM employees ORDER BY salary ASC;

-- Sort descending
SELECT * FROM employees ORDER BY salary DESC;

-- Multiple sort columns
SELECT * FROM employees ORDER BY dept_id ASC, salary DESC;
-- First sort by dept_id ascending, then within each dept by salary descending

-- Sort by column position
SELECT first_name, salary FROM employees ORDER BY 2 DESC;
-- 2 = second column (salary)
```

## 5.5 LIMIT / FETCH — Restrict Rows

```sql
-- PostgreSQL: LIMIT
SELECT * FROM employees ORDER BY salary DESC LIMIT 5;     -- Top 5 salaries
SELECT * FROM employees ORDER BY salary DESC LIMIT 5 OFFSET 5; -- Skip 5, get next 5

-- Oracle: FETCH FIRST
SELECT * FROM employees ORDER BY salary DESC FETCH FIRST 5 ROWS ONLY;
SELECT * FROM employees ORDER BY salary DESC OFFSET 5 ROWS FETCH NEXT 5 ROWS ONLY;

-- Oracle legacy: ROWNUM
-- SELECT * FROM (SELECT * FROM employees ORDER BY salary DESC) WHERE ROWNUM <= 5;
```

## 5.6 Common SQL Functions

### String Functions

```sql
SELECT UPPER('hello');                      -- HELLO
SELECT LOWER('HELLO');                      -- hello
SELECT LENGTH('Rahul');                     -- 5
SELECT SUBSTRING('Rahul' FROM 1 FOR 3);    -- Rah  (PostgreSQL)
-- SELECT SUBSTR('Rahul', 1, 3) FROM DUAL; -- Rah  (Oracle)
SELECT TRIM('  hello  ');                   -- hello
SELECT REPLACE('Hello World', 'World', 'SQL'); -- Hello SQL
SELECT CONCAT('Rahul', ' ', 'Sharma');      -- Rahul Sharma (PostgreSQL)
-- Oracle: 'Rahul' || ' ' || 'Sharma'
```

### Numeric Functions

```sql
SELECT ROUND(45.926, 2);       -- 45.93
SELECT CEIL(45.1);             -- 46
SELECT FLOOR(45.9);            -- 45
SELECT ABS(-15);               -- 15
SELECT MOD(10, 3);             -- 1
SELECT POWER(2, 3);            -- 8
SELECT SQRT(144);              -- 12
```

### Date Functions

```sql
-- Current date/time
SELECT CURRENT_DATE;                    -- 2026-07-11
SELECT CURRENT_TIMESTAMP;              -- 2026-07-11 19:30:00
SELECT NOW();                          -- PostgreSQL: full timestamp

-- Extract parts
SELECT EXTRACT(YEAR FROM hire_date) FROM employees;
SELECT EXTRACT(MONTH FROM hire_date) FROM employees;

-- Date arithmetic
SELECT hire_date + INTERVAL '1 year' FROM employees;   -- PostgreSQL
-- SELECT hire_date + INTERVAL '1' YEAR FROM employees; -- Oracle
SELECT AGE(CURRENT_DATE, hire_date) FROM employees;    -- PostgreSQL: difference

-- Format date (PostgreSQL)
SELECT TO_CHAR(hire_date, 'DD-Mon-YYYY') FROM employees;
-- Oracle: same syntax
```

### NULL Handling

```sql
-- COALESCE: returns first non-null value
SELECT first_name, COALESCE(manager_id, 0) AS manager FROM employees;

-- NULLIF: returns NULL if two values are equal
SELECT NULLIF(10, 10);  -- NULL
SELECT NULLIF(10, 20);  -- 10

-- CASE expression
SELECT first_name, salary,
    CASE
        WHEN salary >= 90000 THEN 'High'
        WHEN salary >= 70000 THEN 'Medium'
        ELSE 'Low'
    END AS salary_grade
FROM employees;
```

---

### 🎯 Chapter 5 — Interview Questions

**Q1. What is the difference between WHERE and HAVING?**  
> **Ans:** WHERE filters rows BEFORE grouping (works on individual rows). HAVING filters groups AFTER GROUP BY (works on aggregated results). WHERE can't use aggregate functions; HAVING can.

**Q2. What is the difference between LIKE and = operator?**  
> **Ans:** `=` is for exact matching. `LIKE` is for pattern matching using wildcards: `%` (any characters) and `_` (single character). Example: `LIKE 'A%'` matches anything starting with A.

**Q3. What is the difference between IN and BETWEEN?**  
> **Ans:** `IN` matches against a specific list of values: `WHERE id IN (1,2,3)`. `BETWEEN` matches a range (inclusive): `WHERE salary BETWEEN 50000 AND 80000`.

**Q4. How to handle NULL values in SQL?**  
> **Ans:** NULL means missing/unknown. Use `IS NULL` or `IS NOT NULL` to check (not `= NULL`). Use `COALESCE(column, default)` to replace NULLs. NULL in arithmetic returns NULL. NULL in comparison returns UNKNOWN.

**Q5. What is the difference between LIMIT and FETCH FIRST?**  
> **Ans:** Both restrict the number of rows returned. `LIMIT` is PostgreSQL/MySQL syntax. `FETCH FIRST N ROWS ONLY` is the SQL standard and Oracle syntax. Both achieve the same result.

---

---

# Chapter 6 — SQL Joins

## 6.1 What is a Join?

A **JOIN** combines rows from **two or more tables** based on a **related column** (usually FK-PK relationship).

## 6.2 Types of Joins

```
     A            B
  ┌──────┐    ┌──────┐
  │ 1  a │    │ 1  x │
  │ 2  b │    │ 2  y │
  │ 3  c │    │ 4  z │
  └──────┘    └──────┘
```

### 6.2.1 INNER JOIN

Returns only **matching rows** from both tables.

```sql
SELECT e.emp_id, e.first_name, d.dept_name
FROM employees e
INNER JOIN departments d ON e.dept_id = d.dept_id;
```

```
Result: Only employees whose dept_id exists in departments table.

┌────────┬────────────┬─────────────┐
│ emp_id │ first_name │ dept_name   │
├────────┼────────────┼─────────────┤
│    101 │ Rahul      │ Engineering │
│    102 │ Priya      │ Engineering │
│    103 │ Amit       │ Marketing   │
│    ...                             │
└────────┴────────────┴─────────────┘
```

```
    A ∩ B (only matching rows)
   ┌───────────┐
   │   █████   │
   │  █░░░░█   │
   │   █████   │
   └───────────┘
```

### 6.2.2 LEFT JOIN (LEFT OUTER JOIN)

Returns **all rows from left table** + matching rows from right table. Non-matching → NULL.

```sql
SELECT e.emp_id, e.first_name, d.dept_name
FROM employees e
LEFT JOIN departments d ON e.dept_id = d.dept_id;
```

```
All employees shown. If no matching department → dept_name = NULL.
```

### 6.2.3 RIGHT JOIN (RIGHT OUTER JOIN)

Returns **all rows from right table** + matching rows from left table. Non-matching → NULL.

```sql
SELECT e.emp_id, e.first_name, d.dept_name
FROM employees e
RIGHT JOIN departments d ON e.dept_id = d.dept_id;
```

```
All departments shown. If no employee in that dept → emp_id = NULL.
```

### 6.2.4 FULL OUTER JOIN

Returns **all rows from both tables**. Non-matching → NULL on the missing side.

```sql
SELECT e.emp_id, e.first_name, d.dept_name
FROM employees e
FULL OUTER JOIN departments d ON e.dept_id = d.dept_id;
```

### 6.2.5 CROSS JOIN (Cartesian Product)

Returns **every combination** of rows from both tables. If A has 3 rows and B has 4 rows → result = 12 rows.

```sql
SELECT e.first_name, d.dept_name
FROM employees e
CROSS JOIN departments d;
-- 8 employees × 4 departments = 32 rows
```

### 6.2.6 SELF JOIN

A table is joined **with itself**. Used for hierarchical data (e.g., employee-manager).

```sql
-- Find each employee and their manager's name
SELECT
    e.first_name AS employee,
    m.first_name AS manager
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.emp_id;
```

```
┌──────────┬─────────┐
│ employee │ manager │
├──────────┼─────────┤
│ Rahul    │ NULL    │  ← No manager (top)
│ Priya    │ Rahul   │
│ Sneha    │ Rahul   │
│ Amit     │ NULL    │
│ Neha     │ Amit    │
│ ...                 │
└──────────┴─────────┘
```

### 6.2.7 NATURAL JOIN

Automatically joins on columns with the **same name** in both tables. Not recommended (fragile).

```sql
SELECT * FROM employees NATURAL JOIN departments;
-- Joins on dept_id (common column)
```

## 6.3 Join Summary

| Join Type | What it Returns | NULL Behavior |
|-----------|----------------|---------------|
| **INNER JOIN** | Only matching rows from both | No NULLs |
| **LEFT JOIN** | All left + matching right | Right side NULL if no match |
| **RIGHT JOIN** | All right + matching left | Left side NULL if no match |
| **FULL OUTER JOIN** | All rows from both | NULLs on either side |
| **CROSS JOIN** | All combinations (Cartesian product) | No NULLs |
| **SELF JOIN** | Table joined with itself | Depends on join type used |

## 6.4 Join with Multiple Tables

```sql
-- 3-table join: employees → departments → locations
SELECT
    e.first_name,
    d.dept_name,
    l.city
FROM employees e
JOIN departments d ON e.dept_id = d.dept_id
JOIN locations l ON d.location_id = l.location_id
WHERE l.city = 'Bangalore';
```

---

### 🎯 Chapter 6 — Interview Questions

**Q1. What is a JOIN? Types?**  
> **Ans:** A JOIN combines rows from two or more tables based on a related column. Types: INNER (only matches), LEFT (all left + matches), RIGHT (all right + matches), FULL OUTER (all from both), CROSS (all combinations), SELF (table with itself).

**Q2. Difference between INNER JOIN and LEFT JOIN?**  
> **Ans:** INNER JOIN returns only matching rows from both tables. LEFT JOIN returns ALL rows from the left table and matching rows from the right table; if no match, right side columns are NULL.

**Q3. What is a Self Join?**  
> **Ans:** A self join is when a table is joined with itself. Used for hierarchical data like employee-manager relationships. You use aliases to treat the same table as two different tables.

**Q4. What is a Cross Join?**  
> **Ans:** A cross join returns the Cartesian product — every possible combination of rows from both tables. If table A has M rows and table B has N rows, result has M×N rows. No ON condition needed.

**Q5. Can we join more than two tables?**  
> **Ans:** Yes! You can chain multiple JOINs. Each additional JOIN connects a new table to the existing result. Common in real-world queries: `A JOIN B ON ... JOIN C ON ... JOIN D ON ...`

**Q6. What is the difference between JOIN and UNION?**  
> **Ans:** JOIN combines columns from different tables horizontally (side by side). UNION combines rows from different queries vertically (stacked on top). JOIN uses relationships; UNION requires same column count and compatible types.

---

---

# Chapter 7 — SQL Aggregate Functions & GROUP BY

## 7.1 Aggregate Functions

Aggregate functions perform calculations on **a set of rows** and return a **single value**.

| Function | What it Does | Example |
|----------|-------------|---------|
| `COUNT()` | Count number of rows | `COUNT(*)` |
| `SUM()` | Sum of values | `SUM(salary)` |
| `AVG()` | Average of values | `AVG(salary)` |
| `MAX()` | Maximum value | `MAX(salary)` |
| `MIN()` | Minimum value | `MIN(salary)` |

```sql
-- Basic aggregates
SELECT COUNT(*) AS total_employees FROM employees;           -- 8
SELECT SUM(salary) AS total_salary FROM employees;           -- 592000
SELECT AVG(salary) AS avg_salary FROM employees;             -- 74000
SELECT MAX(salary) AS highest_salary FROM employees;         -- 95000
SELECT MIN(salary) AS lowest_salary FROM employees;          -- 55000

-- COUNT with conditions
SELECT COUNT(*) FROM employees WHERE dept_id = 1;            -- 3
SELECT COUNT(DISTINCT dept_id) FROM employees;               -- 4 unique departments

-- COUNT(*) vs COUNT(column)
SELECT COUNT(*) FROM employees;              -- Counts ALL rows (including NULLs)
SELECT COUNT(manager_id) FROM employees;     -- Counts only NON-NULL values
```

## 7.2 GROUP BY

Groups rows with the **same values** and applies aggregate functions to each group.

```sql
-- Count employees per department
SELECT dept_id, COUNT(*) AS emp_count
FROM employees
GROUP BY dept_id;

-- Result:
-- dept_id | emp_count
-- --------+----------
--    1    |    3
--    2    |    2
--    3    |    2
--    4    |    1

-- Average salary per department
SELECT dept_id, AVG(salary) AS avg_salary
FROM employees
GROUP BY dept_id
ORDER BY avg_salary DESC;

-- Department name with count (using JOIN + GROUP BY)
SELECT d.dept_name, COUNT(e.emp_id) AS emp_count, AVG(e.salary) AS avg_sal
FROM employees e
JOIN departments d ON e.dept_id = d.dept_id
GROUP BY d.dept_name
ORDER BY emp_count DESC;
```

**Rule:** In a query with GROUP BY, every column in SELECT must be either:
1. In the GROUP BY clause, OR
2. Inside an aggregate function.

```sql
-- ❌ WRONG (first_name not in GROUP BY or aggregate)
SELECT dept_id, first_name, COUNT(*)
FROM employees
GROUP BY dept_id;

-- ✅ CORRECT
SELECT dept_id, COUNT(*), MAX(first_name)
FROM employees
GROUP BY dept_id;
```

## 7.3 HAVING — Filter Groups

```sql
-- Departments with more than 1 employee
SELECT dept_id, COUNT(*) AS emp_count
FROM employees
GROUP BY dept_id
HAVING COUNT(*) > 1;

-- Departments where average salary > 70000
SELECT dept_id, AVG(salary) AS avg_sal
FROM employees
GROUP BY dept_id
HAVING AVG(salary) > 70000;
```

## 7.4 WHERE vs HAVING

| Feature | WHERE | HAVING |
|---------|-------|--------|
| **When** | Before GROUP BY (filters rows) | After GROUP BY (filters groups) |
| **Works on** | Individual rows | Grouped/aggregated results |
| **Aggregate functions** | ❌ Cannot use | ✅ Can use |

```sql
-- Combined: WHERE + GROUP BY + HAVING
SELECT dept_id, AVG(salary) AS avg_sal
FROM employees
WHERE hire_date >= '2021-01-01'          -- Filter individual rows first
GROUP BY dept_id                          -- Then group
HAVING AVG(salary) > 65000               -- Then filter groups
ORDER BY avg_sal DESC;                    -- Then sort
```

**SQL Execution Order:**
```
FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
```

## 7.5 Window Functions (Analytical Functions)

Window functions perform calculations **across a set of rows** but **don't collapse them** into a single row (unlike aggregate functions).

```sql
-- ROW_NUMBER: Assign sequential numbers
SELECT
    first_name,
    salary,
    dept_id,
    ROW_NUMBER() OVER (ORDER BY salary DESC) AS rank
FROM employees;

-- RANK: Same values get same rank (gaps in ranking)
SELECT
    first_name,
    salary,
    RANK() OVER (ORDER BY salary DESC) AS rank
FROM employees;

-- DENSE_RANK: Same values get same rank (NO gaps)
SELECT
    first_name,
    salary,
    DENSE_RANK() OVER (ORDER BY salary DESC) AS dense_rank
FROM employees;

-- Partition: Rank within each department
SELECT
    first_name,
    dept_id,
    salary,
    ROW_NUMBER() OVER (PARTITION BY dept_id ORDER BY salary DESC) AS dept_rank
FROM employees;

-- Running total
SELECT
    first_name,
    salary,
    SUM(salary) OVER (ORDER BY emp_id) AS running_total
FROM employees;

-- LAG / LEAD: Access previous/next row
SELECT
    first_name,
    salary,
    LAG(salary, 1) OVER (ORDER BY emp_id) AS prev_salary,
    LEAD(salary, 1) OVER (ORDER BY emp_id) AS next_salary
FROM employees;
```

### ROW_NUMBER vs RANK vs DENSE_RANK

```
Salary: 95000, 90000, 82000, 82000, 75000

ROW_NUMBER:  1, 2, 3, 4, 5    (always unique, no ties)
RANK:        1, 2, 3, 3, 5    (same value = same rank, GAP after tie)
DENSE_RANK:  1, 2, 3, 3, 4    (same value = same rank, NO gap)
```

---

### 🎯 Chapter 7 — Interview Questions

**Q1. What is the difference between COUNT(*) and COUNT(column)?**  
> **Ans:** `COUNT(*)` counts all rows including those with NULL values. `COUNT(column)` counts only non-NULL values in that specific column.

**Q2. Difference between WHERE and HAVING?**  
> **Ans:** WHERE filters individual rows before grouping (can't use aggregates). HAVING filters groups after GROUP BY (can use aggregates). Example: WHERE salary > 50000 vs HAVING AVG(salary) > 50000.

**Q3. What is the SQL execution order?**  
> **Ans:** FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT. This is why you can't use column aliases in WHERE but can in ORDER BY.

**Q4. Difference between ROW_NUMBER, RANK, and DENSE_RANK?**  
> **Ans:** ROW_NUMBER: always unique sequential numbers. RANK: same values get same rank but leaves gaps (1,2,3,3,5). DENSE_RANK: same values get same rank with no gaps (1,2,3,3,4).

**Q5. What is a Window Function?**  
> **Ans:** A window function performs calculations across a set of rows related to the current row, without collapsing them into a single row. Uses OVER() clause. Examples: ROW_NUMBER(), RANK(), SUM() OVER(), LAG(), LEAD().

**Q6. Find the second highest salary.**  
> **Ans:**
> ```sql
> -- Method 1: Subquery
> SELECT MAX(salary) FROM employees
> WHERE salary < (SELECT MAX(salary) FROM employees);
> 
> -- Method 2: OFFSET
> SELECT salary FROM employees ORDER BY salary DESC LIMIT 1 OFFSET 1;
> 
> -- Method 3: DENSE_RANK
> SELECT salary FROM (
>     SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk
>     FROM employees
> ) t WHERE rnk = 2;
> ```

---

---

# Chapter 8 — Subqueries (Nested Queries)

## 8.1 What is a Subquery?

A **subquery** is a query **inside another query**. The inner query executes first, and its result is used by the outer query.

```sql
-- Find employees who earn more than the average salary
SELECT first_name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

## 8.2 Types of Subqueries

### 8.2.1 Single-Row Subquery

Returns **one value**. Use with `=`, `>`, `<`, `>=`, `<=`, `<>`.

```sql
-- Employee with the highest salary
SELECT * FROM employees
WHERE salary = (SELECT MAX(salary) FROM employees);

-- Employees in the same department as 'Rahul'
SELECT * FROM employees
WHERE dept_id = (SELECT dept_id FROM employees WHERE first_name = 'Rahul');
```

### 8.2.2 Multi-Row Subquery

Returns **multiple values**. Use with `IN`, `ANY`, `ALL`, `EXISTS`.

```sql
-- Employees in Engineering or Marketing departments
SELECT * FROM employees
WHERE dept_id IN (
    SELECT dept_id FROM departments
    WHERE dept_name IN ('Engineering', 'Marketing')
);

-- Employees who earn more than ANY employee in dept 2
SELECT * FROM employees
WHERE salary > ANY (SELECT salary FROM employees WHERE dept_id = 2);

-- Employees who earn more than ALL employees in dept 3
SELECT * FROM employees
WHERE salary > ALL (SELECT salary FROM employees WHERE dept_id = 3);
```

### 8.2.3 Correlated Subquery

The inner query **depends on the outer query** (references outer query's columns). Executes once for each row of the outer query.

```sql
-- Employees who earn more than the average salary of their department
SELECT e.first_name, e.salary, e.dept_id
FROM employees e
WHERE e.salary > (
    SELECT AVG(salary)
    FROM employees
    WHERE dept_id = e.dept_id    -- References outer query's dept_id
);
```

### 8.2.4 EXISTS Subquery

Returns TRUE if the subquery returns **at least one row**.

```sql
-- Departments that have at least one employee
SELECT d.dept_name
FROM departments d
WHERE EXISTS (
    SELECT 1 FROM employees e
    WHERE e.dept_id = d.dept_id
);

-- Departments that have NO employees
SELECT d.dept_name
FROM departments d
WHERE NOT EXISTS (
    SELECT 1 FROM employees e
    WHERE e.dept_id = d.dept_id
);
```

### 8.2.5 Subquery in FROM (Derived Table / Inline View)

```sql
-- Top 3 highest-paid employees per department
SELECT * FROM (
    SELECT
        first_name,
        dept_id,
        salary,
        ROW_NUMBER() OVER (PARTITION BY dept_id ORDER BY salary DESC) AS rn
    FROM employees
) ranked
WHERE rn <= 3;
```

### 8.2.6 Subquery in SELECT

```sql
-- Each employee with their department's average salary
SELECT
    first_name,
    salary,
    (SELECT AVG(salary) FROM employees e2 WHERE e2.dept_id = e1.dept_id) AS dept_avg
FROM employees e1;
```

## 8.3 CTE (Common Table Expression) — WITH Clause

A **CTE** is a temporary named result set. More readable than nested subqueries.

```sql
-- Find employees earning above their department average
WITH dept_avg AS (
    SELECT dept_id, AVG(salary) AS avg_sal
    FROM employees
    GROUP BY dept_id
)
SELECT e.first_name, e.salary, d.avg_sal
FROM employees e
JOIN dept_avg d ON e.dept_id = d.dept_id
WHERE e.salary > d.avg_sal;

-- Recursive CTE: Employee hierarchy
WITH RECURSIVE emp_hierarchy AS (
    -- Base case: top-level managers (no manager)
    SELECT emp_id, first_name, manager_id, 1 AS level
    FROM employees
    WHERE manager_id IS NULL

    UNION ALL

    -- Recursive case: employees under managers
    SELECT e.emp_id, e.first_name, e.manager_id, h.level + 1
    FROM employees e
    JOIN emp_hierarchy h ON e.manager_id = h.emp_id
)
SELECT * FROM emp_hierarchy ORDER BY level, emp_id;

-- Oracle uses: WITH emp_hierarchy (emp_id, first_name, ...) AS (...)
```

---

### 🎯 Chapter 8 — Interview Questions

**Q1. What is a Subquery?**  
> **Ans:** A subquery is a query nested inside another query. The inner query runs first, and its result is used by the outer query. Can be used in WHERE, FROM, SELECT, and HAVING clauses.

**Q2. What is a Correlated Subquery?**  
> **Ans:** A correlated subquery references a column from the outer query. It executes once for each row of the outer query, making it slower than a non-correlated subquery. Example: finding employees who earn more than their department average.

**Q3. Difference between IN and EXISTS?**  
> **Ans:** `IN` compares a value against a list returned by the subquery. `EXISTS` checks if the subquery returns any rows (TRUE/FALSE). EXISTS is generally faster for large datasets because it stops as soon as it finds one match. Use EXISTS when checking existence; IN when comparing values.

**Q4. What is a CTE (Common Table Expression)?**  
> **Ans:** A CTE is a temporary named result set defined using the WITH clause. It makes complex queries more readable. Unlike views, CTEs exist only during query execution. Recursive CTEs can reference themselves for hierarchical queries.

**Q5. Write a query to find the Nth highest salary.**  
> **Ans:**
> ```sql
> -- Using DENSE_RANK
> SELECT salary FROM (
>     SELECT DISTINCT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk
>     FROM employees
> ) t WHERE rnk = N;  -- Replace N with desired rank
> ```

---

---

# Chapter 9 — SQL Views, Indexes & Sequences

## 9.1 Views

A **view** is a **virtual table** based on a SELECT query. It doesn't store data itself — it runs the query every time it's accessed.

```sql
-- Create a view
CREATE VIEW high_earners AS
SELECT emp_id, first_name, last_name, salary, dept_id
FROM employees
WHERE salary > 80000;

-- Use the view like a table
SELECT * FROM high_earners;

-- View with join
CREATE VIEW emp_dept_view AS
SELECT e.emp_id, e.first_name, d.dept_name, e.salary
FROM employees e
JOIN departments d ON e.dept_id = d.dept_id;

-- Update view (replace)
CREATE OR REPLACE VIEW high_earners AS
SELECT emp_id, first_name, salary
FROM employees
WHERE salary > 75000;

-- Drop a view
DROP VIEW high_earners;
DROP VIEW IF EXISTS high_earners;  -- PostgreSQL
```

### Materialized View (PostgreSQL / Oracle)

A **materialized view** actually **stores the data** physically. Faster reads but needs to be refreshed.

```sql
-- Create materialized view
CREATE MATERIALIZED VIEW dept_summary AS
SELECT dept_id, COUNT(*) AS emp_count, AVG(salary) AS avg_salary
FROM employees
GROUP BY dept_id;

-- Refresh (update data)
REFRESH MATERIALIZED VIEW dept_summary;

-- Oracle: can auto-refresh
-- CREATE MATERIALIZED VIEW dept_summary
-- BUILD IMMEDIATE REFRESH ON COMMIT AS ...;
```

| Feature | Regular View | Materialized View |
|---------|:---:|:---:|
| Stores data | ❌ (runs query each time) | ✅ (cached result) |
| Speed | Slower (recomputes) | Faster (pre-computed) |
| Fresh data | Always current | May be stale (needs refresh) |
| Storage | No extra space | Uses disk space |

## 9.2 Indexes

An **index** is a data structure that **speeds up data retrieval** (like a book's index page).

```sql
-- Create an index
CREATE INDEX idx_emp_salary ON employees(salary);

-- Composite index (multiple columns)
CREATE INDEX idx_emp_dept_salary ON employees(dept_id, salary);

-- Unique index
CREATE UNIQUE INDEX idx_emp_email ON employees(email);

-- Drop an index
DROP INDEX idx_emp_salary;
-- Oracle: DROP INDEX idx_emp_salary;
```

### When to Use Indexes

| Use Index When | Don't Use Index When |
|----------------|---------------------|
| Column used frequently in WHERE | Small tables |
| Column used in JOIN conditions | Columns with many NULLs |
| Column used in ORDER BY | Columns rarely used in queries |
| High selectivity (many unique values) | Columns that change frequently |

### Index Types

| Type | Description |
|------|------------|
| **B-Tree** | Default, good for equality and range queries |
| **Hash** | Good for equality only (PostgreSQL) |
| **GIN** | Good for full-text search, arrays (PostgreSQL) |
| **GiST** | Good for geometric/spatial data (PostgreSQL) |
| **Bitmap** | Good for low-cardinality columns (Oracle) |

**Trade-off:** Indexes speed up **reads** but slow down **writes** (INSERT, UPDATE, DELETE must update the index too).

## 9.3 Sequences

A **sequence** generates unique, auto-incrementing numbers.

```sql
-- PostgreSQL: Create sequence
CREATE SEQUENCE emp_id_seq START 1 INCREMENT 1;

-- Use sequence
SELECT nextval('emp_id_seq');    -- Get next value (1, 2, 3, ...)
SELECT currval('emp_id_seq');    -- Get current value

-- Use in INSERT
INSERT INTO employees (emp_id, first_name) VALUES (nextval('emp_id_seq'), 'Test');

-- PostgreSQL: SERIAL type auto-creates a sequence
CREATE TABLE test (id SERIAL PRIMARY KEY, name VARCHAR(50));
-- Equivalent to:
-- CREATE SEQUENCE test_id_seq; CREATE TABLE test (id INT DEFAULT nextval('test_id_seq'), ...);

-- Oracle: Create sequence
-- CREATE SEQUENCE emp_id_seq START WITH 1 INCREMENT BY 1;
-- INSERT INTO employees (emp_id, first_name) VALUES (emp_id_seq.NEXTVAL, 'Test');
-- SELECT emp_id_seq.CURRVAL FROM DUAL;
```

---

### 🎯 Chapter 9 — Interview Questions

**Q1. What is a View?**  
> **Ans:** A view is a virtual table based on a SELECT query. It doesn't store data; it runs the query each time it's accessed. Used for security (restrict column/row access), simplification (hide complex joins), and abstraction.

**Q2. What is a Materialized View?**  
> **Ans:** A materialized view stores the query result physically on disk. Faster than regular views since data is pre-computed, but may show stale data. Needs periodic refresh. Supported in PostgreSQL and Oracle.

**Q3. What is an Index? Why is it used?**  
> **Ans:** An index is a data structure (typically B-Tree) that speeds up data retrieval on a column. Like a book's index, it helps find rows quickly without scanning the entire table. Trade-off: faster reads but slower writes.

**Q4. When should you NOT use an index?**  
> **Ans:** On small tables (full scan is fast enough), columns with many NULLs, columns rarely used in WHERE/JOIN/ORDER BY, columns that are frequently updated (index maintenance overhead), and low-selectivity columns.

**Q5. What is a Sequence?**  
> **Ans:** A sequence is a database object that generates unique, auto-incrementing numbers. Used for generating primary key values. PostgreSQL: SERIAL type. Oracle: CREATE SEQUENCE + .NEXTVAL.

---

---

# Chapter 10 — SQL Constraints

## 10.1 What are Constraints?

**Constraints** are rules enforced on table columns to ensure **data integrity** and **validity**.

## 10.2 Types of Constraints

| Constraint | Description | Example |
|-----------|------------|---------|
| **NOT NULL** | Column cannot have NULL values | name VARCHAR(50) NOT NULL |
| **UNIQUE** | All values must be different | email VARCHAR(100) UNIQUE |
| **PRIMARY KEY** | NOT NULL + UNIQUE (identifies rows) | emp_id INT PRIMARY KEY |
| **FOREIGN KEY** | References PK of another table | REFERENCES departments(dept_id) |
| **CHECK** | Value must satisfy a condition | CHECK (salary >= 0) |
| **DEFAULT** | Sets a default value if none provided | is_active BOOLEAN DEFAULT TRUE |

```sql
CREATE TABLE products (
    product_id   SERIAL PRIMARY KEY,                    -- PK
    name         VARCHAR(100) NOT NULL,                 -- NOT NULL
    sku          VARCHAR(50) UNIQUE,                    -- UNIQUE
    price        DECIMAL(10,2) CHECK (price > 0),       -- CHECK
    quantity     INT DEFAULT 0,                          -- DEFAULT
    category_id  INT REFERENCES categories(cat_id),     -- FK
    created_at   TIMESTAMP DEFAULT CURRENT_TIMESTAMP    -- DEFAULT
);
```

## 10.3 Foreign Key Actions (ON DELETE / ON UPDATE)

What happens when the **referenced row** is deleted or updated?

```sql
CREATE TABLE orders (
    order_id     SERIAL PRIMARY KEY,
    customer_id  INT,
    FOREIGN KEY (customer_id) REFERENCES customers(id)
        ON DELETE CASCADE        -- Delete orders when customer is deleted
        ON UPDATE SET NULL       -- Set NULL if customer ID changes
);
```

| Action | On DELETE | On UPDATE |
|--------|-----------|-----------|
| **CASCADE** | Delete child rows too | Update child FK values too |
| **SET NULL** | Set FK to NULL | Set FK to NULL |
| **SET DEFAULT** | Set FK to default value | Set FK to default value |
| **RESTRICT** | Prevent deletion if children exist | Prevent update if children exist |
| **NO ACTION** | Same as RESTRICT (default) | Same as RESTRICT (default) |

```sql
-- Example: If you delete a department, all employees in that dept are also deleted
FOREIGN KEY (dept_id) REFERENCES departments(dept_id) ON DELETE CASCADE;

-- Example: If you delete a department, employees' dept_id becomes NULL
FOREIGN KEY (dept_id) REFERENCES departments(dept_id) ON DELETE SET NULL;

-- Example: Prevent deleting a department that has employees
FOREIGN KEY (dept_id) REFERENCES departments(dept_id) ON DELETE RESTRICT;
```

---

### 🎯 Chapter 10 — Interview Questions

**Q1. What are Constraints? Name the types.**  
> **Ans:** Constraints are rules on table columns that ensure data integrity. Types: NOT NULL (no NULLs), UNIQUE (all different), PRIMARY KEY (NOT NULL + UNIQUE), FOREIGN KEY (references another table), CHECK (custom condition), DEFAULT (default value).

**Q2. What is ON DELETE CASCADE?**  
> **Ans:** ON DELETE CASCADE means when a referenced row in the parent table is deleted, all related rows in the child table are automatically deleted too. Example: deleting a customer also deletes all their orders.

**Q3. Difference between NOT NULL and DEFAULT?**  
> **Ans:** NOT NULL means the column MUST have a value (INSERT fails without it). DEFAULT provides a value automatically if none is given, but NULL can still be explicitly inserted (unless NOT NULL is also used).

**Q4. Can a Foreign Key reference a non-Primary Key column?**  
> **Ans:** Yes, a foreign key can reference any column with a UNIQUE constraint (not just the primary key). However, it's most commonly used with primary keys.

---

---

# Chapter 11 — Normalization

## 11.1 What is Normalization?

**Normalization** is the process of organizing data in a database to **reduce redundancy** and **prevent anomalies** (insertion, update, deletion anomalies).

## 11.2 Why Normalize?

**Without normalization (redundant data):**

| Student | Course | Teacher | Teacher_Phone |
|---------|--------|---------|---------------|
| Rahul | DBMS | Prof. Sharma | 9876543210 |
| Rahul | OS | Prof. Kumar | 9887766554 |
| Priya | DBMS | Prof. Sharma | 9876543210 |

**Problems:**
- **Update Anomaly:** If Prof. Sharma's phone changes → must update ALL rows with him.
- **Insert Anomaly:** Can't add a new teacher without assigning a student.
- **Delete Anomaly:** If Priya drops DBMS → we lose Prof. Sharma's phone number.

## 11.3 Normal Forms

### First Normal Form (1NF)

**Rule:** Every cell must contain a **single (atomic) value**. No multi-valued attributes.

```
❌ NOT in 1NF:
| Student | Courses          |
|---------|-----------------|
| Rahul   | DBMS, OS, CN    |  ← Multiple values in one cell

✅ In 1NF:
| Student | Course |
|---------|--------|
| Rahul   | DBMS   |
| Rahul   | OS     |
| Rahul   | CN     |
```

### Second Normal Form (2NF)

**Rule:** Must be in 1NF + **No Partial Dependency**.

**Partial Dependency:** A non-key attribute depends on **only part** of the composite primary key.

```
❌ NOT in 2NF (PK = {Student_ID, Course_ID}):
| Student_ID | Course_ID | Student_Name | Grade |
|-----------|-----------|-------------|-------|
| 101       | C1        | Rahul       | A     |
| 101       | C2        | Rahul       | B     |

Student_Name depends only on Student_ID (not the full PK) → PARTIAL DEPENDENCY

✅ Fix: Split into two tables:
Table 1: Students (Student_ID, Student_Name)
Table 2: Enrollments (Student_ID, Course_ID, Grade)
```

### Third Normal Form (3NF)

**Rule:** Must be in 2NF + **No Transitive Dependency**.

**Transitive Dependency:** A non-key attribute depends on another **non-key attribute**.

```
❌ NOT in 3NF:
| Emp_ID | Dept_ID | Dept_Name |
|--------|---------|-----------|
| 101    | D1      | CSE       |
| 102    | D1      | CSE       |

Dept_Name depends on Dept_ID, NOT on Emp_ID → TRANSITIVE DEPENDENCY
(Emp_ID → Dept_ID → Dept_Name)

✅ Fix: Split into two tables:
Table 1: Employees (Emp_ID, Dept_ID)
Table 2: Departments (Dept_ID, Dept_Name)
```

### BCNF (Boyce-Codd Normal Form)

**Rule:** Must be in 3NF + For every functional dependency X → Y, **X must be a super key**.

**Stricter than 3NF.** In 3NF, the dependency can be allowed if Y is part of a candidate key. BCNF doesn't allow this exception.

```
❌ NOT in BCNF:
| Student | Subject   | Professor    |
|---------|-----------|-------------|
| Rahul   | DBMS      | Prof. Sharma |
| Priya   | DBMS      | Prof. Kumar  |
| Rahul   | OS        | Prof. Kumar  |

FD: Professor → Subject (each professor teaches only one subject)
But Professor is NOT a super key → violates BCNF

✅ Fix: Split into:
Table 1: (Student, Professor)
Table 2: (Professor, Subject)
```

### 4NF (Fourth Normal Form)

**Rule:** Must be in BCNF + **No Multi-Valued Dependencies**.

**Multi-valued dependency:** One attribute determines multiple independent sets of values.

### 5NF (Fifth Normal Form)

**Rule:** Must be in 4NF + **No Join Dependency**. A table cannot be decomposed into smaller tables without losing data.

## 11.4 Summary of Normal Forms

| NF | Rule | Eliminates |
|----|------|-----------|
| **1NF** | Atomic values only | Multi-valued attributes |
| **2NF** | 1NF + No partial dependency | Partial dependency |
| **3NF** | 2NF + No transitive dependency | Transitive dependency |
| **BCNF** | 3NF + Every determinant is a super key | Remaining anomalies |
| **4NF** | BCNF + No multi-valued dependency | Multi-valued dependency |
| **5NF** | 4NF + No join dependency | Join dependency |

**In practice, 3NF or BCNF is usually sufficient.**

## 11.5 Denormalization

**Denormalization** = intentionally adding redundancy (going back from normalized form) to **improve read performance**.

**When to use:** When you have heavy read operations and joins are too slow. Common in data warehouses and reporting databases.

**Trade-off:** Faster reads ↔ Slower writes + more storage + risk of inconsistency.

---

### 🎯 Chapter 11 — Interview Questions

**Q1. What is Normalization?**  
> **Ans:** Normalization is the process of organizing database tables to reduce redundancy and prevent anomalies (insertion, update, deletion). It involves breaking large tables into smaller, related tables following normal form rules.

**Q2. Explain 1NF, 2NF, and 3NF with examples.**  
> **Ans:**  
> - **1NF:** Every cell has a single atomic value (no lists, no sets).  
> - **2NF:** 1NF + no partial dependencies (non-key attributes must depend on the ENTIRE composite PK).  
> - **3NF:** 2NF + no transitive dependencies (non-key attributes must depend directly on the PK, not through another non-key attribute).

**Q3. What is BCNF?**  
> **Ans:** Boyce-Codd Normal Form is stricter than 3NF. For every functional dependency X → Y, X must be a super key. It eliminates anomalies that 3NF might miss when there are overlapping candidate keys.

**Q4. What is Denormalization?**  
> **Ans:** Denormalization is intentionally adding redundancy to a normalized database to improve read performance. Used in data warehouses where fast reads are more important than write efficiency.

**Q5. What are Anomalies?**  
> **Ans:** Anomalies are problems caused by poor database design:  
> - **Insertion Anomaly:** Can't add data without other unrelated data.  
> - **Update Anomaly:** Changing one fact requires updating multiple rows.  
> - **Deletion Anomaly:** Deleting data accidentally removes other important data.

**Q6. What is Functional Dependency?**  
> **Ans:** A functional dependency X → Y means the value of X uniquely determines the value of Y. Example: Student_ID → Student_Name (knowing the ID tells you the name). It's the basis for normalization.

---

---

# Chapter 12 — Transactions & ACID Properties

## 12.1 What is a Transaction?

A **transaction** is a **sequence of operations** (SQL statements) that are treated as a **single logical unit of work**. Either ALL operations succeed, or NONE do.

**Example — Bank Transfer:**
```sql
BEGIN;
    UPDATE accounts SET balance = balance - 5000 WHERE id = 1;  -- Debit
    UPDATE accounts SET balance = balance + 5000 WHERE id = 2;  -- Credit
COMMIT;
-- Both must succeed. If one fails, ROLLBACK both.
```

## 12.2 ACID Properties

| Property | Meaning | Example |
|----------|---------|---------|
| **A — Atomicity** | All or nothing. Either all operations complete, or none do. | If debit succeeds but credit fails → rollback debit too |
| **C — Consistency** | Database goes from one valid state to another valid state. | Total money before = total money after transfer |
| **I — Isolation** | Concurrent transactions don't interfere with each other. | Two transfers happening simultaneously don't mix up |
| **D — Durability** | Once committed, data survives crashes (saved to disk). | After COMMIT, even if power fails, data is safe |

### Atomicity (All or Nothing)

```
Transaction: Transfer ₹5000 from A to B
Step 1: Debit A by 5000    ← SUCCESS
Step 2: Credit B by 5000   ← FAILURE (system crash!)

Without Atomicity: A loses ₹5000, B doesn't get it! Money disappears!
With Atomicity: Step 1 is ROLLED BACK. A still has the money. SAFE!
```

### Consistency

```
Before: A = ₹10,000 + B = ₹5,000 = ₹15,000 total
After:  A = ₹5,000  + B = ₹10,000 = ₹15,000 total ✅
The total is CONSISTENT.
```

### Isolation

```
Transaction T1: Transfer ₹5000 from A to B
Transaction T2: Check balance of A

Without Isolation: T2 might see A's balance AFTER debit but BEFORE credit → inconsistent view
With Isolation: T2 either sees the state BEFORE T1 or AFTER T1 — never in between
```

### Durability

```
After COMMIT → data written to disk (WAL / redo log)
Even if power fails immediately after COMMIT → data is recoverable from logs
```

## 12.3 Transaction States

```
┌────────┐    Begin     ┌─────────┐    Read/Write    ┌───────────────┐
│  Idle  │ ──────────→ │ Active  │ ──────────────→  │ Partially     │
└────────┘              └─────────┘                   │ Committed     │
                            │                         └───────┬───────┘
                            │ Failure                         │ Commit
                            ▼                                 ▼
                       ┌─────────┐                    ┌───────────────┐
                       │ Failed  │                    │  Committed    │
                       └────┬────┘                    └───────────────┘
                            │ Rollback
                            ▼
                       ┌─────────┐
                       │ Aborted │
                       └─────────┘
```

| State | Meaning |
|-------|---------|
| **Active** | Transaction is executing operations |
| **Partially Committed** | Last operation executed, waiting for commit |
| **Committed** | All changes saved permanently |
| **Failed** | Error occurred, cannot proceed |
| **Aborted** | Transaction rolled back, changes undone |

## 12.4 Transaction SQL

```sql
-- PostgreSQL transaction
BEGIN;                      -- or START TRANSACTION;
    INSERT INTO orders VALUES (1, 'Laptop', 50000);
    UPDATE inventory SET stock = stock - 1 WHERE product = 'Laptop';
COMMIT;                     -- Save changes permanently

-- Rollback on error
BEGIN;
    UPDATE accounts SET balance = balance - 5000 WHERE id = 1;
    -- Something goes wrong...
ROLLBACK;                   -- Undo all changes since BEGIN

-- Oracle: Transactions start implicitly (no BEGIN needed)
-- INSERT INTO orders VALUES (...);
-- COMMIT;
-- or ROLLBACK;
```

## 12.5 Isolation Levels

Different levels of isolation trade off between **consistency** and **performance**.

| Isolation Level | Dirty Read | Non-Repeatable Read | Phantom Read |
|----------------|:-:|:-:|:-:|
| **READ UNCOMMITTED** | ✅ (possible) | ✅ | ✅ |
| **READ COMMITTED** | ❌ (prevented) | ✅ | ✅ |
| **REPEATABLE READ** | ❌ | ❌ | ✅ |
| **SERIALIZABLE** | ❌ | ❌ | ❌ |

**Default:** PostgreSQL = READ COMMITTED. Oracle = READ COMMITTED.

| Problem | Description |
|---------|------------|
| **Dirty Read** | Reading data from an uncommitted transaction (might be rolled back) |
| **Non-Repeatable Read** | Reading same row twice gives different values (another transaction updated it) |
| **Phantom Read** | Re-executing a query returns extra rows (another transaction inserted rows) |

```sql
-- Set isolation level (PostgreSQL)
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
BEGIN;
    -- Your queries here
COMMIT;

-- Oracle
-- SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
```

---

### 🎯 Chapter 12 — Interview Questions

**Q1. What are ACID properties?**  
> **Ans:** Atomicity (all or nothing), Consistency (valid state to valid state), Isolation (concurrent transactions don't interfere), Durability (committed data survives crashes). These ensure reliable transaction processing.

**Q2. What is Atomicity?**  
> **Ans:** Atomicity ensures that a transaction is treated as a single indivisible unit. Either ALL operations in the transaction succeed and are committed, or NONE are applied (rolled back). No partial execution.

**Q3. What is a Dirty Read?**  
> **Ans:** A dirty read occurs when a transaction reads data modified by another transaction that hasn't been committed yet. If that transaction rolls back, the read data was "dirty" (invalid).

**Q4. What are Isolation Levels?**  
> **Ans:** Isolation levels control how much transactions can interfere with each other. From lowest to highest: READ UNCOMMITTED, READ COMMITTED (default), REPEATABLE READ, SERIALIZABLE. Higher isolation = fewer problems but lower concurrency.

**Q5. What is the difference between COMMIT and ROLLBACK?**  
> **Ans:** COMMIT saves all changes made by the transaction permanently to the database. ROLLBACK undoes all changes made by the transaction, restoring the database to the state before the transaction began.

---

---

# Chapter 13 — Concurrency Control

## 13.1 Why Concurrency Control?

When **multiple transactions** execute simultaneously, we need to ensure data remains consistent. Without control, problems like lost updates, dirty reads, and inconsistencies arise.

## 13.2 Problems in Concurrent Execution

| Problem | Description |
|---------|------------|
| **Lost Update** | Two transactions update the same data; one update is lost |
| **Dirty Read** | Reading uncommitted data from another transaction |
| **Non-Repeatable Read** | Same query returns different values in the same transaction |
| **Phantom Read** | New rows appear between two identical queries |

## 13.3 Schedules

A **schedule** is the order in which operations of concurrent transactions are executed.

| Type | Description |
|------|------------|
| **Serial Schedule** | Transactions execute one after another (no overlap). Always correct but slow. |
| **Non-Serial Schedule** | Operations of transactions are interleaved. Faster but may cause problems. |
| **Serializable Schedule** | A non-serial schedule whose result equals SOME serial schedule. Both correct and efficient. |

## 13.4 Lock-Based Concurrency Control

### Types of Locks

| Lock Type | Also Called | What it Allows |
|-----------|-----------|---------------|
| **Shared Lock (S)** | Read Lock | Multiple transactions can read simultaneously |
| **Exclusive Lock (X)** | Write Lock | Only one transaction can read/write (blocks others) |

**Compatibility Matrix:**

| | S (Read) | X (Write) |
|---|:-:|:-:|
| **S (Read)** | ✅ Compatible | ❌ Conflict |
| **X (Write)** | ❌ Conflict | ❌ Conflict |

### Two-Phase Locking (2PL)

A protocol that ensures **serializability**.

**Two phases:**
1. **Growing Phase:** Transaction can **acquire** locks but cannot release any.
2. **Shrinking Phase:** Transaction can **release** locks but cannot acquire any.

```
Growing Phase          Lock Point          Shrinking Phase
Acquire S(A)     →     (Maximum locks)  →   Release S(A)
Acquire X(B)                                 Release X(B)
```

**Strict 2PL:** Hold ALL locks until **COMMIT** or **ROLLBACK**. Prevents cascading rollbacks.

### Problems with Locking
- **Deadlock** — Two transactions waiting for each other's locks.
- **Starvation** — A transaction never gets the lock it needs.

## 13.5 Timestamp-Based Concurrency Control

- Each transaction gets a **timestamp** when it starts.
- Operations are ordered based on timestamps.
- If a transaction tries to access data in a way that violates timestamp order → it's **aborted and restarted**.

**Rules:**
- **Read too late:** If a younger transaction already wrote → abort.
- **Write too late:** If a younger transaction already read → abort.

## 13.6 MVCC (Multi-Version Concurrency Control)

Used by **PostgreSQL** and **Oracle**.

- Each write creates a **new version** of the row (old version is kept).
- Readers see the version that was committed **before their transaction started**.
- Readers **never block** writers. Writers **never block** readers.

```
Transaction T1 starts at time 10 → sees data as of time 10
Transaction T2 updates a row at time 15
T1 still sees the OLD version (time 10) → consistent read
After T2 commits, new transactions see the updated version
```

**Advantages:**
- No read locks needed.
- High concurrency.
- Used in PostgreSQL (MVCC is core), Oracle (using UNDO segments).

---

### 🎯 Chapter 13 — Interview Questions

**Q1. What is Concurrency Control?**  
> **Ans:** Concurrency control is the mechanism to ensure correct results when multiple transactions access the same data simultaneously. It prevents problems like lost updates, dirty reads, and inconsistencies.

**Q2. What is Two-Phase Locking (2PL)?**  
> **Ans:** 2PL is a concurrency control protocol with two phases: Growing (acquire locks, no releases) and Shrinking (release locks, no acquires). It guarantees serializability but can cause deadlocks.

**Q3. What is MVCC?**  
> **Ans:** MVCC (Multi-Version Concurrency Control) maintains multiple versions of data. Readers see a consistent snapshot without blocking writers. Used by PostgreSQL and Oracle. It provides high concurrency with consistent reads.

**Q4. Difference between Shared and Exclusive locks?**  
> **Ans:** Shared lock (S): multiple transactions can read the same data simultaneously. Exclusive lock (X): only one transaction can access the data (read or write). Two shared locks are compatible; exclusive locks conflict with everything.

**Q5. What is a Serializable Schedule?**  
> **Ans:** A serializable schedule is a concurrent execution of transactions whose result is equivalent to some serial (non-interleaved) execution. It guarantees correctness as if transactions ran one at a time.

---

---

# Chapter 14 — Deadlock in DBMS

## 14.1 What is Deadlock?

**Deadlock** occurs when two or more transactions are **waiting for each other** to release locks, and **none can proceed**.

```
T1 holds lock on A, waiting for lock on B
T2 holds lock on B, waiting for lock on A
→ DEADLOCK! Neither can proceed.
```

## 14.2 Deadlock Handling

### Prevention

| Method | Description |
|--------|------------|
| **Wait-Die** | Older transaction waits; younger transaction is aborted (dies) |
| **Wound-Wait** | Older transaction forces younger to abort (wounds); younger waits |
| **Lock Ordering** | All transactions request locks in a predefined order |
| **Timeout** | If a transaction waits too long for a lock → abort it |

### Detection

- Build a **Wait-For Graph**: Nodes = transactions, Edge = T1 waiting for T2.
- If cycle exists → **Deadlock detected**.
- Choose a **victim** (usually the youngest transaction) → **Rollback** it.

### PostgreSQL Deadlock Handling

```sql
-- PostgreSQL automatically detects deadlocks
-- It checks the wait-for graph periodically (default: 1 second)
-- When detected, it aborts one transaction with error:
-- ERROR: deadlock detected

-- You can set deadlock detection timeout
SET deadlock_timeout = '2s';
```

### Oracle Deadlock Handling

- Oracle **automatically detects** deadlocks.
- It chooses one transaction and raises `ORA-00060: deadlock detected`.
- That transaction's statement is rolled back (not the entire transaction).

---

### 🎯 Chapter 14 — Interview Questions

**Q1. What is Deadlock in DBMS?**  
> **Ans:** Deadlock occurs when two or more transactions are circularly waiting for locks held by each other. None can proceed. Example: T1 locks A and waits for B; T2 locks B and waits for A.

**Q2. How to prevent Deadlock?**  
> **Ans:** Wait-Die (older waits, younger dies), Wound-Wait (older wounds younger), Lock ordering (request locks in order), Timeout (abort if wait too long).

**Q3. How does PostgreSQL handle Deadlock?**  
> **Ans:** PostgreSQL automatically detects deadlocks by checking wait-for graphs. When detected, it aborts one of the involved transactions (the one it deems the least costly to roll back) and raises an error.

---

---

# Chapter 15 — Indexing & Hashing

## 15.1 Why Indexing?

Without an index, the database does a **full table scan** (reads every row). With an index, it jumps **directly to the relevant rows**.

```
Without Index: Scan all 1,000,000 rows → O(n)
With Index:    Search index tree → O(log n) → much faster!
```

## 15.2 Types of Indexing

### Primary Index (Clustering Index)
- Built on the **primary key** (ordered data).
- Data file is **sorted** on the indexed column.
- Only **one** primary index per table.
- Types: Dense (one entry per record) or Sparse (one entry per data block).

### Secondary Index (Non-Clustering Index)
- Built on a **non-key column** (data file not sorted on this column).
- **Multiple** secondary indexes per table.
- Always **dense** (one entry per record).

### Dense vs Sparse Index

| Type | Entries | Speed |
|------|---------|-------|
| **Dense** | One index entry for **every row** | Faster search, more space |
| **Sparse** | One index entry for **each data block** | Slower search, less space |

## 15.3 B-Tree Index (Most Common)

- **Balanced tree** structure.
- All leaves are at the **same level**.
- Supports **equality** (`=`) and **range** (`>`, `<`, `BETWEEN`) queries.
- Default index type in PostgreSQL and Oracle.

```
                    [30 | 60]
                   /    |     \
           [10|20]   [40|50]   [70|80]
           /  |  \   /  |  \   /  |  \
        [Records] [Records] [Records]
```

### B+ Tree (Used in Databases)

- Similar to B-Tree but:
  - **All data pointers are in leaf nodes** (internal nodes only have keys).
  - **Leaf nodes are linked** (fast range queries).
  - More keys per internal node → shorter tree → fewer disk reads.

```
Internal: [30 | 60]          ← Only keys, no data
          /    |     \
Leaves:  [10→20→] → [30→40→50→] → [60→70→80→]  ← Data + linked list
```

## 15.4 Hash Index

- Uses a **hash function** to map keys to buckets.
- **Very fast** for equality searches (`=`).
- **Cannot** do range queries (`>`, `<`, `BETWEEN`).
- Used when you only search for exact values.

```
Hash Function: h(key) = key % 10

key = 42 → h(42) = 2 → go to bucket 2
key = 78 → h(78) = 8 → go to bucket 8
```

### B-Tree vs Hash Index

| Feature | B-Tree | Hash |
|---------|--------|------|
| Equality search (`=`) | Fast | Very Fast |
| Range search (`>`, `<`) | Supported | ❌ Not supported |
| Ordered output | ✅ Yes | ❌ No |
| Default in | PostgreSQL, Oracle | PostgreSQL (explicit) |

```sql
-- Create B-Tree index (default)
CREATE INDEX idx_name ON employees(first_name);

-- Create Hash index (PostgreSQL)
CREATE INDEX idx_name_hash ON employees USING HASH (first_name);
```

---

### 🎯 Chapter 15 — Interview Questions

**Q1. What is Indexing?**  
> **Ans:** Indexing is a data structure technique that speeds up data retrieval. An index creates a separate structure (like a B-Tree) that maps column values to row locations, allowing the database to find rows without scanning the entire table.

**Q2. What is a B+ Tree?**  
> **Ans:** A B+ Tree is a balanced tree where all data pointers are in leaf nodes (connected as a linked list). Internal nodes only hold keys for navigation. It's the most common index structure in databases because it supports both equality and range queries efficiently.

**Q3. Difference between Clustered and Non-Clustered Index?**  
> **Ans:** Clustered index: data is physically sorted by the indexed column (only one per table, usually on PK). Non-clustered index: separate structure pointing to data (multiple per table). Clustered is faster for range queries.

**Q4. When to use Hash vs B-Tree Index?**  
> **Ans:** Use hash index for equality-only searches (exact match — very fast). Use B-Tree for both equality and range queries (>,<, BETWEEN, ORDER BY). B-Tree is the default and most versatile.

---

---

# Chapter 16 — Stored Procedures, Functions & Triggers

## 16.1 Stored Procedure

A **stored procedure** is a precompiled **set of SQL statements** saved in the database. Called by name.

```sql
-- PostgreSQL: Create stored procedure
CREATE OR REPLACE PROCEDURE raise_salary(
    p_emp_id INT,
    p_amount DECIMAL
)
LANGUAGE plpgsql
AS $$
BEGIN
    UPDATE employees
    SET salary = salary + p_amount
    WHERE emp_id = p_emp_id;

    RAISE NOTICE 'Salary updated for employee %', p_emp_id;
END;
$$;

-- Call the procedure
CALL raise_salary(101, 5000);
```

```sql
-- Oracle: Create stored procedure
-- CREATE OR REPLACE PROCEDURE raise_salary(
--     p_emp_id IN NUMBER,
--     p_amount IN NUMBER
-- ) AS
-- BEGIN
--     UPDATE employees SET salary = salary + p_amount
--     WHERE emp_id = p_emp_id;
--     COMMIT;
--     DBMS_OUTPUT.PUT_LINE('Salary updated');
-- END;
-- /
-- EXEC raise_salary(101, 5000);
```

## 16.2 Function

A **function** returns a value. Can be used in SELECT statements.

```sql
-- PostgreSQL: Create function
CREATE OR REPLACE FUNCTION get_annual_salary(p_emp_id INT)
RETURNS DECIMAL
LANGUAGE plpgsql
AS $$
DECLARE
    v_salary DECIMAL;
BEGIN
    SELECT salary * 12 INTO v_salary
    FROM employees
    WHERE emp_id = p_emp_id;

    RETURN v_salary;
END;
$$;

-- Use the function
SELECT first_name, get_annual_salary(emp_id) AS annual_pay
FROM employees;

SELECT get_annual_salary(101);  -- Returns: 900000
```

### Procedure vs Function

| Feature | Procedure | Function |
|---------|-----------|----------|
| Return value | No return value (uses OUT parameters) | Returns a value |
| Use in SELECT | ❌ Cannot | ✅ Can |
| Call syntax | CALL proc_name() | SELECT func_name() |
| Purpose | Perform actions (insert, update, delete) | Compute and return a value |

## 16.3 Triggers

A **trigger** is a block of code that **automatically executes** when a specific event (INSERT, UPDATE, DELETE) occurs on a table.

```sql
-- PostgreSQL: Create trigger

-- Step 1: Create trigger function
CREATE OR REPLACE FUNCTION log_salary_change()
RETURNS TRIGGER
LANGUAGE plpgsql
AS $$
BEGIN
    INSERT INTO salary_audit (emp_id, old_salary, new_salary, changed_at)
    VALUES (OLD.emp_id, OLD.salary, NEW.salary, NOW());
    RETURN NEW;
END;
$$;

-- Step 2: Create trigger
CREATE TRIGGER trg_salary_change
AFTER UPDATE OF salary ON employees
FOR EACH ROW
WHEN (OLD.salary IS DISTINCT FROM NEW.salary)
EXECUTE FUNCTION log_salary_change();

-- Now, every salary update automatically creates an audit log!
UPDATE employees SET salary = 85000 WHERE emp_id = 101;
-- → Automatically inserts a row into salary_audit table
```

### Trigger Types

| Type | When it Fires |
|------|--------------|
| **BEFORE** | Before the event (can modify NEW values) |
| **AFTER** | After the event (for logging, auditing) |
| **INSTEAD OF** | Replaces the event (used on views) |

| Scope | Description |
|-------|------------|
| **FOR EACH ROW** | Fires once per affected row |
| **FOR EACH STATEMENT** | Fires once per SQL statement |

### OLD and NEW References

| Reference | INSERT | UPDATE | DELETE |
|-----------|--------|--------|--------|
| **OLD** | ❌ Not available | ✅ Old row values | ✅ Deleted row values |
| **NEW** | ✅ New row values | ✅ New row values | ❌ Not available |

```sql
-- Oracle trigger syntax:
-- CREATE OR REPLACE TRIGGER trg_salary_change
-- AFTER UPDATE OF salary ON employees
-- FOR EACH ROW
-- BEGIN
--     INSERT INTO salary_audit VALUES (:OLD.emp_id, :OLD.salary, :NEW.salary, SYSDATE);
-- END;
-- /
```

---

### 🎯 Chapter 16 — Interview Questions

**Q1. What is a Stored Procedure?**  
> **Ans:** A stored procedure is a precompiled set of SQL statements stored in the database. It's called by name, can accept parameters, and performs actions like INSERT/UPDATE/DELETE. Benefits: reusability, security, performance.

**Q2. Difference between Procedure and Function?**  
> **Ans:** A function MUST return a value and can be used in SELECT statements. A procedure does NOT return a value (uses OUT parameters instead) and cannot be used in SELECT. Procedures are called with CALL/EXEC.

**Q3. What is a Trigger?**  
> **Ans:** A trigger is a block of code that automatically executes when a specific event (INSERT, UPDATE, DELETE) occurs on a table. Used for auditing, validation, maintaining derived data. Can fire BEFORE or AFTER the event.

**Q4. What are OLD and NEW in triggers?**  
> **Ans:** OLD refers to the row's values before the change. NEW refers to the row's values after the change. In INSERT triggers: only NEW. In DELETE triggers: only OLD. In UPDATE triggers: both OLD and NEW.

---

---

# Chapter 17 — Relational Algebra

## 17.1 What is Relational Algebra?

**Relational algebra** is a **procedural query language** that takes relations (tables) as input and returns a relation as output. It defines the **fundamental operations** used by SQL internally.

## 17.2 Basic Operations

| Operation | Symbol | SQL Equivalent | Description |
|-----------|:------:|---------------|-------------|
| **Select** | σ (sigma) | WHERE | Filter rows based on condition |
| **Project** | π (pi) | SELECT columns | Choose specific columns |
| **Union** | ∪ | UNION | Combine rows from two tables |
| **Set Difference** | − | EXCEPT | Rows in A but not in B |
| **Cartesian Product** | × | CROSS JOIN | All combinations of rows |
| **Rename** | ρ (rho) | AS | Rename a relation or attribute |

## 17.3 Derived Operations

| Operation | Symbol | SQL Equivalent | Description |
|-----------|:------:|---------------|-------------|
| **Natural Join** | ⋈ | NATURAL JOIN | Join on common attributes |
| **Intersection** | ∩ | INTERSECT | Common rows in both tables |
| **Division** | ÷ | Complex subquery | "For all" queries |
| **Theta Join** | ⋈θ | JOIN ON condition | Join with any condition |
| **Equi Join** | ⋈= | JOIN ON = | Join with equality condition |

## 17.4 Examples

```
Table: Students(ID, Name, Dept)
Table: Courses(CID, Title, Dept)

Select students from CSE:        σ_Dept='CSE' (Students)
SQL: SELECT * FROM Students WHERE Dept = 'CSE';

Project names only:              π_Name (Students)
SQL: SELECT Name FROM Students;

Combine: Select + Project:       π_Name (σ_Dept='CSE' (Students))
SQL: SELECT Name FROM Students WHERE Dept = 'CSE';

Join Students and Courses:       Students ⋈_Dept=Dept Courses
SQL: SELECT * FROM Students JOIN Courses ON Students.Dept = Courses.Dept;
```

---

### 🎯 Chapter 17 — Interview Questions

**Q1. What is Relational Algebra?**  
> **Ans:** Relational algebra is a procedural query language that uses mathematical operations (select, project, join, union, etc.) on relations to define queries. It's the theoretical foundation for SQL.

**Q2. What is the difference between Select and Project?**  
> **Ans:** Select (σ) filters **rows** based on a condition (like WHERE). Project (π) selects specific **columns** (like SELECT column_list). Select is horizontal filtering; project is vertical filtering.

**Q3. What is Natural Join?**  
> **Ans:** Natural join combines two tables based on ALL columns with the same name. It automatically matches common columns and removes duplicate columns from the result. Risky if tables have unintended common column names.

---

---

# Chapter 18 — NoSQL vs SQL

## 18.1 SQL (Relational) Databases

- Data stored in **structured tables** with rows and columns.
- **Fixed schema** — must define table structure before inserting data.
- Uses **SQL** for queries.
- Supports **ACID** transactions.
- **Examples:** PostgreSQL, Oracle, MySQL, SQL Server.

## 18.2 NoSQL Databases

- Data stored in **flexible formats** (documents, key-value, graphs, columns).
- **Dynamic schema** — no need to define structure upfront.
- Each type has its own query language.
- Usually follows **BASE** (Basically Available, Soft-state, Eventually consistent).

### Types of NoSQL

| Type | Storage Format | Example | Use Case |
|------|---------------|---------|----------|
| **Document** | JSON/BSON documents | MongoDB, CouchDB | Content management, catalogs |
| **Key-Value** | Key-value pairs | Redis, DynamoDB | Caching, sessions |
| **Column-Family** | Column families | Cassandra, HBase | Time-series, analytics |
| **Graph** | Nodes and edges | Neo4j, ArangoDB | Social networks, recommendations |

## 18.3 SQL vs NoSQL Comparison

| Feature | SQL (RDBMS) | NoSQL |
|---------|:-----------:|:-----:|
| Schema | Fixed (rigid) | Flexible (dynamic) |
| Data Model | Tables (rows/columns) | Documents, KV, Graph, Columns |
| Query Language | SQL (standardized) | Varies by database |
| Transactions | Strong ACID | Usually eventual consistency (BASE) |
| Scalability | Vertical (bigger server) | Horizontal (more servers) |
| Relationships | Strong (JOINs, FK) | Weak (denormalized) |
| Best For | Complex queries, relationships | Big data, real-time, flexible data |
| Examples | PostgreSQL, Oracle | MongoDB, Redis, Cassandra |

## 18.4 CAP Theorem

In a distributed system, you can only guarantee **two out of three**:

| Letter | Meaning |
|--------|---------|
| **C** — Consistency | All nodes see the same data at the same time |
| **A** — Availability | Every request gets a response (success/failure) |
| **P** — Partition Tolerance | System works even if network partitions occur |

```
        Consistency
           /\
          /  \
    CP   /    \   CA
        /  CAP  \
       /  (pick  \
      /   any 2)  \
     /──────────────\
Partition            Availability
Tolerance      AP
```

- **CP:** MongoDB, HBase (sacrifice availability during partition)
- **AP:** Cassandra, DynamoDB (sacrifice consistency during partition)
- **CA:** Traditional RDBMS (don't handle partitions — single server)

---

### 🎯 Chapter 18 — Interview Questions

**Q1. Difference between SQL and NoSQL?**  
> **Ans:** SQL: structured tables, fixed schema, strong ACID, SQL language, vertical scaling (PostgreSQL, Oracle). NoSQL: flexible schema, varied data models, eventual consistency, horizontal scaling (MongoDB, Redis). Choose SQL for complex relationships; NoSQL for big data and flexibility.

**Q2. What is the CAP Theorem?**  
> **Ans:** In a distributed system, you can only guarantee two of three: Consistency (same data everywhere), Availability (always responds), Partition Tolerance (works despite network failures). You must sacrifice one.

**Q3. When would you choose NoSQL over SQL?**  
> **Ans:** When you need: flexible schema (evolving data), horizontal scalability (massive data), high write throughput, no complex joins, real-time applications. Examples: social media feeds, IoT data, caching.

---

---

# Chapter 19 — PostgreSQL & Oracle Specific Features

## 19.1 PostgreSQL-Specific Features

### Data Types Unique to PostgreSQL

```sql
-- JSON / JSONB (binary JSON — faster queries)
CREATE TABLE products (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    attributes JSONB    -- Store flexible data as JSON
);

INSERT INTO products (name, attributes)
VALUES ('Laptop', '{"brand": "Dell", "ram": 16, "storage": "512GB SSD"}');

-- Query JSON data
SELECT name, attributes->>'brand' AS brand FROM products;
SELECT * FROM products WHERE attributes->>'ram' = '16';
SELECT * FROM products WHERE attributes @> '{"brand": "Dell"}';

-- ARRAY type
CREATE TABLE students (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    hobbies TEXT[]    -- Array of text
);

INSERT INTO students (name, hobbies) VALUES ('Rahul', ARRAY['Cricket', 'Coding', 'Reading']);
SELECT * FROM students WHERE 'Cricket' = ANY(hobbies);

-- UUID type
CREATE TABLE sessions (
    id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
    user_id INT,
    created_at TIMESTAMP DEFAULT NOW()
);

-- ENUM type
CREATE TYPE mood AS ENUM ('happy', 'sad', 'neutral');
CREATE TABLE diary (
    id SERIAL PRIMARY KEY,
    entry TEXT,
    feeling mood
);
```

### PostgreSQL Extensions

```sql
-- Full-text search
SELECT * FROM articles
WHERE to_tsvector('english', content) @@ to_tsquery('database & management');

-- UPSERT (INSERT or UPDATE on conflict)
INSERT INTO employees (emp_id, first_name, salary)
VALUES (101, 'Rahul', 80000)
ON CONFLICT (emp_id)
DO UPDATE SET salary = EXCLUDED.salary;

-- RETURNING clause (get affected rows)
INSERT INTO employees (first_name, salary)
VALUES ('Test', 50000)
RETURNING emp_id, first_name;

UPDATE employees SET salary = salary + 5000
WHERE dept_id = 1
RETURNING emp_id, salary;

DELETE FROM employees WHERE emp_id = 108
RETURNING *;

-- LATERAL JOIN
SELECT d.dept_name, top_emp.first_name, top_emp.salary
FROM departments d
CROSS JOIN LATERAL (
    SELECT first_name, salary
    FROM employees e
    WHERE e.dept_id = d.dept_id
    ORDER BY salary DESC
    LIMIT 1
) top_emp;
```

## 19.2 Oracle-Specific Features

```sql
-- DUAL table (single-row dummy table for calculations)
SELECT SYSDATE FROM DUAL;
SELECT 2 + 3 FROM DUAL;

-- ROWNUM (limit rows — legacy)
SELECT * FROM employees WHERE ROWNUM <= 5;

-- NVL (handle NULLs — Oracle's COALESCE equivalent)
SELECT NVL(manager_id, 0) FROM employees;

-- NVL2
SELECT NVL2(manager_id, 'Has Manager', 'No Manager') FROM employees;

-- DECODE (Oracle's CASE equivalent)
SELECT emp_id,
    DECODE(dept_id, 1, 'Engineering', 2, 'Marketing', 'Other') AS dept
FROM employees;

-- CONNECT BY (hierarchical queries — Oracle-specific)
SELECT emp_id, first_name, manager_id, LEVEL
FROM employees
START WITH manager_id IS NULL
CONNECT BY PRIOR emp_id = manager_id
ORDER SIBLINGS BY first_name;

-- MERGE (UPSERT in Oracle)
MERGE INTO employees e
USING (SELECT 101 AS emp_id, 80000 AS salary FROM DUAL) s
ON (e.emp_id = s.emp_id)
WHEN MATCHED THEN
    UPDATE SET e.salary = s.salary
WHEN NOT MATCHED THEN
    INSERT (emp_id, salary) VALUES (s.emp_id, s.salary);

-- Flashback Query (query data as it was in the past!)
SELECT * FROM employees AS OF TIMESTAMP (SYSTIMESTAMP - INTERVAL '1' HOUR);
```

## 19.3 PostgreSQL vs Oracle Comparison

| Feature | PostgreSQL | Oracle |
|---------|-----------|--------|
| **Cost** | Free, open-source | Commercial (expensive) |
| **JSON Support** | Excellent (JSONB) | Good (from 12c) |
| **Auto-increment** | SERIAL / GENERATED ALWAYS | SEQUENCE + TRIGGER or IDENTITY |
| **Limit rows** | LIMIT + OFFSET | FETCH FIRST / ROWNUM |
| **NULL handling** | COALESCE | NVL / NVL2 |
| **Boolean** | Native BOOLEAN | NUMBER(1) / CHAR(1) |
| **String concat** | `\|\|` | `\|\|` |
| **Upsert** | ON CONFLICT DO UPDATE | MERGE |
| **Array support** | Native | VARRAY / Nested Table |
| **Hierarchy** | WITH RECURSIVE | CONNECT BY |
| **MVCC** | Built-in | UNDO tablespace |
| **License** | PostgreSQL License (permissive) | Proprietary |

---

### 🎯 Chapter 19 — Interview Questions

**Q1. What is JSONB in PostgreSQL?**  
> **Ans:** JSONB is a binary JSON data type in PostgreSQL that stores JSON data in a decomposed binary format. It's faster to query than regular JSON, supports indexing (GIN indexes), and allows operators like `@>`, `->`, `->>` for querying nested JSON data.

**Q2. What is MERGE in Oracle (UPSERT)?**  
> **Ans:** MERGE allows you to perform INSERT or UPDATE in a single statement. If the row exists, it updates; if not, it inserts. PostgreSQL equivalent: `INSERT ... ON CONFLICT DO UPDATE`.

**Q3. What is CONNECT BY in Oracle?**  
> **Ans:** CONNECT BY is Oracle's hierarchical query syntax for tree-structured data (like employee-manager relationships). PostgreSQL equivalent: `WITH RECURSIVE` CTE.

**Q4. What is RETURNING in PostgreSQL?**  
> **Ans:** The RETURNING clause returns the affected rows after INSERT, UPDATE, or DELETE. Example: `INSERT INTO ... RETURNING id, name` returns the inserted row. Oracle doesn't have a direct equivalent (uses OUT parameters).

---

---

# Chapter 20 — Top 100 Most Asked Interview Questions

> **Most frequently asked** DBMS & SQL questions in placement interviews at companies like **Bizom, TCS, Infosys, Wipro, Accenture, Cognizant, and product-based companies**.

---

## 🔹 Basic DBMS Concepts (Q1–Q15)

**Q1. What is a Database?**  
> An organized collection of data stored electronically, accessible and manageable through a DBMS.

**Q2. What is DBMS?**  
> Software that manages databases — allows creating, querying, updating, and administering data. Examples: PostgreSQL, Oracle, MySQL.

**Q3. What is RDBMS?**  
> A DBMS that stores data in tables (relations) with rows and columns, and supports relationships between tables using keys. Examples: PostgreSQL, Oracle.

**Q4. Difference between DBMS and RDBMS?**  
> DBMS: stores data as files, no relationships. RDBMS: stores data in tables with relationships, supports ACID, uses SQL. Most modern databases are RDBMS.

**Q5. What is SQL?**  
> Structured Query Language — the standard language for interacting with relational databases. Used for querying, inserting, updating, deleting, and managing data.

**Q6. What are the types of SQL commands?**  
> DDL (CREATE, ALTER, DROP), DML (INSERT, UPDATE, DELETE), DQL (SELECT), DCL (GRANT, REVOKE), TCL (COMMIT, ROLLBACK, SAVEPOINT).

**Q7. What is a Schema?**  
> The logical structure/blueprint of a database — defines tables, columns, data types, relationships, and constraints. Doesn't change frequently.

**Q8. What is an Instance?**  
> The actual data stored in the database at a specific point in time. Changes with every INSERT/UPDATE/DELETE.

**Q9. What is Data Independence?**  
> Ability to change one level of the database without affecting others. Logical independence: change schema without changing views. Physical independence: change storage without changing schema.

**Q10. What is a Relation (Table)?**  
> A relation is a table with rows (tuples) and columns (attributes). Each row is unique, each column has a domain (data type).

**Q11. What is Degree and Cardinality?**  
> Degree = number of columns (attributes). Cardinality = number of rows (tuples).

**Q12. What is a NULL value?**  
> NULL represents missing, unknown, or not applicable data. It's not zero or empty string. NULL = NULL returns UNKNOWN (not TRUE).

**Q13. What is a Stored Procedure?**  
> A precompiled set of SQL statements stored in the database, callable by name. Benefits: reusability, performance, security.

**Q14. What is a Trigger?**  
> Code that automatically executes when a specific event (INSERT, UPDATE, DELETE) occurs on a table. Used for auditing, validation, cascade updates.

**Q15. What is a Cursor?**  
> A database object that allows row-by-row processing of query results. Used when you need to process each row individually rather than as a set.

---

## 🔹 Keys & Constraints (Q16–Q25)

**Q16. What is a Primary Key?**  
> Uniquely identifies each row. Cannot be NULL. Only one per table.

**Q17. What is a Foreign Key?**  
> References the primary key of another table. Establishes relationships. Ensures referential integrity.

**Q18. Difference between Primary Key and Unique Key?**  
> PK: one per table, no NULLs. Unique: multiple per table, allows one NULL.

**Q19. What is a Composite Key?**  
> A primary key made of two or more columns. The combination uniquely identifies rows.

**Q20. What is a Candidate Key?**  
> A minimal set of attributes that can uniquely identify a row. One becomes PK; rest are alternate keys.

**Q21. What is a Super Key?**  
> Any set of attributes that uniquely identifies rows. May contain extra attributes. Every candidate key is a super key, but not vice versa.

**Q22. What is Referential Integrity?**  
> FK values must match a PK value in the referenced table or be NULL. Prevents orphan records.

**Q23. What is ON DELETE CASCADE?**  
> When a parent row is deleted, all child rows (referencing it via FK) are automatically deleted.

**Q24. What are Constraints?**  
> Rules on columns to ensure data validity: NOT NULL, UNIQUE, PRIMARY KEY, FOREIGN KEY, CHECK, DEFAULT.

**Q25. What is a CHECK constraint?**  
> Ensures column values satisfy a specified condition. Example: CHECK (age >= 18).

---

## 🔹 Normalization (Q26–Q35)

**Q26. What is Normalization?**  
> Process of organizing tables to reduce redundancy and prevent anomalies. Uses normal forms (1NF, 2NF, 3NF, BCNF).

**Q27. What is 1NF?**  
> Every cell contains a single atomic value. No repeating groups or arrays.

**Q28. What is 2NF?**  
> 1NF + no partial dependencies. Non-key attributes depend on the ENTIRE composite PK.

**Q29. What is 3NF?**  
> 2NF + no transitive dependencies. Non-key attributes depend directly on PK only.

**Q30. What is BCNF?**  
> Stricter than 3NF. For every FD X→Y, X must be a super key.

**Q31. What is Denormalization?**  
> Intentionally adding redundancy to improve read performance. Used in data warehouses.

**Q32. What is a Functional Dependency?**  
> X→Y means value of X uniquely determines value of Y. Basis for normalization.

**Q33. What is a Partial Dependency?**  
> A non-key attribute depends on only PART of a composite PK. Violates 2NF.

**Q34. What is a Transitive Dependency?**  
> A non-key attribute depends on another non-key attribute (A→B→C). Violates 3NF.

**Q35. What are Anomalies?**  
> Insertion anomaly (can't add without unrelated data), Update anomaly (multiple rows need updating), Deletion anomaly (losing data when deleting).

---

## 🔹 SQL Queries (Q36–Q55)

**Q36. Difference between WHERE and HAVING?**  
> WHERE filters rows before GROUP BY (no aggregates). HAVING filters groups after GROUP BY (can use aggregates).

**Q37. Difference between INNER JOIN and LEFT JOIN?**  
> INNER: only matching rows. LEFT: all left rows + matching right (NULL if no match).

**Q38. What is a Self Join?**  
> A table joined with itself. Used for hierarchical data (employee-manager).

**Q39. What is a Cross Join?**  
> Cartesian product — every row of A combined with every row of B. M×N rows.

**Q40. What is a Subquery?**  
> A query inside another query. Inner query runs first; result used by outer query.

**Q41. What is a Correlated Subquery?**  
> A subquery that references the outer query's columns. Executes once per outer row.

**Q42. Difference between IN and EXISTS?**  
> IN: compare value against list. EXISTS: check if subquery returns any rows. EXISTS is faster for large subqueries.

**Q43. What is UNION? UNION vs UNION ALL?**  
> UNION combines results of two queries vertically (removes duplicates). UNION ALL keeps all rows including duplicates (faster).

**Q44. Difference between DELETE and TRUNCATE?**  
> DELETE: DML, row-by-row, can use WHERE, can rollback, fires triggers. TRUNCATE: DDL, removes all rows at once, cannot use WHERE, cannot rollback, doesn't fire triggers.

**Q45. What is GROUP BY?**  
> Groups rows with same values and applies aggregate functions (COUNT, SUM, AVG, MAX, MIN) to each group.

**Q46. Find the second highest salary.**  
> ```sql
> SELECT MAX(salary) FROM employees
> WHERE salary < (SELECT MAX(salary) FROM employees);
> ```

**Q47. Find duplicate records.**  
> ```sql
> SELECT email, COUNT(*) FROM employees
> GROUP BY email HAVING COUNT(*) > 1;
> ```

**Q48. Find employees with no manager.**  
> ```sql
> SELECT * FROM employees WHERE manager_id IS NULL;
> ```

**Q49. Find the Nth highest salary.**  
> ```sql
> SELECT DISTINCT salary FROM employees
> ORDER BY salary DESC LIMIT 1 OFFSET N-1; -- PostgreSQL
> ```

**Q50. Delete duplicate rows keeping one.**  
> ```sql
> DELETE FROM employees
> WHERE emp_id NOT IN (
>     SELECT MIN(emp_id) FROM employees GROUP BY email
> );
> ```

**Q51. Find employees earning above department average.**  
> ```sql
> SELECT e.* FROM employees e
> WHERE salary > (
>     SELECT AVG(salary) FROM employees WHERE dept_id = e.dept_id
> );
> ```

**Q52. Difference between COUNT(*), COUNT(col), COUNT(DISTINCT col)?**  
> COUNT(*): all rows. COUNT(col): non-NULL values. COUNT(DISTINCT col): unique non-NULL values.

**Q53. What is COALESCE?**  
> Returns the first non-NULL value from a list. `COALESCE(a, b, c)` returns a if not NULL, else b if not NULL, else c.

**Q54. What is a CASE expression?**  
> SQL's IF-THEN-ELSE. Returns different values based on conditions. Can be used in SELECT, WHERE, ORDER BY.

**Q55. What is the SQL execution order?**  
> FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT.

---

## 🔹 Transactions & Concurrency (Q56–Q70)

**Q56. What is a Transaction?**  
> A sequence of operations treated as a single logical unit. Either all succeed (COMMIT) or all fail (ROLLBACK).

**Q57. What are ACID properties?**  
> Atomicity (all or nothing), Consistency (valid state transitions), Isolation (concurrent transactions don't interfere), Durability (committed data survives crashes).

**Q58. What is COMMIT and ROLLBACK?**  
> COMMIT saves changes permanently. ROLLBACK undoes all changes since the last COMMIT/BEGIN.

**Q59. What is a SAVEPOINT?**  
> A marker within a transaction for partial rollback. `ROLLBACK TO savepoint` undoes changes after that point without losing everything.

**Q60. What is a Dirty Read?**  
> Reading uncommitted data from another transaction. Prevented at READ COMMITTED isolation level.

**Q61. What are Isolation Levels?**  
> READ UNCOMMITTED, READ COMMITTED (default), REPEATABLE READ, SERIALIZABLE. Higher = more isolation, less concurrency.

**Q62. What is a Lost Update?**  
> Two transactions update the same row; the last one overwrites the first. Both changes should have been applied.

**Q63. What is a Phantom Read?**  
> A query returns different rows when executed twice in the same transaction (new rows inserted by another transaction).

**Q64. What is Concurrency Control?**  
> Mechanisms to ensure correct results when multiple transactions access the same data simultaneously.

**Q65. What is Two-Phase Locking?**  
> Growing phase (acquire locks only) → Lock point → Shrinking phase (release locks only). Guarantees serializability.

**Q66. What is MVCC?**  
> Multi-Version Concurrency Control. Maintains multiple row versions so readers don't block writers. Used by PostgreSQL and Oracle.

**Q67. What is Deadlock in DBMS?**  
> Two transactions circularly waiting for each other's locks. Neither can proceed. Resolved by aborting one.

**Q68. How do databases handle deadlocks?**  
> PostgreSQL/Oracle automatically detect deadlocks and abort one transaction. PostgreSQL raises ERROR, Oracle raises ORA-00060.

**Q69. What is Optimistic vs Pessimistic Locking?**  
> Pessimistic: lock data before reading/writing (SELECT FOR UPDATE). Optimistic: no locks; check for conflicts at commit time (using version numbers/timestamps).

**Q70. What is a Shared Lock vs Exclusive Lock?**  
> Shared (S): multiple readers allowed. Exclusive (X): only one writer, blocks everyone else.

---

## 🔹 Advanced Concepts (Q71–Q85)

**Q71. What is an Index?**  
> A data structure (B-Tree/Hash) that speeds up data retrieval. Like a book's index. Faster reads but slower writes.

**Q72. What is a B+ Tree?**  
> A balanced tree with data in leaf nodes (linked list). Supports equality and range queries. Default index in most RDBMS.

**Q73. Clustered vs Non-Clustered Index?**  
> Clustered: data physically sorted by index (one per table, usually PK). Non-clustered: separate structure pointing to data (multiple per table).

**Q74. What is a View?**  
> A virtual table based on a SELECT query. Doesn't store data. Used for security, simplification, abstraction.

**Q75. What is a Materialized View?**  
> A view that stores data physically. Faster reads but needs refresh. Supported in PostgreSQL and Oracle.

**Q76. What is a CTE (WITH clause)?**  
> A temporary named result set for complex queries. More readable than nested subqueries. Can be recursive.

**Q77. What are Window Functions?**  
> Functions that perform calculations across a set of rows without collapsing them. ROW_NUMBER(), RANK(), DENSE_RANK(), LAG(), LEAD(), SUM() OVER().

**Q78. ROW_NUMBER vs RANK vs DENSE_RANK?**  
> ROW_NUMBER: unique sequential. RANK: ties get same rank with gaps (1,2,3,3,5). DENSE_RANK: ties with no gaps (1,2,3,3,4).

**Q79. What is a Sequence?**  
> A database object that generates unique auto-incrementing numbers. Used for primary keys.

**Q80. What is EXPLAIN / EXPLAIN ANALYZE?**  
> Shows the query execution plan (how the database will execute your query). EXPLAIN ANALYZE actually runs the query and shows real execution times. Used for performance tuning.

**Q81. What is a Tablespace?**  
> A storage location where database objects (tables, indexes) are stored on disk. Allows distributing data across different disks.

**Q82. What is Partitioning?**  
> Dividing a large table into smaller pieces (partitions) based on a column value. Types: Range, List, Hash. Improves query performance on large tables.

**Q83. What is Replication?**  
> Copying data from one database server to another. Types: Master-Slave (one-way), Master-Master (both ways). Used for high availability and read scaling.

**Q84. What is Sharding?**  
> Splitting data across multiple database servers based on a shard key. Each server holds a subset of data. Used for horizontal scaling.

**Q85. What is Connection Pooling?**  
> Reusing database connections instead of creating new ones for each request. Reduces connection overhead. Example: PgBouncer for PostgreSQL.

---

## 🔹 SQL Practice Queries (Q86–Q100)

**Q86. Find employees who joined in the last 2 years.**  
> ```sql
> SELECT * FROM employees
> WHERE hire_date >= CURRENT_DATE - INTERVAL '2 years';
> ```

**Q87. Find the department with the highest average salary.**  
> ```sql
> SELECT dept_id, AVG(salary) AS avg_sal
> FROM employees GROUP BY dept_id
> ORDER BY avg_sal DESC LIMIT 1;
> ```

**Q88. Find employees whose name starts with 'A' and ends with 'a'.**  
> ```sql
> SELECT * FROM employees
> WHERE first_name LIKE 'A%' AND first_name LIKE '%a';
> ```

**Q89. Count employees per department and show department name.**  
> ```sql
> SELECT d.dept_name, COUNT(e.emp_id) AS emp_count
> FROM departments d
> LEFT JOIN employees e ON d.dept_id = e.dept_id
> GROUP BY d.dept_name;
> ```

**Q90. Find departments with no employees.**  
> ```sql
> SELECT d.dept_name FROM departments d
> LEFT JOIN employees e ON d.dept_id = e.dept_id
> WHERE e.emp_id IS NULL;
> -- OR
> SELECT dept_name FROM departments
> WHERE dept_id NOT IN (SELECT DISTINCT dept_id FROM employees WHERE dept_id IS NOT NULL);
> ```

**Q91. Find the highest paid employee in each department.**  
> ```sql
> SELECT * FROM (
>     SELECT *, ROW_NUMBER() OVER (PARTITION BY dept_id ORDER BY salary DESC) AS rn
>     FROM employees
> ) t WHERE rn = 1;
> ```

**Q92. Swap values of two columns.**  
> ```sql
> UPDATE employees SET first_name = last_name, last_name = first_name;
> ```

**Q93. Find employees earning more than their manager.**  
> ```sql
> SELECT e.first_name AS employee, e.salary, m.first_name AS manager, m.salary
> FROM employees e
> JOIN employees m ON e.manager_id = m.emp_id
> WHERE e.salary > m.salary;
> ```

**Q94. Display alternate/odd rows.**  
> ```sql
> SELECT * FROM (
>     SELECT *, ROW_NUMBER() OVER (ORDER BY emp_id) AS rn
>     FROM employees
> ) t WHERE rn % 2 = 1;
> ```

**Q95. Find common records between two tables.**  
> ```sql
> SELECT * FROM table1
> INTERSECT
> SELECT * FROM table2;
> ```

**Q96. Pivot rows to columns (crosstab).**  
> ```sql
> SELECT
>     dept_id,
>     COUNT(CASE WHEN salary > 80000 THEN 1 END) AS high_salary,
>     COUNT(CASE WHEN salary BETWEEN 60000 AND 80000 THEN 1 END) AS mid_salary,
>     COUNT(CASE WHEN salary < 60000 THEN 1 END) AS low_salary
> FROM employees
> GROUP BY dept_id;
> ```

**Q97. Find consecutive records (gaps).**  
> ```sql
> SELECT emp_id + 1 AS missing_id
> FROM employees e
> WHERE NOT EXISTS (
>     SELECT 1 FROM employees WHERE emp_id = e.emp_id + 1
> );
> ```

**Q98. Running total / cumulative sum.**  
> ```sql
> SELECT emp_id, salary,
>     SUM(salary) OVER (ORDER BY emp_id) AS running_total
> FROM employees;
> ```

**Q99. Year-over-year comparison.**  
> ```sql
> SELECT
>     EXTRACT(YEAR FROM hire_date) AS year,
>     COUNT(*) AS hires,
>     LAG(COUNT(*)) OVER (ORDER BY EXTRACT(YEAR FROM hire_date)) AS prev_year_hires
> FROM employees
> GROUP BY EXTRACT(YEAR FROM hire_date)
> ORDER BY year;
> ```

**Q100. Create a copy of a table with data.**  
> ```sql
> -- PostgreSQL
> CREATE TABLE employees_backup AS SELECT * FROM employees;
> 
> -- Oracle
> -- CREATE TABLE employees_backup AS SELECT * FROM employees;
> 
> -- Copy structure only (no data)
> CREATE TABLE employees_empty AS SELECT * FROM employees WHERE 1=0;
> ```

---

---

# 📝 Quick Revision — One-Line Summaries

| Topic | Key Point |
|-------|-----------|
| DBMS | Software to manage databases |
| RDBMS | Data in tables with relationships |
| Primary Key | Unique identifier, no NULLs, one per table |
| Foreign Key | References another table's PK |
| Normalization | Reduce redundancy (1NF→2NF→3NF→BCNF) |
| 1NF | Atomic values only |
| 2NF | No partial dependency |
| 3NF | No transitive dependency |
| ACID | Atomicity, Consistency, Isolation, Durability |
| Transaction | All-or-nothing unit of work |
| COMMIT | Save changes permanently |
| ROLLBACK | Undo changes |
| JOIN | Combine tables horizontally |
| INNER JOIN | Only matching rows |
| LEFT JOIN | All left + matching right |
| GROUP BY | Group rows for aggregation |
| HAVING | Filter groups (after GROUP BY) |
| Subquery | Query inside a query |
| View | Virtual table from a query |
| Index | Speeds up reads, slows writes |
| B+ Tree | Balanced tree, default index |
| Trigger | Auto-execute on INSERT/UPDATE/DELETE |
| Stored Procedure | Saved SQL code, called by name |
| MVCC | Multiple versions, readers don't block writers |
| Deadlock | Circular wait for locks |
| Window Function | Compute over rows without collapsing |
| CTE | Temporary named result set (WITH clause) |
| Denormalization | Add redundancy for faster reads |
| CAP Theorem | Consistency + Availability + Partition Tolerance (pick 2) |

---

# 📋 SQL Cheat Sheet

```sql
-- ==================== DDL ====================
CREATE TABLE t (id INT PRIMARY KEY, name VARCHAR(50));
ALTER TABLE t ADD COLUMN age INT;
ALTER TABLE t DROP COLUMN age;
DROP TABLE t;
TRUNCATE TABLE t;

-- ==================== DML ====================
INSERT INTO t VALUES (1, 'Rahul');
UPDATE t SET name = 'Priya' WHERE id = 1;
DELETE FROM t WHERE id = 1;

-- ==================== SELECT ====================
SELECT * FROM t;
SELECT DISTINCT col FROM t;
SELECT col AS alias FROM t WHERE condition;
SELECT * FROM t ORDER BY col DESC;
SELECT * FROM t LIMIT 10 OFFSET 5;

-- ==================== JOINS ====================
SELECT * FROM a INNER JOIN b ON a.id = b.id;
SELECT * FROM a LEFT JOIN b ON a.id = b.id;
SELECT * FROM a RIGHT JOIN b ON a.id = b.id;
SELECT * FROM a FULL OUTER JOIN b ON a.id = b.id;
SELECT * FROM a CROSS JOIN b;

-- ==================== AGGREGATES ====================
SELECT dept, COUNT(*), AVG(sal), SUM(sal), MAX(sal), MIN(sal)
FROM emp GROUP BY dept HAVING COUNT(*) > 1;

-- ==================== SUBQUERIES ====================
SELECT * FROM t WHERE col IN (SELECT col FROM t2);
SELECT * FROM t WHERE EXISTS (SELECT 1 FROM t2 WHERE t2.id = t.id);

-- ==================== WINDOW FUNCTIONS ====================
SELECT *, ROW_NUMBER() OVER (ORDER BY sal DESC) FROM emp;
SELECT *, RANK() OVER (PARTITION BY dept ORDER BY sal DESC) FROM emp;

-- ==================== TRANSACTIONS ====================
BEGIN;
  -- SQL statements
COMMIT;  -- or ROLLBACK;

-- ==================== VIEWS ====================
CREATE VIEW v AS SELECT * FROM t WHERE condition;
DROP VIEW v;
```

---

> **📌 Pro Tip for Interviews:** Always write clean, well-indented SQL. Use meaningful aliases. Explain your thought process while writing queries. Interviewers value problem-solving approach over memorized syntax.

---

**🎓 All the best for your placement drive! 🚀**
