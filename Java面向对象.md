# static 静态变量

```java
//该类与下一代码块结合
class Student{
  	String name;
 	int age;
    static String teacherName;
}
```

```java
class Main{
    public static void main(Sting[] args){
       
        Student student1 = new Student();
        student1.teacherName = "张三";
        student1.name = "龙四";
        student1.age = 20;
        
        Student student2 = new Student();
        student2.teacherName = "张三";
        student2.name = "王五";
        student2.age = 22;
        
        //Student.teacherName = "张三";
        //可以直接省略
        //student1.teacherName = "张三";
        //student2.teacherName = "张三";
    }
}
```

> 直接使用类名 "." 上公有变量，可以直接修改；

### 被static修饰的成员变量，叫做静态变量

1. ​	特点
   - 被该类所有对象共享
   - 不属于对象，属于类
   - 随着类的加载而加载，优先于对象存在
2. 调用方法：
   - 类名调用（推荐）
   - 对象名调用

### 被static修饰的成员方法，叫做静态方法

1. 特点：
   - 多用在测试类和工具类中
   - Javabean类中很少会用



![image-20221030190410971](Java面向对象image\image-20221030190410971.png)

### 工具类

- 私有化构造方法

***目的：为了不让外界创建它的对象***

- 静态初始化行为





static的注意事项

- **静态方法只能访问静态变量和静态方法**
- 非静态方法能访问静态变量或者静态方法，也可以访问非静态的成员变量和非静态的成员方法
- 静态方法中没有this关键字



> ***总结： 静态方法中，只能访问静态***
>
> ​			***非静态方法可以访问所有***
>
> ​			**静态方法中没有this关键字**

##### **个人理解：若静态可以访问非静态，静态怎么分辨这个非静态是哪个对象的**

例：

```java
class Test{
    String name;
    int age;
    
    public void show(){
        System.out.println("Hello");
    }
    
    public static void fun(){
        System.out.println(name);//报错，静态方法访问非静态的变量，编译器不知道是哪个对象的变量
        show();//同理调用非静态方法也是不清楚是哪个对象的方法
    }
    
}
```

### 重新认识main方法

 public:		被JVM调用，访问权限足够大
static:			被JVM调用，不用创建对象，直接类名访问
因为main方法是静态的，所以测试类中其他方法也需要是静态的。
void:			被JVM调用，不需要给JVM返回值
main :		一个通用的名称，虽然不是关键字，但是被JVM识别

String[] args:		以前用于 接收键盘录入数据的，现在没用

```java
public class Test {
	public static void main(String[] args) {
//[] :数组
//String 数据类型
//args :数组名
		System. out . print1n(args . length);
		for (int i = 0; i < args.1ength; i++) {
			System . out . print1n(args[i]);
		}
	}
}

```

### 封装总结：

> ​		对象代表什么，就得封装对应的数据，并提供数据对应的行为

·

# 继承

1. 什么是继承、继承的好处?
   `继承是面向对象三大特征之一,可以让类跟类之间产生子父的关系。`
   `可以把多个子类中重复的代码抽取到父类中，子类可以直接使用，减少代码冗余,提高代码的复用性`

2. 继承的格式?

   ```java
   public class 子类 extends 父类{}
   
   ```

3. 继承后子类的特点?
   `子类可以得到父类的属性和行为，子类可以使用。`
   `子类可以在父类的基础.上新增其他功能，子类更强大。`

### 特点：

> 1. Java只能单继承: 一个类只能继承一个直接父类。
> 2. Java不支持多继承、但是支持多层继承。
> 3. Java中所有的类都直接或者间接继承于Object类。



### 子类到底能继承父类中哪些内容：

> 构造方法   非私有       不能   private    不能
> 成员变量   非私有       能       private    能
> 成员方法   虚方法表   能       否则         不能

### 继承中：构造方法的访问特点

