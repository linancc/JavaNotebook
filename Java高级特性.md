### 集合框架

#### 集合类

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

![链表](D:\Java\Aptech资料\JavaNotebook\Java基础\images\链表.jpg)

#### ArrayList

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

   	当前容量：10  添加第11个元素，进行自动扩容
		
   	扩容后的容量 = 10 * 1.5 = 15

   执行添加add()方法会检查容量，不够，会自动扩容

7. ArrayList是单线程，线程不安全

   ```java
   //在多线程下使用，比较安全 
   List list = Collections.synchronizedList(new ArrayList(...)); 
   //多线程下list的创建方式不一样，使用方式完全一样
   ```

8. 可以创建万能桶，什么类型的数据都可以存取，但是会涉及到向上转型，向下转型，使用繁琐；推荐专用桶，给桶加标记，只能专属的保存某一类型的数据，使用起来更方便（泛型）

   ```java
   List<Company> companyList = new ArrayList<Company>();
   companyList.add(new Company("1000", "华为"));
   ```

9. 常用方法

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

1. Set

   1. 常用的类

      HashSet，TreeSet

2. Map

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

- 通过循环存取容器数据

  1. 普通的for循环，使用索引，可以存取（while……            do……while……）

  2. 增强的for循环，foreach循环，适合取，没有索引

  3. 使用迭代器ITerator，通过 hasNext() 和 next() 来取元素

     ITerator  迭代器，在桶（容器）里架设一个水车（梯子），不停的往外面拿数据

     每次只能取一个数据，架设的梯子，一定是在第一个元素的前面，使用 while 循环获取数据

     hasNext()  还有元素吗？

     next() 每次拿一个

     remove() 删除

  4. 使用ListIterator，通过hasNext() 和 next() 来获取元素

  5. lambda表达式 + 函数式编程（jdk1.8+）

#### LinkedList

1. LinkedList的底层数据结构是链表，是双向链表，也可以当作队列，双端队列，堆栈来用

2. LinkedList实现了List‘接口，Deque队列接口，Cloneable克隆接口，Serialable序列化接口

3. 链表不存在扩容问题

4. 实现List接口，基本操作和ArrayList一样

5. 常用方法

   List接口：

   Deque接口（双端队列，Queue队列）：

   	addFirst(element)/addLast()/
		
   	getFirst()/getLast()   获取首尾
		
   	removeFirst()/renoveLast()  删除首尾
		
   	element()  获取元素（获取第一个）

   

   jdk1.6 添加一些方法：

   	offerFirst()/offerLast()  添加首尾
		
   	peekFirst()/peekLast()  获取首尾
		
   	pollFirst()/pollLast()  删除首尾 并返回该元素

   堆栈：（Latst In First Out  LIFO 后进先出）

   	push()  压栈
		
   	pop()  弹栈 弹出栈顶，并返回此元素
		
   	peek()  获取栈顶信息

   6. 有顺序，可重复，可为null

   7. 建议使用加标记的桶（泛型）

   8. LinkedList是单线程，在多线程下使用不安全

      ```java
      List list = Collections.synchronizedList(new LinkedList(...));
      ```

   9. 特点;

      添加和删除比较快，随机查找比较慢

   基本经验：一般正常情况下，优先选择ArrayList

- 链表：

  1. 链表不要求在内存中物理上连续，只要逻辑上连续（链式结构）

  2. 链表没有容量限制，只要内存足够大就OK

  3. 链表由节点组成，节点一般包含数据域，指针域

     数据域：存储数据

     指针域：存储下一个节点的地址

  4. 特点：添加和删除比较快，随机查找比较慢

     添加和删除，只需要改变节点的指针域

     查找，需要从首节点开始

  5. 分类：

     单向链表：

     双向链表：节点有三部分组成，（左链域）上一个节点的，数据域，（右链域）下一个节点的

     循环链表：首节点和尾节点相连

  先进先出  vs  后进先出

  1. 先进先出：数组，动态数组（ArrayList），队列，双端队列，链表
  2. 后进先出：栈（Stack），LinkedList

#### Vector

1. vector 是矢量或向量，数据结构是动态数组

2. 默认容量大小是10，默认扩容1倍；可以自定义扩容增量

   可以指定初始容量  Vector(int initialCapacity) 

   指定初始容量 + 扩容容量 Vector(int initialCapacity, int capacityIncrement)

3. vector 是多线程，在单线程下使用效率不高

4. 有顺序，可重复，可为null

5. 推荐使用专用桶（泛型）

6. 常用方法

    List接口：（参考ArrayList使用）

   	size()/add()/remove()/get()/indexOf()/

   Vextor（元素）相关的方法

   ​	elements()   获取所有元素

#### Stack

1. 栈的操作，LIFO  后进先出
2. Stack是Vector的子类
3. 常用方法
   1. push()  压栈
   2. op()  弹栈  一旦栈中元素为空，再弹栈，会报异常  EmptyStackException
   3. peek()  获取栈顶
   4. empty()  判断栈是否为空
   5. search(Element)  获取栈位置，从1开始，找不到就是-1

#### Set

1. 无顺序，不重复，不为null

2. 常用类：

   1. HashSet，TreeSet，LinkedHashSet

3. HashSet类

   1. HashSet可以存储不同数据类型的数据，推荐标记桶

   2. 不保证顺序，不重复，可为null

   3. 底层实现是HashMap，（HashMap：初始化容量是16，加载因子是0.75）

      只用到HashMap中的key，value一律都是PRESENT（常量）

      可以指定初始化容量和加载因子

