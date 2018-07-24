## Calendar类 

- 处理日期和时间

- 抽象类，表示日历；不能直接实例化

- GregorianCalendar代表公历

- 静态方法 getInstance() 获取Calendar对象

- Calendar.MONTH代表月份，月份起始值是0，设置8月，是7而不是8

### add()和roll()区别
- add(int field,int amount)的功能非常强大，add主要用于改变Calendar的特定字段的值；增加，amount为正数；反之为负数
### add()规则
- 当被修改的字段超出它允许的范围时，会发生进位，即上一级的字段也会增大
- 如果下一级也需要改变时，那么该字段会修正到变化最小的值
### roll()规则与add()的处理规则不同：
- 当被修改的字段超出它允许的范围时，上一级字段不会增大
- 下一级的处理规则与add()类似
## 设置Calendar的容错性
- setLenient(true/false)