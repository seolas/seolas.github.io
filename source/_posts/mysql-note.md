---
title: MySQL 笔记
date: 2024-01-24 21:41:58
tags:
- MySQL
---

## SELECT

```sql
-- 1. 基本的 SELECT 语句 

SELECT *
FROM employees;

SELECT employee_id, last_name, salary
FROM employees;

SELECT * 
FROM departments;

SELECT department_id, department_name
FROM departments;

#空值问题 : 空值参与运算结果还是空值
#列的别名：SQL 中只有给列起别名时使用双引号
SELECT employee_id id, last_name "name", salary, commission_pct, salary * 12 * (1 + IFNULL(commission_pct, 0)) AS "annual sal"
FROM employees;

#显示表结构
DESCRIBE employees;
DESC departments;
```

## WHERE 过滤

```sql
-- 2. WHERE 过滤

-- WHERE 子句紧跟 FROM 子句
SELECT *
FROM employees
WHERE department_id = 90;

SELECT employee_id, last_name, salary
FROM employees
WHERE salary > 10000;

-- SQL 中日期型和字符型必须使用单引号
SELECT employee_id, last_name, salary
FROM employees
WHERE last_name = 'King';

SELECT employee_id, last_name, salary, department_id
FROM employees
-- where department_id <> 90;
WHERE department_id != 90;

#其他比较运算符
-- BETWEEN ... AND ... (包含边界)
SELECT employee_id, last_name, salary
FROM employees
WHERE salary >= 6000 AND salary <= 8000;   

SELECT employee_id, last_name, salary
FROM employees
WHERE salary BETWEEN 6000 AND 8000;

-- in(..., ..., ...) : 等于值列表中的任意一个
SELECT employee_id, last_name, salary, department_id
FROM employees
WHERE department_id = 60 OR department_id = 80 OR department_id = 90;

SELECT employee_id, last_name, salary, department_id
FROM employees
WHERE department_id IN(60, 80, 90);

-- like 模糊查询

-- % : 零个或多个的任意字符

SELECT employee_id, last_name, salary
FROM employees
WHERE last_name LIKE '%e%';

--  _ : 表示1个任意字符

SELECT employee_id, last_name, salary
FROM employees
WHERE last_name LIKE '__e%';

/*update employees
set last_name = 'De_Haan'
where employee_id = 102;*/


SELECT employee_id, last_name, salary
FROM employees
WHERE last_name LIKE '%$_%' ESCAPE '$'; 

SELECT employee_id, last_name, salary
FROM employees
WHERE last_name LIKE '%e%a%' OR last_name LIKE '%a%e%';

-- is (not) null 空(非空)值
SELECT employee_id, last_name, salary, commission_pct
FROM employees
WHERE commission_pct IS NOT NULL;
```

## ORDER BY 排序

```sql
-- 3. ORDER BY 排序

SELECT employee_id, last_name, salary
FROM employees
-- order by salary asc; -- 升序 （默认排序方式）
ORDER BY salary DESC; -- 降序

-- ORDER BY 写在 SELECT 子句的末尾
SELECT employee_id, last_name, salary
FROM employees
WHERE salary BETWEEN 6000 AND 8000
ORDER BY salary DESC;

-- 按别名排序
SELECT employee_id, last_name, salary, salary * 12 * (1 + commission_pct) annual_salary
FROM employees
ORDER BY annual_salary DESC;

-- 多列排序
SELECT employee_id, last_name, salary
FROM employees
ORDER BY salary DESC, employee_id DESC, last_name;
```

```sql
SELECT last_name , job_id , salary AS sal
FROM employees; 

SELECT employee_id , last_name,
salary * 12  "ANNUAL  SALARY"
FROM employees;

-- 4.显示表departments的结构，并查询其中的全部数据
DESC departments;

SELECT * FROM departments;

-- 5.显示出表employees中的全部job_id（不能重复）
SELECT DISTINCT job_id
FROM employees;

-- 6.显示出表employees的全部列，各个列之间用逗号连接，列头显示成OUT_PUT
SELECT CONCAT(employee_id, ',', last_name, ',', salary) OUT_PUT
FROM employees;

```

