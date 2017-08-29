
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



