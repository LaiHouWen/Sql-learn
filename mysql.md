
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
| TINYINT |	1 字节 |	(-128，127) |	(0，255)	| 小整数值 |
  
  
  
  
