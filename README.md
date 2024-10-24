# how-to-sql

<hr />

Summary:

- imports and uploads
- explore/summarize 
- create 
- vizualizations and export
- backups
- workflow improvement
  
<hr>

- Data Definition Language (DDL) <br>
- Data Manipulation Language (DML) <br>
- Data Control Language (DCL) <br>
- Transaction Control Language (TCL) <br>

<hr>

## Data Definition Language (DDL)
`:: CREATE ::` # Create a new table <br>
`:: ALTER TABLE ::` # Modify an existing table structure <br>
`:: DROP ::` # Delete a table or other object in the database <br>
`:: RENAME ::` # <br>
`:: TRUNCATE ::` # <br>
`:: COMMENT ::` # <br>

## Data Manipulation Language (DML)
`:: SELECT ::` # Select data from the database <br>
`:: INSERT INTO ::` # Add new rows to a table <br>
`:: UPDATE ::` # Modify existing table structure <br>
`:: DELETE ::` # Remove rows from a table <br>
`:: MERGE ::` # <br>
`:: CALL ::` # <br>
`:: EXPLAIN PLAN ::` # <br>
`:: LOCK TABLE ::` # <br>

## Data Control Language (DCL)
`:: GRANT ::` # <br>
`:: REVOKE ::` # <br>

## Transactional Control Language (DCL)
`:: COMMIT ::` # Save changes made in the transaction <br>
`:: ROLLBACK ::` # Undo changes made in the transaction <br>

## Window Functions
### Aggregate
`:: AVG() ::` # Calculate the average value a numeric column <br>
`:: COUNT() ::` # Return the value of numeric column <br>
`:: SUM() ::` # Calculate the total sum of a numeric column <br>
`:: MIN() ::` # Return the smallest value of the selected column <br>
`:: MAX() ::` # Return the largest value of the selected column <br>

### Value
`:: ROW_NUMBER() ::` # <br>
`:: RANK() ::` # <br>
`:: DENSE_RANK() ::` # <br>
`:: PERCENT_RANK() ::` # <br>
`:: NTILE() ::` # <br>

### Ranking
`:: LAG() ::` # <br>
`:: LEAD() ::` # <br>
`:: FIRST_VALUE() ::` # <br>
`:: LAST_VALUE() ::` # <br>
`:: NTH_VALUE() ::` # <br>

### Numeric Functions
`:: POWER() ::` # <br>
`:: MOD()::` # <br>
`:: ROUND() ::` # <br>
`:: FLOOR() ::` # <br>
`:: CEILING ::` # <br>
`:: SQUARE() ::` # <br>

### String Functions
`:: LENGTH() ::` # <br>
`:: LCASE() ::` # <br>
`:: UCASE() ::` # <br>
`:: INSTR() ::` # <br>
`:: TRIM() ::` # <br>
`:: SUBSTRING ::` # <br>
`:: CHARINDEX ::` # <br>
`:: CONCAT ::` # <br>
`:: CONCAT_WS ::` # <br>
`:: REPLACE ::` # <br>
`:: TRANSLATE ::` # <br>
`:: LTRIM() ::` # <br>
`:: RTRIM() ::` # <br>
`:: LEFT() ::` # <br>
`:: RIGHT() ::` # <br>

### Date Time Functions
`:: DATE() ::` # <br>
`:: DAY() ::` # <br>
`:: MONTH() ::` # <br>
`:: YEAR() ::` # <br>
`:: NOW() ::` # <br>
`:: MONTHNAME() ::` # <br>
`:: DATEPART ::` # <br>
`:: DATEADD ::` # <br>
`:: DATENAME ::` # <br>
`:: DATEDIFF ::` # <br>
`:: GETDATE ::` # <br>
`:: CURRENT_TIMESTAMP ::` # <br>

### Null Functions
`:: NULLIF ::` # <br>
`:: COALESCE ::` # <br>
`:: ISNULL ::` # Check for empty values <br>

<hr>

`:: SAVEPOINT ::` # <br>
`:: SET TRANSACTION ::` # <br>
`:: FROM ::` # Specify the table to select data from <br>
`:: WHERE ::` # Filter row based on a condition <br>
`:: AS ::` #Rename a column or table an alias <br>
`:: JOIN ::` # Combine row from two or more tables <br>
`:: AND ::` # Combine multiple conditions, all must be true <br>
`:: OR ::` # Combine multiple conditions, at least one must be true <br>
`:: LIMIT ::` #Restrict the number or rows returned <br>
`:: IN ::` # Specify multiple values in a WHERE clause <br>
`:: CASE ::` # Create conditional logic within a SQL statement <br>
`:: LIKE ::` # Search for a specified pattern in a column <br>
`:: GROUP BY ::` # Group rows that have the same values in specified columns into a summary rows <br>
`:: ORDER BY ::` # Sort the result set of query by specified criteria <br>
`:: HAVING ::` # Filter groups based on a condition (used after GROUP BY) <br>
`:: CASE WHEN ::` # <br>

<hr>

Sources:

<!--- https://www.digitalocean.com/community/tutorials/how-to-manage-sql-database-cheat-sheet
