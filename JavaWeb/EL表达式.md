### EL表达式

1. 概念

   ```
   表达式语言（Expression Language），或称EL表达式，简称EL，是Java中的一种特殊的通用编程语言，借鉴于JavaScript和XPath。主要作用是在Java Web应用程序嵌入到网页（如JSP）中，用以访问页面的上下文以及不同作用域中的对象 ，取得对象属性的值，或执行简单的运算或判断操作。EL在得到某个数据时，会自动进行数据类型的转换。
   
   可以过滤作用域中存储数据的null，对象不存在，就是null
   可以过滤作用域中是否存在某个key
   ```

2. 语法

   ```
   ${表达式语句}
   ```

3. 算数运算符

   ```
   1.[]  展示数组，或map
   2. .  展示任意的对象
   3. 算数运算符
   	mod 取模  div 除法
   4.关系运算符
   	eq 等于  ==  [equals]
   	ne 不等于 != [not equals]
   	lt 小于 <  [less than]
   	gt 大于 >
   	le 小于等于 <=
   	ge 大于等于 >=
   5.逻辑运算符
   	and 与 &&
   	or 或 ||
   	not 非 !
   6.空运算符
   	empty 或 empty
   7.三元运算符
   	布尔表达式 ？值1 : 值2
   ```

4. 隐式对象

   ```
   1.作用域有关的隐式对象
   	jsp --> pageContext  el --> pageScope
   	jsp     request             requestScope
   			session				sessionScope
   			application			
   ```

5. 启用/禁用EL表达式

   局部禁用：当前页面禁止使用EL表达式

   ```
   <%@ page isELIgnored="true"%>
   ```

   全局禁用：整个web项目全面禁止使用EL表达式





