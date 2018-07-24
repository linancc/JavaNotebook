### break、continue、return

- break和continue
  - break 语句用于终止某个循环，程序跳转到循环体外的下一条语句
    - break语句可以用于for、while、do……while循环结构
    - break语句通常与if条件语句一起使用
    - 加标签label：退出任意的嵌套循环（不太推荐）
  - continue 语句用于跳出本次循环，进入下一次循环的语句
    - continue语句可以用于for、while、do……while循环结构
    - continue语句只能用于循环结构中
  - break和continue必须放在循环里面  通俗点说，break中断的是循环，如果外层根本没有循环。。
  - 当存在嵌套时，break中断的是上层循环，不是上上层循环、
- return 语句的作用是结束当前方法的执行并退出，返回调用该方法的语句处
  - 在方法中return关键字可以有多个，return关键字可以返回对象包括其它类型的数据
  - 跳出方法
  - 给出结果

### == 和 equals

- equals是字符串判断内容相等
- == 判断两个对象是否指向同一个引用

### this

1. 通过this关键字可以明确地去访问一个类的成员变量，解决与局部变量名称冲突的问题

   ```java
   class Person {
       int age;
   
       public Person(int age) {
           this.age = age;
       }
   
       public int getAge() {
           return age;
       }
   }
   ```

2. 通过this关键字调用成员方法

   ```java
   class Person {
       public void openMouth() {
   
       }
   
       public void speak() {
           this.openMouth();
       }
   }
   ```

3. 构造方法是在实例化对象时被Java虚拟机自动调用的，在程序中不能像调用其他方法一样去调用构造方法，但可以在一个构造方法中使用“this([参数1，参数2...])”的形式来调用其他的构造方法

   ```java
   class Person {
       public Person() {
           System.out.println("无参的构造方法被调用了。。。");
       }
   
       public Person(String name) {
           this();
           System.out.println("有参的构造方法被调用了。。。");
       }
   }
   
   public class Example10 {
       public static void main(String[] args) {
           Person p = new Person("itcast");
       }
   }
   ```

注意：在使用this调用类的构造方法时，应注意一下几点

1. 只能在构造方法中使用this调用其它的构造方法，不能在成员方法中使用
2. 在构造方法中，使用this调用构造方法的语句必须位于第一行，且只能出现一次
3. 不能在一个类的两个构造方法中使用this互相调用

### static

在Java中定义了一个static关键字，它用于修饰类的成员，如成员变量、成员方法以及代码块等

- 静态变量

  ```java
  class Student {
     static String schoolName;
  }
  
  public class Example10 {
      public static void main(String[] args) {
          Student stu1 = new Student();
          Student stu2 = new Student();
          Student.schoolName = "传智播客";
          System.out.println(stu1.schoolName);
          System.out.println(stu2.schoolName);
      }
  }
  ```

- 静态方法

  ```java
  class Person {
      public static void sayHello() {
          System.out.println("hello");
      }
  }
  
  class Example10 {
      public static void main(String[] args) {
          Person.sayHello();
      }
  }
  ```

- 静态代码块

  