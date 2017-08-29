
# mysql 学习

下载地址： http://www.mysql.com/downloads  
Download -> Community ->点击 MySQL Community Server (GPL) 下载

教程地址： http://www.runoob.com/mysql/mysql-install.html

## Window 上安装Mysql
环境变量的配置：
<http://jingyan.baidu.com/article/59a015e34c7973f79488651d.html>

cmd 命令窗口：  
-> net start mysql #启动mysql服务  
-> net stop mysql  #关闭mysql服务

-> mysql -uroot -p  
进入mysql;即连接数据库；

退出 mysql> 命令提示窗口可以使用 exit 命令： mysql> exit

## 操作数据库命令
- 列出 MySQL 数据库管理系统的数据库列表 命令 ：
  mysql> SHOW DATABASES;
  
- USE 数据库名 使员某个数据库 命令：
  mysql> use xxxx;
  
- 显示指定数据库所有表  SHOW TABLES 命令：
  mysql> SHOW TABLES;  
  
- SHOW COLUMNS FROM 数据表:   
    显示数据表的属性，属性类型，主键信息 ，是否为 NULL，默认值等其他信息；  
    mysql> SHOW COLUMNS FROM runoob_tbl;  
    
- SHOW INDEX FROM 数据表:  
  显示数据表的详细索引信息，包括PRIMARY KEY（主键）；  
  mysql> SHOW INDEX FROM runoob_tbl;  
  
-  SHOW TABLE STATUS LIKE [FROM db_name] [LIKE 'pattern'] \G: 
  该命令将输出Mysql数据库管理系统的性能及统计信息；  
  mysql> SHOW TABLE STATUS  FROM RUNOOB;   # 显示数据库 RUNOOB 中所有表的信息  
  mysql> SHOW TABLE STATUS from RUNOOB LIKE 'runoob%';     # 表名以runoob开头的表的信息  
  mysql> SHOW TABLE STATUS from RUNOOB LIKE 'runoob%'\G;   # 加上 \G，查询结果按列打印  
  
## 使用 mysqladmin 创建数据库
  使用root用户登录，root用户拥有最高权限，可以使用 mysql mysqladmin 命令来创建数据库；    
  创建数据库的过程，数据名为 USERMESSAGE: 这是在没有连接数据库的时候创建数据库  
  -> mysqladmin -u root -p create USERMESSAGE  
  删除数据库：  
  -> mysqladmin -u root -p drop USERMESSAGE
  连上数据库时，建立数据库：
  -> mysql> CREATE DATABASE 库名;
  
  - 建立数据表：
  mysql> USE 库名;  
　mysql> CREATE TABLE 表名 (字段名 VARCHAR(20), 字段名 CHAR(1));
 
  - 删除数据库：    
　mysql> DROP DATABASE 库名;

  - 删除数据表：  
　mysql> DROP TABLE 表名;
  
  - 将表中记录清空：  
　mysql> DELETE FROM 表名;
 
 - 往表中插入记录：  
 mysql> INSERT INTO 表名 VALUES ("hyq","M");
 
 - 更新表中数据：  
 mysql-> UPDATE 表名 SET 字段名1='a',字段名2='b' WHERE 字段名3='c';
 
 - 用文本方式将数据装入数据表中：  
 mysql> LOAD DATA LOCAL INFILE "D:/mysql.txt" INTO TABLE 表名;
 
 - 导入.sql文件命令：  
  mysql> USE 数据库名;  
　mysql> SOURCE d:/mysql.sql;
 
 - 命令行修改root密码：  
  　mysql> UPDATE mysql.user SET password=PASSWORD('新密码') WHERE User='root';  
　　mysql> FLUSH PRIVILEGES;
  
## MySQL 数据类型
  MySQL支持多种类型，大致可以分为三类：数值、日期/时间和字符串(字符)类型  
### 数值类型

