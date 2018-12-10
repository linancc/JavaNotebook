Spring 创建对象的三种方式

1. 构造方法
   1. 无参
   2. 有参
2. 实例工厂
3. 静态工厂



装配 Bean

1. 在 XML 进行显式配置

2. 在 Java 中进行显式配置

3. 隐式 bean 发现机制和自动装配

   建议：尽可能使用自动配置机制，显式配置越少越好；必须显式配置，推荐使用类型安全并且比XML更加强大的 JavaConfig

自动化装配 Bean

1. 组件扫描

2. 自动装配

   ```java
   @Component  组件扫描默认不启用，需要显式配置 Spring
   @Component("lonelyHeartsClub") 	bean设置不同的ID 
   Spring支持将@Named作为@Component注解的替代方案
   
   @Configuration
   @ComponentScan 注解启用了组件扫描
   
   XML来启用组件扫描 使用Spring context命名空间的 
   	<context:component-scan base-package="com.how2java.service"> 元素
   
   @Autowired
   Spring同时支持@Inject和@Autowired
   ```




面向切面编程（AOP）

1. 原有功能：切点 pointcut
2. 前置通知：在切点之前执行的功能，before advice
3. 后置通知：在切点之后执行的功能，after advice
4. 如果切点执行过程中出现异常，会触发异常通知 throws advice
5. 所有功能的总称叫切面
6. 织入：把切面嵌入原有功能的过程



Spring MVC 

1. 前端控制器







分页

分类

1. 真分页：分段获取每页数据，在页面展示；数据库连接次数较多 ，每页获取数据较少
2. 假分页：后台一次性获取所有数据，在页面进行拆分；数据量大，页面加载会比较慢

业务逻辑

1. 前台页面分页样式

   首页 上一页 下一页 尾页 总页数 当前页 总记录数  请求页

2. 后台分页 Java 代码

   数据总数，分段列表结果

3. 数据库分页

   数据总数  select count(*) from user where ...

   分段列表  select * from  users where .. limit 分页起点，记录数

```
Spring jar包官网下载地址：
http://repo.spring.io/release/org/springframework/spring/

Spring jar包的描述：针对3.2.2以上版本
org.springframework spring-aop ——Spring的面向切面编程,提供AOP(面向切面编程)实现
org.springframework spring-aspects —— Spring提供对AspectJ框架的整合
org.springframework spring-beans —— SpringIoC(依赖注入)的基础实现
org.springframework spring-context —— Spring提供在基础IoC功能上的扩展服务，此外还提供许多企业级服务的支持，如邮件服务、任务调度、JNDI定位、EJB集成、远程访问、缓存以及各种视图层框架的封装等
org.springframework spring-context-support —— Spring-context的扩展支持,用于MVC方面
org.springframework spring-core —— Spring的核心组件
org.springframework spring-expression —— Spring表达式语言
org.springframework spring-instrument —— Spring对服务器的代理接口
org.springframework spring-instrument-tomcat —— Spring对Tomcat的连接池的集成
org.springframework spring-jdbc —— JDBC支持包，包括数据源设置和JDBC访问支持
org.springframework spring-jms —— JMS支持包，包括辅助类来发送和接收JMS消息
org.springframework spring-messaging —— 信息体系结构和协议的支持
org.springframework spring-orm —— 对象/关系映射，整合第三方的ORM框架，如hibernate,ibatis,jdo，以及spring的JPA实现
org.springframework spring-oxm —— 对象的XML映射，可以让Java与XML之间来回切换
org.springframework spring-test —— 对于单元测试和集成测试的简单封装
org.springframework spring-tx —— 为JDBC、Hibernate、JDO、JPA等提供的一致的声明式和编程式事务管理
org.springframework spring-web —— SpringMVC支持WEB端应用部署架构
org.springframework spring-webmvc —— REST Web服务和Web应用的视图控制器的实现
org.springframework spring-webmvc-portlet —— SpringMVC的增强--MVC的实现作为一个Portlet的环境
org.springframework spring-websocket —— sockjs WebSocket的实现,包括对 STOMP的支持

Spring依赖包的描述：
aopalliance.jar —— AOP联盟的API包，里面包含了针对面向切面的接口。通常Spring等其它具备动态织入功能的框架依赖此包。
aspectjweaver-1.5.0.jar —— 用于在Spring 中集成AspectJ AspectJ LTW织入器
cglib-3.1.jar —— cglib代理 实现AOP的一种方式
commons-collections-3.2.2.jar —— Apache Commons包中的一个，包含了一些Apache开发的集合类，功能比java.util.*强大。
commons-dbcp-1.2.1.jar —— DBCP数据库连接池
commons-logging-1.1.1.jar —— Apache Commons包中的一个，包含了日志功能
commons-pool-1.6.jar —— DBCP是一个依赖commons-pool对象池机制的数据库连接池
standard.jar —— JSP 标准标签库，和jstl.jar 一起使用，jstl-1.2.jar 不在需要。
```

