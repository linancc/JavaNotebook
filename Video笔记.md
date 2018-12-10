#### chu方法的可变参（JDK1.5）

- 前提：方法参数数据类型确定，参数个数任意
- 可变参数语法：数据类型...变量名
- 可变参数，本质是一个数组

```java
public class Demo {
    public static int getSum(int... a) {
        int sum = 0;
        for (int i : a) {
            sum += i;
        }
        return sum;
    }

    public static void main(String[] args) {
        System.out.println(getSum(1, 2, 3, 4, 5, 6));
    }
}
```

- 注意事项：
  1. 一个方法中，可变参数只能有一个
  2. 可变参数必须写在参数列表的最后一位