```sql
-- 1.查询工资大于12000的员工姓名和工资
SELECT last_name, salary
FROM employees
WHERE salary > 12000;

-- 2.查询员工号为176的员工的姓名和部门号
SELECT last_name, department_id
FROM employees
WHERE employee_id = 176;

-- 3.选择工资不在5000到12000的员工的姓名和工资
SELECT last_name, salary
FROM employees
WHERE salary < 5000 OR salary > 12000;

SELECT last_name, salary
FROM employees
WHERE salary NOT BETWEEN 5000 AND 12000;

-- 4.选择在20或50号部门工作的员工姓名和部门号
SELECT last_name, department_id
FROM employees
WHERE department_id IN (20, 50);

SELECT last_name, department_id
FROM employees
WHERE department_id = 20 OR department_id = 50;

-- 5.选择公司中 没有管理者 的员工姓名及job_id
SELECT last_name, job_id
FROM employees
WHERE manager_id IS NULL;

-- 6.选择公司中有奖金的员工姓名，工资和奖金级别
SELECT last_name, salary, commission_pct
FROM employees
WHERE commission_pct IS NOT NULL;

-- 7.选择员工姓名的 第三个字母是a 的员工姓名
SELECT last_name
FROM employees
WHERE last_name LIKE '__a%';

-- 8.选择姓名中有字母a和e的员工姓名
SELECT last_name
FROM employees
WHERE last_name LIKE '%a%e%' OR last_name LIKE '%e%a%';

SELECT last_name
FROM employees
WHERE last_name LIKE '%a%' AND last_name LIKE '%e%';
```

## 多表连接查询

```sql
-- 6. 多表连接查询

/*
按查询情况不同

等值连接 - 非等值连接
内连接 - 外连接
自连接 - 非自连接
*/

-- 问题：当完成多表连接查询时，若不提供表之间的连接条件，将发生笛卡尔集的问题
SELECT employee_id, department_name
FROM employees, departments; -- 2889 

SELECT *
FROM employees; -- 107

SELECT *
FROM departments; -- 27

SELECT 107 * 27;

-- 解决：提供表之间的连接条件
SELECT employee_id, department_name
FROM employees, departments
WHERE employees.`department_id` = departments.`department_id`; -- 106

-- 若完成 n 个表之间的连接查询，至少 n - 1 个连接条件
SELECT employee_id, department_name, city
FROM employees, departments, locations
WHERE employees.`department_id` = departments.`department_id`
AND departments.`location_id` = locations.`location_id`;

SELECT employee_id, department_name
FROM employees, departments
WHERE employees.`department_id` = departments.`department_id`
AND employees.`manager_id` = departments.`manager_id`;

-- 表的别名
SELECT e.employee_id, d.department_name, city, e.department_id
FROM employees e, departments d, locations l
WHERE e.`department_id` = d.`department_id`
AND d.`location_id` = l.`location_id`;

/*use myemployees;

CREATE TABLE job_grades
(grade_level VARCHAR(3),
 lowest_sal  int(6),
 highest_sal int(6));

INSERT INTO job_grades
VALUES ('A', 1000, 2999);

INSERT INTO job_grades
VALUES ('B', 3000, 5999);

INSERT INTO job_grades
VALUES('C', 6000, 9999);

INSERT INTO job_grades
VALUES('D', 10000, 14999);

INSERT INTO job_grades
VALUES('E', 15000, 24999);

INSERT INTO job_grades
VALUES('F', 25000, 40000);*/


SELECT *
FROM job_grades;

-- 非等值连接
SELECT employee_id, last_name, salary, grade_level
FROM employees e, job_grades j
WHERE salary BETWEEN j.`lowest_sal` AND j.`highest_sal`;

-- SQL99语法

-- 内连接：将所有满足条件的数据查询出来
-- INNER JOIN ... ON ...
SELECT employee_id, department_name
FROM employees e
INNER JOIN departments d -- INNER 可以省略不写
ON e.`department_id` = d.`department_id`;

SELECT employee_id, department_name, city
FROM employees e
JOIN departments d
ON e.`department_id` = d.`department_id`
JOIN locations l
ON d.`location_id` = l.`location_id`;

-- 外连接

-- 左外连接 ：不仅将满足条件的数据查询出来，还将 “左表” 中不满足条件的数据也查询出来
SELECT employee_id, department_name
FROM employees e 
LEFT OUTER JOIN departments d  -- OUTER 可以省略不写
ON e.`department_id` = d.`department_id`;


-- 右外连接 ：不仅将满足条件的数据查询出来，还将 “右表” 中不满足条件的数据也查询出来
SELECT employee_id, department_name
FROM employees e 
RIGHT JOIN departments d
ON e.`department_id` = d.`department_id`;

-- 满外连接：Oracle 数据库中使用 FULL OUTER JOIN ... ON ... MySQL 数据库不支持，需要使用关键 UNION
SELECT employee_id, department_name
FROM employees e 
LEFT OUTER JOIN departments d  -- OUTER 可以省略不写
ON e.`department_id` = d.`department_id`
UNION
SELECT employee_id, department_name
FROM employees e 
RIGHT JOIN departments d
ON e.`department_id` = d.`department_id`;

-- 自连接
-- xxx works for xxx
SELECT CONCAT(emp.last_name, ' works for ', mgr.last_name)
FROM employees emp, employees mgr
WHERE emp.`manager_id` = mgr.`employee_id`;

```

