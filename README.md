# Sql-learn
Sql语句的学习

快速学习网址:  
<http://www.runoob.com/sql/sql-top.html>

# 什么是SQL？
SQL 是用于访问和处理数据库的标准的计算机语言； 
- SQL，指结构化查询语言，全称是 Structured Query Language。
- SQL 让您可以访问和处理数据库。
- SQL 是一种 ANSI（American National Standards Institute 美国国家标准化组织）标准的计算机语言。

# RDBMS
- RDBMS 指关系型数据库管理系统，全称 Relational Database Management System；

# SQL 语法

> use RUNOOB; 命令用于选择数据库。
> set names utf8; 命令用于设置使用的字符集。
> SELECT * FROM Websites; 读取数据表的信息。

# 一些最重要的 SQL 命令
- SELECT - 从数据库中提取数据
- UPDATE - 更新数据库中的数据
- DELETE - 从数据库中删除数据
- INSERT INTO - 向数据库中插入新数据
- CREATE DATABASE - 创建新数据库
- ALTER DATABASE - 修改数据库
- CREATE TABLE - 创建新表
- ALTER TABLE - 变更（改变）数据库表
- DROP TABLE - 删除表
- CREATE INDEX - 创建索引（搜索键）
- DROP INDEX - 删除索引

# SQL SELECT 语句
      SELECT column_name,column_name FROM table_name;
  或
      SELECT * FROM table_name;

# SQL SELECT DISTINCT 语句
在表中，一个列可能会包含多个重复值，有时您也许希望仅仅列出不同（distinct）的值，  
DISTINCT 关键词用于返回唯一不同的值
            SELECT DISTINCT column_name,column_name FROM table_name;

# SQL WHERE 子句
WHERE 子句用于提取那些满足指定标准的记录。
            SELECT * FROM Websites WHERE country='CN';
            
 ### WHERE 子句中的运算符
 
运算符    | 描述
----------- | -------------
= | 等于   
<> | 不等于
> | 大于
< | 小于
>= | 大于等于
<= | 小于等于
BETWEEN | 在某个范围内
LIKE | 搜索某种模式
IN | 指定针对某个列的多个可能值


First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  | Content Cell 
Content Cell  | Content Cell
Content Cell  | Content Cell 
Content Cell  | Content Cell
Content Cell  | Content Cell 


# SQL AND & OR 运算符
如果第一个条件和第二个条件都成立，则 AND 运算符显示一条记录；  
如果第一个条件和第二个条件中只要有一个成立，则 OR 运算符显示一条记录；

> SELECT * FROM Websites WHERE country='XX' AND b > 50;

# SQL ORDER BY 关键字
ORDER BY 关键字用于对结果集按照一个列或者多个列进行排序;  
ORDER BY 关键字默认按照升序对记录进行排序。如果需要按照降序对记录进行排序，您可以使用 DESC 关键字;  
> SELECT column_name,column_name FROM table_name ORDER BY column_name ASC|DESC;  
asc:从小到大的顺序排序  
desc:从大到小的顺序排序  

# SQL INSERT INTO 语法
> INSERT INTO table_name VALUES (value1,value2,value3,...);
或
> INSERT INTO table_name (column1,column2,column3,...) VALUES (value1,value2,value3,...);

# SQL UPDATE 语句
> UPDATE table_name SET column1=value1,column2=value2,...
WHERE some_column=some_value;
                     
# SQL DELETE 语句
用于删除表中的行  
> DELETE FROM table_name WHERE some_column=some_value;
### 删除所有数据
> DELETE FROM table_name;
或
> DELETE * FROM table_name;




