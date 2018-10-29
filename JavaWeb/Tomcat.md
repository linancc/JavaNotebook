## 安装后配置

![Tomcat配置](https://raw.githubusercontent.com/linancc/images/master/JavaNotebook_img/tomcat.png)

## 默认 tomcat-user.xml 中的角色和用户配置示例如下：

```xml
<!--
  <role rolename="tomcat"/>
  <role rolename="role1"/>
  <user username="tomcat" password="<must-be-changed>" roles="tomcat"/>
  <user username="both" password="<must-be-changed>" roles="tomcat,role1"/>
  <user username="role1" password="<must-be-changed>" roles="role1"/>
-->
```

如果仅把上述内容去掉并修改密码，重启tomcat后访问http://localhost:8081/manager/html，会报403 Access Denied无法登录管理界面。

正确的配置如下：

```xml
<role rolename="manager-gui"/>
<role rolename="manager-script"/>
<role rolename="manager-jmx"/>
<role rolename="manager-status"/>
<user username="admin" password="123456" roles="manager-gui,manager-script,manager-jmx,manager-status"/>
```

原因是tomcat8中定义了以下4种角色，所以配置文件中的角色名称是不能任意填写的。



## 关于配置Tomcat的URIEncoding

遇到的问题：
​       程序需要发送http GET请求到服务器，请求的参数中包含了中文字符。程序中参数为UTF-8格式，且经过了UTF-8 URL编码再发送。使用的tomcat服务器，但服务器端后台程序中取到的参数的中文是乱码。

问题原因：
经过分析，应该是Tomcat在解析参数的时候没有使用正确的编码格式（UTF-8）去解码。

查看$TOMCAT_HOME/webapps/tomcat-docs/config/http.html这个说明文档，有如下说明： 
URIEncoding：This specifies the character encoding used to decode the URI bytes, after %xx decoding the URL. If not specified, ISO-8859-1 will be used.

也就是说，如果没有设置URIEncoding， Tomcat默认是按ISO-8859-1进行URL解码，ISO-8859-1并未包括中文字符，这样的话中文字符肯定就不能被正确解析了。

解决办法：
修改Tomcat的Server.xml，在Connector标签中加上URLEncoding参数：

<Connector connectionTimeout="20000" port="8081" protocol="HTTP/1.1" redirectPort="8443" URIEncoding="UTF-8"/>



## 配置tomcat端口为80

server.xml 文件
修改 <Connector port="80" protocol="HTTP/1.1"
​               connectionTimeout="20000"
​               redirectPort="8443" />