```sql
-- 1.显示所有员工的 姓名，部门号和部门名称。
SELECT last_name, e.department_id, department_name
FROM employees e
INNER JOIN departments d
ON e.`department_id` = d.`department_id`;


SELECT last_name, e.department_id, department_name
FROM employees e, departments d
WHERE e.`department_id` = d.`department_id`;


-- 2.查询90号部门员工的job_id和90号部门的location_id
SELECT e.job_id, d.department_id, d.location_id
FROM employees e
JOIN departments d
ON e.`department_id` = d.`department_id`
WHERE d.`department_id` = 90;

SELECT e.job_id, d.department_id, d.location_id
FROM employees e, departments d
WHERE e.`department_id` = d.`department_id`
AND d.`department_id` = 90;


-- 3.选择 所有有奖金的 员工的 last_name , department_name , location_id , city
SELECT e.last_name, d.department_name, l.location_id, l.city
FROM employees e, departments d, locations l
WHERE e.`department_id` = d.`department_id`
AND d.`location_id` = l.`location_id`
AND commission_pct IS NOT NULL;

SELECT e.last_name, d.department_name, l.location_id, l.city
FROM employees e
JOIN departments d 
ON e.`department_id` = d.`department_id`
JOIN locations l
ON d.`location_id` = l.`location_id`
WHERE commission_pct IS NOT NULL; 


-- 4.选择 city在Toronto 工作的员工的 last_name , job_id , department_id , department_name 
SELECT e.last_name , e.job_id , e.department_id , d.department_name 
FROM employees e, departments d, locations l
WHERE e.`department_id` = d.`department_id`
AND d.`location_id` = l.`location_id`
AND l.`city` = 'Toronto';

SELECT e.last_name , e.job_id , e.department_id , d.department_name 
FROM employees e
JOIN departments d
ON e.`department_id` = d.`department_id`
JOIN locations l
ON d.`location_id` = l.`location_id`
WHERE l.`city` = 'Toronto';

 
-- 5.选择指定员工的姓名，员工号，以及他的管理者的姓名和员工号，结果类似于下面的格式
-- employees	Emp#	manager	 Mgr#
-- kochhar	101	king	 100
SELECT e.last_name employees, e.employee_id "Emp#", m.last_name manager, m.employee_id "Mgr#"
FROM employees e, employees m
WHERE e.manager_id = m.employee_id;

SELECT e.last_name employees, e.employee_id "Emp#", m.last_name manager, m.employee_id "Mgr#"
FROM employees e
JOIN employees m
ON e.manager_id = m.employee_id;
```

## 单行函数

```sql
-- 2. 单行函数

-- 日期型
SELECT NOW();

-- 字符型
SELECT LOWER('HelloWorld'), UPPER('HelloWorld');

SELECT LOWER(last_name), UPPER(last_name)
FROM employees;

/*CONCAT('Hello', 'World')
SUBSTR('HelloWorld',1,5)
LENGTH('HelloWorld')
INSTR('HelloWorld', 'W')
LPAD(salary,10,'*')
RPAD(salary, 10, '*')
TRIM('H' FROM 'HelloWorld')
REPLACE('abcd','b','m')*/

SELECT REPLACE('abcdabababab','b','mmmm');

SELECT TRIM('p' FROM 'HelloHHWorldHHH');

SELECT LPAD(salary,10,'0'), RPAD(salary, 10, '*')
FROM employees;

-- 获取指定字符在字符串中的索引位置, 没有指定字符返回0
SELECT INSTR('HelloWorld', 'p');

SELECT LENGTH('HelloWorld');

-- SQL 中索引值从 1 开始
-- 从第几个索引位置开始截取，截取几个
SELECT SUBSTR('HelloWorld', 2, 5);

SELECT CONCAT('Hello', 'World');

SELECT CONCAT(last_name, first_name)
FROM employees;

-- 数值型
SELECT ROUND(123.456, 2), ROUND(123.556, 0), ROUND(153.456, -2);

SELECT TRUNCATE(123.456, 2), TRUNCATE(123.556, 0), TRUNCATE(153.456, -2);

SELECT MOD(15, 7);

-- 练习：查询部门号为 10, 20, 30 的员工信息, 若部门号为 10, 
-- 则打印其工资的 1.1 倍, 20 号部门, 则打印其工资的 1.2 倍, 
-- 30 号部门打印其工资的 1.3 倍数
SELECT employee_id, last_name, salary, department_id, CASE department_id WHEN 10 THEN salary * 1.1
									 WHEN 20 THEN salary * 1.2
									 WHEN 30 THEN salary * 1.3
									 END "new_salary"
FROM employees
WHERE department_id IN (10, 20, 30);

-- 练习：查询 所有 的员工信息, 若部门号为 10, 
-- 则打印其工资的 1.1 倍, 20 号部门, 则打印其工资的 1.2 倍, 
-- 30 号部门打印其工资的 1.3 倍数，其他的打印工资的 1.4 倍

SELECT employee_id, last_name, salary, department_id, CASE department_id WHEN 10 THEN salary * 1.1
									 WHEN 20 THEN salary * 1.2
									 WHEN 30 THEN salary * 1.3
									 ELSE salary * 1.4
									 END "new_salary"
FROM employees;
```

