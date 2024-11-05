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

- Views
- Subqueries
- Common Table Expressions
- Store Procedures

<hr>

## Data Definition Language (DDL)
`:: CREATE TABLE::` # Create a new table <br>
`:: ALTER TABLE ::` # Modify an existing table structure <br>
`:: DROP ::` # Delete a table or other object in the database <br>
`:: RENAME ::` # <br>
`:: TRUNCATE ::` # <br>
`:: COMMENT ::` # <br>

`````Ruby

-- Create Table:

CREATE TABLE [dbo].BUTTER(
	[ID] [nchar](10) NOT NULL,
	[DATE] [date] NOT NULL,
	[MONEY] [money] NOT NULL,
	[COMMODITY] [nchar](10) NULL,
	[REPORTNAME] [nchar](10) NULL,
	[DATEUPDATED] [date] NULL
) ON [PRIMARY]
GO

-- Stored Procedure to correct spelling mistake:

EXEC sp_rename "CHIKCKEN_BREAST", "CHICKEN_BREAST";

-- Add two new columns

ALTER TABLE CHUCK_ROAST
ADD CURRENCY [nchar] (10) NULL,
   FREQUENCY [nchar] (10) NULL;

-- Update data column with new datatype

ALTER TABLE RICE
ALTER COLUMN DATE [datetime] NULL;

-- Add new column

ALTER TABLE SUGAR
ADD REPORTEDBY [nchar](10) NULL;

-- Update Column to Upper case
UPDATE PCOCOUSDM
SET FREQUENCY = UPPER(CURRENCY),
	REPORTEDBY = UPPER(REPORTEDBY),
	MEASUREMENT = UPPER(MEASUREMENT);

-- ADD YEAR, MONTH and DAY columns
ALTER TABLE PCOCOUSDM
ADD YEAR DATE,
	MONTH DATE,
	DAY DATE;

-- ADD YEAR, MONTH and DAY values to columns
UPDATE PCOCOUSDM
SET YEAR = YEAR(DATE),
	MONTH = MONTH(DATE),
	DAY = DAY(DATE);

-- UPDATE COLUMN to show values with 2 decimals places
ALTER TABLE PCOCOUSDM 
ALTER COLUMN PRICE decimal(19,2);

-- Create a copy of a table
SELECT *
INTO COMM_COL_REF
FROM COCOA;

-- Create an empty reference table using TRUNCATE
TRUNCATE TABLE COMM_COL_REF;

-- Query highest prices and dates
SELECT TOP 3 PRICE, DATE
FROM PCOCOUSDM
ORDER BY PRICE DESC;

-- Query Aggregates
SELECT 
	COUNT(ITEMID) AS RECORD_COUNT,
	MAX(PRICE) AS HIGHEST_PRICE,
	MIN(PRICE) AS LOWEST_PRICE,
	AVG(PRICE) AS AVERAGE_PRICE
FROM PCOCOUSDM

-- Query top 3 average annual price
SELECT TOP 3
	YEAR, 
	CAST(ROUND(AVG(PRICE), 2) AS DECIMAL(10, 2)) AS ANNUAL_AVERAGE_PRICE
FROM PCOCOUSDM
GROUP BY YEAR
ORDER BY ANNUAL_AVERAGE_PRICE DESC;

-- Query top 3 average monthly price
SELECT TOP 3
	YEAR,
	MONTH,
	CAST(ROUND(AVG(PRICE), 2) AS DECIMAL(10, 2)) AS MONTHLY_AVERAGE_PRICE
FROM PCOCOUSDM
GROUP BY YEAR, 
	MONTH
ORDER BY MONTHLY_AVERAGE_PRICE DESC;

-- Rename column
EXEC sp_rename 'PCOCOUSDM.PCOCOUSDM', 'COMMODITY', 'COLUMN';

-- Select top 3 highest average prices, by commodity, year, and month
SELECT TOP 3
	COMMODITY,
	YEAR,
	MONTH,
	CAST(ROUND(AVG(PRICE), 2) AS DECIMAL(10, 2)) AS MONTHLY_AVERAGE_PRICE
FROM PCOCOUSDM
GROUP BY COMMODITY,
		YEAR, 
		MONTH
ORDER BY MONTHLY_AVERAGE_PRICE DESC;

-- Create view for top average price, by year, month and by commodity
CREATE VIEW TOP_3_COMM_BY_YR_MNTH AS
SELECT TOP 3
	COMMODITY,
	YEAR,
	MONTH,
	CAST(ROUND(AVG(PRICE), 2) AS DECIMAL(10, 2)) AS MONTHLY_AVERAGE_PRICE
FROM PCOCOUSDM
GROUP BY COMMODITY,
		YEAR, 
		MONTH
ORDER BY MONTHLY_AVERAGE_PRICE DESC;

-- Update table and replace null values
UPDATE SUGAR
SET PRICE = '4.24'
WHERE DATE >= '2018-10-01' AND DATE <= '2019-09-01';

-- Create VIEW ALL_COMMODITIES AS
SELECT *
	FROM APU0000701312
	UNION
	SELECT *
	FROM APU0000711211
	UNION
	SELECT *
	FROM APU0000712311
	UNION
	SELECT *
	FROM APU0000715211
	UNION
	SELECT *
	FROM APU0000717311
	UNION
	SELECT *
	FROM APU0000FF1101
	UNION
	SELECT *
	FROM APU0000FS1101
	UNION
	SELECT *
	FROM APU0300703213
	UNION
	SELECT *
	FROM PCOCOUSDM;


-- Create Monthly REF table
INSERT INTO MONTH_REF (MONTHID, MONTH_NAME, MONTH_NAM)
VALUES (1, 'JANUARY','JAN'),
	(2, 'FEBRUARY','FEB'),
	(3, 'MARCH', 'MAR'),
	(4, 'APRIL', 'APR'),
	(5, 'MAY', 'MAY'),
	(6, 'JUNE', 'JUN'),
	(7, 'JULY', 'JUL'),
	(8, 'AUGUST', 'AUG'),
	(9, 'SEPTEMBER', 'SEPT'),
	(10, 'OCTOBER', 'OCT'), 
	(11, 'NOVEMBER', 'NOV'),
	(12, 'DECEMBER', 'DEC');


`````

![cookie-joins](https://github.com/vasquezme/how-to-sql/blob/main/images/cookie-monster.svg)


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