- 父类中的构造方法不会被子类继承。
- 子类中所有的构造方法默认先访问父类中的无参构造，再执行自己。

### 为什么?

- 子类在初始化的时候， 有可能会使用到父类中的数据，如果父类没有完成初始化,子类将无法使用父类的数据。	
- 子类初始化之前， 一定要调用父类构造方法先完成父类数据空间的初始化。

### 继承中构造方法的访问特点是什么?

- 子类不能继承父类的构造方法，但是可以通过super调用
- 子类构造方法的第一行，有一个默认的super();
- 默认先访问父类中无参的构造方法，再执行自己。
- 如果想要方法文父类有参构造，必须手动书写。

### this、super使用总结

-  this: 理解为一个变量，表示当前方法调用者的地址值
- super:代表父类存储空间

![image-20221103224252655](Java面向对象image\image-20221103224252655.png)

```java
public class Student {
	String name;
	int age;
	String school;
	//需求:
	//默认为传智大学
	public Student() {
		//表示调用本类其他构造方法
    	//细节：虚拟机就不会再添加super();
		this( name: nu1l, age: 12, school: "传智大学");
    }
	public Student(String name, int age, String school) {
        super();
		this.name = name;
		this.age = age;
		this.school = school;
    }
}
```

# 多态

### 什么是多态?

- 对象的多种形态。

### 2.多态的前提?

- 有继承/实现关系
- 有父类引用指向子类对象
- 有方法的重写

### 3.多态的好处?

- 使用父类型作为参数，可以接收所有子类对象,
- 体现多态的扩展性与便利。



### 多态的优势：

- 在多态形式下，右边对象可以实现解耦合,便于扩展和维护。

```java
Person p = new Student();
p.work(); // 业务逻辑发生改变时，后续代码无需修改
```



- 定义方法的时候，使用父类型作为参数，可以接收所有子类对象,体现多态的扩展性与便利。



### 多态的和弊端：

**若创建子类对象赋值给父类类型，父类只能调用父类中与子类共有的方法，不能调用子类特有的方法。**

```java
class test(){
 	psvm(String[] args){
		Animal a = new Dog();
 		a.eat();//运行结果：吃骨头
        a.lookHome();//运行报错
        
        //解决方法：
        //将Animal类型转为Dog类型
     	if(a instanceof Dog){//Animal 为判断一个对象真实是啥变量的，理解为对象的照妖镜就行了
            Dog d = (Dog)a;
        }
        //jdk11后有新特性解决此问题
        if(a instanceof Dog d){//与上面代码意思一模一样，为jdk11后的优化写法
            
        }
 	}
}
class Animal{
    public void eat(){
        sout("吃东西");
    }
}
class Dog extends Animal{
    public void eat(){
        sout("吃骨头");
    }
    public void lookHome(){
        sout("看家");
    }
}
class Cat extends Animal{
    public void eat(){
        sout("吃鱼");
    }
}

```

![image-20221105152316554](\Java面向对象image\image-20221105152316554.png)

### 包

![image-20221105153853408](\Java面向对象image\image-20221105153627178.png)

# final

1. final修饰方法:
   表明该方法是最终方法，不能被重写
2. final修饰类:
   表明该类是最终类，不能被继承
3. final修饰变量:
   叫做常量，只能被赋值一次（define一样作用）

### 常量

实际开发中，常量一般作为系统的配置信息，方便维护，提高可读性。
常量的命名规范:

- 单个单词:全部大写

- 多个单词:全部大写，单词之间用**下划线**隔开

### 细节:

- final修饰的变量是基本类型:那么变量存储的**数据值**不能发生改变。
- final修饰的变量是引用类型:那么变量存储的**地址值**不能发生改变,对象内部的可以改变。

权限修饰符

private < 缺省/默认 < protected < public 

![image-20221105155849364](\Java面向对象image\image-20221105155849364.png)

### 代码块

