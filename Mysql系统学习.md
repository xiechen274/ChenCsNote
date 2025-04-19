



# SQL练习

`1.查询公司入职超过一万天的员工姓名和入职时间`

```mysql
SELECT last_name, hire_date 
FROM employees 
WHERE DATEDIFF(CURRENT_DATE, hire_date) > 10000;

```

- `DATEDIFF(CURRENT_DATE, hire_date)`：计算当前日期 (`CURRENT_DATE`) 与员工入职日期 (`hire_date`) 之间的天数。
- `WHERE ... > 10000`：筛选出入职时间超过 10,000 天的员工

`2.查询管理者手下员工最低的工资，最低工资不能低于6000，没有管理者的员工不在计算内`

```mysql
SELECT MIN(salary) AS min_salary, manager_id
FROM employees
WHERE manager_id IS NOT NULL
GROUP BY manager_id
HAVING MIN(salary) >= 6000;
	
```

- `SELECT MIN(salary) AS min_salary, manager_id`：选择每个 `manager_id` 下员工的最低工资，并将其命名为 `min_salary`。
- `WHERE manager_id IS NOT NULL`：排除没有管理者的员工。
- `GROUP BY manager_id`：按 `manager_id` 分组。
- `HAVING MIN(salary) >= 6000`：确保每个管理者手下员工的最低工资不低于 6000。

`3.查询所有部门的名字，location_id，员工数量和平均工资，并按平均工 资降序`

所有部门的名字，location_id,根据这个得出需要按这两个列分组

```mysql
SELECT department_name, location_id, COUNT(employee_id), AVG(salary) avg_sal
FROM employees e RIGHT JOIN departments d
ON e.`department_id` = d.`department_id`
GROUP BY department_name, location_id
ORDER BY avg_sal DESC;
```

`查找最晚入职员工的所有信息`

这道题设计了最晚日期的查询，一开始的思路是将标准时间戳转换为DAY的数目，忽略了MAX可以直接比较天数。。。

```mysql
SELECT *
FROM employees
WHERE hire_date = (SELECT MAX(hire_date) FROM employees);
```



# 1.基础语法



## 0.基础基础

Mysql的启动

- 可以直接依赖第三方的可视化工具
- 或者直接在终端中输入Mysql  -uroot -p,再根据提示输入密码（**密码是手机号**）



### 注释相关

在 MySQL 中，`#` 和 `--` 都可以用来添加注释，但它们有一些细微的区别：

1. **`#`注释：**
   - `#` 注释的风格源自 Unix shell 脚本。
   - 它只能用于单行注释。
   - 示例：
     ```sql
     SELECT * FROM users; # 这是一个注释
     ```

2. **`--`注释：**
   - `--` 是 SQL 标准中的注释风格。
   - 在 MySQL 中，`--` 必须紧跟至少一个空格或制表符才能生效。
   - 它也只能用于单行注释。
   - 示例：
     ```sql
     SELECT * FROM users; -- 这是一个注释
     ```

总结：
- 使用 `#` 时，无需在符号后面加空格。
- 使用 `--` 时，必须在符号后面加一个空格或制表符。

这两种方式都只能用于单行注释，如果需要多行注释，可以使用 `/* ... */`：

```sql
/*
这是一个多行注释
它可以跨越多行
*/
SELECT * FROM users;
```

在实际使用中，根据个人或团队的习惯选择合适的注释方式即可。



## 1.order by

```mysql


select
  name,
  age,
  score
from
  student
order by 
--按照成绩降序列（desc），成绩相同就升序（asc）
  score desc, 
  age asc;
```

## 2.limit

```sql
select
  name,
  age
from
  student
order by
--下表是类似数组的下表
--下面的意思是从第二条开始获取三条
  age asc limit 1,3;
	
```

## 3.分支语句

![image-20240530183756713](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240530183756713.png)

​	假设有一个学生表 `student`，包含以下字段：`name`（姓名）、`age`（年龄）。请你编写一个 SQL 查询，将学生按照年龄划分为三个年龄等级（age_level）：60 岁以上为 "老同学"，20 岁以上（不包括 60 岁以上）为 "年轻"，20 岁及以下、以及没有年龄信息为 "小同学"。

返回结果应包含学生的姓名（name）和年龄等级（age_level），并按姓名升序排序。

```mysql
--这道题很综合
select
  name,
 --对age的查询条件做分支
  case
    when (
      age < 20
      or age is null
      or age = ''
    ) then '小同学'
    when (age > 60) then '老同学'
    else '年轻'
  end as age_level
from
  student
order by
  name asc;
```

## 4.聚合函数

常见的聚合函数包括：

- COUNT：计算指定列的行数或非空值的数量。
- SUM：计算指定列的数值之和。
- AVG：计算指定列的数值平均值。
- MAX：找出指定列的最大值。**MAX可以自动转换标准的日期时间戳用于比较日期**！！
- MIN：找出指定列的最小值。

```mysql
/*
假设有一个学生表 student，包含以下字段：id（学号）、name（姓名）、class_id（班级编号）、score（成绩）。请你编写一个 SQL 查询，汇总学生表中所有学生的总成绩（total_score）、平均成绩（avg_score）、最高成绩（max_score）和最低成绩（min_score）。
 */
select
  sum(score) as total_score,
  avg(score) as avg_score,
  max(score) as max_score,
  min(score) as min_score
from
  student
```

## 5.多个Group-By

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240602175320106.png" alt="image-20240602175320106" style="zoom:50%;" />

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240531115615957.png" alt="image-20240531115615957" style="zoom:50%;" />

查询结果

| customer_id | product_id | total_amount |
| ----------- | ---------- | ------------ |
| A001        | 1          | 250          |
| A001        | 2          | 50           |
| A002        | 1          | 200          |
| A003        | 1          | 50           |

```mysql
/*假设有一个学生表 student，包含以下字段：id（学号）、name（姓名）、class_id（班级编号）、exam_num（考试次数）、score（成绩）。请你编写一个 SQL 查询，统计学生表中的班级编号（class_id），考试次数（exam_num）和每个班级每次考试的总学生人数（total_num）*/
select
  class_id,
  exam_num,
  count(*) as total_num
from
  student
group by
  class_id,
  exam_num;
```

