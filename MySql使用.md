]

MySQL配置

```mysql
my.ini文件  注意：MySql5.7文件在隐藏文件夹ProgramData中

[mysql]
default-character-set=utf8

[mysqld]
character-set-server=utf8

default-storage-engine=InnoDB/MYISAM  默认存储引擎
```

查看xxx的设置

```mysql
SHOW VARIABLES LIKE 'character_set_%'; 查看字符集的设置
SHOW VARIABLES LIKE 'storage_engine%'; 查看默认存储引擎
```

常用命令

```mysql
FIND：找到 SELECT：查询 ALTER：修改 DESC：查看
TRUNCATE 删表重建
DELETE 删除数据行
SET　NAMES gbk; DOS窗口编码
HELP xx; 帮助信息
status 系统信息
show status 运行状态
\c 跳出执行
```

```mysql
数据库模式定义语言DDL(Data Definition Language)
数据操纵语言DML(Data Manipulation Language)
数据查询语言DQL(Data Query Language)
```

主键

```
又叫主码，用来唯一标识某一行记录，与业务无关的列；
主键不能重复，主键默认自带索引
主键的列，可以一列，也可以多列（复合主键），强烈不推荐
主键设计时，强烈推荐使用数字类型（int bigint）
每张表只能有一个主键，强烈建议，必须加主键，名称为id
```

外键

```
相对于主键而言，主键的数据在从表中的表现形式
主表 主键 数据  ----》 从表 外键
外键又叫引用完整性
```

关系型数据库管理系统【RDBMS】

```
最核心的概念是表、二维表、二维数组，包含行和列
行：实体，记录，元祖
列：字段
关系型数据库就是由多张表组成的，表和表之间是有关系的
关系 --》 引用 --》 指针
维护关系：主-外键关系
表现形式：
	1.通过结构来维护 添加主外键约束
	2.通过数据来维护
		从表中的外键列保存的数据必须是主表中主键列存在的数据
```

创建数据库

```mysql
CREATE DATABASE [IF NOT EXISTS] 数据库名 [DEFAULT CHARACTER SET 字符集];
```

修改数据库

```mysql
ALTER DATABASE 数据库名 CHARACTER SET 字符集;
```

删除数据库

```mysql
#删除数据库，会把该数据库所有的对象（表、索引、视图、自定义函数、存储过程。。。）全部删除
#删除结构和数据，要慎重
DROP DATABASE [IF EXISTS] 数据库名;
```

创建表

```mysql
DROP TABLE IF EXISTS 表名；
CREATE TABLE 表名(
#省略代码
)CHARSET=字符集名；
```

查看表

```mysql
SHOW TABLES;
DESCRIBE 表名;
DESC 表名;
```

删除表

```mysql
DROP TABLE IF EXISTS 表名;
```

修改表

```mysql
ALTER TABLE 旧表名 RENAME 新表名; 修改表名

ALTER TABLE 表名 ADD 字段名 数据类型【属性】; 添加字段
ALTER TABLE 表名 ADD　CONSTRAINT 主键名 PRIMARY KEY 表名（主键字段）; 添加主键约束
ALTER TABLE 表名 ADD　CONSTRAINT 外键名 FOREIGN KEY 表名（主键字段）; 添加外键约束

ALTER TABLE 表名 DROP 字段名; 删除字段

ALTER TABLE 表名 CHANGE 原字段名 新字段名 数据类型【属性】; 修改字段
```

DML插入数据

```mysql
INSERT INTO 表名[(字段名列表)] VALUES (值列表)； 插入单行数据
INSERT INTO 新表[(字段名列表)] VALUES (值列表1)，(值列表2)，。。。(值列表n)； 插入多行数据
CREATE TABLE 新表(SELECT 字段1，字段2，。。FROM 原表)；将查询结果插入到新表
```

DML更新数据

```mysql
UPDATE 表名 SET 列名 = 更新值 [WHERE 更新条件]; 
```

DML删除数据

```mysql
DELETE [FROM] 表名 [WHERE <删除条件>];
TRUNCATE TABLE student; 执行速度快，占用资源少，删除数据后表的标识列重新开始编号
注意：删除所有行，功能上类似没有 WHERE 子句的 DELETE 语句；不建议使用，数据不能恢复还原
```

DQL查询语句

```mysql
SELECT <列名|表达式|函数|常量>
FROM <表名>
[WHERE<查询条件表达式>]   #可选的
[ORDER BY <排序的列名>[ASC 或 DESC]]；  #排序的

SELECT * FROM student; 查询所有的数据行和列

SELECT studentNO，studentName,address FROM student WHERE adress ='河南新乡';  查询部分行和列

SELECT firstName+‘.’+lastName AS 姓名 FROM employee;  查询中使用列的别名

SELECT studentName FROM student WHERE email IS NULL; 查询空值

SELECT studentName AS 姓名,address AS 地址,'北京新兴桥' AS 学校名称 FROM student;在查询中使用常量列
```

