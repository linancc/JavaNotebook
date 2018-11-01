[Mysql多表查询](https://www.cnblogs.com/smyhvae/p/4042303.html)

MySQL配置

```mysql
my.ini文件  注意：MySql5.7文件在隐藏文件夹ProgramData中

#客户端默认字符集
[mysql]
default-character-set=utf8

#服务器端默认字符集
[mysqld]
character-set-server=utf8

#客户端和服务器端的端口号
port：3306

#默认存储引擎
default-storage-engine=InnoDB/MYISAM  
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

InnoDB和MyISAM存储引擎比较

|     功能     | InnoDB | MyISAM |
| :----------: | :----: | :----: |
|   支持事务   |  支持  | 不支持 |
| 支持全文索引 | 不支持 |  支持  |
|   外键约束   |  支持  | 不支持 |
|  表空间大小  |  较大  |  较小  |
|  数据行锁定  |  支持  | 不支持 |

InnoDB和MyISAM各自的使用场合如下

```
InnoDB存储引擎，该存储引擎在事务处理上有优势，即支持具有提交、回滚和崩溃恢复能力的事务安装，所以占用更多的磁盘空间，因此需要进行频繁的更新、删除操作，同时还对事务的完整性要求较高，需要实现并发控制，适合使用该存储引擎

MyISAM存储引擎，该存储引擎不支持事务，也不支持外键，访问速度比较快，因此对不需要进行事务处理，以访问为主的应用适合使用该引擎
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

DISTINCT 唯一数据【去除重复得数据】

SELECT NOW(),SYSDATE(),CURDATE(),CURTIME()
#dual是一张虚表
#sysdate()/dual  ORACLE的
SELECT NOW(),SYSDATE(),CURDATE(),CURTIME() FROM dual;
```

limit 限定数据行数 【top ten，分页】

```
LIMIT 4,4;从第五条记录开始显示四条数据，第一条记录位置是0；

top ten：先排序，再获取限定数据
MySQL: 
SQL server:
Oracle: order by
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

子查询：

```mysql
1.概念
	sql语句中嵌套sql语句：可以出现在sql语句的任何地方
	可以操作的sql语句有：insert，update，delete，
	子查询可以用在单表操作，也可以用在多表操作中
	
2.形式
	1.select 后面
	2.from 后面
	3.where 后面
	4.in
	5.exists
	6.insert

```



EXISTS子查询

```mysql
DROP TABLE IF EXISTS temp;

SELECT ... FROM 表名 WHERE EXISTS (子查询);
```

NOT EXISTS子查询



分组查询

使用GROUP BY进行分组查询

```mysql
SELECT subjectNo,AVG(studentResult) AS 课程平均成绩
FROM result
GROUP BY subjectNo;
```

多列分组查询



使用HAVING子句进行分组筛选

```
having 分组条件
1.一般情况下having可以替代where，复杂查询【同时存在】不能替代，不推荐
2.having 仅限于针对分组得结果进行分组过滤，不能替代where
```

多表连接查询



内连接查询



外连接查询







数据库表之间的关系

```
1.分类
	a.1对1关系
		生活中：一夫一妻，一人一证
    b.1对n关系
    	生活中：1个老师：n个学生，一个老板：n个公司
    c.m对n关系【相互的1：n的关系】
    	生活中：1个老师：n个学生（1：n）；一个学生：n个老师（1：n）
    	数据库：主外键关系；3张表；在第三张关联表中有多条数据与前两张表进行关联
```

查询

```mysql
#1.内连接（inner join）
	select * from 主表 t1，附表t2 where t1.主键=t2.外键[条件];
	select * from 主表 t1 [inner] join 附表 t2 on t1.主键=t2.外键[条件];
	
#2.左外部连接（left [outer] join）: 以主表为主，右表为辅；右表没有对应数据，为null
	SELECT * FROM employee t1 LEFT OUTER JOIN salary t2 ON t1.id=t2.eid;
	
#3.右外部连接（right [outer] join）: 以右表为主，左表为辅，左表没有对应数据，为null
	SELECT * FROM employee t1 RIGHT OUTER JOIN salary t2 ON t1.id=t2.eid;
	
#4.全连接（full [outer] join）：全连接没有主次关系，MySQL暂不支持
	SELECT * FROM employee t1 FULL JOIN salary t2 ON t1.id=t2.eid;
	
#5.交叉表连接（cross join 笛卡尔集 2表数据连接）
	SELECT * FROM 主表 t1 CROSS JOIN salary;
	
#6.关联连接（union多个查询结果的关联，列数相同,数据类型可以转化;查询结果堆积,查询）
```

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

