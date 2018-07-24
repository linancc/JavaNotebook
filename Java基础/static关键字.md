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

  