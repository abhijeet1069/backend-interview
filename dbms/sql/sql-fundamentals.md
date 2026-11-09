# SQL fundamentals

## SELECT

Used to retrieve data from a table

```sql
SELECT column1, column2
FROM table_name;

-- Retrieve all columns
SELECT * FROM employees;

-- retrieve calculated values
SELECT name, salary, salary * 12 AS annual_salary
FROM employees;
```

## INSERT

Used to insert new records into a table

```sql
INSERT INTO table_name (column1, column2)
VALUES (value1, value2);

INSERT INTO employees (id, name, salary, department)
VALUES (1, 'John', 50000, 'Engineering');

-- insert multiple values
INSERT INTO employees (id, name, salary, department)
VALUES
    (2, 'Alice', 60000, 'HR'),
    (3, 'Bob', 70000, 'Engineering');

-- columns with defaults or nullable values can be ommitted
```

## UPDATE

Used to modify existing records.

```sql
UPDATE table_name
SET column1 = value1
WHERE condition;

UPDATE employees
SET salary = 75000
WHERE id = 1;
```

## DELETE

Used to remove records from a table.

```sql
DELETE FROM table_name
WHERE condition;

DELETE FROM employees
WHERE id = 1;

-- removes all data
DELETE FROM employees;
```

## WHERE

Used to filter rows based on conditions.

```sql
SELECT *
FROM employees
WHERE salary > 50000;
```

### Comparision operators:

* Equal =
* Not equal !=
* Greater than >
* Less than <
* Greater than or equal >=
* Less than or equal  <=

### Logical operators:

* AND
* OR
* NOT

### BETWEEN

BETWEEN is inclusive of both boundaries.

### IN

```sql
SELECT *
FROM employees
WHERE department IN ('HR', 'Finance', 'Engineering');
```

### LIKE

Used for pattern matching

```sql
-- Names beginning with A
SELECT * FROM employees
WHERE name LIKE 'A%';

-- _ represents exactly one character.

-- Never use = NULL. Use IS NULL or IS NOT NULL.
SELECT *
FROM employees
WHERE department IS NULL;
```

## GROUP BY

Used to group rows that have the same values in specified columns.

> Every non-aggregated column in SELECT must be grouped or functionally dependent on the grouped columns

Aggregate Function:

* COUNT() - Counts rows/values
* SUM() - Calculates sum
* AVG() - Calculates average
* MIN() - Finds minimum
* MAX() - Finds maximum

```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department;

Remember: When using GROUP BY, selected columns generally need to be either:
* Included in GROUP BY.
* Used inside an aggregate function.
```

## HAVING

Used to filter groups after GROUP BY.

This is an important distinction:

* WHERE filters individual rows.
* HAVING filters groups.

```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department
HAVING COUNT(*) > 5;

SELECT department, AVG(salary) AS avg_salary
FROM employees
WHERE salary > 30000
GROUP BY department
HAVING AVG(salary) > 50000;

select name from Employee
where id in (
    select managerId from Employee
    where managerId is not null
    group by managerId
    having count(*) >= 5
)
```

## ORDER BY

Used to sort query results.

```sql

-- ASC is default
SELECT *
FROM employees
ORDER BY salary DESC;

-- sort by multiple columns
-- sort by department alphabetically, 
-- then within each department sort by salary from highest to lowest
SELECT *
FROM employees
ORDER BY department ASC, salary DESC;
```

## DISTINCT

Used to eliminate duplicate rows from query results.

```sql
SELECT DISTINCT department
FROM employees;

-- distinct with multiple columns
-- SQL considers the uniqueness of department and salary
SELECT DISTINCT department, salary
FROM employees;
```

## LIMIT/OFFSET

These clauses are used for pagination.

```sql
SELECT *
FROM employees
LIMIT 10 OFFSET 10; -- Skips the first 10 rows and returns the next 10.

-- OFFSET = (page_number - 1) * page_size
SELECT *
FROM employees
ORDER BY id
LIMIT 10 OFFSET 20;
```

## IS NULL

```sql
select name, bonus from
Employee e left join Bonus b
on e.empId = b.empId
where bonus < 1000 or bonus is null;
```

## DDL

### Types

* char(n): A fixed-length character string with user-specified length n
* varchar(n): A variable-length character string with user-specified maximum length n
* int: An integer (a finite subset of the integers that is machine dependent).
* smallint: A small integer (a machine-dependent subset of the integer type).
* numeric(p, d): A fixed-point number with user-specified precision. 
* real, double precision: Floating-point and double-precision floating-point numbers with machine-dependent precision.
* float(n): A floating-point number with precision of at least n digits.

### Create table

```sql
create table department
    (dept name varchar (20),
    building varchar (15),
    budget numeric (12,2),
    primary key (dept name));
```