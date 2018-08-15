### 集合框架

- 集合类;

  1. 又叫集合框架，容器类，容器框架，一个桶；

     容器框架是用来存放对象的对象，内存中之前存放的是一个一个对象，不方便访问和管理（散装数据）在内存中创建不同规格的桶，来存放对象（打包数据）

  2. 分类

     1. 数组

        1. 固定的长度（使用不太方便）
        2. 内存中连续的空间（很好管理）
        3. 相同的数据类型（不同类型的数据无法存取）
        4. 索引从0开始（通过下标访问，查找比较快）
        5. 内存地址（第一个元素的地址决定）
        6. 大小是length属性（无论是多维数组，length由一维的大小决定）

     2. List

        1. 常用的类

           ArrayList，LinkedList，Vector，Stack

        2. List接口：

           1. 特点：有顺序，可重复，可为null
           2. 常用类：ArrayList，LinkedList，Vector,Stack

        3. ArrayList

           ```java
           public class ArrayList<E> extends AbstractList<E>
                   implements List<E>, RandomAccess, Cloneable, java.io.Serializable
           ```

           1. 可变长度的数组，数据结构：线性表，一个线性表

           2. 初始化容量是10（jdk1.8以前），jdk1.8+默认是0

              可以自定义容量

           3. 有顺序，可重复，可为null

           4. 有索引，索引为负数或大于容量，报错：索引越界 IndexOutOfBoundsException

           5. 实现了三个标识接口（RandomAccess, Cloneable, java.io.Serializable）

              随机访问接口、克隆接口、序列化接口

           6. 扩容

              可变长度的数组，动态数组，长度根据插入的数据进行自动扩容、

              ```java
              jdk1.8
              List list = new ArrayList; //默认容量是0
              list.add("aa");//默认扩容是10
              ```

              扩容的时机：添加的元素数量 = 当前的元素数量 +1；

              扩容的容量：当前容量的1.5倍

              ​	当前容量：10  添加第11个元素，进行自动扩容

              ​	扩容后的容量 = 10 * 1.5 = 15

              执行添加add()方法会检查容量，不够，会自动扩容

              

           7. 常用方法

              1. add()  添加元素，可指定索引

              2. size()  容器大小

              3. get()  获取元素，根据索引，一个一个获取

              4. isEmpty()  是否为空，只能判断容器中的元素是否为空，不能判断是否有这个桶

                 ```java
                 //判断桶是否为空（桶是否存在，桶里有没有元素）
                 if (list != null && list.size() > 0) {
                             
                 }
                 ```

              5. clear()  清空所有的元素，不能清空桶

              6. set(int index, E element)  替换元素（索引）

              7. remove(index)/remove(object)  删除元素

              8. removeRange(int fromIndex, int toIndex)   按照索引区间进行删除
                           移除列表中索引在 fromIndex（包括）和 toIndex（不包括）之间的所有元素。

              9. contains(Object o)   判断是否包含指定元素
                           如果此列表中包含指定的元素，则返回 true。

              10. indexOf(Object o) 
                            返回此列表中首次出现的指定元素的索引，或如果此列表不包含元素，则返回 -1。

              11. toArray()   把List转换成数组
                            按适当顺序（从第一个到最后一个元素）返回包含此列表中所有元素的数组。

           项目经验：在使用容器之前一定要判断是否为空（桶是否存在，桶是否存在）

     3. Set

        1. 常用的类

           HashSet，TreeSet

     4. Map

        1. 常用的类

           HashMap，Hashtable，TreeMap，LinkedHashMap

- 注意：

  - ArrayList 默认长度是10
  - Java中属于线程安全的是 Vector HashTable
  - Collections类提供的方法都是静态方法，所以可以直接调用执行，不需实例化对象 

- 二进制有关的操作符：

  - 按位运算符

    &  与 

    |  或

    ~ 取反  正数取反 = 正数 + 1 取负  负数取反 = 负数 +1 取正

    ^  异或

  - 移位运算符

    ```java
    << 左移  --> 乘法  结果 = 数字 * 2^n（左移n位）
    >>  右移  --> 除法  结果 = 数字 / 2^n(右移n位)
    >>> 无符号右移（非负数）结果 = 数字 / 2^n(右移n位)
    ```

  - 取反涉及到原码 反码 补码

    