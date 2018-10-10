MySQL配置

```
my.ini文件  注意：MySql5.7文件在隐藏文件夹ProgramData中

[mysql]
default-character-set=utf8

[mysqld]
character-set-server=utf8

default-storage-engine=InnoDB/MYISAM  默认存储引擎
```

查看xxx的设置

```
SHOW VARIABLES LIKE 'character_set_%'; 查看字符集的设置
SHOW VARIABLES LIKE 'storage_engine%'; 查看默认存储引擎
```

常用命令

```
FIND：找到 SELECT：查询 ALTER：修改 DESC：查看
TRUNCATE 删表重建
DELETE 删除数据行
SET　NAMES gbk; DOS窗口编码
HELP xx; 帮助信息
\c 跳出执行
```

```
数据库模式定义语言DDL(Data Definition Language)
数据操纵语言DML(Data Manipulation Language)
数据查询语言DQL(Data Query Language)
```

创建表

```
DROP TABLE IF EXISTS 表名；
CREATE TABLE 表名(
#省略代码
)CHARSET=字符集名；
```

查看表

```
SHOW TABLES;
DESCRIBE 表名;
DESC 表名;
```

删除表

```
DROP TABLE IF EXISTS 表名;
```

修改表

```
ALTER TABLE 旧表名 RENAME 新表名; 修改表名

ALTER TABLE 表名 ADD 字段名 数据类型【属性】; 添加字段
ALTER TABLE 表名 ADD　CONSTRAINT 主键名 PRIMARY KEY 表名（主键字段）; 添加主键约束
ALTER TABLE 表名 ADD　CONSTRAINT 外键名 FOREIGN KEY 表名（主键字段）; 添加外键约束

ALTER TABLE 表名 DROP 字段名; 删除字段

ALTER TABLE 表名 CHANGE 原字段名 新字段名 数据类型【属性】; 修改字段
```

DML插入数据

```
INSERT INTO 表名[(字段名列表)] VALUES (值列表)； 插入单行数据
INSERT INTO 新表[(字段名列表)] VALUES (值列表1)，(值列表2)，。。。(值列表n)； 插入多行数据
CREATE TABLE 新表(SELECT 字段1，字段2，。。FROM 原表)；将查询结果插入到新表
```

DML更新数据

```
UPDATE 表名 SET 列名 = 更新值 [WHERE 更新条件]; 
```

DML删除数据

```
DELETE [FROM] 表名 [WHERE <删除条件>];
TRUNCATE TABLE student; 执行速度快，占用资源少，删除数据后表的标识列重新开始编号
注意：删除所有行，功能上类似没有 WHERE 子句的 DELETE 语句；不建议使用，数据不能恢复还原
```

DQL查询语句

```
SELECT <列名|表达式|函数|常量>
FROM <表名>
[WHERE<查询条件表达式>]   #可选的
[ORDER BY <排序的列名>[ASC 或 DESC]]；  #排序的

SELECT * FROM student; 查询所有的数据行和列

SELECT studentNO，studentName,address FROM student WHERE adress ='河南新乡';  查询部分行和列

SELECT firstName+‘.’+lastName AS 姓名 FROM employee;  查询中使用列的别名

SELECT studentName FROM student WHERE email IS NULL; 查询空值
```