使用group之后可以可以加上with rollup关键字计算合并分组的数量

```mysql
SELECT department_id,AVG(salary)
FROM employees
WHERE department_id > 80
GROUP BY department_id WITH ROLLUP;
/*注意:
当使用ROLLUP时，不能同时使用ORDER BY子句进行结果排序，即ROLLUP和ORDER BY是互相排斥的。*/
```



## 6.Having

***HAVING语句只能在分组聚合之后使用（搭配聚合函数或这个group-by）***

​	在 SQL 中，HAVING 子句**用于在分组聚合后对分组**进行过滤。它允许我们对分组后的结果进行条件筛选，只保留满足特定条件的分组。HAVING 子句与条件查询 WHERE 子句的区别在于，WHERE 子句用于在 **分组之前** 进行过滤，而 HAVING 子句用于在 **分组之后** 进行过滤。

**题目**

​	假设有一个学生表 `student`，包含以下字段：`id`（学号）、`name`（姓名）、`class_id`（班级编号）、`score`（成绩）。请你编写一个 SQL 查询，统计学生表中班级的总成绩超过 150 分的班级编号（class_id）和总成绩（total_score）。

```mysql

select
  class_id,
  sum(score) as total_score
from
  student
group by
  class_id
having
  sum(score) > 150
  
```

### 与where之间的差别

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240602180019433.png" alt="image-20240602180019433" style="zoom:50%;" />

## 7.子查询

对于在子查询中混合使用OrderBy等语句，如下面这个例子，下面这个例子中，又可以使用子查询也可以使用外连接来查询，**这样的时候优先使用外连接来查询会更加高效**

下面图片中使用外连接的sql语句为

```mysql
SELECT e.employee_id, e.salary
FROM employees e
JOIN departments d ON e.department_id = d.department_id
ORDER BY d.department_name;

```

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240606230233079.png" alt="image-20240606230233079" style="zoom:50%;" />

子查询（Subquery）是嵌套在另一条 SQL 查询中的查询。它可以出现在 SELECT、INSERT、UPDATE 和 DELETE 语句中，通常用于在条件中引用。子查询能够返回单个值、行或表，为主查询提供动态的数据。

### 子查询的基本语法

子查询通常包含在圆括号内。以下是一个基本的子查询语法示例：

```sql
SELECT column_name
FROM table_name
WHERE column_name = (SELECT column_name FROM table_name WHERE condition);
```

### 子查询的类型

1. **标量子查询（Scalar Subquery）**：
   返回单个值，可以用于比较或计算。
   ```sql
   SELECT employee_id, first_name, last_name
   FROM employees
   WHERE salary > (SELECT AVG(salary) FROM employees);
   ```

2. **行子查询（Row Subquery）**：
   返回单行，可以用于比较多个字段。
   ```sql
   SELECT employee_id, first_name, last_name
   FROM employees
   WHERE (department_id, job_id) = (SELECT department_id, job_id FROM employees WHERE employee_id = 100);
   ```

3. **表子查询（Table Subquery）**：
   返回多行多列，可以用在 FROM 子句中作为一个临时表。
   ```sql
   SELECT employee_id, first_name, salary
   FROM (SELECT employee_id, first_name, salary FROM employees WHERE department_id = 10) AS dept10_employees
   WHERE salary > 5000;
   ```

### 子查询的使用场景

1. **在 SELECT 子句中**：
   用于计算列的值。
   ```sql
   SELECT employee_id, (SELECT department_name FROM departments WHERE departments.department_id = employees.department_id) AS department_name
   FROM employees;
   ```

2. **在 WHERE 子句中**：
   用于过滤记录。
   ```sql
   SELECT first_name, last_name
   FROM employees
   WHERE department_id = (SELECT department_id FROM departments WHERE department_name = 'Sales');
   ```

3. **在 FROM 子句中**：
   用于提供一个临时表。
   ```sql
   SELECT avg_salary
   FROM (SELECT AVG(salary) AS avg_salary FROM employees) AS avg_salary_table;
   ```

4. **在 HAVING 子句中**：
   用于过滤分组后的记录。
   ```sql
   SELECT department_id, AVG(salary)
   FROM employees
   GROUP BY department_id
   HAVING AVG(salary) > (SELECT AVG(salary) FROM employees);
   ```

### 子查询的注意事项

1. **性能影响**：
   子查询可能会对性能产生影响，尤其是在处理大量数据时。对于复杂的查询，可以考虑使用 JOIN 替代。

2. **相关子查询与非相关子查询**：
   - **非相关子查询**：独立执行，不依赖于外部查询。
     ```sql
     SELECT employee_id, first_name
     FROM employees
     WHERE department_id = (SELECT department_id FROM departments WHERE department_name = 'Sales');
     ```
   - **相关子查询**：依赖于外部查询，每次执行都会参考外部查询的一行数据。
     ```sql
     SELECT employee_id, first_name
     FROM employees e1
     WHERE salary > (SELECT AVG(salary) FROM employees e2 WHERE e1.department_id = e2.department_id);
     ```

3. **使用 EXISTS**：
   使用 EXISTS 关键字来检查子查询是否返回结果，通常用于检查存在性。
   ```sql
   SELECT first_name, last_name
   FROM employees
   WHERE EXISTS (SELECT 1 FROM departments WHERE departments.department_id = employees.department_id);
   ```

### 子查询实例

