---
layout: post
title: What are Subqueries in SQL
date: 2023-01-02 12:00:00
categories: [data, analysis, sql]
---

A subquery is a SELECT statement that is nested within another SELECT, INSERT, UPDATE, DELETE, or SET statement. Subqueries are often used to select rows for a query based on complex criteria or to perform calculations within a query.

## Syntax

The syntax for a subquery is similar to that of a regular SELECT statement, with a few key differences. A subquery must be enclosed in parentheses, and it must be placed within the WHERE or FROM clause of the outer query.

Here is the basic syntax for a subquery:

```
SELECT column1, column2, ...
FROM table1
WHERE column1 IN (SELECT column1 FROM table2 WHERE condition);
```

In this example, the subquery `(SELECT column1 FROM table2 WHERE condition)` is used to select rows from `table2` based on the condition `condition`. The outer query then selects only those rows from `table1` where `column1` is in the result set returned by the subquery.

## Types of Subqueries

There are several types of subqueries that can be used in SQL, depending on the context and the needs of the query. Here are a few common types of subqueries:

### Single-row Subqueries

A single-row subquery is a subquery that returns a single row of values. Single-row subqueries are often used with comparison operators such as `=`, `>`, `<`, `>=`, `<=`, and `<>`.

Here is an example of a single-row subquery that returns the name of the employee with the highest salary:

```
SELECT name FROM employees
WHERE salary = (SELECT MAX(salary) FROM employees);
```

In this example, the subquery `(SELECT MAX(salary) FROM employees)` returns the maximum salary in the `employees` table, and the outer query selects only the employee with that salary.

### Multiple-row Subqueries

A multiple-row subquery is a subquery that returns more than one row of values. Multiple-row subqueries must be used with an operator such as IN, ANY, or ALL, which allows the subquery to be evaluated based on the values returned.

Here is an example of a multiple-row subquery that returns the names of all employees who have a salary greater than the average salary of all employees:

```
SELECT name FROM employees
WHERE salary > ANY (SELECT salary FROM employees);
```

The subquery `(SELECT salary FROM employees)` returns the salary of all employees, and the outer query selects only those employees whose salary is greater than any of the salaries returned by the subquery.

### Correlated Subqueries

A correlated subquery is a subquery that references a column from the outer query. Correlated subqueries are used to select rows based on the values in the outer query.

Here is an example of a correlated subquery that returns the names of all employees who have a salary greater than the salary of their manager:

```
SELECT name FROM employees e1
WHERE salary > (SELECT salary FROM employees e2 WHERE e2.id = e1.manager_id);
```

### Using Subqueries in the FROM Clause

Subqueries can also be used in the FROM clause of a SELECT statement. This is known as a derived table or inline view. Derived tables are useful when you need to use the same subquery multiple times in a query or when you want to use a subquery to create a temporary table for the duration of the query.

Here is the syntax for using a subquery in the FROM clause:

```
SELECT column1, column2, ...
FROM (SELECT column1, column2, ... FROM table1 WHERE condition) AS alias;
```

The subquery `(SELECT column1, column2, ... FROM table1 WHERE condition)` is used to select rows from `table1` based on the condition `condition`. The outer query then selects the specified columns from the derived table `alias`.

Here is an example of a derived table that returns the names and salaries of all employees who have a salary greater than the average salary of all employees:

```
SELECT name, salary FROM (SELECT name, salary FROM employees) AS e
WHERE salary > (SELECT AVG(salary) FROM employees);
```

`(SELECT name, salary FROM employees)` is used to create a derived table `e` that contains the names and salaries of all employees, and the outer query selects only those employees whose salary is greater than the average.

### Using Subqueries in the SET Clause

Subqueries can also be used in the SET clause of an UPDATE statement. This is useful when you want to update a column based on the value of another column or the result of a calculation.

Here is the syntax for using a subquery in the SET clause:

```
UPDATE table1
SET column1 = (SELECT column2 FROM table2 WHERE condition);
```

`(SELECT column2 FROM table2 WHERE condition)` is used to select a value from table2, and the outer query updates `column1` in `table1` to that value.

Here is an example of an `UPDATE` statement that uses a subquery in the `SET` clause to update the salary of all employees to the average salary of all employees:

```
UPDATE employees
SET salary = (SELECT AVG(salary) FROM employees);
```

`(SELECT AVG(salary) FROM employees)` is used to calculate the average salary of all employees, and the outer query updates the salary of all employees to that value.

## Limitations of Subqueries

It's important to note that subqueries have a few limitations that you should be aware of when using them in your queries.

First, subqueries can only return a single value or a single row of values. If a subquery returns more than one row, it must be used with an operator such as IN, ANY, or ALL, which allows the subquery to be evaluated based on the values returned.

Second, subqueries can be slower than regular queries due to the overhead of executing the nested query. To improve the performance of your queries, you may want to consider using table joins or temporary tables instead of subqueries when possible.

Finally, not all databases support subqueries, so you may need to use alternative techniques depending on the database you are using.

## Conclusion
Subqueries are a powerful tool in SQL that allow you to perform complex queries and calculations within a single statement. By understanding the different types of subqueries and how to use them effectively, you can write more efficient and effective queries for your data analysis needs.

It's worth noting that subqueries can be slower than other techniques such as table joins or temporary tables, so you should consider the performance implications of your queries and choose the technique that best meets your needs.








