- nextLine()的输入是碰到回车就终止输入，next()方法是碰到空格，回车，Tab键都会被视为终止符，终止接收输入。

- next()一定要读取到有效字符后才可以结束输入，对输入有效字符之前遇到的空格键、Tab键或Enter键等结束符，next()方法会自动将其去掉，只有在输入有效字符之后，next()方法才将其后输入的空格键、Tab键或Enter键等视为分隔符或结束符。简单地说，next()查找并返回来自此扫描器的下一个完整标记。完整标记的前后是与分隔模式匹配的输入信息，所以next方法不能得到带空格的字符串而nextLine()方法的结束符只是Enter键，即nextLine()方法返回的是Enter键之前的所有字符，它是可以得到带空格的字符串的。

###  当next()与nextLine()方法分别单独使用时，区别如下：

1. next()单独使用

```java
Scanner scanner = new Scanner(System.in);  
String s = scanner.next(); 
```

输入:"Hello World!"，s中只会存储Hello\r\n如果想要next()方法也和nextLine()方法一样效果，可以进行如下设置：

```java
Scanner scanner = new Scanner(System.in);
scanner.useDelimiter("\n");
String s = scanner.next(); 
```

通过useDelimiter(String pattern);该方法参数为一个正则表达式，理论可以自行设置任意结束符号......

2. nextLine()单独使用

```java
Scanner scanner = new Scanner(System.in);  
String s = scanner.nextLine(); 
```

输入:"Hello World"，s中会存储Hello World

### 当next()与nextLine()方法结合使用时

1. nextLine()方法在next()方法之前使用

```java
String s1, s2;
Scanner sc = new Scanner(System.in);
System.out.print("请输入第一个字符串：");
s1 = sc.nextLine();
System.out.print("请输入第二个字符串：");
s2 = sc.next();
System.out.println("输入的字符串是：" + s1 + "  " + s2);
```

在控制台输入并得到如下结果：

请输入第一个字符串：Hello

请输入第二个字符串：World

输入的字符串是：Hello  World

2. next()方法在nextLine()方法之前使用

```java
String s1, s2;
Scanner sc = new Scanner(System.in);
System.out.print("请输入第一个字符串：");
s1 = sc.next();
System.out.print("请输入第二个字符串：");
s2 = sc.nextLine();
System.out.println("输入的字符串是：" + s1 + "  " + s2); 
```

在控制台输入并得到如下结果：

请输入第一个字符串：Hello

请输入第二个字符串：输入的字符串是：Hello 

原因是nextLine()自动读取了结束next()输入的Enter作为他的结束符，所以没办法给s2从键盘输入值。经过验证，其他的next的方法，如nextDouble() ，nextFloat() ，nextInt() 等与nextLine()连用时都存在这个问题。
 解决方案如下：

1. 在每一个 next()、nextDouble() 、nextFloat()、nextInt() 等语句之后加一个nextLine()语句，将结束next()等方法输入的Enter结束符过滤掉。

```java
String s1, s2;
Scanner sc = new Scanner(System.in)
System.out.print("请输入第一个字符串：");
s1 = sc.next();
sc.nextLine();
System.out.print("请输入第二个字符串：");
s2 = sc.nextLine();
System.out.println("输入的字符串是：" + s1 + "  " + s2);
```

在控制台输入并得到如下结果：

请输入第一个字符串：Hello

请输入第二个字符串：World

输入的字符串是：Hello World