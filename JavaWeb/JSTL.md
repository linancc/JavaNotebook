### JSTL

1. 概述

   JSTL（JavaServer Pages Standard Tag Library，JSP标准[标签库](https://baike.baidu.com/item/%E6%A0%87%E7%AD%BE%E5%BA%93/5088969))

   开放源代码的JSP标签库，是由apache的jakarta小组来维护

   在JSP 2.0中也是作为标准支持的。

   JSTL有流程控制，一般和EL表达式配合使用

   主要目标：代替jsp脚本，简化代码，用来展示数据【从四大作用域中获取数据】

2. 分类

   core标签  核心标签库  【重要，必学】

   fmt标签  格式化标签	【日期、数字格式化】

   sql标签  数据库操作的标签	【违反了分层思想，安全性差，不推荐使用】

   xml标签  解析xml标签库	【xml是核心的配置文件，不推荐前台调用】

   fn标签  字符串的函数标签	【把后台字符串处理函数用在前台，推荐使用】

3. 使用

   1. 下载JSTL标签库的jar包

   2. 把JSTL的jar包放到lib文件夹下

      jstl.jar

      standard.jar

   3. 核心标签[jsp页面顶部]

      ```
      <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
      <%@ taglib prefix="sql" uri="http://java.sun.com/jsp/jstl/sql" %>
      <%@ taglib prefix="x" uri="http://java.sun.com/jsp/jstl/xml" %>
      <%@ taglib prefix="fn" uri="http://java.sun.com/jsp/jstl/functions" %>
      ```

   4. 在jsp中使用JSTL标签
   5. core标签使用

      1. c:out	标签	输出作用域变量的值

   流程控制有关的

   ```
   1. c:if
   
   2. c:choose   多条件判断  相当于if 。。else  if 。。else。。+ switch
   
      c:when  嵌套在choose内部
   
      c:otherwise  
   
   3. c:forEach  c:forTokens
   ```

   其它标签

   ```
   c:redirect
   c:import
   c:catch
   C:url
   ```

   格式化标签fmt

   ```
   日期格式化
   fmt：formateDate
   fmt:Number
   ```

   字符串处理函数标签 fn

   ```
   fn:contains()	测试指定的字符串是否包含指定的字符
   fn:length()	长度
   fn:replace()	替换
   fn:spilt()	字符串拆分
   fn:trim()	移除首位空白符
   ```