#### 示例 1：找出工资高于公司平均工资的员工
```sql
SELECT employee_id, first_name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

#### 示例 2：找出属于 'Sales' 部门的员工
```sql
SELECT first_name, last_name
FROM employees
WHERE department_id = (SELECT department_id FROM departments WHERE department_name = 'Sales');
```

#### 示例 3：找出与其他员工工资最高的员工所在部门相同的员工
```sql
SELECT employee_id, first_name, last_name
FROM employees
WHERE department_id = (SELECT department_id FROM employees WHERE salary = (SELECT MAX(salary) FROM employees));
```

通过以上详细介绍，您应该对 MySQL 中的子查询有了更深入的理解和掌握。子查询是强大的工具，在适当的场景下能够简化复杂的查询逻辑。

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240606223938558.png" alt="image-20240606223938558" style="zoom: 33%;" />

多个子查询

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240606224402863.png" alt="image-20240606224402863" style="zoom:33%;" />

多行子查询（Multi-row Subquery）指的是返回多个行的子查询。与单行子查询不同，返回的结果可能包含多条记录。在 MySQL 中，多行子查询通常与 `IN`、`ANY`、`ALL` 等关键字一起使用，用于比较或过滤主查询的结果。

### 多行子查询的基本语法



```sql
SELECT column_name
FROM table_name
WHERE column_name IN (SELECT column_name FROM table_name WHERE condition);
```

### 多行子查询的使用场景

1. **使用 `IN` 操作符**：
   `IN` 操作符用于匹配子查询返回的多个值中的任意一个。
   ```sql
   SELECT first_name, last_name
   FROM employees
   WHERE department_id IN (SELECT department_id FROM departments WHERE location_id = 1700);
   ```

2. **使用 `ANY` 操作符**：
   `ANY` 操作符用于与子查询返回的任意一个值进行比较，通常与比较操作符（如 `=`、`>`、`<` 等）一起使用。
   ```sql
   SELECT employee_id, first_name, salary
   FROM employees
   WHERE salary > ANY (SELECT salary FROM employees WHERE department_id = 50);
   ```

3. **使用 `ALL` 操作符**：
   `ALL` 操作符用于与子查询返回的所有值进行比较，通常与比较操作符（如 `=`、`>`、`<` 等）一起使用。
   
   ```sql
   SELECT employee_id, first_name, salary
   FROM employees
   WHERE salary > ALL (SELECT salary FROM employees WHERE department_id = 50);
   ```

### 多行子查询的实例

示例 1：找出在特定位置（location_id = 1700）工作的所有员工

```sql
SELECT first_name, last_name
FROM employees
WHERE department_id IN (SELECT department_id FROM departments WHERE location_id = 1700);
```

示例 2：找出工资高于特定部门（department_id = 50）任何一个员工工资的员工

```sql
SELECT employee_id, first_name, salary
FROM employees
WHERE salary > ANY (SELECT salary FROM employees WHERE department_id = 50);
```

示例 3：找出工资高于特定部门（department_id = 50）所有员工工资的员工

```sql
SELECT employee_id, first_name, salary
FROM employees
WHERE salary > ALL (SELECT salary FROM employees WHERE department_id = 50);
```

使用 `EXISTS` 操作符

`EXISTS` 操作符用于检查子查询是否返回任何行。它返回一个布尔值，如果子查询返回一个或多个行，则为 `TRUE`，否则为 `FALSE`。

示例 4：找出有员工的部门

```sql
SELECT department_name
FROM departments d
WHERE EXISTS (SELECT 1 FROM employees e WHERE e.department_id = d.department_id);
```

注意事项

1. **性能考虑**：
   多行子查询可能会对性能产生影响，尤其是在数据量较大时。适当的索引和优化可以提高查询效率。

2. **NULL 值的处理**：
   如果子查询返回的结果中包含 `NULL` 值，使用 `IN` 操作符时需要特别注意，因为 `NULL` 不等于任何值，包括它自己。

3. **相关子查询与非相关子查询**：
   - **非相关子查询**：独立执行，不依赖外部查询。
   - **相关子查询**：依赖外部查询的每一行，通常性能较差，但在某些情况下非常有用。

相关子查询示例

#### 示例 5：找出工资高于本部门平均工资的员工
```sql
SELECT employee_id, first_name, salary
FROM employees e1
WHERE salary > (SELECT AVG(salary) FROM employees e2 WHERE e1.department_id = e2.department_id);
```

### 其他子查询

还有相关更新，相关删除的方式

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240606230643292.png" alt="image-20240606230643292" style="zoom:33%;" />

## 8.select的总结

目前所学的查询结构

```mysql
#方式1:
SELECT （DISTINCT）...,....,...
FROM ...,...,....
WHERE 多表的连接条件
AND 不包含组函数的过滤条件 GROUP BY ...,...
HAVING 包含组函数的过滤条件 ORDER BY ... ASC/DESC LIMIT ...,...
#方式2:
SELECT （DISTINCT）...,....,...
FROM ... JOIN ...
ON 多表的连接条件
JOIN ...
ON ...
WHERE 不包含组函数的过滤条件 AND/OR 不包含组函数的过滤条件 GROUP BY ...,...
HAVING 包含组函数的过滤条件 ORDER BY ... ASC/DESC LIMIT ...,...
```

select中的关键字书写顺序和执行顺序不同！

关键词顺序` SELECT ... FROM ... WHERE ... GROUP BY ... HAVING ... ORDER BY ... LIMIT...`

执行顺序(Mysql与Oracle相似)

`FROM -> WHERE -> GROUP BY -> HAVING -> SELECT 的字段 -> DISTINCT -> ORDER BY -> LIMIT`

**执行原理**

1. 首先先通过 CROSS JOIN 求笛卡尔积，相当于得到虚拟表 vt(virtual table)1-1;
2. 通过 ON 进行筛选，在虚拟表 vt1-1 的基础上进行筛选，得到虚拟表 vt1-2;
3. 添加外部行。如果我们使用的是左连接、右链接或者全连接，就会涉及到外部行，也就是在虚拟

表 vt1-2 的基础上增加外部行，得到虚拟表 vt1-3。

 

# 2.多表查询

## 内连接和外连接



内连接和外连接是SQL中用于连接多个表的两种主要连接方式，它们在处理匹配和不匹配数据行方面有不同的方式。

### 内连接（Inner Join）

内连接是最常用的连接类型。它返回两个表中匹配连接条件的行。只有当两个表中有匹配的行时，才会在结果集中包含这些行。如果没有匹配的行，则不会在结果集中出现。

**语法：**

```sql
SELECT *
FROM 表1
INNER JOIN 表2
ON 表1.列A = 表2.列B;
```

**示例：**

假设我们有两张表：`students` 和 `classes`，其中 `students` 表有学生信息，`classes` 表有班级信息。我们希望查询每个学生及其班级名称。

```sql
students:
+----+---------+----------+
| id | name    | class_id |
+----+---------+----------+
| 1  | Alice   | 101      |
| 2  | Bob     | 102      |
| 3  | Charlie | 101      |
+----+---------+----------+

