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