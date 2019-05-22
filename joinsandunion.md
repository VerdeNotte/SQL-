# Joins

|Type of join | Description|
|---- | -----|
| Inner Join| Selects all records from Table A and Table B, where the join condition is met|
|Left Join| Selects all records from Table A, along with records from Table B for which the join condition is met (if at all)
|Right Join| Selects all records from Table B, along with records from Table A for which the join condition is met (if at all)|
| Full Joins| Select all records from Table A and Table B, regardless of whether the join condition is met or not|


![Joins](https://github.com/VerdeNotte/SQL-/blob/master/Joins.PNG "Joins")

 You must match joins on a primary key. All must use `ON` or `HAVING`.

 ## Self Joins
This is a query where you join the table onto itself. You can then compare values in a column with the *same column in the same table.*

You must use alias to differentiate the tables. There is no keyword for `SELF JOIN` so you simply use `JOIN`

It is useful for querying hierarchical data or comparing rows within the same table.

# Set Theory Clause

Table A: NZ, Australia, UK, US, US
Table B: NZ, France, Germany, UK, UK

|Set Theory Clause |What | Final Results|
|----|----|----|
|UNION|Eliminates duplicated matches, number of columns and datasets must be the same| NZ, Australia, UK, US, France, Germany|
|UNION ALL| Concatenates all rows - will show duplications|NZ, NZ, Australia, France, Germany, UK, UK, UK, US, US|
|INTERSECT|Only matches on both tables| NZ, UK|
|EXCEPT|Keeps rows from Table A that aren't included in Table B| Australia, US|


## Differences between Joins and Union

- `JOIN` : Combines data into new columns. If two tables are joined together, then the data from the first time is shown in one set of column alongside the second table's column in the same row.
- `UNION`: Combines data into new rows. If two tables are `UNION`ed together, then the data from the first table is in one set of rows, and the table from the second table is in another set. The rows are in the same results.