```sql
-- 1.显示系统时间(注：日期+时间)
SELECT NOW();


-- 2.查询员工号，姓名，工资，以及 工资提高百分之20%后 的结果（new salary）
SELECT employee_id, last_name, salary, salary * 1.2 "new salary"
FROM employees;


-- 3.将员工的姓名按首字母排序，并写出姓名的长度（length）
SELECT last_name, LENGTH(last_name)
FROM employees
ORDER BY last_name;


-- 4.做一个查询，产生下面的结果 <last_name> earns <salary> monthly but wants <salary*3>
-- 		Dream Salary
-- King earns 24000 monthly but wants 72000
SELECT CONCAT(last_name, ' earns ', TRUNCATE(salary, 0), ' monthly but wants ', TRUNCATE(salary * 3, 0)) "Dream Salary"
FROM employees;


-- 5.使用case-when，按照下面的条件：
-- job                  grade
-- AD_PRES            	A
-- ST_MAN             	B
-- IT_PROG             	C
-- SA_REP              	D
-- ST_CLERK           	E

-- 产生下面的结果
-- Last_name	Job_id		Grade
-- king		AD_PRES		A

SELECT last_name "Last_name", job_id "Job_id", CASE job_id WHEN 'AD_PRES' THEN 'A'
							   WHEN 'ST_MAN' THEN 'B'
							   WHEN 'IT_PROG' THEN 'C'
							   WHEN 'SA_REP' THEN 'D'
							   WHEN 'ST_CLERK' THEN 'E'
							   ELSE 'F'
							   END "Grade"
FROM employees;
```

## 分组函数

```sql
-- 4. 分组函数（多行函数）

-- AVG() COUNT() SUM() MAX() MIN()

SELECT AVG(salary), COUNT(salary), SUM(salary), MAX(salary), MIN(salary)
FROM employees;

SELECT MAX(last_name), MIN(last_name), MAX(LENGTH(last_name))
FROM employees;

SELECT COUNT(employee_id)
FROM employees;

SELECT COUNT(*)
FROM employees;

-- 组函数都不计算空值
SELECT COUNT(commission_pct)
FROM employees;

SELECT AVG(commission_pct), SUM(commission_pct) / COUNT(commission_pct)
FROM employees;
```

## GROUP BY 分组

```sql
-- 5. GROUP BY 分组（重点）

SELECT AVG(salary)
FROM employees;

#求出公司中 各个部门 的平均工资
SELECT AVG(salary), department_id
FROM employees
GROUP BY department_id;

-- 出现在 SELECT 子句后的非分组函数，一定出现在 GROUP BY 子句后
SELECT employee_id, AVG(salary), department_id
FROM employees
GROUP BY department_id, employee_id; -- 多级分组

#求出 各个部门中 每个工种（job_id）的平均工资
SELECT AVG(salary), department_id, job_id
FROM employees
GROUP BY department_id, job_id;

-- WHERE 子句不能过滤组函数，若需要过滤组函数使用 HAVING
SELECT AVG(salary)
FROM employees
GROUP BY department_id
HAVING AVG(salary) > 8000;

SELECT MAX(salary)
FROM employees
GROUP BY department_id
HAVING MAX(salary) > 10000;

-- MySQL 中组函数不能嵌套，但是 Oracle 中可以
SELECT MAX(AVG(salary))
FROM employees
GROUP BY department_id;

SELECT AVG(salary)
FROM employees
GROUP BY department_id;

SELECT MAX(avg_sal)
FROM (
	SELECT AVG(salary) avg_sal
	FROM employees
	GROUP BY department_id
) e;
```

