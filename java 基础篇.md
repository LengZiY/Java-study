#          Java 基础篇

编写第一个程序Hello World

类名定义格式，大驼峰，第一个单词大写：`XxxYyyZzz`

方法名定义格式，小驼峰，第一个单词小写：`xxxYyyZzz`

```java
public class 类名 //此处类名必须和文件名一样 "文件名.java"
class 类名 //---> 标识符
class HelloCold{
public static void main(String[] args){
    System.out.println("Hello Cold!");
	}
}
```





# 变量的使用和定义

- 变量需要先定义后使用
- 变量都定义在其作用域内，在作用域内有效，不在同一作用域的变量失效
- 同一个作用域不可以声明两个同名的变量

```java
class VariableTest{
    public static void main(String[] args){
        //定义变量
        int mAge = 10;
        //变量的使用 
        System.out.println(mAge);
        int num = 1000;
        System.out.println(num);
    }
}
```

## 变量的数据类型

### 基本数据类型(primitive type)

1. ###### 								整型（byte， short， int， long）

2. ###### 								浮点型（float， double）

3. ###### 								字符型（char）	

4. ###### 								布尔类型（boolean）

### 引用数据类型(reference type)

1. ###### 								类（class）             <------------  字符串

2. ###### 								接口（interface）

3. ###### 								数组（[ ]）

```java
class Variable {
    public static void main(String[] args){
        long num = 29999999999L;//定义long类型必须以小写"l"或大写"L"结尾
        Ststem.out.println(num);
        
        float num1 = 0.1234567F;//定义float类型需加小写"f"或大写"F"结尾
        /*单精度float类型尾数可以精确到7位有效数字，很多情况很难满足需求。
        double:双精度，精度是float的两倍。通常采用此类型*/
        System.out.println(num1);
        
        boolean falg = true;
    		
        if(flag){
            System.out.println("你就不能参加\"单身\"party了!");
        }else{
            System.out.println("想什么呢！\\n");
        }
    }
}
```

基本数据类型之间的运算规则：

前提：这里讨论的只是7种基本数据类型变量间的运算。不包含boolean类型。

### 自动类型提升

结论：当容量小的数据类型的变量与大的数据类型的变量做运算时，结果自动提升为容量的数据类型。

byte 、 short 、 char ---> int ---> long ---> float ---> double

特别的：当byte、char、short三种类型的变量做运算时，结果都是int类型。

### 强制类型转换

定义：自动类型提升的逆运算。

1. 需要使用强转符：()
2. 注意点：强转类型转换，可能导致精度损失。 

注意在定义变量中会发生的情况：

```java
class VariableTest{
public static void main(String[] args){
    /*情况1*/
    long num = 12312;//没有加L
    System.out.println(num);//此种情况编译可通过
    
    /*--------------------------------------*/
    
    /*情况2*/
    long num = 1234132321345;//没有加L
    System.out.println(num);//此种情况编译不通过
    
    /*--------------------------------------*/
    
    //整型常量，默认类型为int型
    //浮点型常量，默认类型为double型
    /*情况1*/
    float f1 = 12.3;//不加F编译失败
    float fi = (float)12.3;//编译通过
    /*情况2*/
    byte b = 12;
    byte b1 = b + 1;//编译失败
    /*情况3*/
    byte b = 12;
    float f1 = b + 12.3;//编译失败
    
    /*---------------------------------------*/
    
  
```



###     String类型变量的使用

1.  	String属于引用数据类型

2. 声明String类型变量时，使用一对""

3. String可以和8种基本数据类型变量做运算，且运算只能时连接运算：+

4. 运算结果仍然时String类型

   

```java
String s1 = "Hello World!";

System.out.println(s1);
String s2 = "a";//编译通过
String s3 = "";//若无内容编译通过

char c = '';//若无内容则编译不通过

int number = 1001;
String numberStr = "学号：";
String info = numberStr + number;//连接运算
System.out.println(info);

String ch = "开关：";
boolean flag = true;
String ch1 = ch + flag;//连接运算

System.out.println(ch1);
```