classes:
+---------+-------------+
| class_id| class_name  |
+---------+-------------+
| 101     | Math        |
| 102     | English     |
+---------+-------------+
```

使用内连接查询：

```sql
SELECT students.name, classes.class_name
FROM students
INNER JOIN classes
ON students.class_id = classes.class_id;
```

**结果：**

```sql
+---------+-------------+
| name    | class_name  |
+---------+-------------+
| Alice   | Math        |
| Charlie | Math        |
| Bob     | English     |
+---------+-------------+
```

### 外连接（Outer Join）

外连接用于返回连接表中所有匹配的行，以及某一表中不匹配的行。根据返回非匹配行的表的不同，外连接分为左外连接（LEFT OUTER JOIN）、右外连接（RIGHT OUTER JOIN）和全外连接（FULL OUTER JOIN）。

#### 左外连接（LEFT OUTER JOIN）

左外连接返回左表中的所有行，即使右表中没有匹配的行。对于右表中没有匹配的行，结果集中将包含NULL。

**语法：**

```sql
SELECT *
FROM 表1
LEFT JOIN 表2
ON 表1.列A = 表2.列B;
```

**示例：**

继续使用前面的 `students` 和 `classes` 表，我们希望查询所有学生及其班级名称，即使有些学生没有分配班级。

```sql
SELECT students.name, classes.class_name
FROM students
LEFT JOIN classes
ON students.class_id = classes.class_id;
```

**结果：**

```sql
+---------+-------------+
| name    | class_name  |
+---------+-------------+
| Alice   | Math        |
| Bob     | NULL        |
| Charlie | Math        |
+---------+-------------+
```

#### 右外连接（RIGHT OUTER JOIN）

右外连接返回右表中的所有行，即使左表中没有匹配的行。对于左表中没有匹配的行，结果集中将包含NULL。

**语法：**

```sql
SELECT *
FROM 表1
RIGHT JOIN 表2
ON 表1.列A = 表2.列B;
```

#### 全外连接（FULL OUTER JOIN）

**`	下面是其中外连接的sql实现`**

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240601215923110.png" alt="image-20240601215923110" style="zoom:50%;" />

**Mysql不支持全外连接**，可以使用union all/union在mysql中实现full outer join，  union all没有去重，速度比union更快

全外连接返回左表和右表中的所有行，不管是否有匹配的行。对于没有匹配的行，结果集中将包含NULL。

**语法：**

```sql
SELECT *
FROM 表1
FULL OUTER JOIN 表2
ON 表1.列A = 表2.列B;
```

- **内连接** 仅返回两个表中匹配连接条件的行。如果没有匹配的行，则不会在结果集中出现这些行。
- **外连接** 包括左外连接、右外连接和全外连接，返回匹配和不匹配的行：
  - **左外连接** 返回左表中的所有行，匹配和不匹配的行。
  - **右外连接** 返回右表中的所有行，匹配和不匹配的行。
  - **全外连接** 返回左表和右表中的所有行，匹配和不匹配的行。

# 3.常用函数

## 1.数值计算相关

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240602112305220.png" alt="image-20240602112305220" style="zoom:50%;" />

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240602163147487.png" alt="image-20240602163147487" style="zoom:40%;" />

## 2.字符串相关

- Concat

![image-20240602163459495](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240602163459495.png style="zoom:40%")

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240602163328023.png" style="zoom:50%;" />

## 3.日期函数

### 获取日期和时间

- date相关：返回的是当前的**年月日**
- time相关：返回的是当前的**时分秒**

​	常用如下

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240602164212815.png" alt="image-20240602164212815" style="zoom:50%;" />

### 时间转换



<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240602164434059.png" alt="image-20240602164434059" style="zoom:50%;" />

# 4.创建库和管理表

数据库的常用数据结构

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240614130723265.png" alt="image-20240614130723265" style="zoom:50%;" />

## 1.创建数据库

推荐第三种创建数据库

```mysql
CREATE DATABASE 数据库名;

CREATE DATABASE 数据库名 CHARACTER SET 字符集#; 方式3:判断数据库是否已经存在，不存在则创建数据库( 推荐 )