```sql
-- 1.where子句可否使用组函数进行过滤?  NO

-- 2.查询公司员工工资的最大值，最小值，平均值，总和
SELECT MAX(salary), MIN(salary), AVG(salary), SUM(salary)
FROM employees;

-- 3.查询各job_id的员工工资的最大值，最小值，平均值，总和
SELECT MAX(salary), MIN(salary), AVG(salary), SUM(salary)
FROM employees
GROUP BY job_id;

-- 4.选择具有各个job_id的员工人数
SELECT job_id, COUNT(job_id)
FROM employees
GROUP BY job_id;


-- 5.查询员工最高工资和最低工资的差距（DIFFERENCE）
SELECT MAX(salary) - MIN(salary) "DIFFERENCE"
FROM employees;


-- 6.查询各个管理者手下员工的最低工资，其中最低工资不能低于6000，没有管理者的员工不计算在内
SELECT MIN(salary)
FROM employees
WHERE manager_id IS NOT NULL
GROUP BY manager_id
HAVING MIN(salary) > 6000;


-- 7.查询所有部门的名字，location_id，员工数量和工资平均值
SELECT department_name, location_id, COUNT(employee_id), AVG(salary)
FROM employees e
JOIN departments d
ON e.`department_id` = d.`department_id`
GROUP BY department_name, location_id;
```

## 子查询

```sql
-- 7. 子查询

-- 谁的工资比 Abel 高?

SELECT salary
FROM employees
WHERE last_name = 'Abel';

SELECT employee_id, last_name, salary
FROM employees
WHERE salary > 11000;

-- 主查询(外查询)
SELECT employee_id, last_name, salary
FROM employees
WHERE salary > (
	-- 子查询(内查询)
	SELECT salary
	FROM employees
	WHERE last_name = 'Abel'
);

-- 题目：返回job_id与141号员工相同，salary比143号员工多的 员工姓名，job_id 和工资

SELECT last_name, job_id, salary
FROM employees
WHERE job_id = (
	SELECT job_id
	FROM employees
	WHERE employee_id = 141
) AND salary > (
	SELECT salary
	FROM employees
	WHERE employee_id = 143
);


-- 题目：返回公司工资最少的员工的last_name,job_id和salary

SELECT last_name, job_id, salary
FROM employees
WHERE salary = (
	SELECT MIN(salary)
	FROM employees
);

-- 题目：查询 最低工资 大于 50号部门最低工资 的部门id和其最低工资

SELECT department_id, MIN(salary)
FROM employees
GROUP BY department_id
HAVING MIN(salary) > (
	SELECT MIN(salary)
	FROM employees
	WHERE department_id = 50
);

-- 非法使用子查询
SELECT employee_id, last_name
FROM   employees
WHERE  salary =
                (SELECT   MIN(salary)
                 FROM     employees
                 GROUP BY department_id);

-- 子查询的空值问题
SELECT last_name, job_id
FROM   employees
WHERE  job_id =
                (SELECT job_id
                 FROM   employees
                 WHERE  last_name = 'Haas');


-- 题目：返回 其它部门中 比 job_id为‘IT_PROG’部门 任一 工资低的员工的员工号、姓名、job_id 以及salary

-- any : 满足任意一个条件
SELECT employee_id, last_name, job_id, salary
FROM employees
WHERE salary < ANY(
	SELECT salary
	FROM employees
	WHERE job_id = 'IT_PROG'
) AND job_id <> 'IT_PROG';

-- 题目：返回其它部门中比job_id为‘IT_PROG’部门 所有 工资都低的员工的员工号、姓名、job_id 以及salary

-- all : 满足所有条件
SELECT employee_id, last_name, job_id, salary
FROM employees
WHERE salary < ALL(
	SELECT salary
	FROM employees
	WHERE job_id = 'IT_PROG'
) AND job_id <> 'IT_PROG';

SELECT employee_id, last_name, job_id, salary
FROM employees
WHERE salary IN(
	SELECT salary
	FROM employees
	WHERE job_id = 'IT_PROG'
) AND job_id <> 'IT_PROG';

```

