# SQL Cheat Sheet: FUNCTIONS and Implicit JOIN

| Command | Syntax | Description | Example |
| --- | --- | --- | --- |
| **COUNT** | `SELECT COUNT(column_name) FROM table_name WHERE condition;` | Returns the number of rows that match a specified criterion. | `SELECT COUNT(dep_id) FROM employees;` |
| **AVG** | `SELECT AVG(column_name) FROM table_name WHERE condition;` | Returns the average value of a numeric column. | `SELECT AVG(salary) FROM employees;` |
| **SUM** | `SELECT SUM(column_name) FROM table_name WHERE condition;` | Returns the total sum of a numeric column. | `SELECT SUM(salary) FROM employees;` |
| **MIN** | `SELECT MIN(column_name) FROM table_name WHERE condition;` | Returns the smallest value of the selected column. | `SELECT MIN(salary) FROM employees;` |
| **MAX** | `SELECT MAX(column_name) FROM table_name WHERE condition;` | Returns the largest value of the selected column. | `SELECT MAX(salary) FROM employees;` |
| **ROUND** | `SELECT ROUND(2number, decimals, operation) AS RoundValue;` | Rounds a number to a specified number of decimal places. | `SELECT ROUND(salary) FROM employees;` |
| **LENGTH** | `SELECT LENGTH(column_name) FROM table;` | Returns the length of a string (in bytes). | `SELECT LENGTH(f_name) FROM employees;` |
| **UCASE** | `SELECT UCASE(column_name) FROM table;` | Displays the column name in uppercase. | `SELECT UCASE(f_name) FROM employees;` |
| **LCASE** | `SELECT LCASE(column_name) FROM table;` | Displays the column name in lowercase. | `SELECT LCASE(f_name) FROM employees;` |
| **DISTINCT** | `SELECT DISTINCT column_name FROM table;` | Displays data without duplicates. | `SELECT DISTINCT UCASE(f_name) FROM employees;` |
| **DAY** | `SELECT DAY(column_name) FROM table;` | Returns the day of the month for a given date. | `SELECT DAY(b_date) FROM employees where emp_id = 'E1002';` |
| **CURRENT_DATE** | `SELECT CURRENT_DATE;` | Displays the current date. | `SELECT CURRENT_DATE;` |
| **DATEDIFF()** | `SELECT DATEDIFF(date1, date2);` | Calculates the difference between two dates or time stamps. | `SELECT DATEDIFF(CURRENT_DATE, date_column) FROM table;` |
| **FROM_DAYS()** | `SELECT FROM_DAYS(number_of_days);` | Converts a given number of days to YYYY-MM-DD format. | `SELECT FROM_DAYS(DATEDIFF(CURRENT_DATE, date_column)) FROM table;` |
| **DATE_ADD()** | `SELECT DATE_ADD(date, INTERVAL n type);` | Calculates the date after a specified number of units. | `SELECT DATE_ADD(date, INTERVAL 3 DAY);` |
| **DATE_SUB()** | `SELECT DATE_SUB(date, INTERVAL n type);` | Calculates the date before a specified number of units. | `SELECT DATE_SUB(date, INTERVAL 3 DAY);` |
| **Subquery** | `SELECT column_name [, column_name ] FROM table1 [, table2 ] WHERE column_name OPERATOR (SELECT column_name [, column_name ] FROM table1 [, table2 ] [WHERE]);` | A query within another SQL query embedded within the WHERE clause. | Example 1:<br/>`SELECT emp_id, f_name, l_name, salary FROM employees WHERE salary < (SELECT AVG(salary) FROM employees);`<br/><br/>Example 2:<br/>`SELECT * FROM (SELECT emp_id, f_name, l_name, dep_id FROM employees) AS emp4all;`<br/><br/>Example 3:<br/>`SELECT * FROM employees WHERE job_id IN (SELECT job_ident FROM jobs);` |
| **Implicit Inner Join** | `SELECT column_name(s) FROM table1, table2 WHERE table1.column_name = table2.column_name;` | Combines records and displays matching values in both tables. Inner join applies only to specified columns. | `SELECT * FROM employees, jobs WHERE employees.job_id = jobs.job_ident;` |
| **Implicit Cross Join** | `SELECT column_name(s) FROM table1, table2;` | Cartesian product where rows in the first table are multiplied by rows in the second table. | `SELECT * FROM employees, jobs;` |