CREATE DATABASE IF NOT EXISTS 数据库名;# 如果MySQL中已经存在相关的数据库，则忽略创建语句，不再创建数据库
```

- **注意:DATABASE 不能改名。一些可视化工具可以改名，它是建新库，把所有表复制到新库，再删 旧库完成的。**

## 2.使用数据库

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240614132454824.png" alt="image-20240614132454824" style="zoom:50%;" />

## 3.修改数据库

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240614132610196.png" alt="image-20240614132610196" style="zoom:50%;" />

## 4.删除数据库

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240614132825438.png" alt="image-20240614132825438" style="zoom:50%;" />

## 5.创建表

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240614133213350.png" alt="image-20240614133213350" style="zoom:50%;" />

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240614133814835.png" alt="image-20240614133814835" style="zoom:50%;" />

- 根据查询的信息也可以建表

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240614134045357.png" alt="image-20240614134045357" style="zoom:50%;" />

- 复制表中的数据/不复制数据

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240617210345111.png" alt="image-20240617210345111" style="zoom:50%;" />

### 查看表的结构

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240617210436267.png" alt="image-20240617210436267" style="zoom:50%;" />

## 6.修改表

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240617211406025.png" alt="image-20240617211406025" style="zoom:50%;" />

修改表结构是数据库管理中的常见任务，包括添加、删除和修改列、约束、索引等。以下是一些常见的操作及其对应的SQL语法：

### 1. 添加列
向表中添加新列时，可以使用 `ALTER TABLE` 语句。

```sql
ALTER TABLE table_name
ADD COLUMN new_column_name column_definition;
```

例如，向 `employees` 表中添加一个 `birthdate` 列：

```sql
ALTER TABLE employees
ADD COLUMN birthdate DATE;
```

### 2. 删除列
删除表中的列可以使用 `DROP COLUMN` 关键字。

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

例如，删除 `employees` 表中的 `birthdate` 列：

```sql
ALTER TABLE employees
DROP COLUMN birthdate;
```

### 3. 修改列的数据类型或名称
可以使用 `MODIFY` 或 `CHANGE` 关键字来更改列的**数据类型**(一般不修改类型)或名称。

#### 修改数据类型

```sql
ALTER TABLE table_name
MODIFY COLUMN column_name new_column_definition;
```

例如，将 `employees` 表中的 `salary` 列的数据类型改为 `DECIMAL`：

```sql
ALTER TABLE employees
MODIFY COLUMN salary DECIMAL(10, 2);
```

#### 修改列名称和数据类型

```sql
ALTER TABLE table_name
CHANGE COLUMN old_column_name new_column_name new_column_definition;
```

例如，将 `employees` 表中的 `salary` 列改名为 `annual_salary` 并修改数据类型为 `DECIMAL`：

```sql
ALTER TABLE employees
CHANGE COLUMN salary annual_salary DECIMAL(10, 2);
```

### 4. 添加约束
可以向表中添加各种约束，例如主键、外键、唯一约束等。

#### 添加主键

```sql
ALTER TABLE table_name
ADD PRIMARY KEY (column_name);
```

例如，向 `employees` 表中的 `employee_id` 列添加主键约束：

```sql
ALTER TABLE employees
ADD PRIMARY KEY (employee_id);
```

#### 添加外键

```sql
ALTER TABLE table_name
ADD CONSTRAINT constraint_name FOREIGN KEY (column_name) REFERENCES other_table (other_column_name);
```

例如，向 `orders` 表中的 `customer_id` 列添加外键约束，引用 `customers` 表中的 `customer_id` 列：

```sql
ALTER TABLE orders
ADD CONSTRAINT fk_customer
FOREIGN KEY (customer_id) REFERENCES customers (customer_id);
```

### 5. 删除约束
可以使用 `DROP` 关键字来删除约束。

#### 删除主键

```sql
ALTER TABLE table_name
DROP PRIMARY KEY;
```

#### 删除外键

```sql
ALTER TABLE table_name
DROP FOREIGN KEY constraint_name;
```

### 6. 添加索引
可以使用 `ADD INDEX` 来添加索引。

```sql
ALTER TABLE table_name
ADD INDEX index_name (column_name);
```

例如，向 `employees` 表中的 `last_name` 列添加索引：

```sql
ALTER TABLE employees
ADD INDEX idx_last_name (last_name);
```

### 7. 删除索引
可以使用 `DROP INDEX` 来删除索引。

```sql
DROP INDEX index_name ON table_name;
```

例如，删除 `employees` 表中的 `idx_last_name` 索引：

```sql
DROP INDEX idx_last_name ON employees;
```

通过使用上述的SQL语句，可以有效地修改表的结构以满足业务需求。在修改表结构时，建议首先备份数据，并在开发环境中进行测试，确保不会影响生产环境中的数据完整性和应用程序的正常运行。

### 8.重命名表

是重命名表不是重命名列

![image-20240617213136418](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240617213136418.png)

### 9.清空表

#### TRUNCATE TABLE

`TRUNCATE TABLE` 语句用于快速清空表的所有数据。与 `DELETE FROM` 不同的是，`TRUNCATE TABLE` 不能用于删除特定的行。它的速度非常快，因为它不会逐行删除数据，而是直接重置表。以下是它的主要特点：

- **速度快**：因为它不逐行删除数据，而是直接重置表。
- **不触发 DELETE 触发器**：`TRUNCATE` 操作不会触发 `DELETE` 触发器。
- **自动提交**：`TRUNCATE` 操作会隐式地提交事务，不能在事务中回滚。
- **重置 AUTO_INCREMENT**：`TRUNCATE` 会重置表的 `AUTO_INCREMENT` 计数器。

语法：

```
sql
复制代码
TRUNCATE TABLE table_name;
```

例如，清空 `employees` 表：

```
sql
复制代码
TRUNCATE TABLE employees;
```

#### DELETE FROM

`DELETE FROM` 语句用于删除表中的行。可以删除所有行，也可以通过 `WHERE` 子句删除特定的行。删除所有行时，它比 `TRUNCATE` 慢，因为它逐行删除数据并触发 `DELETE` 触发器。

- **逐行删除**：逐行删除数据，可以使用 `WHERE` 子句。

- **触发 DELETE 触发器**：会触发 `DELETE` 触发器。

- **事务控制**：可以在事务中执行，支持回滚。

- **AUTO_INCREMENT 重置**：`TRUNCATE TABLE` 会重置 `AUTO_INCREMENT` 计数器，`DELETE FROM` 不会。

  删除特定行

  ```mysql
  DELETE FROM table_name WHERE condition;
  ```

  

  #### 选择合适的方法

  - 如果你需要保留表结构并快速删除所有数据，且不需要触发 `DELETE` 触发器或在事务中操作，使用 `TRUNCATE TABLE`。
  - 如果你需要逐行删除数据、触发 `DELETE` 触发器，或在事务中控制操作，使用 `DELETE FROM`。

### 10.Mysql8的原子性

​	在MySQL 8.0版本中，InnoDB表的DDL支持事务完整性，**即 DDL操作要么成功要么回滚** 。DDL操作回滚日志 写入到data dictionary数据字典表mysql.innodb_ddl_log(该表是隐藏的表，通过show tables无法看到) 中，用于回滚操作。通过设置参数，可将DDL操作日志打印输出到MySQL错误日志中

例如同时删除一个存在和不存在的表，由于语句中有不存在的表，所以语句会报错

- 对于mysql8 **这两个都不会删除，会直接回滚事物**（事务不可分割）
- 对于mysql5.7 会删除存在的一个表，然后遇到第二个不存在的表再报错

### 11.注意事项

1.在写sql语句的时候注意删除列和删除行不一样。。。一开始写的时候没有注意

- 删除列使用alter+drop column
- 删除行使用delete from或者 truncate table

2.跨数据库复制数据创建表也是可以的，就是在创建的时候附加上对应数据库的前缀

# 5.DML（数据增删改）

在数据库管理系统（DBMS）中，数据处理的增删改操作是日常管理和维护数据库的核心任务。这些操作通常由SQL（结构化查询语言）来执行。下面详细介绍这三种操作：

### 1. 数据插入（INSERT）
插入操作用于向表中添加新的记录。常见的SQL语法如下：

```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```

#### 示例
假设有一个名为`students`的表，包含`id`、`name`和`age`三个列。向表中插入一条新记录：

```sql
INSERT INTO students (id, name, age)
VALUES (1, 'Alice', 20);
```

同时插入多行数据

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240618180534487.png" alt="image-20240618180534487" style="zoom:50%;" />

#### 多行添加单行添加的效率

`一个同时插入多行记录的INSERT语句等同于多个单行插入的INSERT语句，但是多行的INSERT语句 在处理过程中 效率更高 。因为MySQL执行单条INSERT语句插入多行数据比使用多条INSERT语句 快，所以在插入多条记录时最好选择使用单条INSERT语句的方式插入。`

#### 子查询的插入

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240618180938360.png" alt="image-20240618180938360" style="zoom: 33%;" />

```mysql
INSERT INTO sales_reps(id, name, salary, commission_pct)
SELECT employee_id, last_name, salary, commission_pct
FROM   employees
WHERE  job_id LIKE '%REP%';
```

**小结**

- VALUES 也可以写成 VALUE ，但是VALUES是标准写法。 
- 字符和日期型数据应包含在单引号中。

### 2. 数据更新（UPDATE）

更新操作用于修改表中已存在的记录。常见的SQL语法如下：

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

#### 示例
修改`students`表中`id`为1的学生的年龄为21：

```sql
UPDATE students
SET age = 21
WHERE id = 1;
```

需要注意的是，`WHERE`子句用于指定哪些记录需要更新。如果没有`WHERE`子句，**表中所有记录都会被更新**。

### 3. 数据删除（DELETE）
删除操作用于从表中删除记录。常见的SQL语法如下：

```sql
DELETE FROM table_name
WHERE condition;
```

#### 示例
删除`students`表中`id`为1的学生记录：

```sql
DELETE FROM students
WHERE id = 1;
```

同样需要注意，`WHERE`子句用于指定哪些记录需要删除。**如果没有`WHERE`子句，表中所有记录都会被删除**。

### 计算列（Mysql8）

#### 1.1 虚拟计算列（VIRTUAL Generated Column）

虚拟计算列是基于其他列的计算值，但其结果不会实际存储在表中，而是每次查询时动态计算。

#### 1.2 存储计算列（STORED Generated Column）

存储计算列与虚拟计算列类似，但其计算结果会实际存储在表中，因此查询时可以提高性能，但会增加存储空间。

#### 2. 计算列的定义

#### 2.1 基本语法

定义计算列时，可以在表创建时或者通过ALTER TABLE语句添加。基本语法如下：

```sql

CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    generated_column_name datatype [GENERATED ALWAYS] AS (expression) [VIRTUAL | STORED]
);

ALTER TABLE table_name ADD COLUMN generated_column_name datatype [GENERATED ALWAYS] AS (expression) [VIRTUAL | STORED];
```

#### 3. 示例

#### 3.1 创建表时定义计算列

假设我们有一个`employees`表，我们希望添加一个计算列来计算员工的年薪（假设每个月的薪水保存在`monthly_salary`列中）。

```sql

CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    monthly_salary DECIMAL(10, 2),
    annual_salary DECIMAL(10, 2) AS (monthly_salary * 12) STORED
);
```

在这个例子中，`annual_salary`列是一个存储计算列，它基于`monthly_salary`列计算出年薪。

#### 3.2 使用ALTER TABLE添加计算列

如果我们已经有一个`employees`表，现在想添加一个计算列，可以使用ALTER TABLE语句：

```mysql

ALTER TABLE employees
ADD COLUMN annual_salary DECIMAL(10, 2) AS (monthly_salary * 12) STORED;
```

#### 4. 使用计算列

#### 4.1 插入和查询数据

向表中插入数据时，不需要显式提供计算列的值，它会自动计算：

```mysql

INSERT INTO employees (id, name, monthly_salary) VALUES (1, 'John Doe', 5000.00);
INSERT INTO employees (id, name, monthly_salary) VALUES (2, 'Jane Smith', 6000.00);
```

查询数据时，计算列的值会自动显示：

```
sql
复制代码
SELECT id, name, monthly_salary, annual_salary FROM employees;
```

结果：

```
diff
复制代码
+----+------------+---------------+--------------+
| id | name       | monthly_salary| annual_salary|
+----+------------+---------------+--------------+
|  1 | John Doe   |       5000.00 |      60000.00|
|  2 | Jane Smith |       6000.00 |      72000.00|
+----+------------+---------------+--------------+
```

#### 5. 注意事项

- **索引支持**：存储计算列可以被索引，虚拟计算列不能被索引。
- **性能影响**：虚拟计算列的值每次查询时都会计算，因此可能会影响查询性能。存储计算列则会占用额外的存储空间，但查询性能较好。
- **限制**：计算列不能引用其他计算列，并且表达式中不能使用子查询。

### 事务管理

在进行增删改操作时，事务管理是确保数据完整性和一致性的重要机制。事务可以保证一组操作要么全部成功，要么全部失败。常用的事务控制语句包括：

- `BEGIN`：开始一个事务
- `COMMIT`：提交事务
- `ROLLBACK`：回滚事务

#### 示例
在MySQL中，进行一系列操作并使用事务管理：

```sql
BEGIN;

INSERT INTO students (id, name, age) VALUES (2, 'Bob', 22);
UPDATE students SET age = 23 WHERE id = 2;

COMMIT;
```

如果在事务中发生错误，可以使用`ROLLBACK`回滚事务，以确保数据的原子性：

```sql
BEGIN;

INSERT INTO students (id, name, age) VALUES (3, 'Charlie', 23);
UPDATE students SET age = 24 WHERE id = 3;

