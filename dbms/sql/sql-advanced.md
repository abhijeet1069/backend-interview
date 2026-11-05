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