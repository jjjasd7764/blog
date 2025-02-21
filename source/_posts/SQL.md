title: SQL文档
date: 2025-2-3 17:33:33
tags:
-----

### 1、查询表，例如

```
SELECT * FROM table_name;
```

其意思是，查询该表下的所有，table_name 表示表名

2、查询表下的名称，从 “Websites” 表中选取国家为 “CN” 的所有网站

```
SELECT * FROM Websites WHERE country='CN';
```

3、搜索 emp表中所有empno 等于 7900 的数据：

```
Select * from emp where empno=7900
```

## 逻辑运算

```mermaid
Select * from emp where sal > 2000 and sal < 3000;
```

条件查询，and，查询emp表下sal大于2000且小于3000的值

条件查询，or，查询emp表下 sal大于2000或comn大于500的值

```
Select * from emp where sal > 2000 or comm > 500;
```

条件查询，not，查询emp表下所有sal不大于1500的值

```
select * from emp where not sal > 1500;
```

**1.空值判断： is null**

```
Select * from emp where comm is null;
```

**2.between 和 （在 之间的值）**

```
Select * from emp where sal between 1500 and 3000;
```

注意：大于等于 1500 且小于等于 3000， 1500 为下限，3000 为上限，下限在前，上限在后，查询的范围包涵有上下限的值。

3、Like模糊查询

```
Select * from emp where ename like 'M%';
```

查询 EMP 表中 Ename 列中有 M 的值，M 为要查询内容中的模糊信息。

* **%**表示多个字值，_ 下划线表示一个字符;
* M% ： 为能配符，正则表达式，表示的意思为模糊查询信息为 M 开头的。
* %M% ： 表示查询包含M的所有内容。
* %M_ ： 表示查询以M在倒数第二位的所有内容。

4、运算符下面的 SQL 语句从 “Websites” 表中选取国家为 “CN” 且alexa排名大于 “50” 的所有网站：

```
SELECT * FROM Websites
WHERE country='CN'
AND alexa > 50;
```

下面的 SQL 语句从 “Websites” 表中选取国家为 “USA” 或者 “CN” 的所有客户：

```
SELECT * FROM Websites
WHERE country='USA'
OR country='CN';
```

以把 AND 和 OR 结合起来（使用圆括号来组成复杂的表达式）。

下面的 SQL 语句从 "Websites" 表中选取 alexa 排名大于 "15" 且国家为 "CN" 或 "USA" 的所有网站：

```
SELECT * FROM Websites
WHERE alexa > 15
AND (country='CN' OR country='USA');
```

### 排序

下面的 SQL 语句从 "Websites" 表中选取所有网站，并按照 "alexa" 列排序：

```
SELECT * FROM Websites
ORDER BY alexa;
```

表示升序

还可以按多列进行排序，下面的 SQL 语句从 "Websites" 表中选取所有网站，并按照 "country" 和 "alexa" 列排序：

```
SELECT * FROM Websites
ORDER BY country,alexa;
```

### 数据增加

数据库演示

```
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 教程      | http://www.run.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
+----+--------------+---------------------------+-------+---------+
```

假设我们要向 "Websites" 表中插入一个新行。

我们可以使用下面的 SQL 语句：

```
INSERT INTO Websites (name, url, alexa, country)
VALUES ('百度','https://www.baidu.com/','4','CN');
```

假设我们要把 "教程" 的 alexa 排名更新为 5000，country 改为 USA。

```
UPDATE Websites 
SET alexa='5000', country='USA' 
WHERE name='教程';
```

### 删除

假设我们要从 "Websites" 表中删除网站名为 "Facebook" 且国家为 USA 的网站。

```
DELETE FROM Websites
WHERE name='Facebook' AND country='USA';
```

### 高级用法

查询前三行，字段名为EmployeeName, Salary，表名为Employees的数据。

```
SELECT TOP 3 EmployeeName, Salary
FROM Employees;
```

**返回前 10% 的数据：**

```
SELECT TOP 10 PERCENT EmployeeName, Salary
FROM Employees;
```

**MySQL 返回前 3 行数据：**

```
SELECT EmployeeName, Salary
FROM Employees
LIMIT 3;
```


假设我们有一个名为 Products 的表，包含以下数据：


| 产品 ID | 产品名称            | 类别   |
| ------- | ------------------- | ------ |
| 1       | 苹果手机 12         | 电子学 |
| 2       | 三星 Galaxy S21     | 电子学 |
| 3       | 戴尔 XPS 13         | 电子学 |
| 4       | 耐克 Air Zoom       | 鞋     |
| 5       | 阿迪达斯 Ultraboost | 鞋     |
| 6       | 索尼 PlayStation 5  | 电子学 |

使用 **%** 通配符找出所有以 “iPhone” 开头的产品：

```
SELECT ProductName, Category
FROM Products
WHERE ProductName LIKE 'iPhone%';
```

下面的 SQL 语句选取 name 以字母 "G" 开始的所有客户：

```
SELECT * FROM Websites
WHERE name LIKE 'G%';
```

下面的 SQL 语句选取 name 以字母 "k" 结尾的所有客户：

```
SELECT * FROM Websites
WHERE name LIKE '%k';
```

下面的 SQL 语句选取 name 包含模式 "oo" 的所有客户：

```
SELECT * FROM Websites
WHERE name LIKE '%oo%';
```

下面的 SQL 语句选取 name 不包含模式 "oo" 的所有客户：

```
SELECT * FROM Websites
WHERE name NOT LIKE '%oo%';
```


## 使用 SQL % 通配符

下面的 SQL 语句选取 url 以字母 "https" 开始的所有网站：

```
SELECT * FROM Websites
	WHERE url LIKE 'https%';
```

下面的 SQL 语句选取 url 包含模式 "oo" 的所有网站：

```
SELECT * FROM Websites
WHERE url LIKE '%oo%';
```

下面的 SQL 语句选取 name 以一个任意字符开始，然后是 "oogle" 的所有客户：

```
SELECT * FROM Websites

WHERE name LIKE '_oogle';
```

下面的 SQL 语句选取 name 以 "G" 开始，然后是一个任意字符，然后是 "o"，然后是一个任意字符，然后是 "le" 的所有网站：

```
SELECT * FROM Websites
WHERE name LIKE 'G_o_le';
```


## IN 操作符实例

下面的 SQL 语句选取 name 为 "Google" 或 "菜鸟教程" 的所有网站：

```
SELECT * FROM Websites

WHERE name IN ('Google','教程');
```
