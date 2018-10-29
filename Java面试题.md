## JavaCore

1. 如何理解面向对象？它有哪些特征？

   ```
   一切皆对象，
   特征：
   	封装：
   	继承：
   	多态：
   	抽象：
   	唯一性：
   ```

2. [Java数据类型有哪些？](https://blog.csdn.net/truelove12358/article/details/60143499)

   ```
   8中基本数据类型
   	字符型 char
   	整型 数值型  byte short int long
   		浮点型 float double
       布尔型 boolean
   5种引用类型
   	类 class
   	数组 array
   	接口 interface
   	枚举 enum
   	注解 Annotation
   ```

   | 序号 |    数据类型    | 大小/位 |  封装类   | 默认值 |              可表示数据范围              |
   | :--: | :------------: | :-----: | :-------: | :----: | :--------------------------------------: |
   |  1   |    byte(位)    |    8    |   Byte    |   0    |                 -128~127                 |
   |  2   | short(短整数)  |   16    |   Short   |   0    |               -32768~32767               |
   |  3   |   int(整数)    |   32    |  Integer  |   0    |          -2147483648~2147483647          |
   |  4   |  long(长整数)  |   64    |   Long    |   0L   | -9223372036854775808~9223372036854775807 |
   |  5   | float(单精度)  |   32    |   Float   |  0.0F  |           1.4E-45~3.4028235E38           |
   |  6   | double(双精度) |   64    |  Double   |  0.0D  |     4.9E-324~1.7976931348623157E308      |
   |  7   |   char(字符)   |   16    | Character |   空   |                 0~65535                  |
   |  8   |    boolean     |    8    |  Boolean  | flase  |               true或false                |

   自动类型的转化

     ``` java
      低--------------------------------------------->高
      byte,short,char-> int -> long -> float -> double
     ```

3. 重载和重写有什么区别？

   ```
   重载：在同一个类中，方法名相同，参数列表不同，与返回值类型和权限修饰符无关
   重写：在父子类中，方法名相同，参数列表相同，返回值类型相同，权限修饰符不能小于被重写方法
   ```

4. Java序列化是什么意思？如何实现序列化？

   ```
   	Java 提供了一种对象序列化的机制，该机制中，一个对象可以被表示为一个字节序列，该字节序列包括该对象的数据、有关对象的类型的信息和存储在对象中数据的类型。
   	将序列化对象写入文件之后，可以从文件中读取出来，并且对它进行反序列化，也就是说，对象的类型信息、对象的数据，还有对象中的数据类型可以用来在内存中新建对象。
   实现：
   	1.该类必须实现 java.io.Serializable 对象。
   	2.该类的所有属性必须是可序列化的。如果有一个属性不是可序列化的，则该属性必须注明是短暂的。
   ```

5. switch使用哪些类型？

   ```
   byte short int char 枚举 String(JDk1.7新增)
   ```

6. [如何理解static？](https://www.cnblogs.com/chenssy/p/3386721.html)

7. [如何理解final？](http://www.importnew.com/7553.html)

8. ==和equals有什么区别？
   ![img](https://pic3.zhimg.com/80/v2-d9dc4362f0334802413e3a3ff2f53c2e_hd.png)

   ```java
   1. == 基本类型和引用类型都能使用，equals只能用于引用类型
   
      == 基本类型：比较值 ； 引用类型：比较地址
   
      equals 引用类型：一般比较内容
   
   2. == 比较内存地址；equals  一般情况下比较内容
   
   3. equals 分两种情况;
   
      自定义类  没有重写equals() 和 hashCode()  ：  和 ==  一样，比较内存地址
   
      自定义类  重写equals() 和 hashCode()  ： 比较内容
   
      重写hashCode()  是为了业务需要，和 equals()  保持一致性
   
   4. String 实现了常量池技术，字面量相同，内存地址相同；
   
      new出来的字符串，单独处理，可以纳入常量池：intern()
   
      String b = new String("cc");
      String c = "cc";
      System.out.println(a.equals(b));//比较内容  true
      System.out.println(a == b);//比较地址  false
      System.out.println(a == c);//比较地址  true 常量池 一个地址
      
   5. 基本类型的包装类 （数字有关）
   
      1. 实现了缓存技术，在 [-128,127]进行缓存，超过阈值，缓存失效
   
   
      Byte Short  Character  Integer  Long 
      内部静态类：IntegerCache,LongCache
   
   
      2. 没有实现缓存技术
   
   
      Float  Double
   
   
      3. 案例：
   
      Integer a = 12;  Integer b = 12;  a == b;   true
      Integer a = 212; Integer b = 212; a == b;   false
      Float a = 12F; Float b = 12F;  a == b;  false; 
   
   ```

9. 抽象类和接口有什么区别？

   ```
   抽象类：
   	由关键字abstract修饰，不能创建实例对象
   	方法不必须是抽象的
   	抽象方法必须在子类中实现，子类没有实现所有abstract方法，那么子类也是抽象类
   	可以有成员变量  
   	可以有构造方法
   	可以有普通方法
   	可以有静态方法
   	可以有静态成员变量，抽象类中可以是任意类型，接口中中默认为public static final
   	一个类可以实现多个接口，但只能继承一个抽象类
   接口：
   	由关键字interface修饰
   	接口名和方法默认由public修饰，没有方法题（Jdk1.8新增默认实现default）
   ```

10. Java可以实现多继承吗？如果有，怎么实现？

    ```
    不可以。Java是单继承多实现
    ```

11. String是基本数据类型吗？String可以被继承吗？

    ```
    String是引用类型  不可以被继承 String是final的
    ```

12. [说说常用的日期类？](https://www.cnblogs.com/yangming1996/p/6919191.html)
    [jdk1.8新增日期类](https://juejin.im/post/5addc7a66fb9a07aa43bd2a0)

13. Java的IO流分几种？有哪些常用类？
    ![](http://www.runoob.com/wp-content/uploads/2013/12/iostream2xx.png)

14. List和Set有什么区别？

15. Map有什么特点？

16. 所有集合类的父类/父接口是Collection吗？

17. 数组有没有length方法？字符串有没有length方法？

    ```
    数组是length属性  字符串是length()方法
    ```

18. [Error和Exception有什么区别？](https://blog.csdn.net/goodlixueyong/article/details/47122487)

19. CheckedException和UnCheckedException有什么区别？

20. [Throw和throws有什么区别？](https://blog.csdn.net/luoweifu/article/details/10721543)

21. final、finally、finalize有什么区别？

    ```
    final 用于声明属性,方法和类, 分别表示属性不可变, 方法不可覆盖, 类不可继承.
    finally 是异常处理语句结构的一部分，表示总是执行.
    finalize 是Object类的一个方法，在垃圾收集器执行的时候会调用被回收对象的此方法，可以覆盖此方法提供垃圾收集时的其他资源回收，例如关闭文件等. JVM不保证此方法总被调用.
    ```

22. 进程和线程有什么区别？实现多线程有哪几种方法？

    ```
    方法：
    	实现Runnable 接口；
    	可以继承Thread类。
    ```

23. [堆和栈有什么区别？](https://www.jb51.net/article/59936.htm)

24. 值传递和引用传递？

    ```
    1. 定义：
       - 基本类型的传递是值传递
       - 引用类型的传递是引用传递
       - 侧重：在方法中的传递（形参、实参）
    2. 规律
       - 基本类型传递（值传递），传递的是值的副本；传递之前和之后，变量的值不变
       - 引用类型的传递（引用传递），传递的是内存的引用地址
         - 方法内对象的地址不变，变量（对象）属性值可变
         - 方法内对象的地址改变，变量（对象）属性值不变
    3. 总结
       - Java本质上都是值传递，基本类型的值和引用类型的地址都是值
       - 传递之前和之后，变量的值不变
    ```

25. ArrayList跟LinkedList区别，还有Vector？

26. HashMap和Hashtable区别？List和Map区别？

27. 权限修饰符有哪些？各代表什么意思？

28. [JDK1.5的新特性？](https://www.jianshu.com/p/37b52f1ebd4a)

29. Collection是所有集合的父类吗？

30. Collection和Collecyions的区别？

31. StringBuffer 和 StringBuilder 类

    ```java
    当对字符串进行修改的时候，需要使用 StringBuffer 和 StringBuilder 类。
    和 String 类不同的是，StringBuffer 和 StringBuilder 类的对象能够被多次的修改，并且不产生新的未使用对象。
    StringBuilder 类在 Java 5 中被提出，它和 StringBuffer 之间的最大不同在于 StringBuilder 的方法不是线程安全的（不能同步访问）。
    由于 StringBuilder 相较于 StringBuffer 有速度优势，所以多数情况下建议使用 StringBuilder 类。
    ```