ROLLBACK; -- 撤销所有未提交的操作
```



# 6.MYSQL数据类型介绍

MySQL 提供了一系列的数据类型，用于定义表中列的数据。根据数据的性质和用途，可以将这些数据类型分为几大类：数值类型、日期和时间类型、字符串类型、JSON类型和空间数据类型。下面详细介绍这些数据类型。

### 1. 数值类型

数值类型用于存储数字，可以进一步分为整数类型和小数类型。

#### 1.1 整数类型
- **TINYINT**：1字节，范围 -128 到 127 或 0 到 255（无符号）。
- **SMALLINT**：2字节，范围 -32768 到 32767 或 0 到 65535（无符号）。
- **MEDIUMINT**：3字节，范围 -8388608 到 8388607 或 0 到 16777215（无符号）。
- **INT（INTEGER）**：4字节，范围 -2147483648 到 2147483647 或 0 到 4294967295（无符号）。
- **BIGINT**：8字节，范围 -9223372036854775808 到 9223372036854775807 或 0 到 18446744073709551615（无符号）。

示例：
```sql
CREATE TABLE example (
    tiny_column TINYINT,
    int_column INT
);
```

#### 1.2 小数类型
- **FLOAT**：4字节，单精度浮点数。

- **DOUBLE**：8字节，双精度浮点数。

- **DECIMAL**：精确的定点数，**用于存储高精度的数值数据**。语法为 `DECIMAL(M, D)`，其中 `M` 是总位数，`D` 是小数位数。

  **二者区别**

- 浮点数相对于定点数的优点是在长度一定的情况下，浮点类型取值范围大，但是不精准，适用 于需要取值范围大，又可以容忍微小误差的科学计算场景(比如计算化学、分子建模、流体动 力学等)

-  定点数类型取值范围相对小，但是精准，没有误差，适合于对精度要求极高的场景 (比如涉 及金额计算的场景)

`推荐使用DECIMAL，高精确！`

示例：
```sql
CREATE TABLE example (
    float_column FLOAT,
    decimal_column DECIMAL(10, 2)
);
```



### 2. 日期和时间类型概述

MySQL支持多种日期和时间类型，以满足不同的需求。主要的日期和时间类型包括：

- **DATE**：仅存储日期，不包含时间部分。
- **TIME**：仅存储时间，不包含日期部分。
- **DATETIME**：同时存储日期和时间。
- **TIMESTAMP**：时间戳，存储从1970年1月1日午夜（UTC）开始的秒数。
- **YEAR**：仅存储年份。

#### 2. DATE 类型

##### 2.1 格式
`DATE` 类型的格式为 `YYYY-MM-DD`，例如 `2023-06-18`。

##### 2.2 范围
`DATE` 类型的值范围为 `1000-01-01` 到 `9999-12-31`。

##### 2.3 示例
```sql
CREATE TABLE example (
    date_column DATE
);

INSERT INTO example (date_column) VALUES ('2023-06-18');

SELECT date_column FROM example;
```

#### 3. TIME 类型

##### 3.1 格式
`TIME` 类型的格式为 `HH:MM:SS`，例如 `13:45:30`。它也可以存储超过24小时的时间间隔，例如 `25:00:00`。

##### 3.2 范围
`TIME` 类型的值范围为 `-838:59:59` 到 `838:59:59`。

##### 3.3 示例
```sql
CREATE TABLE example (
    time_column TIME
);

INSERT INTO example (time_column) VALUES ('13:45:30');

SELECT time_column FROM example;
```

#### 4. DATETIME 类型

##### 4.1 格式
`DATETIME` 类型的格式为 `YYYY-MM-DD HH:MM:SS`，例如 `2023-06-18 13:45:30`。

##### 4.2 范围
`DATETIME` 类型的值范围为 `1000-01-01 00:00:00` 到 `9999-12-31 23:59:59`。

##### 4.3 示例
```sql
CREATE TABLE example (
    datetime_column DATETIME
);

INSERT INTO example (datetime_column) VALUES ('2023-06-18 13:45:30');

SELECT datetime_column FROM example;
```

#### 5. TIMESTAMP 类型

##### 5.1 格式
`TIMESTAMP` 类型的格式为 `YYYY-MM-DD HH:MM:SS`，例如 `2023-06-18 13:45:30`。`TIMESTAMP` 类型会根据存储和读取的时区自动进行转换，通常用于记录事件发生的精确时间。

##### 5.2 范围
`TIMESTAMP` 类型的值范围为 `1970-01-01 00:00:01 UTC` 到 `2038-01-19 03:14:07 UTC`。

##### 5.3 示例
```sql
CREATE TABLE example (
    timestamp_column TIMESTAMP
);

INSERT INTO example (timestamp_column) VALUES ('2023-06-18 13:45:30');