| 类型 |	大小 |	范围（有符号）	| 范围（无符号）	| 用途 |
| :---- | :------ | :----- | :------ | :-------- |
| TINYINT |	1 字节 |	(-128，127) |	(0，255)	| 小整数值 |
| SMALLINT| 2 字节|(-32 768，32 767)|	(0，65 535)|	大整数值|
|MEDIUMINT	|3 字节|	(-8 388 608，8 388 607)|	(0，16 777 215)|	大整数值|
|INT或INTEGER|	4 字节	|(-2 147 483 648，2 147 483 647)|	(0，4 294 967 295)|	大整数值|
|BIGINT|	8 字节	|(-9 233 372 036 854 775 808，9 223 372 036 854 775 807)|	(0，18 446 744 073 709 551 615)|	极大整数值|
|FLOAT	|4 字节|	(-3.402 823 466 E+38，-1.175 494 351 E-38)，0，(1.175 494 351 E-38，3.402 823 466 351 E+38)	|0，(1.175 494 351 E-38，3.402 823 466 E+38)	|单精度,浮点数值|
|DOUBLE	|8 字节	|(-1.797 693 134 862 315 7 E+308，-2.225 073 858 507 201 4 E-308)，|0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308)	0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308)	|双精度,浮点数值|
|DECIMAL	|对DECIMAL(M,D) ，如果M>D，为M+2否则为D+2	|依赖于M和D的值|	依赖于M和D的值|	小数值|

## 日期和时间类型
表示时间值的日期和时间类型为DATETIME、DATE、TIMESTAMP、TIME和YEAR

|类型|	大小(字节)|	范围|	格式|	用途|
|:----|:-----|:-----|:----|:-----|
|DATE|	3|	1000-01-01/9999-12-31 |	YYYY-MM-DD|	日期值|
|TIME|	3|	'-838:59:59'/'838:59:59'|	HH:MM:SS|	时间值或持续时间|
|YEAR|	1|	1901/2155|	YYYY|	年份值|
|DATETIME|	8|	1000-01-01 00:00:00/9999-12-31 23:59:59|	YYYY-MM-DD HH:MM:SS	混合日期和时间值|
|TIMESTAMP|	4	|1970-01-01 00:00:00/2037 年某时|	YYYYMMDD |HHMMSS	混合日期和时间值，时间戳|

## 字符串类型
  字符串类型指CHAR、VARCHAR、BINARY、VARBINARY、BLOB、TEXT、ENUM和SET;  
  
|类型	|大小|	用途|
|:----|:-----|:-----|
|CHAR|	0-255字节|	定长字符串|
|VARCHAR|	0-65535 字节|	变长字符串|
|TINYBLOB|	0-255字节	|不超过 255 个字符的二进制字符串|
|TINYTEXT|	0-255字节|	短文本字符串|
|BLOB |	0-65 535字节	|二进制形式的长文本数据|
|TEXT |	0-65 535字节	|长文本数据|
|MEDIUMBLOB|	0-16 777 215字节	|二进制形式的中等长度文本数据|
|MEDIUMTEXT|	0-16 777 215字节	|中等长度文本数据|
|LONGBLOB|	0-4 294 967 295字节	|二进制形式的极大文本数据|
|LONGTEXT|	0-4 294 967 295字节	|极大文本数据|
  
## 创建MySQL数据表需要以下信息：
- 表名
- 表字段名
- 定义每个表字段
创建MySQL数据表的SQL通用语法：  
-> CREATE TABLE table_name (column_name column_type);  
eg:  
```javascript
      CREATE TABLE IF NOT EXISTS `runoob_tbl`(
         `runoob_id` INT UNSIGNED AUTO_INCREMENT,
         `runoob_title` VARCHAR(100) NOT NULL,
         `runoob_author` VARCHAR(40) NOT NULL,
         `submission_date` DATE,
         PRIMARY KEY ( `runoob_id` )
      )ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

### 插入数据
插入数据通用的 INSERT INTO SQL语法： 
```javascript
    INSERT INTO table_name ( field1, field2,...fieldN )
                           VALUES
                           ( value1, value2,...valueN );
