[本文地址](https://www.cnblogs.com/xdp-gacl/p/3791993.html)

response实现请求重定向（客户端行为）

```
请求重定向指：一个web资源收到客户端请求后，通知客户端去访问另外一个web资源，这称之为请求重定向。

应用场景：用户登陆，用户首先访问登录页面，登录成功后，就会跳转到某个页面，这个过程就是一个请求重定向的过程

实现方式：response.sendRedirect(String location)，即调用response对象的sendRedirect方法实现请求重定向

sendRedirect内部的实现原理：使用response设置302状态码和设置location响应头实现重定向
```



web工程中URL地址的推荐写法

```
如果"/"是给服务器用的，则代表当前的web工程，如果"/"是给浏览器用的，则代表webapps目录。

①.ServletContext.getRealPath(String path)获取资源的绝对路径
this.getServletContext().getRealPath("/download/1.JPG");

②.在服务器端forward到其他页面
this.getServletContext().getRequestDispatcher("/index.jsp").forward(request, response);

③.使用include指令或者<jsp:include>标签引入页面
```



"/"代表webapps目录的常见应用场景

```
①.使用sendRedirect实现请求重定向
 response.sendRedirect(request.getContextPath()+"/index.jsp");
 
②.使用超链接跳转
<a href="${pageContext.request.contextPath}/index.jsp">跳转到首页</a>

③.Form表单提交
<form action="${pageContext.request.contextPath}/servlet/CheckServlet" method="post">
         <input type="submit" value="提交">
</form>

④.js脚本和css样式文件的引用
<%--使用绝对路径的方式引用js脚本--%>
 <script type="text/javascript" src="${pageContext.request.contextPath}/js/index.js"></script>
 <%--${pageContext.request.contextPath}与request.getContextPath()写法是得到的效果是一样的--%>
 <script type="text/javascript" src="<%=request.getContextPath()%>/js/login.js"></script>
 <%--使用绝对路径的方式引用css样式--%>
 <link rel="stylesheet" href="${pageContext.request.contextPath}/css/index.css" type="text/css"/>
```



cookie vs session

```
Cookie是客户端技术，程序把每个用户的数据以cookie的形式写给用户各自的浏览器。当用户使用浏览器再去访问服务器中的web资源时，就会带着各自的数据去。这样，web资源处理的就是用户各自的数据了。

Session是服务器端技术，利用这个技术，服务器在运行时可以为每一个用户的浏览器创建一个其独享的session对象，由于session为用户浏览器独享，所以用户在访问服务器的web资源时，可以把各自的数据放在各自的session中，当用户再去访问服务器中的其它web资源时，其它web资源再从用户各自的session中取出数据为用户服务。

如果创建了一个cookie，并将他发送到浏览器，默认情况下它是一个会话级别的cookie（即存储在浏览器的内存中），用户退出浏览器之后即被删除。若希望浏览器将该cookie存储在磁盘上，则需要使用maxAge，并给出一个以秒为单位的时间。将最大时效设为0则是命令浏览器删除该cookie。
```



