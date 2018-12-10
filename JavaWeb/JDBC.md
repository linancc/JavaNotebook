## JDBC

1. 概念

   JDBC（Java DataBase Connectivity，java数据库连接）

   java提供操作数据库的一套完整API

   提供统一的访问接口，兼容主流数据库厂商（MySQL、Oracle、SQL Server、db2）

   访问具体的数据库，该数据库厂商必须提供jdbc驱动实现

   微软操作数据库的接口：**ODBC**（Open Database Connectivity，开放数据库互连）

2. 分类

   1. 本地API（操作系统底层实现，C语言）
   2. JDBC-ODBC桥（通过ODBC桥来连接数据库；效率不高，移植性差）
   3. 本地纯java驱动（强烈推荐）
   4. 基于网络的java驱动

3. 相关API

   1. Connection 数据库连接
   2. Statement 命令语句对象
   3. PreparedStatement 预处理语句对象（执行sql对象）
   4. ResultSet 记录集对象（封装查询结果，迭代器/游标）
   5. DatabaseMetaData（封装数据库的元数据：数据库本身的一些信息：数据库厂商、版本号）
   6. ResultSetMetaData（封装记录集的元数据：表/视图本身的一些信息：列名，列的数据类型。。。）

4. 使用

   1. 下载驱动（jar文件）

      [MVNRepository](https://mvnrepository.com/)

   2. 驱动保存到工程

      非web项目：保存到自建lib文件夹  ===》add to build path

      web项目：保存到 项目名称/WebContent/WEB-INF/lib文件夹下

      maven项目：在项目的pom.xml追加驱动坐标（maven自动下载驱动）

   3. 在代码中使用

   4. 加载驱动的三种方式

5. 乱码和验证

   1. 出现乱码，排查思路

      数据库编码、表的编码、jdbc url中的编码

   2. mysql5.6+版本有ssl验证和加密功能，出现红色警告

      url地址后追加;useSSL=false(开发时把会话通道关闭)

   3. mysql8.0连接不上

      url地址后追加：serverTimezone=UTC

------

## DAO

Data Access Object 数据访问对象，java操作数据库的代码

是一种分层的思想；属于数据持久化层

最基本的实现：CURD 【增删改查】

增删改查

​	添加 insert()

​	修改 update()

​	删除 delete()

​	查询 select()



------

### Java读取properties配置文件

1. [几种读取properties的方式](https://blog.52itstyle.com/archives/879/)
2. [大牛笔记：properties文件读取](http://www.daniubiji.cn/archives/357)

```properties
#db_config.properties
jdbc.url=jdbc:mysql://localhost:3306/test?useSSL=false
jdbc.username=root
jdbc.password=123456
jdbc.driver=com.mysql.jdbc.Driver
```



```java
import java.io.FileNotFoundException;
import java.io.IOException;
import java.io.InputStream;
import java.util.Properties;

public class ReadDemo {
	public static void main(String[] args) throws FileNotFoundException {
		Properties prop = new Properties();
		InputStream is = Thread.currentThread().getContextClassLoader().getResourceAsStream("db_config.properties");
//		InputStream is = new FileInputStream(new File("db_config.peroperties"));
		try {
			prop.load(is);
		} catch (IOException e) {
			e.printStackTrace();
		}
		System.out.println(prop.getProperty("jdbc.url"));
		System.out.println(prop.getProperty("jdbc.username"));
		System.out.println(prop.getProperty("jdbc.password"));
		System.out.println(prop.getProperty("jdbc.driver"));
	}
}
```

