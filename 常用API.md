# 面向对象之API的使用

## 浅克隆

### clone()克隆对象

```java
 protected native Object clone() //clone是受保护的
```

Cloneable 接口

- 如果一个接口里面没有抽象方法
- 表示当前的接口是一个标记性接口
- 现在Cloneable表示一旦了实现，那么当前类的对象就可以被克隆
- 如果没有实现，当前类的对象就不能克隆



> 也就是子类和父类在不在同一个包中对于父类protected修饰的成员访问权限是不同的。
> 子类与父类在同一包中:被声明为 protected 的成员能被同一个包中的任何其他类访问；
> 子类与父类不在同一包中:那么在子类中，子类只可以访问其从父类继承而来的自己的protected成员，而不能访问父类实例以及和父类在同一个包下的其他子类实例的protected成员。
>
> 很典型的一个例子就是Object的clone（）方法，这个方法只能允许对象克隆自己的对象,而不能克隆Object对象,因为所有对象的clone方法都是继承的Object类的clone方法,但是这个方法是protected修饰的,它的可见性是Object的所有子类和java.lang包但是异包子类不能直接访问父类的受保护成员

## 深克隆

使用第三方工具实现

导入别人写的代码gson.jar包到lib，再点击Add as Library

```java
Gson gson = new Gson();
String s = gson.toJson(要深克隆的对象);//他会将数据转化为字符串
Student s =gson.fromJson(s, Student.class);//s为克隆对象转化的字符串， Student.class 为 s 要转化后的类名
```



## 总结

1. Object是Java中的顶级父类。
所有的类都直接或间接的继承于0bject类。
2. toString()： 一般会重写，打印对象时打印属性。
3. equals()： 比较对象时会重写，比较对象属性值是否相同。
4. clone( )：默认浅克隆。
如果需要深克隆需要重写方法或者使用第三方工具类。（Gson）



## Objects工具类

1. Objects是一个对象工具类，提供了一些操作对象的方法。
2. equals(对象1,对象2) ：先做非空判断，比较两个对象。
3. isNull(对象)：判断对象是否为空。
4. nonNull(对象)：判断对象是否不是空。



## BigInteger

#### 构造方法小结：

- 如果BigInteger表示的数字没有超出long的范围，可以用静态方法获取。
- 如果BigInteger表示的超出long的范围，可以用构造方法获取。
- 对象一旦创建，BigInteger内部记录的值不能发生改变。
- 只要进行计算都会产生一个新的BigInteger对象

 

#### 使用方法演例：

> 如果你要计算的数据在-16~16之间就不用new，直接调用其静态方法valueOf()；

#### 方法小结：

1. BigInteger表示一一个大整数。
2. 如何获取BigInteger的对象?
  1. BigInteger b1 = BigInteger . value0f(0.1);
  2. BigInteger b1 = new BigInteger("整数" );
3. 常见操作
  1. 加: add
  2. 减: subtract
  3. 乘: multiply
  4. 除: divide、 divideAndRemainder
  5. 比较: equals、 max、min
  6. 次幂: pow
  7. 转成整数: intValue、 longValue



## BigDecima

用途：小数的精确运算



细节注意：

- 如果要表示的数字不大，没有超出double的取值范围，建议使用静态方法
- 如果要表示的数字比较大，超出了double的取值范围， 建议使用构造方法
- 如果我们传递的是0~10之间的整数，包含0和10，那么用方法返回已经创建好的对象。

> HALF_UP 四舍五入





1. BigDecimal的作用是什么?、
  - 表示较大的小数和解决小数运算精度失真问题
2. BigDecimal的对象 如何获取?
   - BigDecimal bd1 = new BigDecimal("较大的小数");
   - BigDecimal bd2 = BigDecimal. value0f(0.1);
3. 常见操作 
   - 加: add
   - 减: subtract
   - 乘: multiply
   - 除: divide (四舍五入: RoundingMode .HALF_ UP)



## 正则表达式

> 作用一：校验字符串是否满足规则
> 作用二：在一段文本中查找满足要求的内容

![image-20221118171212790](D:\Java\Java学习内容\1、Java基础语法篇\笔记\常用API_image\image-20221118171212790.png)

![image-20221118171324408](D:\Java\Java学习内容\1、Java基础语法篇\笔记\常用API_image\image-20221118171324408.png)

```
\表示转义字符
\\前面的\是一个转义字符，改变了后面\原本的含义，把他变成一个普普通通的\而己。
```

##### any-rule插件：写正则表达式的插件





小结：

![image-20221118180248232](D:\Java\Java学习内容\1、Java基础语法篇\笔记\常用API_image\image-20221118180248232.png)

![image-20221118180331840](D:\Java\Java学习内容\1、Java基础语法篇\笔记\常用API_image\image-20221118180331840.png)

- Pattern：表示正则表达式
- Matcher：文本匹配器，作用按照正则表达式的规则去读取字符串，从头开始读取。
  在大串中去找符合匹配规则的子串。

![image-20221119220630169](D:\Java\Java学习内容\1、Java基础语法篇\笔记\常用API_image\image-20221119220630169.png)

1. 正则表达式中分组有两种:
   - 捕获分组、非捕获分组
2. 捕获分组(默认):
   - 可以获取每组中的内容反复使用。