```sql
-- 1.查询和Zlotkey相同部门的员工姓名
SELECT last_name
FROM employees
WHERE department_id = (
	SELECT department_id
	FROM employees
	WHERE last_name = 'Zlotkey'
);

-- 2.查询工资比公司平均工资高的员工的员工号，姓名和工资。
SELECT employee_id, last_name, salary
FROM employees
WHERE salary > (
	SELECT AVG(salary)
	FROM employees
);

-- 3.查询各部门中工资比 本 部门平均工资高的员工的员工号, 姓名和工资
SELECT e1.employee_id, e1.last_name, e1.salary
FROM employees e1
WHERE e1.`salary` > (
	SELECT AVG(e2.salary)
	FROM employees e2
	WHERE e2.`department_id` = e1.`department_id`
);

SELECT employee_id, last_name, salary
FROM employees e
JOIN (
	SELECT department_id, AVG(salary) avg_sal
	FROM employees
	GROUP BY department_id
) n
ON e.`department_id` = n.department_id
WHERE e.`salary` > n.avg_sal;

SELECT employee_id, last_name, salary
FROM employees e, (
	SELECT department_id, AVG(salary) avg_sal
	FROM employees
	GROUP BY department_id
) n
WHERE e.`department_id` = n.department_id
AND e.`salary` > n.avg_sal;

-- 4.查询和姓名中包含字母u的员工在相同部门的员工的员工号和姓名
SELECT employee_id, last_name
FROM employees
WHERE department_id = ANY(
	SELECT department_id
	FROM employees
	WHERE last_name LIKE '%u%'
);


-- 5.查询在部门的location_id为1700的部门工作的员工的员工号
SELECT employee_id
FROM employees
WHERE department_id IN(
	SELECT department_id
	FROM departments
	WHERE location_id = 1700
);


-- 6.查询管理者是King的  员工姓名和工资
SELECT last_name, salary 
FROM employees
WHERE manager_id IN (
	SELECT employee_id
	FROM employees
	WHERE last_name = 'King'
);
```

## 创建和管理表

```sql
-- 9. 创建和管理表

-- DDL ：数据定义语言

-- 1. 新建表 CREATE TABLE
-- 方式一：
CREATE TABLE emp1(
	id INT(10),
	`name` VARCHAR(20), 
	salary DOUBLE(10, 2),
	hire_date DATE
);

CREATE TABLE emp2(
	id INT(10) AUTO_INCREMENT,
	NAME VARCHAR(20),
	PRIMARY KEY(id)
);

-- 方式二：基于现有表创建新表(相当于表的复制)
CREATE TABLE emp3
AS
SELECT * FROM employees;

SELECT * FROM emp3;

DESC employees;
DESC emp3;

CREATE TABLE emp4
AS
SELECT employee_id, last_name, salary
FROM employees
WHERE department_id = 90;

SELECT * FROM emp4;

-- 基于现有表创建新表，但是不导入数据
CREATE TABLE emp5
AS
SELECT employee_id, last_name, salary
FROM employees
WHERE 1 = 2;

SELECT * FROM emp5;

-- 2. 修改表 ALTER TABLE

-- ①添加列
ALTER TABLE emp4
ADD gender VARCHAR(5);

ALTER TABLE emp4
ADD age INT(10) DEFAULT 0;

SELECT * FROM emp4;

-- ②修改列
ALTER TABLE emp4
MODIFY gender VARCHAR(20);

DESC emp4;


-- ③重命名列
ALTER TABLE emp4
CHANGE gender gender22 VARCHAR(10);

-- ④删除列
ALTER TABLE emp4
DROP COLUMN gender22;


-- 3. 重命名表
ALTER TABLE emp4
RENAME employees4;

SELECT * FROM employees4;


-- 4. 清空表
TRUNCATE TABLE emp4;


-- 5. 删除表
DROP TABLE employees4;


-- DML : 数据操纵语言
SELECT * FROM emp4;

DELETE FROM emp4; -- 删除表中所有的数据

DESC emp1;


-- 取消自动提交
SET autocommit = FALSE;


-- DCL : 数据控制语言

COMMIT; -- 提交


ROLLBACK; -- 回滚，默认回滚到上一次 commit

-- DDL 都是不可以回滚的，每一个 DDL 都自动 commit
```

