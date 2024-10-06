# 30-day-SQL-queries
Welcome to the 30 Days of SQL Queries project! Each day, you'll find new SQL queries that progress from basic to advanced, covering topics like data retrieval, joins, aggregation, subqueries, window functions, CTE's and optimization.

Create  salaries table
CREATE TABLE Salaries (
emp_name VARCHAR(50),
department VARCHAR(50),
salary INT,
PRIMARY KEY (emp_name, department)
);



INSERT INTO Salaries (emp_name, 
					  department, salary) VALUES
('Kathy', 'Engineering', 50000),
('Roy', 'Marketing', 30000),
('Charles', 'Engineering', 45000),
('Jack', 'Engineering', 85000),
('Benjamin', 'Marketing', 34000),
('Anthony', 'Marketing', 42000),
('Edward', 'Engineering', 102000),
('Terry', 'Engineering', 44000),
('Evelyn', 'Marketing', 53000),
('Arthur', 'Engineering', 32000)



Q1: Write an SQL query to calculate the difference between the highest salaries in the marketing and engineering department. Output the absolute difference in salaries.
Using CTE and window function
      WITH dpt_salary AS(
      	SELECT department, salary,
      	ROW_NUMBER() OVER(PARTITION BY department ORDER BY salary DESC) as sal_rank
      	FROM salaries 
      )
      SELECT 
      	ABS(
      		MAX(CASE WHEN department = 'Engineering' THEN salary END)-
      		MAX(CASE WHEN department = 'Marketing' THEN salary END)
      	)as sal_diff
      FROM dpt_salary
      WHERE sal_rank <=1

   Links to the questions solved in DataLemur: 
   
  2Q:    https://datalemur.com/questions/click-through-rate - 
  3Q:    https://datalemur.com/questions/teams-power-users
         https://datalemur.com/questions/sql-page-with-no-likes
        