3. 组号的特点:
   - 从1开始，连续不间断
   - 以左括号为基准,最左边的是第一-组
4. 非捕获分组:
   -  分组之后不需要再用本组数据，仅仅把数据括起来，不占组号。
   - (?:) (?=) (?!)都是非捕获分组

## Date 时间

1. 如何创建日期对象?
   - Date date = new Date();
   - Date date = new Date(指定毫秒值);
2. 如何修改时间对象中的毫秒值	
   - setTime(毫秒值);
3. 如何获取时间对象中的毫秒值
   - getTime();



```java
String start = "2023年11月11日0:0:0";
String end = "2023年11月11日0:10:0";  //定义字符串形式的时间
String order = "2023年11月11日 0:0:3";

SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日HH:mm:ss");
Date startDate = sdf.parse(start);
Date endDate = sdf.parse(end);//解析字符串得到日期对象
Date orderorder = sdf.parse(order);
long startTime = startDate.getTime();
long endTime = endDate.getTime();//得到毫秒值
long orderTime = orderorder.getTime();
if(orderTime >= startTime && orderTime <= endTime){//判断
	System.out.println("参加秒杀活动成功");
}else{
	System.out.println("未在指定时间下单");

```





## SimpleDateFormat 时间

![image-20221120191114382](D:\Java\Java学习内容\1、Java基础语法篇\笔记\常用API_image\image-20221120191114382.png)

使用方法：

1. 指定一个时间显示格式，就是new 一个SimpleDateFormat对象
2. 将时间字符串解析parse成时间对象date
3. sout 时间对象

```java
String girlFriend = "2000-11-11";
SimpleDateFormat s = new SimpleDateFormat("yyyy-MM-dd");
Date parse = s.parse(girlFriend);
SimpleDateFormat ns = new SimpleDateFormat("yyyy年MM月dd日");
String format = ns.format(parse);//格式对象去转化date成想要的字符串
System.out.println(format);
```

1. SimpleDateFormat的两个作用
格式化 parse 
解析 format
2. 如何指定格式
    yyyy年MM月dd日HH: mm: SS

## Calendar

| 方法名                                       | 说明                        |
| :------------------------------------------- | :-------------------------- |
| public final Date **getTime**()              | 获取日期对象                |
| public final **setTime**(Date date)          | 给日历设置日期对象          |
| public long **getTimeInMillis**( )           | 拿到时间毫秒值              |
| public void **setTimeInMillis**(long millis) | 给日历设置时间毫秒值        |
| public int **get**(int field)                | 取日历中的某个字段信息      |
| public void **set**(int field, int value)    | 修改日历的某个字段信息      |
| public void **add**(int field, int amount)   | 为某个字段增加/减少指定的值 |

####  细节：

1. Calendar是一个接口，不能创建它的抽象方法，可以通过它的一个静态方法获得到子类对象

   Calendar.getInstance();

   底层原理:
   	会根据系统的不同时区来获取不同的日历对象,默认表示当前时间。
   	把会把时间中的纪元，年，月，日，时，分，秒，星期，等等的都放到一个数组当中

2. **月份:范围0~11 如果获取出来的是e.那么实际上是1月。**

3. 星期:在老外的眼里，星期日是一周中的第一天

   1 (星期日)

   2 (星期一) 

   3 (星期二)

   4 (星期三)

   5 (星期四)

   6 (星期五)

   7 (星期六)


![image-20221121181718494](D:\Java\Java学习内容\1、Java基础语法篇\笔记\常用API_image\image-20221121181718494.png)

## JDK8新增时间类

![image-20221121193706623](D:\Java\Java学习内容\1、Java基础语法篇\笔记\常用API_image\image-20221121193706623.png)

![image-20221121230231227](D:\Java\Java学习内容\1、Java基础语法篇\笔记\常用API_image\image-20221121230231227.png)

## Instant时间戳

| 方法名                                      | 说明                              |
| ------------------------------------------- | --------------------------------- |
| static Instant **now**()                    | 获取当前时间的nstant对象(标准时间 |
| static Instant **ofXxxx**(long epochMilli)  | 根据(秒/毫秒/纳秒)获取Instant对象 |
| ZonedDateTime **atZone**(ZoneId zone)       | 指定时区                          |
| boolean **isXxx**(Instant otherInstant)     | 判断系列的方法                    |
| Instant **minusXxx**(long millisToSubtract) | 减少时间系列的方法                |
| Instant **plusXxx**(long millisToSubtract)  | 增加时间系列的方法                |



## ZoneDateTime带时区的时间

| 方法名                              | 说明                            |
| ----------------------------------- | ------------------------------- |
| static ZonedDateTime **now**()      | 获取当前时间的ZonedDateTime对象 |
| static ZonedDateTime ofXxxx(。。。) | 获取指定时间的ZonedDateTime对象 |
| ZonedDateTime **withxxx**(时间)     | 修改时间系列的方法              |
| ZonedDateTime **minusXxx**(时间)    | 减少时间系列的方法              |
| ZonedDateTime **plusxxx**(时间)     | 增加时间系列的方法              |





## DateTimeFormatter 用于时间的格式化和解析

| 方法名                                       | 说明               |
| -------------------------------------------- | ------------------ |
| static DateTimeFormatter **ofpattern**(格式) | 获取格式对象       |
| string format(时间对象)                      | 按照指定方式格式化 |







