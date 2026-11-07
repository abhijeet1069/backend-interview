# Advanced SQL

## Subqueries

A subquery is a query inside another SQL query. The inner query produces a value or
set of rows that the outer query uses.

### Subquery in WHERE

```sql
-- Find employees who earn more than the company-wide average
SELECT name, salary
FROM employees
WHERE salary > (
  SELECT AVG(salary)
  FROM employees
);
```

### Subquery with IN

```sql
-- Find employees who work in a department located in New York
SELECT name
FROM employees
WHERE department_id IN (
  SELECT department_id
  FROM departments
  WHERE location = 'New York'
);
```

### Subquery in FROM

A subquery in FROM acts like a temporary result table. Many databases require it to have an alias,
such as department_averages.

```sql
-- Find the average salary by department, then show departments whose average is over 70,000
SELECT department_id, average_salary
FROM (
  SELECT department_id, AVG(salary) AS average_salary
  FROM employees
  GROUP BY department_id
) AS department_averages
WHERE average_salary > 70000;
```

## Correlated Subqueries

A correlated subquery refers to a column from the outer query. Because of that reference, 
its result depends on the current row being considered by the outer query.

```sql
-- Find employees who earn more than the average salary in their own department
SELECT e.name, e.department_id, e.salary
FROM employees AS e
WHERE e.salary > (
  SELECT AVG(e2.salary)
  FROM employees AS e2
  WHERE e2.department_id = e.department_id
);
```

## EXISTS

EXISTS checks whether a subquery returns at least one row.

```sql
-- does this customer have any orders?
SELECT c.customer_id, c.name
FROM customers AS c
WHERE EXISTS (
  SELECT 1 -- returns the constant value 1 for every row the query finds.
  FROM orders AS o
  WHERE o.customer_id = c.customer_id
);
```

## CTE

A Common Table expression is a temporary named result set that you define using the WITH clause.

```sql
-- The confirmation rate of a user is the number of 'confirmed' 
-- messages divided by the total number of requested confirmation 
-- messages. The confirmation rate of a user that did not request 
-- any confirmation messages is 0. Round the confirmation rate to 
-- two decimal places.
Signups table:
+---------+---------------------+
| user_id | time_stamp          |
+---------+---------------------+
| 3       | 2020-03-21 10:16:13 |
| 7       | 2020-01-04 13:57:59 |
| 2       | 2020-07-29 23:09:44 |
| 6       | 2020-12-09 10:39:37 |
+---------+---------------------+
Confirmations table:
+---------+---------------------+-----------+
| user_id | time_stamp          | action    |
+---------+---------------------+-----------+
| 3       | 2021-01-06 03:30:46 | timeout   |
| 3       | 2021-07-14 14:00:00 | timeout   |
| 7       | 2021-06-12 11:57:29 | confirmed |
| 7       | 2021-06-13 12:58:28 | confirmed |
| 7       | 2021-06-14 13:59:27 | confirmed |
| 2       | 2021-01-22 00:00:00 | confirmed |
| 2       | 2021-02-28 23:59:59 | timeout   |
+---------+---------------------+-----------+
Output: 
+---------+-------------------+
| user_id | confirmation_rate |
+---------+-------------------+
| 6       | 0.00              |
| 3       | 0.00              |
| 7       | 1.00              |
| 2       | 0.50              |
+---------+-------------------+


WITH Confirmed_times as(
    SELECT s.user_id, count(c.action) as confirmed_count
    from Signups as s
    JOIN Confirmations as c
    ON s.user_id = c.user_id
    WHERE c.action = 'confirmed'
    GROUP BY s.user_id
),
Messages as(
    SELECT s.user_id, count(*) as messages_count
    FROM Signups as s
    LEFT JOIN Confirmations as c
    ON s.user_id = c.user_id
    GROUP BY s.user_id
)

SELECT m.user_id, COALESCE(ROUND(CAST(c.confirmed_count AS NUMERIC)/CAST(m.messages_count AS NUMERIC), 2), 0) AS confirmation_rate
FROM Messages as m
LEFT JOIN Confirmed_times as c
ON m.user_id = c.user_id
```

## Recursive CTE

A recursive CTE is a CTE that references itself.

It is useful when you have hierarchical data or need to repeatedly generate new rows based on 
previously generated rows.

```sql
WITH RECURSIVE Numbers AS (

    -- Anchor member
    SELECT 1 AS n

    UNION ALL

    -- Recursive member
    SELECT n + 1
    FROM Numbers
    WHERE n < 5

)
SELECT * FROM Numbers;
```

```sql
WITH RECURSIVE EmployeeHierarchy AS (

    -- 1. Start with CEO
    SELECT id, name, manager_id
    FROM Employee
    WHERE manager_id IS NULL

    UNION ALL

    -- 2. Find employees reporting to current employees
    SELECT e.id, e.name, e.manager_id
    FROM Employee e
    INNER JOIN EmployeeHierarchy h
        ON e.manager_id = h.id

)
SELECT *
FROM EmployeeHierarchy;
```

## CASE

The SQL CASE expression adds conditional, if-then-else logic to your queries

```sql
-- For each department, how many employees are there in total, how many are female, and how many are male?
SELECT 
    department_id,
    COUNT(*) AS total_employees,
    SUM(CASE WHEN gender = 'F' THEN 1 ELSE 0 END) AS female_count,
    SUM(CASE WHEN gender = 'M' THEN 1 ELSE 0 END) AS male_count
FROM employees
GROUP BY department_id;
```

## COALESCE

COALESCE() is a SQL function that returns the first non-NULL value from a list of expressions.

```sql
-- 10
SELECT COALESCE(NULL, NULL, 10, 20);
```