```

### 查询数据
查询数据通用的 SELECT 语法:  
```javascript
  SELECT column_name,column_name
  FROM table_name
  [WHERE Clause]
  [OFFSET M ][LIMIT N]
```
- 查询语句中你可以使用一个或者多个表，表之间使用逗号(,)分割，并使用WHERE语句来设定查询条件。
- SELECT 命令可以读取一条或者多条记录。
- 你可以使用星号（*）来代替其他字段，SELECT语句会返回表的所有字段数据
- 你可以使用 WHERE 语句来包含任何条件。
- 你可以通过OFFSET指定SELECT语句开始查询的数据偏移量。默认情况下偏移量为0。
- 你可以使用 LIMIT 属性来设定返回的记录数。

### WHERE 子句
使用 WHERE 子句从数据表中读取数据的通用语法：  
```javascript
    SELECT field1, field2,...fieldN FROM table_name1, table_name2...
    [WHERE condition1 [AND [OR]] condition2.....
```
- 查询语句中你可以使用一个或者多个表，表之间使用逗号, 分割，并使用WHERE语句来设定查询条件。
- 你可以在 WHERE 子句中指定任何条件。
- 你可以使用 AND 或者 OR 指定一个或多个条件。
- WHERE 子句也可以运用于 SQL 的 DELETE 或者 UPDATE 命令。
- WHERE 子句类似于程序语言中的 if 条件，根据 MySQL 表中的字段值来读取指定的数据。

注：MySQL 的 WHERE 子句的字符串比较是不区分大小写的。 你可以使用 BINARY 关键字来设定 WHERE 子句的字符串比较是区分大小写的。  
eg: mysql> SELECT * from runoob_tbl WHERE BINARY runoob_author='runoob.com';

### UPDATE 查询
 UPDATE 命令修改 MySQL 数据表数据的通用 SQL 语法：  
```javascript 
    UPDATE table_name SET field1=new-value1, field2=new-value2
    [WHERE Clause]
```
- 你可以同时更新一个或多个字段。
- 你可以在 WHERE 子句中指定任何条件。
- 你可以在一个单独表中同时更新数据。
eg: mysql> UPDATE runoob_tbl SET runoob_title='学习 C++' WHERE runoob_id=3;  

###  DELETE 语句
 SQL DELETE 语句从 MySQL 数据表中删除数据的通用语法：
 ```javascript
 DELETE FROM table_name [WHERE Clause]
```
- 如果没有指定 WHERE 子句，MySQL 表中的所有记录将被删除。
- 你可以在 WHERE 子句中指定任何条件
- 您可以在单个表中一次性删除记录。

###  LIKE 子句
SQL SELECT 语句使用 LIKE 子句从数据表中读取数据的通用语法：  
```javascript
    SELECT field1, field2,...fieldN 
    FROM table_name
    WHERE field1 LIKE condition1 [AND [OR]] filed2 = 'somevalue'
```
- 你可以在 WHERE 子句中指定任何条件。
- 你可以在 WHERE 子句中使用LIKE子句。
- 你可以使用LIKE子句代替等号 =。
- LIKE 通常与 % 一同使用，类似于一个元字符的搜索。
- 你可以使用 AND 或者 OR 指定一个或多个条件。
- 你可以在 DELETE 或 UPDATE 命令中使用 WHERE...LIKE 子句来指定条件。
eg: mysql> SELECT * from runoob_tbl  WHERE runoob_author LIKE '%COM';


###  UNION 操作符
MySQL UNION 操作符语法格式：  
```javascript
    SELECT expression1, expression2, ... expression_n
    FROM tables
    [WHERE conditions]
    UNION [ALL | DISTINCT]
    SELECT expression1, expression2, ... expression_n
    FROM tables
    [WHERE conditions];
```
- expression1, expression2, ... expression_n: 要检索的列。
- tables: 要检索的数据表。
- WHERE conditions: 可选， 检索条件。
- DISTINCT: 可选，删除结果集中重复的数据。默认情况下 UNION 操作符已经删除了重复数据，所以 DISTINCT 修饰符对结果没啥影响。
- ALL: 可选，返回所有结果集，包含重复数据。

### MySQL 排序
SQL SELECT 语句使用 ORDER BY 子句将查询数据排序后再返回数据：  
```javascript
    SELECT field1, field2,...fieldN table_name1, table_name2...
    ORDER BY field1, [field2...] [ASC [DESC]]
```
- 你可以使用任何字段来作为排序的条件，从而返回排序后的查询结果。
- 你可以设定多个字段来排序。
- 你可以使用 ASC 或 DESC 关键字来设置查询结果是按升序或降序排列。 默认情况下，它是按升序排列。
- 你可以添加 WHERE...LIKE 子句来设置条件。

eg: mysql> SELECT * from runoob_tbl ORDER BY submission_date ASC;//升序  
 mysql> SELECT * from runoob_tbl ORDER BY submission_date DES;//降序
 
 ### GROUP BY 语句
 GROUP BY 语句根据一个或多个列对结果集进行分组。
在分组的列上我们可以使用 COUNT, SUM, AVG,等函数。 
```javascript
    SELECT column_name, function(column_name)
    FROM table_name
    WHERE column_name operator value
    GROUP BY column_name;
 ```
 eg: mysql> SELECT name, COUNT(*) FROM   employee_tbl GROUP BY name;
 
### 使用 WITH ROLLUP
WITH ROLLUP 可以实现在分组统计数据基础上再进行相同的统计（SUM,AVG,COUNT…）。
eg: 按名字进行分组，再统计每个人登录的次数：  
mysql> SELECT name, SUM(singin) as singin_count FROM  employee_tbl GROUP BY name WITH ROLLUP;

可以使用 coalesce 来设置一个可以取代 NUll 的名称，coalesce 语法：
```javascript
    select coalesce(a,b,c);
```
参数说明：如果a==null,则选择b；如果b==null,则选择c；如果a!=null,则选择a；如果a b c 都为null ，则返回为null（没意义）。
以下实例中如果名字为空我们使用总数代替：  
eg: mysql> SELECT coalesce(name, '总数'), SUM(singin) as singin_count FROM  employee_tbl GROUP BY name WITH ROLLUP;

##  MySQL 的 JOIN 在两个或多个表中查询数据
JOIN 按照功能大致分为如下三类：
- **INNER JOIN（内连接,或等值连接）：**获取两个表中字段匹配关系的记录。
- **LEFT JOIN（左连接）：**获取左表所有记录，即使右表没有对应匹配的记录。
- **RIGHT JOIN（右连接）：** 与 LEFT JOIN 相反，用于获取右表所有记录，即使左表没有对应匹配的记录。

eg:  
mysql> SELECT a.runoob_id, a.runoob_author, b.runoob_count FROM runoob_tbl a INNER JOIN tcount_tbl b ON a.runoob_author = b.runoob_author;
等价于   
mysql> SELECT a.runoob_id, a.runoob_author, b.runoob_count FROM runoob_tbl a, tcount_tbl b WHERE a.runoob_author = b.runoob_author;

### NULL 值处理
MySQL提供了三大运算符:  
- IS NULL: 当列的值是 NULL,此运算符返回 true。
- IS NOT NULL: 当列的值不为 NULL, 运算符返回 true。
- <=>: 比较操作符（不同于=运算符），当比较的的两个值为 NULL 时返回 true;  
eg: mysql> SELECT * FROM runoob_test_tbl WHERE runoob_count IS NULL;

###  正则表达式
查找name字段中以'st'为开头的所有数据： mysql> SELECT name FROM person_tbl WHERE name REGEXP '^st';
查找name字段中以'ok'为结尾的所有数据： mysql> SELECT name FROM person_tbl WHERE name REGEXP 'ok$';
查找name字段中包含'mar'字符串的所有数据：  mysql> SELECT name FROM person_tbl WHERE name REGEXP 'mar';
查找name字段中以元音字符开头或以'ok'字符串结尾的所有数据：mysql> SELECT name FROM person_tbl WHERE name REGEXP '^[aeiou]|ok$';

### MySQL 事务
MySQL 事务主要用于处理操作量大，复杂度高的数据。  
- 在 MySQL 中只有使用了 Innodb 数据库引擎的数据库或表才支持事务。
- 事务处理可以用来维护数据库的完整性，保证成批的 SQL 语句要么全部执行，要么全部不执行。
- 事务用来管理 insert,update,delete 语句
一般来说，事务是必须满足4个条件（ACID）： Atomicity（原子性）、Consistency（稳定性）、Isolation（隔离性）、Durability（可靠性）  
- **1、事务的原子性：**一组事务，要么成功；要么撤回。
- **2、稳定性 ：**有非法数据（外键约束之类），事务撤回。
- **3、隔离性：**事务独立运行。一个事务处理后的结果，影响了其他事务，那么其他事务会撤回。事务的100%隔离，需要牺牲速度。
- **4、可靠性：**软、硬件崩溃后，InnoDB数据表驱动会利用日志文件重构修改。可靠性和高速度不可兼得， innodb_flush_log_at_trx_commit 选项 决定什么时 候吧事务保存到日志里。  

### 事物控制语句：
- BEGIN或START TRANSACTION；显式地开启一个事务；
- COMMIT；也可以使用COMMIT WORK，不过二者是等价的。COMMIT会提交事务，并使已对数据库进行的所有修改称为永久性的；
- ROLLBACK；有可以使用ROLLBACK WORK，不过二者是等价的。回滚会结束用户的事务，并撤销正在进行的所有未提交的修改；
- SAVEPOINT identifier；SAVEPOINT允许在事务中创建一个保存点，一个事务中可以有多个SAVEPOINT；
- RELEASE SAVEPOINT identifier；删除一个事务的保存点，当没有指定的保存点时，执行该语句会抛出一个异常；
- ROLLBACK TO identifier；把事务回滚到标记点；
- SET TRANSACTION；用来设置事务的隔离级别。InnoDB存储引擎提供事务的隔离级别有READ UNCOMMITTED、READ COMMITTED、REPEATABLE READ和SERIALIZABLE。

### MYSQL 事务处理主要有两种方法：
1、用 BEGIN, ROLLBACK, COMMIT来实现  
- BEGIN 开始一个事务
- ROLLBACK 事务回滚
- COMMIT 事务确认  
2、直接用 SET 来改变 MySQL 的自动提交模式:  
- SET AUTOCOMMIT=0 禁止自动提交
- SET AUTOCOMMIT=1 开启自动提交

### ALTER命令
当我们需要修改数据表名或者修改数据表字段时，就需要使用到MySQL ALTER命令。  

删除，添加或修改表字段   
如下命令使用了 ALTER 命令及 DROP 子句来删除以上创建表的 i 字段：  
  mysql> ALTER TABLE testalter_tbl  DROP i;

MySQL 中使用 ADD 子句来向数据表中添加列，如下实例在表 testalter_tbl 中添加 i 字段，并定义数据类型:  
   mysql> ALTER TABLE testalter_tbl ADD i INT;
   ```javascript
      ALTER TABLE testalter_tbl DROP i;
      ALTER TABLE testalter_tbl ADD i INT FIRST;
      ALTER TABLE testalter_tbl DROP i;
      ALTER TABLE testalter_tbl ADD i INT AFTER c;
 ```
 
### 修改字段类型及名称
如果需要修改字段类型及名称, 你可以在ALTER命令中使用 MODIFY 或 CHANGE 子句 。

eg: 把字段 c 的类型从 CHAR(1) 改为 CHAR(10)，可以执行以下命令: 
  mysql> ALTER TABLE testalter_tbl MODIFY c CHAR(10);
  
  mysql> ALTER TABLE testalter_tbl CHANGE i j BIGINT;

  mysql> ALTER TABLE testalter_tbl CHANGE j j INT;
  
### ALTER TABLE 对 Null 值和默认值的影响
  mysql> ALTER TABLE testalter_tbl MODIFY j BIGINT NOT NULL DEFAULT 100;

修改字段默认值 
  mysql> ALTER TABLE testalter_tbl ALTER i SET DEFAULT 1000;

**注意：**查看数据表类型可以使用 SHOW TABLE STATUS 语句。

### 修改表名
如果需要修改数据表的名称，可以在 ALTER TABLE 语句中使用 RENAME 子句来实现  

mysql> ALTER TABLE testalter_tbl RENAME TO alter_tbl;

### MySQL 索引
#### 创建索引
这是最基本的索引，它没有任何限制。它有以下几种创建方式：  
> CREATE INDEX indexName ON mytable(username(length)); 
如果是CHAR，VARCHAR类型，length可以小于字段实际长度；如果是BLOB和TEXT类型，必须指定 length。  

#### 修改表结构(添加索引)
> ALTER table tableName ADD INDEX indexName(columnName)  
创建表的时候直接指定
```javascript
    CREATE TABLE mytable(  
    ID INT NOT NULL,   
    username VARCHAR(16) NOT NULL,  
    INDEX [indexName] (username(length))  
    );  
```

#### 删除索引的语法
> DROP INDEX [indexName] ON mytable; 

修改表结构  
ALTER table mytable ADD UNIQUE [indexName] (username(length))

#### 使用ALTER 命令添加和删除索引
有四种方式来添加数据表的索引：
- **ALTER TABLE tbl_name ADD PRIMARY KEY (column_list):** 该语句添加一个主键，这意味着索引值必须是唯一的，且不能为NULL。
- **ALTER TABLE tbl_name ADD UNIQUE index_name (column_list): ** 这条语句创建索引的值必须是唯一的（除了NULL外，NULL可能会出现多次）。
- **ALTER TABLE tbl_name ADD INDEX index_name (column_list): ** 添加普通索引，索引值可出现多次。
- **ALTER TABLE tbl_name ADD FULLTEXT index_name (column_list):** 该语句指定了索引为 FULLTEXT ，用于全文索引。

#### 使用 ALTER 命令添加和删除主键
···javascript
  mysql> ALTER TABLE testalter_tbl MODIFY i INT NOT NULL;
  mysql> ALTER TABLE testalter_tbl ADD PRIMARY KEY (i);
  mysql> ALTER TABLE testalter_tbl DROP PRIMARY KEY;
···

#### 显示索引信息
> mysql> SHOW INDEX FROM table_name; \G

#### 临时表
MySQL 临时表在我们需要保存一些临时数据时是非常有用的。临时表只在当前连接可见，当关闭连接时，Mysql会自动删除表并释放所有空间。

#### MySQL 及 SQL 注入
所谓SQL注入，就是通过把SQL命令插入到Web表单递交或输入域名或页面请求的查询字符串，最终达到欺骗服务器执行恶意的SQL命令。

防止SQL注入，我们需要注意以下几个要点：
- 1.永远不要信任用户的输入。对用户的输入进行校验，可以通过正则表达式，或限制长度；对单引号和 双"-"进行转换等。
- 2.永远不要使用动态拼装sql，可以使用参数化的sql或者直接使用存储过程进行数据查询存取。
- 3.永远不要使用管理员权限的数据库连接，为每个应用使用单独的权限有限的数据库连接。
- 4.不要把机密信息直接存放，加密或者hash掉密码和敏感的信息。
- 5.应用的异常信息应该给出尽可能少的提示，最好使用自定义的错误信息对原始错误信息进行包装
- 6.sql注入的检测方法一般采取辅助软件或网站平台来检测，软件一般采用sql注入检测工具jsky，网站平台就有亿思网站安全平台检测工具。MDCSOFT SCAN等。
   采用 MDCSOFT-IPS可以有效的防御SQL注入，XSS攻击等。


#### MySQL 导出数据
使用 SELECT ... INTO OUTFILE 语句导出数据  
> mysql> SELECT * FROM runoob_tbl INTO OUTFILE '/tmp/tutorials.txt';

mysql> SELECT * FROM passwd INTO OUTFILE '/tmp/tutorials.txt'
     FIELDS TERMINATED BY ',' ENCLOSED BY '"'
     LINES TERMINATED BY '\r\n';

SELECT a,b,a+b INTO OUTFILE '/tmp/result.text'
FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"'
LINES TERMINATED BY '\n'
FROM test_table;
 
### SELECT ... INTO OUTFILE 语句有以下属性:
- LOAD DATA INFILE是SELECT ... INTO OUTFILE的逆操作，SELECT句法。为了将一个数据库的数据写入一个文件，使用SELECT ... INTO OUTFILE，为了将文件读回数据库，使用LOAD DATA INFILE。
- SELECT...INTO OUTFILE 'file_name'形式的SELECT可以把被选择的行写入一个文件中。该文件被创建到服务器主机上，因此您必须拥有FILE权限，才能使用此语法。
- 输出不能是一个已存在的文件。防止文件数据被篡改。
- 你需要有一个登陆服务器的账号来检索文件。否则 SELECT ... INTO OUTFILE 不会起任何作用。
- 在UNIX中，该文件被创建后是可读的，权限由MySQL服务器所拥有。这意味着，虽然你就可以读取该文件，但可能无法将其删除。

### 导出表作为原始数据
mysqldump是mysql用于转存储数据库的实用程序。它主要产生一个SQL脚本，其中包含从头重新创建数据库所必需的命令CREATE TABLE INSERT等。
```javascript
  $ mysqldump -u root -p --no-create-info \  
              --tab=/tmp RUNOOB runoob_tbl  
  password ******
```
#### 导出SQL格式的数据
```javascript
  $ mysqldump -u root -p RUNOOB runoob_tbl > dump.txt
  password ******
```

### 将数据表及数据库拷贝至其他主机
如果你需要将数据拷贝至其他的 MySQL 服务器上, 你可以在 mysqldump 命令中指定数据库名及数据表。
在源主机上执行以下命令，将数据备份至 dump.txt 文件中:
```javascript
$ mysqldump -u root -p database_name table_name > dump.txt
password *****
```  
如果你需要将备份的数据库导入到MySQL服务器中，可以使用以下命令，使用以下命令你需要确认数据库已经创建：
```javascript
$ mysql -u root -p database_name < dump.txt
password *****

//你也可以使用以下命令将导出的数据直接导入到远程的服务器上，但请确保两台服务器是相通的，是可以相互访问的：</p>

$ mysqldump -u root -p database_name \
       | mysql -h other-host.com database_name
```
以上命令中使用了管道来将导出的数据导入到指定的远程主机上。

#### 使用 LOAD DATA 导入数据
MySQL 中提供了LOAD DATA INFILE语句来插入数据。 以下实例中将从当前目录中读取文件 dump.txt ，将该文件中的数据插入到当前数据库的 mytbl 表中。
 
 > mysql> LOAD DATA LOCAL INFILE 'dump.txt' INTO TABLE mytbl;

如果指定LOCAL关键词，则表明从客户主机上按路径读取文件。如果没有指定，则文件在服务器上按路径读取文件。  
你能明确地在LOAD DATA语句中指出列值的分隔符和行尾标记，但是默认标记是定位符和换行符。  
两个命令的 FIELDS 和 LINES 子句的语法是一样的。两个子句都是可选的，但是如果两个同时被指定，FIELDS 子句必须出现在 LINES 子句之前。  


### 使用 mysqlimport 导入数据
mysqlimport客户端提供了LOAD DATA INFILEQL语句的一个命令行接口。mysqlimport的大多数选项直接对应LOAD DATA INFILE子句。

```
$ mysqlimport -u root -p --local database_name dump.txt
password *****

$ mysqlimport -u root -p --local --fields-terminated-by=":" \
   --lines-terminated-by="\r\n"  database_name dump.txt
password *****

$ mysqlimport -u root -p --local --columns=b,c,a \
    database_name dump.txt
password *****

```

### mysqlimport的常用选项介绍