```sql
-- 1.创建表dept1
-- name			type
-- id			int(7)
-- name			Varchar(25)

CREATE TABLE dept1(
	id INT(7),
	`name` VARCHAR(25)
);

SELECT * FROM dept1;
 
-- 2.将表departments中的数据插入新表dept2中
CREATE TABLE dept2
AS
SELECT * FROM departments;

DESC dept2;

SELECT * FROM dept2;

-- 3.创建表emp5
-- name			type
-- id			int(7)
-- First_name		Varchar(25)
-- Last_name		Varchar(25)
-- Dept_id		int(7)

CREATE TABLE emp5(
	id INT(7),
	first_name VARCHAR(25),
	last_name VARCHAR(25),
	dept_id INT(7)
);

DESC emp5;
 
-- 4.将列Last_name的长度增加到50
ALTER TABLE emp5
MODIFY last_name VARCHAR(50);

DESC emp5;


-- 5.根据表employees创建employees2
CREATE TABLE employees2
AS
SELECT * FROM employees;

DESC employees2;

SELECT * FROM employees2;

-- 6.删除表emp5
DROP TABLE emp5;

SELECT * FROM emp5;

-- 7.将表employees2重命名为emp5
ALTER TABLE employees2
RENAME emp5;


-- 8.在表dept和emp5中添加新列test_column，并检查所作的操作
ALTER TABLE dept1
ADD test_column VARCHAR(20);

DESC dept1;


-- 9.直接删除表emp5中的列 dept_id
ALTER TABLE emp5
DROP COLUMN test_column;
```

## 数据处理之增删改

```sql
-- 11. 数据处理之增删改

-- DDL ：数据定义语言
CREATE TABLE emp(
	id INT(10),
	NAME VARCHAR(20),
	salary DOUBLE(10, 2),
	hire_date DATE
);

-- DML ：数据操纵语言

-- 添加数据 INSERT INTO ... VALUES ...
INSERT INTO emp
VALUES(101, '张三', 9999.99, '1999-9-9');

INSERT INTO emp(id, `name`, hire_date)
VALUES(102, '李四', NOW());

#基于现有表导入数据
INSERT INTO emp(id, NAME, salary)
SELECT employee_id, last_name, salary
FROM employees
WHERE department_id = 90;


-- 修改数据 UPDATE ... SET ...
UPDATE emp
SET salary = 8888.88
WHERE id = 101;

#同时修改多列
UPDATE emp
SET salary = 9999.99, hire_date = '2000-10-10'
WHERE id = 100;

-- 删除数据 DELETE FROM ...
DELETE FROM emp
WHERE id = 100;

-- 查询数据
SELECT * FROM emp;
```

## 约束

```sql
-- 1. 约束

-- NOT NULL 非空约束，规定某个字段不能为空
CREATE TABLE emp1(
	id INT,
	NAME VARCHAR(20) NOT NULL  -- 列级约束
);

INSERT INTO emp1
VALUES(NULL, '李四');

SELECT * FROM emp1;

INSERT INTO emp1
VALUES(3111111111, '王五');

CREATE TABLE emp2(
	id INT,
	NAME VARCHAR(20)
);

INSERT INTO emp2
VALUES(101, NULL);

SELECT * FROM emp2;

#添加非空约束
ALTER TABLE emp2
MODIFY NAME VARCHAR(20) NOT NULL;

#删除非空约束
ALTER TABLE emp2
MODIFY NAME VARCHAR(20) NULL;

-- UNIQUE  唯一约束，规定某个字段在整个表中是唯一的
CREATE TABLE emp3(
	id INT,
	NAME VARCHAR(20),
	phone VARCHAR(20),
	CONSTRAINT emp3_phone_un UNIQUE(phone) -- 表级约束
);

SELECT * FROM emp3;

INSERT INTO emp3
VALUES(102, '张三2', '1234567');

#组合唯一约束
CREATE TABLE emp4(
	id INT,
	NAME VARCHAR(20),
	phone VARCHAR(25),
	email VARCHAR(25),
	CONSTRAINT emp4_phoneAndEmail_un UNIQUE(phone, email)
);

SELECT * FROM emp4;

INSERT INTO emp4
VALUES(102, '张三', '12345677777', 'zhangs666@abc.com');

#添加唯一约束
ALTER TABLE emp4
ADD CONSTRAINT emp4_name_un UNIQUE(NAME);

#删除唯一约束
ALTER TABLE emp4
DROP INDEX emp4_name_un;

-- PRIMARY KEY 主键(非空且唯一):通常使用主键去确定唯一一条数据
CREATE TABLE emp5(
	id INT,
	NAME VARCHAR(20),
	CONSTRAINT emp5_id_pk PRIMARY KEY(id)
);

SELECT * FROM emp5;

INSERT INTO emp5
VALUES(NULL, '张三22');

DELETE FROM emp5 WHERE id = 101;

#添加主键约束
ALTER TABLE emp5
ADD CONSTRAINT emp5_id_pk PRIMARY KEY(id);

#删除主键约束
ALTER TABLE emp5
DROP PRIMARY KEY;

ALTER TABLE emp5
MODIFY id INT NULL;

-- FOREIGN KEY 外键约束：外键关联另一个表的主键，出现在外键表中的数据一定出现在主键表中

CREATE TABLE dept1(
	dept_id INT PRIMARY KEY,
	dept_name VARCHAR(20)
);

CREATE TABLE emp6(
	id INT PRIMARY KEY,
	NAME VARCHAR(20),
	depart_id INT,
	CONSTRAINT emp6_depart_id_fk FOREIGN KEY(depart_id) REFERENCES dept1(dept_id)
	-- ON DELETE CASCADE -- (级联删除): 当父表中的列被删除时，子表中相对应的列也被删除
	ON DELETE SET NULL -- (级联置空): 子表中相应的列置空
);

SELECT * FROM dept1;

SELECT * FROM emp6;

INSERT INTO dept1
VALUES(10, 'IT');

INSERT INTO emp6
VALUES(102, '张三', 10);

DELETE FROM emp6
WHERE id = 101;

DELETE FROM emp6
WHERE depart_id = 10;

#添加外键约束
ALTER TABLE emp6
ADD CONSTRAINT emp6_depart_id_fk FOREIGN KEY(depart_id) REFERENCES dept1(dept_id);

#删除外键约束
ALTER TABLE emp6
DROP CONSTRAINT emp6_depart_id_fk;

-- CHECK 检查约束, MySQL5.7 之间都不支持，MySQL 8.0 支持
CREATE TABLE emp7(
	id INT,
	NAME VARCHAR(20),
	salary DOUBLE(10, 2),
	CONSTRAINT emp7_salary_ck CHECK(salary > 3000)
);

SELECT * FROM emp7;

INSERT INTO emp7
VALUES(101, '张三', 2000);

```

