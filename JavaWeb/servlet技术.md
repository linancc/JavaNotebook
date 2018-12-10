

### servlet技术

1. 概述

   全称是server applet，服务器端小程序用于web的交互式访问，动态生成web内容

   需要web服务器支持

   本质上是一个类，是一个特殊的类，继承抽象的父类HttpServlet

   这个类运行在服务器端，可以通过浏览器端的网址来激活/调用这个类的功能

   servlet类是程序员编写，容器（web服务器）来创建对象

   程序员开发servlet，创建一个类，配置和网址的映射关系

   一个类可以有多个url地址关联，一个url网址不能对应多个类

2. 使用

   1. 自定义一个类，继承抽象类HttpServlet，重写doGet() 或者是doGet()方法

3. 常用API【servlet接口和规范】

   https://www.cnblogs.com/haimishasha/p/5609261.html#autoid-3-4-0

   项目中缺失servlet相关的包

   1. 把tomcat的lib目录下的servlet-api.jar拷贝到项目下的lib目录
   2. 当前项目build path环境 --》server runtime

4. 生命周期