常用函数

1. 聚合函数

   | 函数名  | 作用   |
   | ------- | ------ |
   | AVG()   | 平均值 |
   | COUNT() | 行数   |
   | MAX()   | 最大值 |
   | MIN()   | 最小值 |
   | SUM()   | 和     |

2. 字符串函数

   | 函数名                     | 作用                                                         | 举例                                                         |
   | -------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
   | CONCAT(str1,str2,...,strn) | 连接字符串为一个完整的字符串                                 | SELECT CONCAT('My','S','QL');返回：MySQL                     |
   | INSERT(str,pos,len,newstr) | 将字符串str从pos位置开始，len个字符长的子串替换为字符串newstr | SELECT INSERT('这是Oracle数据库',3,6,'MySQL数据库');返回：这是MySQL数据库 |
   | LOWER(str)                 | 将字符串str中的所有字符变为小写                              | SELECT LOWER('MySQL');返回：mysql                            |
   | UPPER(str)                 | 将字符串str中所有字符变为大写                                | SELECT UPPER('MySQL');返回：MYSQL                            |
   | SUBSTRING(str,num,len)     | 返回字符串str的第num个位置开始长度为len的子字符串            | SELECT SUBSTRING('JavaMySQLOracle',5,5);                     |

3. 时间日期函数

   | 函数名                | 作用                               | 举例                              |
   | --------------------- | ---------------------------------- | --------------------------------- |
   | CURDATE()             | 获取当前日期                       | SELECT CURDATE();返回：2016-08-08 |
   | CURTIME()             | 获取当前时间                       | SELECT CURTIME();返回：19:19:26   |
   | NOW()                 | 获取当前日期和时间                 |                                   |
   | WEEK(date)            | 获取日期date为一年中的第几周       |                                   |
   | YEAR(date)            | 返回日期date的年份                 |                                   |
   | HOUR(time)            | 返回时间time的小时值               |                                   |
   | MINUTE(time)          | 返回时间time的分钟值               |                                   |
   | DATEDIFF(date1,date2) | 返回日期date1和date2之间相隔的天数 |                                   |
   | ADDDATE(date,n)       | 计算日期参数date加上n天后的日期    |                                   |

4. 数学函数

   | 函数名   | 作用                          | 举例                         |
   | -------- | ----------------------------- | ---------------------------- |
   | CEIL(x)  | 返回大于或等于数值x的最小整数 | SELECT CEIL(2.3);   返回：3  |
   | FLOOR(x) | 返回小于或等于数值x的最大整数 | SELECT FLOOR(2.3);   返回：2 |
   | RAND()   | 返回0-1之间的随机数           |                              |

高级查询

EXISTS子查询

```mysql
DROP TABLE IF EXISTS temp;

SELECT ... FROM 表名 WHERE EXISTS (子查询);
```

NOT EXISTS子查询



分组查询

使用GROUP BY进行分组查询



多列分组查询



使用HAVING子句进行分组筛选



多表连接查询



内连接查询



外连接查询



事务

```
事务是一种机制、一个操作序列，它包含了一组数据库操作命令，并且把所有得命令作为一个整体一起向系统提交或撤销操作请求

数据库事物具有如下特性（ACID）
1.原子性
2.一致性
3.隔离性
4.持久性

使用下列语句来管理事务
BEGIN 或 START TRANSACTION（开始事务）
COMMIT（提交事务）
ROLLBACK（回滚事务）
或者使用SET autocommit=0 设置自动提交关闭，进行事务提交或回滚后，在使用SET autocommit=1 开启自动提交
```

视图

```
视图是一种查看数据库一个或多个表中数据的方法
视图是一种虚拟表，通常作为执行查询的结果而创建的
视图充当着查询中指定表的筛选器
使用 CREATE VIEW 语句创建视图
使用 SELECT 语句查看视图的查询结果
```

索引

```
建立索引有助于快速检索数据；索引分为普通索引、唯一索引、主键索引、复合索引、全文索引、空间索引
```

备份和恢复

```
常用的数据库备份和恢复方式使用 mysqldump 命令备份数据库
使用 mysql 命令恢复数据库
通过复制文件实现数据备份和恢复

表数据的导出和导入
使用 SELECT 。。。INTO OUTFILE 语句实现表数据的导出
使用 LOAD DATA INFILE 。。。INTO 语句实现表数据的导入
```

