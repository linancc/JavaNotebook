#### IO：

Input/Output  输入/输出

1. File 类

   1. 是 Java 中 IO 操作的起点，很重要

   2. 把物理存储设备中的文件或目录的一种抽象表示，File 类不区分文件和目录

   3. 常用的方法

      1. 构造方法

         1. File(path)  根据path字符串创建文件对象
         2. File(father,son) 

      2. 针对文件操作：

         1. getPath()  获取路径（根据设置的路径，相对路径 或 绝对路径）

         2. getAbsolutePath()  绝对路径

         3. getCanonicalPath()  获取文件的抽象路径，和绝对路径保持一致

            ```java
            相对路径：一定会有一个参照物，参照物是一个目录或文件
            ../  上一个目录
            ./   当前目录
            绝对路径：文件的绝对地址
            ```

         4. getParent()  /  getParentFile()  获取父目录
         5. lastModified()  最后修改时间的偏移量
         6. length()  文件大小
         7. createNewFile()  创建新文件

      3. 针对目录操作

         1. mkdir()  创建单层目录，如果嵌套的父目录不存在，创建失败；如果存在，不创建
         2. mkdirs()  创建嵌套目录，如果嵌套的父目录不存在，统一创建所有目录；如果存在，不创建
         3. list()
         4. listFiles()  

      4. 针对判断操作

         1. isDirectory()
         2. isFile()
         3. canRead()
         4. canWrite()
         5. canExecute()
         6. exists() 
         7. isHidden()  是否隐藏
         8. isAbsolution()

      5. 设置和修改操作

         1. seReadOnly()  /  setWriteOnly()
         2. renameTo()

2. 分类

   1. 流的方向：

      1. 输入流  读的操作  - -》需要源文件
      2. 输出流  写的操作  - -》目标文件（地址）

   2. 流的单位：

      1. 字节流  读写的是二进制文件
      2. 字符流  读写的是文本文件

      二进制文件：视频、音频、图片、word、Excel、.class。。。凡是用notepad打开乱码的都是

      文本文件：记事本，java源代码，属性文件，xml文件，css文件。。。凡是用notepad打开不乱码的都是

   3. IO流，字节流，输入流

      1. 传统的IO流无论是字节流还是字符流，都是一个阻塞流，只能进行单向操作

         阻塞流，数据传输一旦阻塞，中断数据传输操作，作后面的数据就无法传输

         单向流：数据只能向一个方向运动，不能往回走；IO流的管道只能单向操作：读取数据的管道，或者是写数据的管道不能同时读写

      2. InputStream 输入流操作

         1. FileInputStream 输入流读取文件操作

            步骤;

            1. 创建需要读取的源文件
            2. 创建文件输入流
            3. 循环读取文件
            4. 关闭资源

      3. 字节读取的三种方式

         1. 单字节读取（一个一个字节读取，效率不高）
         2. 字节数组读取（一次性把字节读取到数组中，效率较高）

   4. IO流，字节流，输出流

      1. OutputStream FileOutputStreamm BufferedOutputStream

   5. NIO：面向管道和缓冲区的流，可以同时读写

3. 字节流
   1. 输入流：
      1. InputStream   抽象类（输入流）
      2. FileInputStream  文件输入流
      3. BufferInputStream  缓存输入流
   2. 输出流：
      1. OutputStream  抽象类（输出流）
      2. FileOutputStream  文件输出流
      3. BufferedOutputStream  缓存输出流

4. 字符流
   1. 输入流
      1. Reader  抽象类（文本输入流）
      2. FileReader  文件输入流（文本）
      3. BufferedReader  缓存输入流（文本）
   2. 输出流
      1. Writer   抽象类（文本输出流）
      2. FileWriter  文件输出流
      3. BufferedWriter  缓存输出流

5. 序列化 与 反序列化 

6. 其它的类
   1. 字节流：
      1. DataInputStream  /  DataOutputStream
      2. ObjectInputStream  /  ObjectOutputStream
   2. 字符流：

   字节流  ----》 字符流

   InputStreamReader  /  OutputStreamWriter

7. IO流的基本规律