SELECT timestamp_column FROM example;
```

##### 5.4 自动初始化和更新
`TIMESTAMP` 列可以配置为在行插入或更新时自动设置或更新。

```sql
CREATE TABLE example (
    id INT PRIMARY KEY,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

#### 6. YEAR 类型

##### 6.1 格式
`YEAR` 类型的格式为 `YYYY`，例如 `2023`。

##### 6.2 范围
`YEAR` 类型的值范围为 `1901` 到 `2155`。

##### 6.3 示例
```sql
CREATE TABLE example (
    year_column YEAR
);

INSERT INTO example (year_column) VALUES (2023);

SELECT year_column FROM example;
```

#### 7. 日期和时间函数

MySQL 提供了丰富的日期和时间函数，用于操作日期和时间值。常用的函数包括：

##### 7.1 获取当前日期和时间
- **CURRENT_DATE()**：返回当前日期。
- **CURRENT_TIME()**：返回当前时间。
- **CURRENT_TIMESTAMP()** 或 **NOW()**：返回当前日期和时间。

```sql
SELECT CURRENT_DATE();
SELECT CURRENT_TIME();
SELECT CURRENT_TIMESTAMP();
```

##### 7.2 日期和时间的加减
- **DATE_ADD()**：加上指定的时间间隔。
- **DATE_SUB()**：减去指定的时间间隔。
- **ADDDATE()** 和 **SUBDATE()**：类似于 `DATE_ADD()` 和 `DATE_SUB()`。

```sql
SELECT DATE_ADD('2023-06-18', INTERVAL 10 DAY);
SELECT DATE_SUB('2023-06-18', INTERVAL 5 DAY);
```

##### 7.3 提取日期和时间部分
- **YEAR()**：提取年份。
- **MONTH()**：提取月份。
- **DAY()**：提取日期。
- **HOUR()**：提取小时。
- **MINUTE()**：提取分钟。
- **SECOND()**：提取秒。

```sql
SELECT YEAR('2023-06-18 13:45:30');
SELECT MONTH('2023-06-18 13:45:30');
SELECT DAY('2023-06-18 13:45:30');
SELECT HOUR('2023-06-18 13:45:30');
SELECT MINUTE('2023-06-18 13:45:30');
SELECT SECOND('2023-06-18 13:45:30');
```

##### 7.4 日期格式化
- **DATE_FORMAT()**：按指定格式格式化日期。

```sql
SELECT DATE_FORMAT('2023-06-18', '%W, %M %d, %Y');
```

#### 8. 总结

​	用得最多的日期时间类型，**就是 DATETIME** 。虽然 MySQL 也支持 YEAR(年)、 TIME(时间)、 DATE(日期)，以及 TIMESTAMP 类型，但是在实际项目中，尽量用 DATETIME 类型。因为这个数据类型 包括了完整的日期和时间信息，取值范围也最大，使用起来比较方便。毕竟，如果日期时间信息分散在 好几个字段，很不容易记，而且查询的时候，SQL 语句也会更加复杂。

## 3. 字符串类型

字符串类型用于存储文本数据。

- **CHAR**：定长字符串，长度范围为0到255。
- **VARCHAR**：变长字符串，长度范围为0到65535。
- **TEXT**：大文本，长度范围为0到65535。
- **MEDIUMTEXT**：中等长度文本，长度范围为0到16777215。
- **LONGTEXT**：长文本，长度范围为0到4294967295。
- **BINARY**：定长二进制数据。
- **VARBINARY**：变长二进制数据。
- **BLOB**：二进制大对象，用于存储大量二进制数据。

示例：
```sql
CREATE TABLE example (
    char_column CHAR(10),
    varchar_column VARCHAR(255),
    text_column TEXT
);
```

### 4. JSON类型

MySQL 5.7 引入了 JSON 类型，用于存储 JSON 格式的数据。

示例：
```sql
CREATE TABLE example (
    json_column JSON
);
```

### 5. 空间数据类型

空间数据类型用于存储地理空间数据，MySQL 支持多种空间数据类型，包括：

- **GEOMETRY**：通用的空间数据类型。
- **POINT**：表示一个点。
- **LINESTRING**：表示一条线。
- **POLYGON**：表示一个多边形。

示例：
```sql
CREATE TABLE example (
    geom_column GEOMETRY,
    point_column POINT
);
```

### 6. 特殊数据类型

- **ENUM**：枚举类型，用于存储一组预定义的字符串值之一。
- **SET**：集合类型，用于存储一个字符串集合。
- **BIT**

#### 6.1 ENUM 示例：
```sql
CREATE TABLE example (
    status ENUM('active', 'inactive', 'suspended')
);
```

#### 6.2 SET 示例：
```sql
CREATE TABLE example (
    permissions SET('read', 'write', 'execute')
);
```

### 7.数据类型的属性

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240618210542257.png" alt="image-20240618210542257" style="zoom: 33%;" />

# 7.约束

## 1.什么事约束

![image-20241014195410171](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241014195410171.png)

## 2.删除、修改约束

这是一个用于**删除和修改 MySQL 约束**的通用模板，你可以根据不同的约束类型来替换相应的部分：

### 1. **删除约束的通用模板**

#### 删除 `NOT NULL` 约束
```sql
ALTER TABLE table_name
MODIFY column_name column_type NULL;
```

#### 删除 `UNIQUE` 约束
```sql
ALTER TABLE table_name
DROP INDEX unique_constraint_name;
```

#### 删除 `PRIMARY KEY` 约束
```sql
ALTER TABLE table_name
DROP PRIMARY KEY;
```

#### 删除 `FOREIGN KEY` 约束
```sql
ALTER TABLE table_name
DROP FOREIGN KEY foreign_key_name;
```

#### 删除 `CHECK` 约束
```sql
ALTER TABLE table_name
DROP CHECK check_constraint_name;
```

#### 删除 `DEFAULT` 约束
```sql
ALTER TABLE table_name
ALTER COLUMN column_name DROP DEFAULT;
```

---

### 2. **修改约束的通用模板**

#### 修改为 `NOT NULL`
```sql
ALTER TABLE table_name
MODIFY column_name column_type NOT NULL;
```

#### 修改 `UNIQUE` 约束（需要先删除旧的 UNIQUE 约束，然后重新添加）
1. 删除：
    ```sql
    ALTER TABLE table_name
    DROP INDEX unique_constraint_name;
    ```
2. 添加新的：
    ```sql
    ALTER TABLE table_name
    ADD CONSTRAINT unique_constraint_name UNIQUE (column_name);
    ```

#### 修改 `PRIMARY KEY` 约束（需要先删除旧的 PRIMARY KEY，再添加新的）
1. 删除：
    ```sql
    ALTER TABLE table_name
    DROP PRIMARY KEY;
    ```
2. 添加新的：
    ```sql
    ALTER TABLE table_name
    ADD PRIMARY KEY (column_name);
    ```

#### 修改 `FOREIGN KEY` 约束（需要先删除旧的 FOREIGN KEY，再添加新的）
1. 删除：
    ```sql
    ALTER TABLE table_name
    DROP FOREIGN KEY foreign_key_name;
    ```
2. 添加新的：
    ```sql
    ALTER TABLE table_name
    ADD CONSTRAINT foreign_key_name FOREIGN KEY (column_name) REFERENCES referenced_table_name(referenced_column_name);
    ```

#### 修改 `CHECK` 约束（需要先删除旧的 CHECK 约束，再添加新的）
1. 删除：
    ```sql
    ALTER TABLE table_name
    DROP CHECK check_constraint_name;
    ```
2. 添加新的：
    ```sql
    ALTER TABLE table_name
    ADD CONSTRAINT check_constraint_name CHECK (condition);
    ```

---

这些模板适用于大多数情况，删除和修改约束时，可以根据需要调整列名、表名和约束的具体名称。

## 3.主键约束

