# Intro

SQL stands for Structured Query Language. SQL is a language for interacting with data that is store in a relational database.

A relational database is a collection of tables like a spreadsheet that represents one type of entity. Each row or record, of a table contains information about a single entity. Each column, or field, of a table contains a single attribute for all rows in the table.

If you want to select all the unique values from a column, you can use the   DISTINCT keyword. This might be useful, for example when you're interested in seeing one column represented.

`SELECT`ing column(s)

You select data from a column using the `SELECT` statement and `FROM`

`SELECT`
`FROM` are called keywords. They are not case sensitive but it's good practice to write these uppercase so that it's easier to differenciate them from other parts of your query. It's also good practice to add a `;` to the end of your query.

## DISTINCT

Let's you select all the unique values from a column.

`SELECT DISTINCT languages
FROM films; `

The COUNT statement let's you count all the number of employees from your employees table. For example this code gives the number of rows in the people table:

## COUNT
The `COUNT` statement lets you count all the number of rows in one or more columns.

`SELECT COUNT (*)
FROM people; `

As you've seen, `COUNT( * )` tells you how many rows are in a table. However, if you want to count the number of non-missing values in a particular column, you can call `COUNT` on just that column.

For example, to count the number of birth dates present in the people table:

`SELECT COUNT(birthdate)
FROM people;`

It's also common to combine COUNT with DISTINCT to count the number of distinct values in a column.
For example, this query counts the number of distinct birth dates contained in the people table:

`SELECT COUNT(DISTINCT birthdate)
FROM people;`

Simple filtering of numeric values
As you learned in the previous exercise, the WHERE clause can also be used to filter numeric records, such as years or ages.
For example, the following query selects all details for films with a budget over ten thousand dollars:
SELECT *
FROM films
WHERE budget > 10000;

## Filtering

The `WHERE` clause is used to filter text results.

For example, this query gets the job role of all employees who are male.

`SELECT job_role
FROM employees
WHERE sex = 'Male';`

You can also use `WHERE` and `AND` when you want to combine multiple queries.

`SELECT job_role
FROM employees
WHERE sex = 'MALE' AND birth_year <1990;`

This will return all the job roles whre sex is male and birth year is before 1990.

If you want to select rows that met some but not all the conditions you can use the `OR` operator.

`SELECT job_role
FROM employees
WHERE birth_year = 1990 or birth_year = 2000;`

You need to specify every column or it'll be invalid.

You can also combine `WHERE`, `AND` & `OR` but remmeber to use parenthesis.

`SELECT job_role
FROM employees
WHERE (birth_year = 1990 OR birth_year = 2000) AND (sex = 'MALE');`

This will select job role from the Employee table where the birth year is 1990 or 2000 and the sex is Male.

`BETWEEN` is used as a shorthand for filtering between a specified range.

`SELECT job_role
FROM employees
WHERE birth_year >= 1994
AND birth_year <= 2000;`

is the same as

`SELECT job_role
FROM employees
WHERE birth_year BETWEEN 1994 AND 2000;`

`IN` allows you to specify multiple values in a `WHERE` clasue, making it quicker and easier to say what you want.

`SELECT job_role
FROM employees
WHERE birth_year IN (1994,1995,1996);`

You can use  `WHERE` with aggregate functions.

## NULL and IS NULL

`NULL` is a missing or unknown value, you can check for `NULL` values using the expression `IS NULL`

`SELECT job_role
FROM employees
WHERE death_year IS NULL;`

Using `IS NULL` with `WHERE` is powerful to see what data you are missing.

If you want to filter out missing values so you only results which are not `NULL`, to do this you use the `IS NOT NULL` operator.

`SELECT job_role
FROM employees
WHERE death_year IS NOT NULL;`

## Like and Not like

The `LIKE` operator is used in conjunction with `WHERE` to search for a pattern. There are two wildcards you use `%` & `_` and these work as a placeholder for values.

`%` - will match the characters in the tables

`SELECT name
FROM employees
WHERE name LIKE 'Alex%'`

This will match names like Alexa, Alexander, Alexandra, Alexia, Alexus etc

`_` - will match a single character
`SELECT name
FROM employees
WHERE name LIKE 'D_n'`

This will match names like Dan, Don. Den, Din

The `NOT LIKE` operator will find records that don't match the pattern that is specified.

## Aggregate Functions

`AVG`
`MAX`
`MIN`
`SUM`
`COUNT`

Aggregate functions also work with `WHERE` clauses.

SQL when performing basic arithmetic will assume if you divide an integer with an integer, you'll want an integer back.

## Aliasing

When you select two columns that have the same name you can use `AS` to alias which assigns a temporary name to something. This also makes results more readable.

## ORDER BY

Use order by to sort columns. You can sort multiple columns which will sort in the order you list them.
`ORDER BY`
`ORDER BY DESC`
`ORDER BY ASC`

## GROUP BY
Groups the results by one or more columns.
Commonly, `GROUP BY` is used with aggregate functions like `COUNT()`` or `MAX()`

 Note that `GROUP BY` always goes after the `FROM` clause!

 You can not use `GROUP BY` and the `WHERE` clause with aggregate functions. Here you have to use the `HAVING` clause.

 `HAVING`

`SELECT job_role
FROM employees
GROUP BY job_role
WHERE COUNT (job_role) >10; ` will bring an error

`SELECT job_role
FROM employees
GROUP BY job_role
HAVING COUNT (job_role) >10; `

`LIMIT` keyword is used to limit the number of rows returned.