简介：代码块就是写在大括号"{}"里的就统一称为代码块。

### 构造代码块

未使用构造代码块：

```java
class Tset{
    private int age;
    private String name;
    
    public Test(){
        sout("Hello World");
    }
    public Test(int age, String name){
        sout("Hello World");
    }
}
```

使用了构造代码块：

```java
class Tset{
    private int age;
    private String name;
    
    {
        sout("Hello World");//这就是默认每一个构造里都执行语句
    }
    
    //还有静态代码块通常用来初始化成员变量
    static {
        //静态代码块内容
    }
    public Test(){
        
    }
    public Test(int age, String name){
       
    }
}
```

# 抽象类

### 一、[抽象类](https://so.csdn.net/so/search?q=抽象类&spm=1001.2101.3001.7020)与抽象方法的定义

- 抽象类：只在普通类的基础上扩充了一些抽象方法
- 抽象方法：只声明而未实现的实体（即抽象方法没有方法体）



> 所有的[抽象方法](https://so.csdn.net/so/search?q=抽象方法&spm=1001.2101.3001.7020)和抽象方法所在的类都要使用abstract关键字定义，用abstract关键字定义的抽象方法所在的类称为抽象类

> 抽象类中包含抽象方法，抽象方法不包含方法体，即抽象类中没有具体实现，所以抽象类中不能直接产生实例化对象

例：

```java
abstract class Person{
	public String name;//属性
	public int age;//属性
			
	public abstract void eat();//抽象方法
			
	public void play(){//普通方法
		System.out.println(name+"玩")；
	}
			
}
```

### 二、抽象类的使用规则

- 所有的抽象类必须含有子类；
- final和abstract不能同时使用；
- 抽象类的自雷必须腹泻抽象类的所有抽象方法（子类不是抽象类）；
- private和abstract不能同时使用；
- 抽象类实例化对象，必须通过子类向上转型来实例化对象（抽象类无法直接实例化对象）

举例：抽象类的使用:

```java
abstract class Person{
    public String name;//属性
     
    public String getName(){//普通方法
         return this.name;
    }
	
    public void setName(String name){
         this.name = name;
    }
    //{}为方法体，所有抽象方法上不包括方法体
 
	public void play(){//普通方法
		System.out.println(name+"玩")；
	}
    public abstract void eat();//抽象方法
}
 
//继承抽象类	
class Student extends Person{
	public abstract void eat(){
		System.ouut.println("I am eating food");
	}
}
 
public class Teat{
	public static void main(String[] args){
		Person person = new Student;//实例化子类，向上转型
		person.eat();//被子类覆写的方法
	}
}	
```

### 三、抽象类的相关规定

- 抽象类比普通类多了一些抽象方法，所以在抽象类中也允许提供构造方法，并且子类遵循对象的实例化流程（先调用父类的构造方法，再调用子类构造方法）。实例化子类时一定要先调用父类的构造方法；
- 如果父类没有无参构造，那么子类必须使用super明确指出父类的哪个构造方法；
- 抽象类中可以不定义任何的构造方法，但该抽象类无法直接创建实例化对象；
- 抽象类不能用final声明，因为final声明的类不允许有子类，而abstract抽象类必须有子类；
- 抽象方法不能用private定义，因为抽象方法必须要被覆写；
- 抽象类也分为内部抽象类和外部抽象类，内部抽象类可以使用static定义来描述外部抽象类。

# 接口

 官方解释：Java接口是一系列方法的声明，是一些方法特征的集合，一个接口只有方法的特征没有方法的实现，因此这些方法可以在不同的地方被不同的类实现，而这些实现可以具有不同的行为（功能）。

> 我的解释：接口可以理解为一种特殊的类，里面全部是由全局常量和公共的抽象方法所组成。接口是解决Java无法使用多继承的一种手段，但是接口在实际中更多的作用是制定标准的。或者我们可以直接把接口理解为100%的抽象类，既接口中的方法必须全部是抽象方法。（JDK1.8之前可以这样理解）

### 接口的特点

 就像一个类一样，一个接口也能够拥有方法和属性，但是在接口中声明的方法默认是抽象的。（即只有方法标识符，而没有方法体）。

 

- 接口指明了一个类必须要做什么和不能做什么，相当于类的蓝图。
- 一个接口就是描述一种能力，比如“运动员”也可以作为一个接口，并且任何实现“运动员”接口的类都必须有能力实现奔跑这个动作（或者implement move()方法），所以接口的作用就是告诉类，你要实现我这种接口代表的功能，你就必须实现某些方法，我才能承认你确实拥有该接口代表的某种能力。
- 如果一个类实现了一个接口中要求的所有的方法，然而没有提供方法体而仅仅只有方法标识，那么这个类一定是一个抽象类。（必须记住：抽象方法只能存在于抽象类或者接口中，但抽象类中却能存在非抽象方法，即有方法体的方法。接口是百分之百的抽象类）
- 一个JAVA库中接口的例子是：Comparator 接口，这个接口代表了“能够进行比较”这种能力，任何类只要实现了这个Comparator接口的话，这个类也具备了“比较”这种能力，那么就可以用来进行排序操作了。

### 为什么要用接口

-  接口被用来描述一种抽象。
- **因为Java不像C++一样支持多继承，所以Java可以通过实现接口来弥补这个局限。**
- 接口也被用来实现解耦。
- 接口被用来实现抽象，而抽象类也被用来实现抽象，为什么一定要用接口呢？接口和抽象类之间又有什么区别呢？原因是抽象类内部可能包含非final的变量，但是在接口中存在的变量一定是final，public,static的

### 接口的语法实现

为了声明一个接口，我们使用interface这个关键字，在接口中的所有方法都必须只声明方法标识，而不要去声明具体的方法体，因为具体的方法体的实现是由继承该接口的类来去实现的，因此，接口并不用管具体的实现。接口中的属性默认为Public Static Final.一个类实现这个接口必须实现这个接口中定义的所有的抽象方法。

**一个简单的接口就像这样：拥有全局变量和抽象方法。**



### 总结

![image-20221109152427990](\Java面向对象image\image-20221109152427990.png)

### 接口与类之间的关系

- 类与类之间的关系

  - 继承关系，只能单继承，不能多继承，但是可以多层继承

- 类与接口的关系

  - 实现关系，可以单实现，也可以多实现，还可以在继承一个类的同时实现多个接口

  **情况：若接口中的抽象方法与类里的方法重名只要重写一次两个接口都被重写**

- 接口和接口的关系

  - 继承关系，可以单继承，也可以多继承

### 扩展

- jdk7以前：接口中只能定义抽象方法。
- jdk8的新特性：接口中可以定义有方法体的方法。（默认、静态）
- jdk9的新特性：接口中可以定义私有方法

![image-20221109173621217](Java面向对象image\image-20221109173621217.png)

# 内部类

内部类就是定义在类里面的类就是内部类

### 特点

- ​	内部类可以直接访问外部类的成员，包括私有
- ​	外部类要访问内部类的成员，必须创建对象

![image-20221110204523744](C:\Users\Cold\AppData\Roaming\Typora\typora-user-images\image-20221110204523744.png)

![image-20221110205256081](Java面向对象image\image-20221110205256081.png)

### 成员内部类行为方法重名分析![image-20221110215701353](\Java面向对象image\image-20221110215701353.png)

![image-20221110215746829](\Java面向对象image\image-20221110215746829.png)

### 静态内部类

![image-20221110220529321](\Java面向对象image\image-20221110220529321.png)

### 局部内部类

![image-20221110221042787](Java面向对象image\image-20221110221042787.png)

![image-20221110223151515](Java面向对象image\image-20221110223151515.png)