​    例题:

```java

System.out.println("*	*");
System.out.println('*' + '\t' + '*');//93
System.out.println('*' + "\t" + '*');//*	*
System.out.println('*' + '\t' + "*");//51*
System.out.println('*' + ('\t' + "*"));//*	 *
```
- "" 字符串之间运算是拼接运算（连接运算）
- '' 字符之间运算是对照[ascll](//"" 字符串之间运算是拼接运算（连接运算）
  //'' 字符之间运算是对照ascll转换成int类型进行加法运算结果为int类型
  int + String + int + int + int；
  //若加法运算中遇到String就拼接运算)转换成int类型进行加法运算结果为int类型
- int + String + int + int + int；
- 若加法运算中遇到String就拼接运算

#  计算机中不同进制的使用

​    

### 整数的四种进制

1. 二进制（binary）0, 1, 满2进1, 以[0b]()或[0B]()开头。
2. 八进制（octal）0 ~ 7, 满8进1, 以数字0开头表示
3. 十进制（decimal）0 ~ 9, 满10进1。
4. 十六进制（hex）0 ~ 9 及 A ~ F, 满16进1, 以[0x]()或[0X]()开头表示。此处的A-F不区分大小写。[]()
   如：[0x21AF]() + 1 = [0X21B0]()

### 二进制

Java整数常量默认是int类型， 当用二进制定义整数时，其第32位是符号位;
当是long类型时，二 进制默认占64位，第64位是符号位。

#### 二进制的整数有如下三种形式:

- 原码:直接将一一个数值换成二进制数。最高位是**符号位**
- 负数的反码:是对原码按位取反，只是最高位(符号位)确定为1。
- 负数的补码:其反码加1。 

#### 计算机以二进制补码的形式保存所有的整数。

- 正数的原码、反码、补码都相同
- 负数的补码是其反码+1

结论：计算机底层都以补码的方式存储数据！

### Integer 类中转换进制方法

```java
Integer class{
	toBinaryString();//转二进制方法
	toHexString();//转十六进制
	toOctalString();//转八进制
}
```

# 运算符



运算符是一种特殊的符号，用以表示数据的运算、赋值、和比较等。

- 算术运算符
- 赋值运算符
- 比较运算符（关系运算符）
- 逻辑运算符
- 位运算符
- 三元运算符

> ![image-20220923211442183](\Java基础image\image-20220923211442183.png)

> ![image-20220923212303207](\Java基础image\image-20220923212303207.png)

> ![image-20220923212150539](\Java基础image\image-20220923212150539.png)

> 比较运算符的结果都是boolean型，也就是要么是true，要么是false。
>
> 比较运算符“==”千万不能写成“=”。



```java
class LogicTest{
    public static void main(){
        boolean flag = true;
        int num = 10;
        if(flag & (num++ > 0)){
            System.out.print("Hello");
        }else{
            Syetem.out.print("World");
        }
        System.out.println(num);
    }
}
```

运行结果：`Hello11`

```java
class LogicTest{
    public static void main(){
        boolean flag = false;
        int num = 10;
        if(flag && (num > 0)){
            System.out.print("Hello");
        }else{
            System.out.print("World");
        }
        System.out.print(num);
    }
}
```

运行结果：`World10`

## 位运算

![image-20220924113222045](\Java基础image\image-20220924113222045.png)

```java
class BitTest{
    public static void main(String[] args){
        int i = 21;
        i = -21;
        System.out.println("i >> 2 :" + (i >> 2));
        //11101011 ---右移2位---> 11111010 = -6
    }
}
```

![image-20220924134837649](\Java基础image\image-20220924134837649.png)

### 交换数据：

##### 方式一：定义临时变量的方式

```java
public class Test1{
public static void main(String[] args){
int temp = num1;
num1 = num2;
num2= temp;
}
}
```

##### 方式二：使用数差的方式

```java 
public class Test2{
public static void main(String[] args){
num1 = num1 + num2;//num1 = 10 + 20 = 30
num2 = num1 - num2;//num2 = 30 - 20 = 10
num1 = num1 - num2;//num1 = 30 - 10 = 20
}
}
```

##### 方式三：使用位运算符

```java
public class Test3{
    public static void main(String[] args){
       num1 = num1 ^ num2;
       num2 = num1 ^ num2;
       num1 = num1 ^ num2;
    }
}
```

## 三元运算符（三目运算符）

1. 结构：（条件表达式）？表达式1：表达式2；

2. 说明

   - 条件表达式的结果位boolean类型。
   - 根据表达式真假，决定执行表达式1，还是表达式2。
   - 如果表达式位true，则执行表达式1，反之则执行表达式2。
   - 表达式1和表达式2要求是一致的。
   - 三元运算符可以嵌套使用

3. 凡事可以用三元运算符的地方，都可以改写为if - else

   反之不成立。

4. 如果程序既可以使用三元运算符，又可以使用if - else结构，那么优先选择三元运算符。原因：简洁、执行效率高。

```java
public classTest4{
	public static void main(String[] args){
		int m = 12, n = 5;
		max = (n < m) ? "m大" : ((n == m) ? "n == m" : "n大");
	}
}
```

#### 三个数最大值

```java
public class Test4{
	public static void main(String[] args){
	int n1 = 10;
	int n2 = 20;
	int n3 = -30;
        
        int max1 = (n1 < n2) ? n2 : n1;
        int max2 = (max1 < n3) ? n3 : max1;
       	System.out.print("最大的数为：" + max2);
        //等量代换，将ma1用(n1 < n2) ? n2 : n1;表示
        int max3 = ((n1 < n2) ? n2 : n1 < n3) ? n3 : (n1 < n2) ? n2 : n1;
        //解这种题找相同的用变量代替
	}
}

```

## 运算符的优先级

运算的优先级与结合性

![image-20220924211429671](\Java基础image\image-20220924211429671.png)

## 流程控制

- 顺序结构

- 选择结构

  ```java
  	if(条件表达式){
  执行表达式1;
  }
  ```

  ```java
  if(条件表达式){
  执行表达式1;
  }else{
  执行表达式2;
  }
  ```

  ```java
  if(条件表达式1){
  执行表达式1;
  }else if(条件表达式2){
  执行表达式2；
  }else if(条件表达式3){
  执行表达式3;
  }
  ```

  

- 循环结构

```java
while(布尔类型){
    执行表达式;
}

do{
    执行表达式;
}while();

for(; ; ){
    执行表达式;
}
```

# 类的导入和使用之Scanner类

如何从键盘中获取不同的类型的变量：需要使用Scanner类

具体实现步骤：

1. 导包：`import java.util.Scanner;`

2. Scanner的实例化（后期面向对象的时候详讲）

   `Scanner scan = new Scanner(System.in);`

3. 调用Scanner类的相关方法(`next() / nextXx`)，来获得指定类型的变量

```java
import java.util.Scanner;
class ScannerTest{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        int num = nextInt();
        System.out.println(num);
    }
}
```

<img src="\Java基础image\image-20220925010156019.png" alt="image-20220925010156019" style="zoom: 67%;" />	

求质数例题：

```java
class Test{
    public static void main(String[] args){
        boolean flag = true;
        long start = System.currentTimeMillis();
        for(int i = 2; i <= 100; i++){
          		  for(int j = 2; j < i; j++)
                  {
                      flag = false;
                  }
            if(flag == true){
            System.out.println(i);
        	}
            flag = false;
        }
        
        long end = System.currentTimeMillis();
        
        System.out.println("运行时间为：" + (end - start) + "毫秒");
    }
}
    
```

# 数组

数组本身是**引用类型**，而数组中的元素可以是任何类型，包括基本数据类型和引用类型。

创建数组对象会在内存中开辟一整快连续的空间，而数组名中引用的是这块空间连续空间的首地址。

数组的**长度一旦确定，就不能修改**。

我们可以直接通过下标（或索引）的方式调用指定位置的元素，速度很快。

数组的分类：

1. 按照维度：一维数组、二维数组、三维数组、……
2. 按照元素的数据类型分：基本数据类型元素的数组、引用数据类型元素的数组（即对象数组） 



## 数组的声明与初始化

```java
class Test{
    public static void main(String[] args){
        
        int num;//声明
        num = 10;//初始化
       	int id = 1001;//声明 + 初始化
        //一维数组
        int[] array;//数组的声明
        array = new int[]{1001, 1002, 1003, 1004};//数组的初始化
        String[] names = new String[5];
    }
}
```

## 错误声明和初始化

```java
class Test2{
	public static void main(String[] args){
        int[] arr1 = new int[];
        int[5] arr2 = new int[5];
        int[] arr3 = new int[3] = {1, 2, 3};
        
        //数组一但初始化完成，其长度就确定了。
    }
}

```

## Java的内存分配

- 堆：方法运行时使用的内存，比如main方法，进入方法栈中执行
- 栈：存储对象或者数组，new来创建的，都存储在堆内存
- 方法区：存储可以运行的class文件
- 本地方法栈：[JVM]()在使用操作系统功能的时候使用，和我们开发无关
- 寄存器：给CPU使用，和我们开发无关



## 数组的内存

两个数组指向同一个空间的内存图

 

```java
class ArrayTest{
    public static void main(String[] args){
        int[] arr1 = {11, 22};
        int[] arr2 = arr1;
        
        System.out.println("arr1[0] = " + arr1[0]);
        System.out.println("arr1[1] = " + arr1[1]);
        
        System.out.println("arr2[0] = " + arr2[0]);
        System.out.println("arr2[1] = " + arr2[0]);
        
        System.out.println("----------修改后---------");
        arr2[0] = 100;
        
        System.out.println("arr1[0] = " + arr1[0]);
        System.out.println("arr1[1] = " + arr1[1]);
        
        System.out.println("arr2[0] = " + arr2[0]);
        System.out.println("arr2[1] = " + arr2[1]);
    }
}
```

> `运行结果`:

```java
arr1[0] = 11
arr1[1] = 22
arr2[0] = 11
arr2[1] = 11
----------修改后---------
arr1[0] = 100
arr1[1] = 22
arr2[0] = 100
arr2[1] = 22
```



> 当两个数组指向同一个小空间时，其中一个数组对小
> 空间中的值发生了改变，那么其他数组再次访问的时
> 候都是修改之后的结果了。

# 方法

1. Java类及类的成员
2. 面向对象的三大特征
3. 其他关键字

> 理解:方法就是一个C语言中的函数而已



## Java的参数传递机制：值传递

在传输实参给方法的形参的时候，并不是传输实参变量本身，而是传输实参变量中存储的值，这就是`值传递`。

### 注意：

- 实参：如在方法内部定义的变量。
- 形参：如在定义方法时，“（）”中所声明的参数。

#### 基本类型传递：

```java
class Test{
     public static void main(String[] args){
         //理解Java的基本类型的参数传递，值传递。
         int a = 10;
         change(10);
     }
    
    
    public static void change(int a){
        System.out.println(a);
        a = 20;
        System.out.println(a);
    }
}
```



#### 引用类型传递：

```java
class Test{
    public static void main(String[] args){
        int[] arrs = new int[]{10, 20, 30};
        change(arrs);
        System.out.println(arrs[1]);
    }
    public static void change(int[] arrs){
        System.out.println(arrs[1]);
        arrs[1] = 222;
        System.out.println(arrs[1]);
    }
}
```

#### 总结：

- 基本类型的参数传存储的数据值。
- 引用类型的参数传存储的地址值。`（如数组跟C语言一样都是传首元素地址）`







## 方法

方法是程序中最小的执行单元

定义：把一些代码打包在一起，该过程称为`方法的定义`。

调用：方法定义后并不是直接运行的，需要手动调用才能执行，该过程称为`方法调用`。

### 方法简单定义格式：

```java
public static void 方法名(){
    方法体(就是打包起来的代码);
}

public static void playGame(){
    System.out.println("Hello World!");
}
```

### 调用：

```java
class Test1{
    public static void main(String[] args){
		方法名();
    }
}


class Test2{
    public static void main(String[] args){
		playGame();        
    }
}

```

### 方法完整定义格式：

```java
修饰符 返回值 方法名(形参列表){
    方法体代码(需要执行的功能代码)
        return 返回值;
}
```

### 示例：

```java
/* public static 方法的修饰符*/
/* int 返回值类型*/
/* add 方法名称*/
/* (int a, int b) 形参列表*/
public static int add(int a, int b){
    int c = a + b;
    return c;
}
```

### 方法重载:

- 同一个类中，出现多个方法名称相同，但是形参列表不同的，那么这些方法就是重载方法。

### 示例：

```java
class Test{
    public static void main(String[] args){
        fire();
    }
    
    public static void fire(){
        System.out.println("默认操作");
    }
    
    public static void fire(int x){
        for(int i = 0; i < x; i++){
        System.out.println("默认操作");
        }
    }
    
    public static void fire(int x, String name){
        for(int i = 0; i < x; i++){
            System.out.println(name);
        }
    }
}
```

*总结：重载不过是一个函数实现多个功能罢了！*

#### 方法重载的优化写法：

```java
class Test{
    public static void main(String[] args){
        fire();
    }
    
    public static void fire(){
        fire(1,"默认操作");
    }
    
    public static void fire(int x){
        fire(x, "默认操作");
    }
    
    public static void fire(int x, String name){
        for(int i = 0;  i < x; i++){
            System.out.println(name);
        }
    }
}
```

> `总结：优化写法不过是将参数较少的函数结合一身为参数最多那一个！`

### 单独使用`return`关键字

```java
class Test{
    public static void main(String[] args){
        count(1, 0);
    }
    
    public static void count(int a, int b){
        if(b == 0){
            System.out.println("b不能为除数！");
            return;
        }
        int c = a / b;
        System.out.println("结果为：" + c);
    }
}
```

# 面向对象 

介绍：

​	面向对象并不是一个技术，而是一种编程思想。

- 面向：拿、找
- 对象：能干活的东西
- 面向对象编程：拿东西过来做对应的事情

### 面向对象编程的指导思想、优点:

- 在程序中也把现实世界的具体事物全部看成一个一个的对象来解决问题。
- 按照面向对象编程来设计程序：程序代码符合人类思维习惯，更易理解、更简单。



### 类的定义：

- 类是共同特征的描述(设计图)；对象：是真实存在的具体实例。

> 理解：描述一个人，类就是说这个人应该有啥，对象就是说这个人有的东西详细是啥



```java
//类定义
public class 类名{
    1.成员变量(代表属性的, 一般是名词)
    2.成员方法(代表行为的, 一般是动词)
        
}
```

```java
类名 对象名 = new 类名();
```

例：

```java
---------------手机的设计图-------------------
    //类的定义
public class Phone{
    String 螺丝;
    String 屏幕;
    String 边框;
    
    public void 打电话(){
        System.out.println("手机正在打电话");
    }
    
    public void 玩游戏(){
        System.out.println("手机正在玩游戏");
    }
}

```

```java
//类的使用
public class Test{
    public static void main(String[] args){
        Phone p = new Phone();//准备一个手机的图纸模型
        
        //开始装修类
        p.螺丝 = "郑州富士康"; 
        p.屏幕 = "三星OLED";
        p.边框 = "华强北";
        
        
        
    }
}
```

### 类定义建议：

1. *类名首字母大写、英文、有意义，满足驼峰模式，不能用关键字，满足标识符规定;*
2. *一个Java文件中可以定义多个类，但是只能一个类是public修饰的，public修饰的类名必须是Java代码的文件名称。*



## 封装

> ​	**对象代表什么，就得封装对应的数据，并提供数据对应的行为**



例子：人画圆是对人设计花圆方法，还是对圆设计画圆方法

解： 人只是对画圆进行了一个作用力，是圆本身画出来的，所以是对圆设计画圆方法。

总结：人关门，也是对门设计关门的方法；张三用砍刀把李四砍死了，也是对李四设计死亡的方法。

### private关键字



- 是一个权限修饰符
- 可以修饰成员（成员变量和成员方法）
- 被private修饰的成员只能在本类中才能访问

`拓展：public与private相反，public是表示公共的、公开的，在所有的类中都可以使用他的方法。`

实现正确的数据才能赋值，错误的不能被赋值。

```java
class GirlFriend{
   	private int age;
    
    public void setAge(int a){
        if(a >= 18 && a <= 50){
            age = a;
        }else{
            System.out.println("非法数据");
        }
    }
    public void getAge(){
        System.out.println(age); 
    }
    //针对每一个私有化的成员变量，都要提供get和set方法
    //get方法：对外提供成员变量的值，方法用public修饰
    //set方法：给成员变量赋值，方法用public修饰
}

```

```java
class Test{
    private int age;
    
    public void method(){
        int age = 10;
        this.age = age;
        //this也可使用在private修饰的变量中
    }
}
```



## 构造器

作用：在创建对象的时候，由虚拟机自动调用，给成员变量进行初始化。

- 用于初始化一个类的对象，并返回对象的地址。

  ```java
  Car c = new Car();
  ```

  

### 构造器的定义格式

```java
修饰符 类名(参数){
    方法体;
}

public class Car{
    ...
        public Car(){
        ...
    }
}
```



注意事项;

- 任何类定义出来，默认就自带了无参构造器，写不写都有。
- 一旦定义了有参构造器，无参构造器就没有了，此时就需要自己写一个无参构造器了。

```java
public class Car{
    ...
        //无参构造器（默认存在的）  
}
```

```java
public class Car{
    ...
    //无参构造器（需要写出来了）
    public Car(){
    }
    //有参构造器
    public Car(String n, String b){
    }
}
```



## this关键字

作用：出现再成员方法、构造器中代表当前对象的地址、用于访问当前对象的成员变量、成员方法。

```java
public class Car{
    String name;
    double price;
    
    public Car(String n, double b){
        name = n;
        price = b;
    }
}

//-------------------------------------------------------------
public class Car{
    String name;
    double price;
    
    public Car(String name, double price){
        this.name = name;
        this.price = price;
        //this的用法就是区分对象和成员变量的
    }
}
```

> 总结：主要是用于区分成员变量和局部变量

## JavaBean类

- 也可以理解成实体类，其对象可以用于在程序中封装数据。

### 标准JavaBean须满足如下要求：



1. 类名需要见名知意

2. 成员变量使用private修饰。

3. 提供至少两种构造方法

   - 无参构造方法
   - 带全部参数的构造方法

4. 成员方法

   - 提供每一个成员变量对应的setXxx() / getXxx()。
   - 如果还有其他行为，也需要写上

   

> 成员变量完整定义格式是：修饰符 数据类型 变量名称 = 初始化值；



例：

```java
class Test{
    //属性
    private String username;
    private String password;
    private String email;
    private String gender;
    private int age;
    
    public Test(){}//无参构造器
    public Test(String username, String password, String email, String gender, int age){
        this.username = username;
        this.password = password;
        this.email = email;
        this.gender = gender;
        this.age = age;
    }
    //get和set方法
    public void setUsername(String username){
        this.username = username;
    }
    
    public String getUsername(){
        return username;
    }
    
    //快捷键：
    alt + insert;
    
    
}
```



# 对象内存图



### JVM 包含

- 栈
- 堆
- 方法区
- 本地方法栈
- 寄存器

> 从JDK8开始，取消方法区，新增元空间。把原来方法区的多种功能进行拆分,有的功能放到了堆中，有的功能放到了元空间中。
>

1. 加载class文件 
2. 申明局部变量
3. 在堆内存中开辟一个空间
4. 默认初始化
5. 显示初始化
6. 构造方法初始化
7. 将堆内存中的地址赋值给左边的局部变量

> class文件被一个对象使用加载后，例外再有一个对象使用就不用加载，直接使用





# 对象的创建（String）



```java
class Test{
    public static void main(String[] args){
        String s1 = "abc";
        System.out.pringln(s1);
        
        //空参构造
        String s2 = new String();
        //输出：     //效果相当于输出""
        
        //有参构造
        String s3 = new String("abc");
        //输出：abc 
        
        //有参构造应用场景
        char[] chs = {'a', 'b', 'c'};
        String s4 = new String(chs);
        //输出：abc
        
        //传递一个字节数组，根据字节数组内容再创建一个新的字符串对象，应用场景在网络传输的数据其实是字节信息，我们通过这个构造进行传输和转义成字符串
        byte[] bytes = {97, 98, 99};
        String s5 = new String(bytes);
        //输出：abc
        //根据ascll码转义输出                           
    }
}
```





### Java 的内存模型

![image-20221022224923072](\Java基础image\image-20221022224923072.png)



> 当使用双引号直接赋值时，系统会检查该字符串在串池中是否存在。
>
> 不存在：创建新的
>
> 存在：复用

`new 出来的都是在堆中开辟一个新空间`





### 字符串比较

“ == ” 比的是什么：

1. 基本数据类型：比较的是数据值
2. 引用数据类型：比较的是地址值

比较的方法：

- boolean equals方法（要比较的字符串）//完全一样
- boolean equalsIgnoreCase（要比较I的字符串） //忽略大小写







### StringBuilder 类的使用

作用：

1. 一个可变的操作字符串的容器。	
2. 可以高效的拼接字符串， 还可以将容器的内容反转。



方法：

```java
append();
```





### StringJoiner类的使用

应用场景：和StringBuilder一样

构造方法：

```java
public StringJoiner(间隔符号)
public StringJoiner(间隔符号, 开始符号, 结束符号)   
```

例：

```java
class Test{
    public static void main(String[] args){
        StringJoiner sj = new StringJoiner("-");
        //1-2-3
        StringJoiner sj = new StringJoiner(",", "[", "]");
        //[1,2,3]
    }
}
```

成员方法：

> 由于返回值可以改变原值，所以可以用链式编程。

例：

```java
class Test{
    public static void main(String[] args){
        StringJoiner sj = new StringJoiner(",");
        sj.add("a").add("b").add("c");
        int lne = sj.length(); //5
        System.out.println(sj);
        
        String str = sj.toString();//转换成字符串
        Syste,.out.println(str);
    }
}
```



### 字符串拼接的底层原理

- 如果没有变量参与，都是字符串直接相加，编译之后就是拼接之后的结果，会复用串池中的字符串。
- 如果有变量参与，每- -行拼接的代码，都会在内存中创建新的字符串,浪费内存。



### StringBuilder提高效率原理图

- 所有要拼接的内容都会往StringBuilder中放，不会创建很多无用的空间，节约内存

![image-20221025203759883](\Java基础image\image-20221025203759883.png)

# 集合ArrayList

集合定义后类型不固定，大小是可变的。

```java
class Test{
    public static void main(String[] args){
        //1.创建ArrayList集合的对象
        //JDK8前写法      
        ArrayList<String> list = new ArrayList<String>();
        //JDK8后
        ArrayList<String> list = new ArrayList<>();
        
    }
}
```