## 分页

```sql
-- 2. 分页

-- 公式：（当前页数-1）*每页条数，每页条数
SELECT employee_id, last_name, salary
FROM employees
ORDER BY salary DESC
LIMIT 20, 10;

-- MySQL8.0 中的 row_number 窗口函数

-- 去重
SELECT department_id, last_name, salary
FROM (
	SELECT row_number() over(PARTITION BY department_id) rownum, department_id, last_name, salary
	FROM employees
) t
WHERE t.rownum = 1;

SELECT *
FROM (
	SELECT row_number() over(PARTITION BY department_id ORDER BY salary DESC) rownum, department_id, last_name, salary
	FROM employees
) t
WHERE t.rownum <= 3;
```

```sql
CREATE TABLE emp(
	emp_id INT PRIMARY KEY AUTO_INCREMENT,
	emp_name VARCHAR(30),
	salary DOUBLE(10, 2),
	birthday DATE
);

SELECT * FROM emp;

INSERT INTO emp(emp_name, salary, birthday)
VALUES('马云', 123.56, '1999-9-9'),
('马化腾', 222.22, '2000-10-10'),
('李彦宏', 333.33, '1988-8-8');

ALTER TABLE emp
ADD telephone VARCHAR(30);

ALTER TABLE emp
ADD depart_id_fk INT;

CREATE TABLE depart(
	depart_id INT PRIMARY KEY AUTO_INCREMENT,
	depart_name VARCHAR(20)
);

ALTER TABLE emp
ADD CONSTRAINT emp_depart_id_fk FOREIGN KEY(depart_id_fk) REFERENCES depart(depart_id);

SELECT * FROM emp;
SELECT * FROM depart;

DELETE FROM emp
WHERE emp_id = 5;

UPDATE emp
SET salary = salary + 200, telephone = '1234365789'
WHERE emp_id = 17;

SELECT * FROM emp WHERE emp_id = 17;

SELECT * FROM emp;

SELECT birthday, telephone
FROM emp
WHERE emp_name = 'Linda';

SELECT emp_name, salary
FROM emp
WHERE salary > 2000 AND salary < 5000;

SELECT emp_name, salary
FROM emp
WHERE salary BETWEEN 2000 AND 5000;

SELECT COUNT(*)
FROM emp
WHERE salary > 3000;

SELECT *
FROM emp
WHERE salary IN(1000, 3000, 5000);

SELECT *
FROM emp
WHERE emp_name LIKE '%o%';

SELECT *
FROM emp
WHERE telephone IS NULL;

SELECT salary
FROM emp e
JOIN depart d
ON e.`depart_id_fk` = d.`depart_id`
WHERE d.`depart_name` = 'Sales'
ORDER BY salary;

SELECT *
FROM emp
LIMIT 0, 10;
```

```sql
```

```sql
```