4. 常用方法、

   add() / clear()  /  isEmpty()  /  iterator()  /    

5. 在单线程下使用，多线程下不安全

   多线程下使用 ```Set s = Collections.synchronizedSet(new HashSet(...));```

6. 循环取数据，不能使用普通的for循环（没有索引）

   1. foreach() / iterator()  /lambda + 函数式编程

#### TreeSet

1. 凡是类当中带有Tree单词，说明元素是有顺序的

2. 底层实现是TreeMap()   （TreeMap底层实现是二叉树）

3. TreeSet具有排序功能，自定义的类，程序员需要自行提供排序规则

   1. 添加的元素具有排序功能（Comparable比较器）

      City具有排序功能，

      	实现接口java.lang.Comparable 

   2. 桶具有排序功能（Comparator比较器）

      1. 自定义排序类，实现Comparator接口，重写compare(o1,o2)方法
      2. 桶的构造方法，注入此排序类的对象（排序对象……）

4. 单线程，非同步；在多线程下使用不安全

5. 常用方法

   1. add()  

#### LinkedHashSet

1. 底层实现数据结构：哈希表 和 链表

#### Map

1. 保存一对值（key，value），键值对

2. key不能重复，value可以重复，key和value可为null

3. 常用的类

   1. HashMap,TreeMap,Hashtable,LinkedHashMap,Properties

4. HashMap

   1. key不能重复（重复value会被覆盖），value可以重复

      key和value可为null，不保证顺序

   2. HashMap的底层数据结构

      jdk1.8以前：数组 + 链表（单链表）

      jdk1.8以后：数组 + 链表（单链表） +  红黑树

      链表中元素的个数大于等于 8 ，把链表转换成红黑树

      如果是红黑树删除或扩容，在 6 个以下还原成链表（单链表）

      节点数大于等于 64 ，HashMap会进行树形化

   3. HashMap默认容量是16，默认加载因子是0.75

      添加的容量 超过  容量 * 加载因子 = 16 * 0.75 = 12  需要进行扩容

      扩容的规则 = 现有容量的 1 倍

   4. 常用方法

      put(key,value)  添加

      get(key) 根据key获取value

      size()  获取大小

      remove(key)  根据key删除

      isEmpty()  是否为空

      clear()  清空桶  重复的使用桶

      containsKey()  判断是否相等

   5. 循环获取HashMap中的数据

      1. lambda 表达式

      2. 把所有的key放在Set桶里，通过key来获取value

         keySet()  -  -  》foreach() / iterator / lambda

      3. 把Map中的元素打包成Entry放到Set桶里
      4. 把所有的 value 放到Collection中

      备注：

      1. 前面 1，2，3 能获取所有的 key和 value，4 只能获取 value

      2. Collection 是List 和 Set 的父接口，和Map没有直接关系

      3. Map 可以转换成 Collection

         key  --- 》 Set （Collection）

         key,value --》 Set(Collection)

         value  --- > Collection

      4. 所有容器类的父接口/父类是Collection（错的）

   6. 单线程下使用效率较高，多线程下有安全隐患

#### TreeMap

1. 底层结构是二叉树，还是红黑树
2. 具有排序功能，按照key排序；常用类String，Integer，Float等已经实现了 Comparable 接口，具有排序功能
   1. 自定义类，需要实现 Comparable 接口
   2. 容器具有排序功能，实现 Comparator 接口

3. 常用方法

#### Hashtable  vs  HashMap

1. 底层数据结构

   底层实现的数据结构：数组 + 单链表（HashMap基本相同jdk1.7）

2. 父类不同

   Hashtable 继承抽象类 Dictionary ，HashMap 继承抽象类AbstractMap

3. 默认容量不同

   HashMap 默认是 16，加载因子是 0.75

   Hashtable 默认是 11，加载因子是 0.75

4. 扩容规则不一样

   HashMap 扩容1倍（以前的 2 倍）

   Hashtable 扩容1倍+1（以前的 2 倍 +1）

5. 是否为null

   HashMap key 和 value 都可以为空

   Hashtable key 和 value 都不能为null

6. 是否多线程

   HashMap 是单线程的

   Hashtable 是多线程的

- 一般情况下，Hashtable 的使用方式和 HashMap 一样
- 常用方法：
  - get()  /  size()  /  remove()  /  clear()  /isEmpty()  /  put()  /  
  - keySet()  /  entrySet()   /  values()     -  -  - 》HashMap
  - keys()  /  elements()   - - - -> 特有 
- foreach不能遍历Map，遍历的Set

#### LinkedHashMap

1. 底层数据结构：数组  +  双重链表 +  哈希算法
2. 进出有序
3. 单线程效率高，多线程下效率低
4. LinkedHashMap 是 HashMap 的子类
5. 使用方式和HashMap一样

#### Properties

1. Properties 是 Hashtable 的子类

2. 代表的是一个属性集，key 和 value 都是 String类型；创建对象不用加标记

3. 常用方法

   	setProperty(key,value)  设置键 - 值对

   	getProperty(key,value)  获取键 - 值对

   	load(Reader) / load(InputStream) 加载文件流（读取文件）

   propertyNames()  返回所有键

#### Collections

1. 针对集合类进行操作的工具类
2. 常用方法
   1. sort()  排序
   2. max() / min()  最大值/最小值
   3. fill(KList,Element)
      1. reverse(List)  1qaQ	AZ
   4. shuffle(List)  混排（随机、没有顺序）
   5. addAll()  