[toc]

# 相关链接

[文字教学](http://c.biancheng.net/java/) 

[b站 黑马java](https://www.bilibili.com/video/BV1Cv411372m) 

[菜鸟教程java](https://www.runoob.com/java/java-tutorial.html) 









---



# 环境与工具



## JDK的组成

<img src="https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20220109125613610.png" alt="image-20220109125613610" style="zoom: 50%;" />





## Java项目结构

* project（项目、工程）
* module（模块）
* package（包）
* class（类）

<img src="https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20220109131436301.png" alt="image-20220109131436301" style="zoom: 67%;" />

<img src="https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20220109131724413.png" alt="image-20220109131724413" style="zoom:67%;" />

### 包

包是用来分门别类的管理各种不同类的，类似于文件夹、建包利于程序的管理和维护。

建包的语法格式: `package 公司域名倒写.技术名称`。包名建议全部英文小写，且具备意义

```java
package com.baidu.javabean;
```

* **相同包下的类可以直接访问，不同包下的类必须导包,才可以使用!** 

导包格式: `import 包名.类名;` 





## IDEA常用快捷键

| 快捷键                      | 功能                              |
| --------------------------- | --------------------------------- |
| Alt + Enter                 | 提供快速修复选择                  |
| Ctrl + D                    | 复制当前行到下一行                |
| Ctrl + X                    | 删除所在行                        |
| Ctrl + Alt + L              | 格式化代码                        |
| ALT + Shift + ↑/↓           | 上下移动当前代码                  |
| Ctrl + / , Ctrl + Shift + / | 注释                              |
| F2                          | 跳转到下一个高亮错误 或 警告位置  |
| Ctrl + Shift + Z            | 取消撤销                          |
| Ctrl + Alt + T              | 快速将代码包含在if,for,while...里 |



| 快捷语句   | 生成                                          |
| ---------- | --------------------------------------------- |
| main, psvm | public static void main(String[] args) {    } |
| sout       | System.out.println();                         |
| fori       | for (int i = 0; i < ; i++) {      }           |
| arr.fori   | for (int i = 0; i < arr.length; i++) {    }   |





## IDEA设置

仅个人喜好，记录用

```
文件 -> 设置 -> 插件
搜索 Chinese，找到中文语言包，安装
搜索 CodeGlance 安装
搜索 Alibaba Java CodingGuidelines，安装。工具 -> 阿里编码规约 ->关闭实时检测功能

视图 -> 外观
工具栏打开

文件 -> 设置 -> 编辑器 -> 代码样式 -> java -> 制表符和缩进
使用制表符 打开
智能制表符 打开

文件 -> 设置 -> 编辑器 -> 代码样式 -> java -> 代码生成 -> 注释的代码
行注释在第一列 关闭
在注释开始添加一个空格 打开

文件 -> 设置 -> 编辑器 -> 常规 -> 鼠标控制
使用 ctrl + 鼠标轮更改字体大小 打开

文件 -> 设置 -> 编辑器 -> 配色方案 -> 常规 -> 错误和警告 -> 未知符号
前景 颜色72737A (原BC3F3C)
效果 打开，选择波浪下划线，颜色9D236D

文件 -> 设置 -> 编辑器 -> 常规 -> 外观
显示方法分隔符 打开

文件 -> 设置 -> 编辑器 -> 常规 -> 代码完成
匹配大小写 关闭
```





## DEBUG工具

![image-20220110154919891](https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20220110154919891.png)









---



# JAVA基础语法

## 注释

### 单行注释

```java
//单行注释，快捷键Ctrl + /
```



### 多行注释

```java
/*
	多行注释，快捷键Ctrl + Shift + /
	略略略
*/
```



### 文档注释

```java
/**
	文档注释
	略略略
*/
```





## 变量

### 声明变量

```java
数据类型 变量名称 = 初始值;
数据类型 变量名称;

int a = 1;
double b;
```





## 数据类型

![image-20220110154204339](https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20220110154204339.png)

### 基本数据类型

| 数据类型 |          关键字           |                  取值范围                  | 内存占用（字节数） |
| :------: | :-----------------------: | :----------------------------------------: | :----------------: |
|   整数   |           byte            |                 -128 ~ 127                 |         1          |
|   整数   |           short           |               -32768 ~ 32767               |         2          |
|   整数   |        int（默认）        |          -2147483648 ~ 2147483647          |         4          |
|   整数   | long（常量后面要加 l/L）  | -9223372036854775808 ~ 9223372036854775807 |         8          |
|  浮点数  | float（常量后面要加 f/F） |        1.401298e-45 ~ 3.402823e+38         |         4          |
|  浮点数  |      double（默认）       |       4.9000000e-324 ~ 1.797693e+308       |         8          |
|   字符   |           char            |                 0 ~ 65535                  |         2          |
|   布尔   |          boolean          |                true, false                 |         1          |



### 引用数据类型

* 引用类型变量存储的是堆区域的地址

```java
String
数组
```



### 强制类型转换

* 注意数据溢出会丢数据

```java
数据类型 变量1 = (数据类型)变量2/数据
byte b = (byte)a;
```



### 枚举

枚举是Java中的一种特殊类型，是为了做信息的标志和信息的分类

```java
修饰符 enum 枚举名称{
    //第一行都是罗列枚举类实例的名称
}
```

实例：

```java
public enum Direction{
    UP,DOWN,LEFT,RIGHT;
}

public static void move(Direction d){
    switch (d){
        case UP:
            System.out.println("上！");break;
        case DOWN:
            System.out.println("下！");break;
        case LEFT:
            System.out.println("左！");break;
        case RIGHT:
            System.out.println("右！");break;
    }
}
```





## 运算符

### 算术运算符

```java
+
-
*
/ //(整除)
%
++ //(前缀，后缀)
-- //(前缀，后缀)
```



### 赋值运算符

```java
=
+=
-=
*=
/=
%=
```



### 关系运算符

```java
==
!=
>
>=
<
<=
```



### 逻辑运算符

```java
&  //与（不短路）
&& //双与（短路）
|  //或（不短路）
|| //双或（短路）
!  //非
^  //异或
```



### 三元运算符

```java
条件表达式 ? 值1 : 值2;
//为真返回值1，为假返回值2
```





## 分支控制

### if...else

* 同c

```java
if(条件表达式){
    语句体1;
}
else if(条件表达式2){
    语句体2
}
...
else{
    语句体3;
}
```



### switch...case

* 表达式类型只能是`byte, short, int, char`，JDK5开始支持`枚举`，JDK7开始支持`String`，**不支持`double, float, long`**。 
* case给出的值不允许重复，且只能是常量
* 不要忘记break！

```java
switch(表达式){
    case 值1:
        执行代码...;
        break;
    case 值2:
        执行代码...;
        break;
    ...
    default:
        执行代码...;
}
```





## 循环控制

### for

* 同c

```java
for(初始化语句; 循环条件; 迭代语句){
    循环体语句;
}

for (int i = 0; i < 3; i++) {
    System.out.println("Hello World");
}
```



### 只读for

* 该语句是java5的新特征
* 该循环只读，无法修改数组内元素

```java
for(数据类型 临时变量名 : 数组名){
    临时变量将会逐次获得数组内的值;
}

double[] arr = new double[]{1,2,3};
for (double element: arr) {
    System.out.println(element);
}
```



### while

* 同c

```java
while(循环条件){
    循环体语句;
    迭代语句;
}

int i = 0;
while(i<3){
    System.out.println("Hello World");
    i++;
}
```



### do...while

* 同c

```java
do{
    循环体语句;
    迭代语句;
}while(循环条件);

int i = 0;
do {
    System.out.println("Hello World");
    i++;
} while (i < 3);
```



### break，continue

#### 基础用法

```java
break;    //跳出当前循环
continue; //跳出当前循环层
```

#### 标签

在循环语句之前可以给循环打上标签，之后可以利用`break`和`continue`跳出多层循环

```java
标签名:
外循环入口{
    内循环入口{
        ...;
        break 标签名;
        //continue 标签名;
    }
}

OUT:
while(true){
    for(int i = 1; i <= 100; i++){
        if(i == 20){
            break OUT;
        }
    }
}
```





## 数组

### 定义数组

#### 静态初始化数组

```java
数据类型[] 数组名 = new 数据类型[]{初始化列表};
数据类型[] 数组名 = {初始化列表};//简化形式

int arr[] = new int[] {1, 2, 3};
int arr[] = {1, 2, 3};

int a[][] = new int[][]{{1,2}, {3,4}};//二维数组
```

#### 动态初始化数组

* `int, byte, short, char, long`类型元素的默认值为`0` 
* `double, float`类型元素的默认值为`0.0`  
* `boolean`类型元素的默认值为`false` 
* `String, 类, 接口, 数组`类型元素的默认值为`null` 

```java
数据类型[] 数组名 = new 数据类型[长度];

int[] arr = new int[3];
```



### 访问数组

* 下标从0开始
* 允许修改指定元素

```java
数组名[下标];

arr[2];
```



### 数组属性

| 属性       | 说明     |      |
| ---------- | -------- | ---- |
| arr.length | 数组长度 |      |









---



# 面向对象

## 类

* 一个Java文件中可以定义多个class类，**且只能一个类是`public`修饰，而且`public`修饰的类名必须为代码文件名**。建议一个文件定义一个class类

### 定义类

* 成员变量可以不指定初始化值，存在默认值

```java
public class 类名{
    1.成员变量(属性);
    2.成员方法(行为);
    3.构造器(构造方法);
    4.代码块;
    5.内部类;
}
```





## 对象

### 声明对象

```java
类名 对象名 = new 类名(参数);
Car c = new Car()
```





## 方法

### 定义方法

* 注意基本数据类型是值传递，引用类型是地址传递

```java
修饰符 返回值类型 方法名(形参列表){
    具体代码;
    return 返回值;
}

public static int sum(int a, int b){
    int c = a + b;
    return c;
}
```



### 方法重载

同一个类中，出现多个方法名称相同，但是形参列表是不同的，那么这些方法就是重载方法。





## 构造器(构造方法)

**在生成一个对象的时候自动调用执行构造器**，构造器用于初始化一个类的对象，并返回对象的地址。

构造器根据传入参数的有无分为 无参构造器 和 有参构造器

* 任何类定义出来，默认就自带了无参数构造器。
* 一旦定义了有参数构造器，默认的无参数构造器就没有了，此时就需要自己写一个无参数构造器。

```java
修饰符 类名(形参列表){
    ...
}

class People{
    private String name;
    // 无参构造器
    public People(){
        name = "张三";
    }
    
    // 有参构造器
    public People(String name){
        this.name = name;
    }
}
```





## final修饰符

final 关键字是最终的意思，可以修饰（方法，变量，类) 

* 修饰方法：表明该方法是最终方法，不能被[重写](#方法重写)。
* 修饰变量：表示该变量第一次赋值后，不能再次被赋值(有且仅能被赋值一次)。
* 修饰类：表明该类是最终类，不能被继承。

示例：(比较少用)

```java
public final class String{
    ...;
}
```

### 常量

常量是使用了`public static final`修饰的成员变量，必须有初始化值，而且执行的过程中其值不能被改变。

可以用于做系统的配置信息，方便程序的维护，同时也能提高可读性。

* 建议命名全部大写，间隔用下划线`_`连接，如`MAX_WIDTH` 
* 在编译阶段会进行“宏替换”，把使用常量的地方全部替换成真实的字面量。

```java
public static final double PI = 3.1415926;
```





## this关键字

出现在成员方法、构造器中**代表当前对象的地址**，用于访问当前对象的成员变量、成员方法。





## static关键字

定义一个共享的信息，给所有对象共享访问。静态成员变量相当于整个类的信息

静态变量和方法是属于类的，不是属于对象的

### 定义

* 静态成员方法中不能使用非静态成员变量和方法
* 非静态成员方法中可以使用静态成员变量和方法

```java
// 1.定义静态成员变量
修饰词 public 数据类型 成员变量名称;
public static int num = 0;

// 2.定义静态成员方法
修饰词 static 返回值数据类型 成员方法名称(形参列表){...}
public static int getMax(int a, int b){return a > b ? a : b;}
```



### 静态成员对象/方法的访问

* `类名.静态成员变量/方法`(推荐)
* `对象.静态成员变量/方法`(不推荐)





## 代码块

在Java类下，使用(}括起来的代码被称为代码块。

代码块分为 静态代码块 和 构造代码块

### 静态代码块

* 格式：`static{}` 
* 特点：随着类的加载而加载，并且自动触发、只执行一次
* 使用场景：在类加载的时候做一些静态数据初始化的操作，以便后续使用。



### 构造代码块

* 格式：`{}`
* 特点：每次创建对象，调用构造器执行时，都会执行该代码块中的代码，并且在构造器执行前执行
* 使用场景：初始化实例资源





## 内部类

内部类就是定义在一个类里面的类，

* 内部类可以访问外部类的成员，包括私有成员

```java
public class People{// 外部类
    ...;
    public class Heart{// 内部类
        ...;
    }
}

创建内部类对象：
外部类名.内部类名 对象名 = new 外部类构造器().new 内部类构造器();
People.Heart h = new People().new Heart();
```

### 内部类访问外部类的同名成员

```java
外部类.this.成员;

示例：
public class People {
    double weight = 120;//外部类的成员
    
    public class Heart{
        double weight = 0.3;//内部类的成员
        public void show(){
            double ratio = weight / People.this.weight;//访问外部类的成员
            System.out.println("重量占比：" + ratio * 100 + "%");
        }
    }
}

People.Heart h = new People().new Heart();//创建内部类对象
h.show();// 重量占比：0.25%
```



### 匿名内部类

本质上是一个没有名字的局部内部类，定义在方法中、代码块中、等。

作用：方便创建子类对象，最终目的为了简化代码编写。

格式：

```java
new 类|接口(){
    重写方法
}
```

示例：

```java
public abstract class Animal {//抽象类
    abstract void eat();
}
//------------------------------------------------
// 1.不使用匿名内部类
public class Tiger extends Animal{
    @Override
    void eat() {
        System.out.println("吃肉");
    }
}

Animal tiger = new Tiger();//需要提前定义一个子类
tiger.eat(); // 吃肉
//-------------------------------------------------
// 2.使用匿名内部类
Animal tiger = new Animal() {//不需要定义子类
	@Override
	void eat() {
		System.out.println("吃肉");
    }
};
tiger.eat(); // 吃肉
```





## 封装

封装是隐藏类的内部实现机制，可以在不影响使用的情况下，改变类的内部结构，同时也保护了数据。且对外部只保留一些对外接口使之与外部发生联系。

加强了程序代码的安全性。适当的封装可以提升开发效率，同时可以让程序更容易理解与维护

### 权限修饰符

用来控制一个成员能够被访问的范围的

作用范围从小到大：(`private`$\to$`缺省-`$\to$`protected`$\to$`public`)

|  修饰符   | 同一个类中 | 同一个包中其他类 | 不同包下的子类 | 不同包下的无关类 |
| :-------: | :--------: | :--------------: | :------------: | :--------------: |
|  private  |     √      |        ×         |       ×        |        ×         |
|   缺省    |     √      |        √         |       ×        |        ×         |
| protected |     √      |        √         |       √        |        ×         |
|  public   |     √      |        √         |       √        |        √         |



### JavaBean

JavaBean是一种书写类的规范，表达实体和信息的规范，便于封装重用，类内部提供了一些公共的方法以便外界对该对象内部属性进行操作，比如set、get操作。

#### 书写标准

标准avaBean须满足如下要求:

1. 成员变量使用private修饰。
2. 提供每一个成员变量对应的`setXxx() / getXxx()`。 
3. 必须提供一个无参构造器。



#### 快捷生成代码

```
自动生成setXxx() / getXxx()
右键，Generate，Getter and Setter

自动生成有参构造器
右键，Generate，Constructor

自动生成无参构造器
右键，Generate，Constructor，Select None
```





## 继承

子类继承父类之后会有父类的所以方法和属性，父类的私有方法是不能被继承的。子类可以重写父类的所有方法。

子类又称为派生类，父类又称为基类或超类。

* Java不支持多继承（一个类继承于多个父类），但是支持多层继承
* Java中所有的类都是`Object类`的子类

### 格式

* 关键字 `extends` 

```java
修饰符 class 类名 extends 父类民{...}
public class Student extends People{}
```



### 方法重写

子类拥有和父类名称相同，参数相同的方法，就是方法重写覆盖。

* 私有方法不能被重写
* 子类重写父类方法时，访问权限必须大于或者等于父类方法（`缺省` < `protected` < `public`）

#### @override重写注解

* `@Override`是放在重写后的方法上，作为重写是否正确的校验注解。
* 加上该注解后如果重写错误，编译阶段会出现错误提示。
* 这样既安全又规范



### 访问成员变量/方法的顺序

​	就近原则

1. 子类局部范围找
2. 子类成员范围找
3. 父类成员范围找，没找到则报错

直接在父类中寻找成员：`super.父类成员变量/方法;` 类比于`this`在当前类中查找 

例：

```java
class Animal{
    public String name = "父类动物";
}

class Wolf extends Animal{
    public String name = "子类动物";
    public void showName(){
        String name = "局部名称";
        
        System.out.println(name);// 局部名称
        System.out.println(this.name);// 子类动物
        System.out.println(super.name);// 父类动物
    }
}
```



### 构造器执行规则

子类中所有的构造器默认都会先访问父类中无参的构造器，再执行自己。

因为子类初始化之前，一定要调用父类构造器先完成父类数据空间的初始化。

原理：子类构造器的第一行语句默认都是：`super()`，不写也存在。

**注意：** 

​	如果父类中没有无参数构造器，只有有参构造器，则会报错。

​	解决方法是：在子类构造器中书写`super(...)`来手动调用父类的有参构造器



### 抽象类

父类只定义功能的基本要求，具体实现由子类完成，这个类就可以是一个抽象类.。

**抽象类不能实例化对象**，但是类的其它功能依然存在，成员变量、成员方法和构造方法的访问方式和普通类一样

在 Java 语言中使用 `abstract class` 来定义抽象类

示例：

```java
public abstract class Animal {
    ...;
}
```



### 抽象方法

就是抽象类中定义的子类必须完成的功能的基本要求。**子类必须重写或者将其继续定义为抽象方法**！

没有方法体，只有方法签名，必须`abstract`修饰。

示例：

```java
public abstract class Animal {
    public abstract void run();
}
```





## 多态

同类型的对象，执行同一个行为，会表现出不同的行为特征。

比如说：

```
现实中，比如我们按下 F1 键这个动作：
	如果当前在 Flash 界面下弹出的就是 AS 3 的帮助文档；
	如果当前在 Word 下弹出的就是 Word 帮助；
	在 Windows 下弹出的就是 Windows 帮助和支持。
同一个事件发生在不同的对象上会产生不同的结果。
```



### 多态实现形式

1. 声明对象时，将父类引用指向子类对象

```java
父类 对象名称 = new 子类();
接口 对象名称 = new 实现类();

Animal a = new Dog;
```

2. 方法的参数写父类类型，则该参数可以接收该父类的一切子类

```java
修饰符 返回值 方法名(父类类型){
    ...;
}

public void feed(Animal a){
    a.eat();
}

Dog pet1 = new Dog();
Cat pet2 = new Cat();
feed(pet1);//可以传入
feed(pet2);//可以传入
```



### 多态下引用数据类型的类型转换

就是将父类强制转换为子类，可以解决[多态下不能调用子类独有功能的问题](#注意点) 

* 如果转型后的类型和对象真实类型不是同一种类型，那么在转换的时候就会出现`ClassCastException`异常
* Java建议强转转换前使用`instanceof`判断当前对象的真实类型，再进行强制转换

```java
子类 对象变量 = (子类)父类类型变量

Animal a = new Dog();

if(pet1 instanceof Dog){//官方建议先判断类型再强转
	Dog d = (Dog)a;//强制类型转换
	d.work();//可以使用子类独有的功能
}
```



### 注意点

1. **方法调用子类的，变量调用父类的**。多态更看重方法，多态其实很少调用变量

```java
public class People {
    String name = "父类变量";
    void say(){
        System.out.println("父类方法");
    }
}

public class Student extends People{
    String name = "子类变量";
    void say(){
        System.out.println("子类方法");
    }
}

public static void main(String[] args) {
    People aa = new Student();
    System.out.println(aa.name);// 输出 “父类变量”
    aa.say();// 输出 “子类方法”
}
```

2. 多态下不能使用子类独有的变量和方法，但是可以通过强制类型转换解决

```java
public abstract class Animal {//父类
}

public class Dog extends Animal{//子类2
    void work() {//子类独有的方法
        System.out.println("看家！");
    }
}

public class Cat extends  Animal{//子类2
    void work() {//子类独有的方法
        System.out.println("捉老鼠！");
    }
}
//////////////////////////////////////////////////////////
Animal pet1 = new Dog();
Animal pet2 = new Cat();
pet1.work();// 报错！无法使用子类独有的方法
petWork(pet1); // 看家！
petWork(pet2); // 捉老鼠！

public void petWork(Animal a){
    if(a instanceof Dog){
        ((Dog) a).work();// 强制类型转换
    }
    else if(a instanceof Cat){
        ((Cat) a).work();// 强制类型转换
    }
}
```









---



# 垃圾回收机制

Java存在自动垃圾回收器，会定期进行清理。

当堆内存中的类对象或数组对象，没有被任何变量引用（指向）时，就会被判定为内存中的“垃圾”。









---



# 接口

在 Java 中，接口可理解为对象间相互通信的协议。接口在继承中扮演着很重要的角色。接口是更加彻底的抽象。

接口只定义派生要用到的方法，但是方法的具体实现完全取决于派生类。

## 定义

* 接口都是`public`修饰的，写不写都是

```java
public interface 接口名{
    //常量(前缀可省略)
    //抽象方法(前缀可省略)
    
    //默认方法(JDK 8 新增，基本不用)
    //静态方法(JDK 8 新增，基本不用)
    //私有方法(JDK 9 新增，基本不用)
}

public interface Human{
    int MAX_AGE = 200;
    void eat(String food);
}
```





## 实现接口

关键字：`implements` 

* **接口中的抽象方法全部都要重写 或者该类继续定义为抽象类！** 
* 一个类既继承了父类，也实现了接口，**继承要写在接口前面**，否则报错

```java
修饰符 class 类名 implements 接口1,接口2,接口3,...{
    
}

public class Student implements Human{
    @Override
    public void eat(String food){
        System.out.println("正在吃" + food);
    }
}
```





## 接口之间的继承

接口和接口是可以多继承的，即一个接口可以同时继承多个接口。

* 若所继承的接口之间存在 <u>方法名相同，参数列表相同，但是返回值不同</u> 的方法时，会产生冲突不能同时继承
* 若所继承的接口存在 <u>名称相同的常量</u> 时，虽然可以继承，但是无法使用此常量

```java
public interface 接口名 extends 接口1,接口2,接口3,... {
    
}
```





## 接口中新增的方法

### 默认方法

JKD 8 新增的方法，用`default`修饰，该方法可以且必须有主体！

```java
default 返回值 方法名(参数列表){
    主体部分,是必须写的！
}
```



### 静态方法

JKD 8 新增的方法，用`static`修饰，该方法必须有主体！且只能使用`接口名.方法()`调用

```java
static 返回值 方法名(参数列表){
    主体部分,是必须写的！
}

调用：
接口名.方法名(参数列表);
```



### 私有方法

JKD 9 新增的方法，用`private`修饰，该方法必须有主体！且只能使用被当前接口内部的<u>默认方法</u>调用

```java
private 返回值 方法名(参数列表){
    主体部分,是必须写的！
}
```









---



# lamda(箭头函数)



？？？







---



# 常用API

## Object

Object类是所有java类的祖宗类，所有类都直接继承或间接继承于它

### 常用方法

| 方法                 | 返回值  | 说明                                                         |
| -------------------- | ------- | ------------------------------------------------------------ |
| obj.toString()       | String  | 默认返回当前对象在堆内存中的地址信息：`类的全限名@内存地址` 如`package1.Student@3b07d329 ` |
| obj.equals(Object o) | boolean | 默认比较当前对象与另一个对象的地址是否相同                   |

`toString`存在的意义就是被重写，由开发者自定义类的返回内容

`equals`存在的意义就是被重写，由开发者自定义对象的比较规则





## Objects

Objects类还是继承于Object，该类从JDK 1.7后才有，提供了更安全的比较相等的方法

### 常用方法

| 方法                               | 返回值  | 说明                                                         |
| ---------------------------------- | ------- | ------------------------------------------------------------ |
| Objects.equals(Object a, Object b) | boolean | 比较两个对象，先进行非空判断避免空指针异常，再进行equals比较 |
| Objects.isNull(Object obj)         | boolean | 判断对象是否为`null`                                         |





## String

String类定义的变量可以用于存储字符串，同时String类提供了很多操作字符串的功能

Java程序中的所有字符串文字（例如“abc”）都为此类的对象。

### 创建对象

```java
// 1.简写形式(推荐)
String name = "ged";

// 2.脱裤子放屁
String name = new String("ged");

// 3.根据字符数组的内容，创建字符串对象
char[] chars = {'g', 'e', 'd'};
String name = new String(chars);
```

**！注意：**

第一种创建方法：会创建一个对象，在常量池中，**指向常量池中地址** 

第二种创建方法：会创建两个对象，一个在常量池中，一个在堆中，**指向堆中地址 ** 

**所以String类型判断相等不要用 "=="，要用equals等方法** 

```java
String s1 = "abc";
String s2 = new String("abc");
System.out.println(s1 == s2);//false

String s3 = "a" + "b" + "c";//编译时会被优化为String s3 = "abc";
System.out.println(s1 == s3);//true
```



### 对象方法

| 方法                                           | 返回值   | 说明                                       |
| :--------------------------------------------- | -------- | ------------------------------------------ |
| str.equals(String s2)                          | boolean  | 判断两个String类是否内容相等               |
| str.equalsIgnoreCase(String s2)                | boolean  | 忽略大小写比较字符串是否相等               |
| str.length()                                   | int      | 返回字符串长度                             |
| str.charAt(int index)                          | char     | 返回指定下标处的字符                       |
| str.toCharArray()                              | char[]   | 把字符串转换成字符数组                     |
| str.substring(int beginIndex, int endIndex)    | String   | 截取字符串，左闭右开！                     |
| str.replace(String target, String replacement) | String   | 文本替换，返回替换后的文本，不影响原字符串 |
| str.contains(String s)                         | boolean  | 查看字符串中是否存在某字符串               |
| str.split(String regex)                        | String[] | 以指定分隔符将字符串分割成数组             |





## StringBuilder

StringBuilder是一个可变的字符串类，可以提高字符串的操作效率，如拼接、修改等。(其实String对象的拼接操作底层是用StringBuilder来做的)

字符串的拼接，反转建议用StringBuilder

### 创建对象

```java
// 1.创建一个可变的空字符串对象
StringBuilder sb = new StringBuilder();

// 2.创建一个指定字符串内容的可变字符串对象
StringBuilder sb = new StringBuilder(String str);
```



### 常用方法

| 方法                | 返回值        | 说明                               |
| ------------------- | ------------- | ---------------------------------- |
| sb.append(任意类型) | StringBuilder | 将数据拼接在字符串后面，且返回自身 |
| sb.reverse()        | StringBuilder | 字符串翻转，且返回自身             |
| sb.length()         | int           | 返回字符串长度                     |
| sb.toString()       | String        | 将StringBuilder类转换成String类    |





##  ArrayList

ArrayList代表的是集合类，集合是一种容器，与数组类似，不同的是**集合的大小和数据类型是不固定的**。同时ArrayList提供了比数组更好用，更丰富的API (功能)给程序员使用。

### 创建对象

```java
//1. 默认可以存储任意类型
ArrayList list = new ArrayList();

//2. 只能存储特定类型的数据：ArrayList<E>
ArrayList<Integer> ls1 = new ArrayList<Integer>();//只能存储整数类型的数据
ArrayList<Integer> ls1 = new ArrayList<>();//从JDK 1.7开始，泛型后面的类型申明可以不写
```



### 常用方法

| 方法                           | 返回值  | 说明                                                         |
| ------------------------------ | ------- | ------------------------------------------------------------ |
| list.add(element)              | boolean | 向数组中添加元素，类型不定。返回是否添加成功                 |
| list.add(int index, element)   | void    | 向指定下标位置添加元素(超过大小会报错)                       |
| list.get(int index)            | E       | 返回索引处的元素                                             |
| list.size()                    | int     | 返回集合中元素的个数                                         |
| list.remove(int index)         | E       | 删除指定索引的元素，返回被删除的元素                         |
| list.remove(Object o)          | boolean | 删除指定的第一个元素，返回删除是否成功(若要删除整数则这样写：`(Integer) 数字`) |
| list.set(int index, E element) | E       | 修改指定索引处的元素，返回被修改的元素                       |





## Scanner

用来读取键盘输入

### 创建对象

```java
Scanner sc = new Scanner(System.in);
```



### 常用方法

| 方法         | 返回值 | 说明                           |
| ------------ | ------ | ------------------------------ |
| sc.nextInt() | int    | 等待输入一个int类型，并返回    |
| sc.next()    | String | 等待输入一个String类型，并返回 |

例：

```java
int age = sc.nextInt();//等待输入一个int类型，并返回
System.out.println(age);

String name = sc.next();//等待输入一个String类型，并返回
System.out.println(name);
```





## System

System类不能被实例化

### 常用方法

| 方法                                                         | 返回值 | 说明                                            |
| ------------------------------------------------------------ | ------ | ----------------------------------------------- |
| System.currentTimeMillis()                                   | long   | 返回系统当前的时间戳                            |
| System.arraycopy(源数组,起始索引,目的数组,起始索引,拷贝个数) | void   | 数组拷贝                                        |
| System.exit(int status)（慎用，用之前做好跑路的准备）        | void   | 终止当前运行的Java虚拟机，status非0表示异常终止 |

示例：

```java
// 1.利用System.currentTimeMillis()测试程序运行时间
long starTime = System.currentTimeMillis();
for (int i = 0; i < 100000; i++) {
	System.out.println(i);
}
long endTime = System.currentTimeMillis();
System.out.println((endTime - starTime) / 1000.0 + "s");

// 2.数组拷贝
int[] arr1 = {10, 20, 30, 40, 50, 60, 70};
int[] arr2 = new int[6];
System.arraycopy(arr1,3,arr2,2,3);
System.out.println(Arrays.toString(arr2)); // [0, 0, 40, 50, 60, 0]
```





## Random

用来产生随机数

### 创建对象

```java
Random r = new Random(); //创建随机数类

Random r = new Random(System.currentTimeMillis());//使用当前时间作为Random对象的种子

Random r = new Random(233);//自定义种子
```



### 常用方法

| 方法             | 返回值  | 说明                                   |
| ---------------- | ------- | -------------------------------------- |
| r.nextInt(int n) | int     | 生成0到n(左闭右开)之间的随机整数并返回 |
| r.nextDouble()   | double  | 生成0.0到1.0之间的随机小数             |
| r.nextBoolean()  | boolean | 生成true 或 false                      |

例：

* 生成a到b之间的数：`r.nextInt(b - a + 1) + a` 

```java
int number = r.nextInt(10);  //生成0~9之间的整数
System.out.println(number);
```





## Math

Math类包含执行基本数字运算的方法。Math类不能被实例化

### 常用方法

| 方法                         | 返回值 | 说明                                   |
| ---------------------------- | ------ | -------------------------------------- |
| Math.abs(int a)              | int    | 取绝对值                               |
| Math.ceil(double a)          | double | 向上取整                               |
| Math.floor(double a)         | double | 向下取整                               |
| Math.round(float a)          | int    | 四舍五入                               |
| Math.max(int a, int b)       | int    | 取最大值                               |
| Math.pow(double a, double b) | double | 返回a的b次方                           |
| Math.random()                | double | 返回0.0到1.0之间的随机小数（左闭右开） |





## BigDecimal

用于解决浮点型运算精度失真的问题

```java
// 精度失真
System.out.println(0.09 + 0.01); // 0.09999999999999999
System.out.println(1.0 - 0.32);  // 0.6799999999999999
System.out.println(1.015 * 100); // 101.49999999999999
System.out.println(1.301 / 100); // 0.013009999999999999
System.out.println(0.1 + 0.2);   // 0.30000000000000004
```

### 创建对象

不建议用构造器创建对象，因为也有精度问题

```java
BigDecimal a = BigDecimal.valueOf(0.1);
BigDecimal b = BigDecimal.valueOf(0.2);

BigDecimal c = a.add(b);
System.out.println(c);
```



### 常用方法

注意：

* BigDecimal一定只能处理精度运算，比如说计算`10.0 / 3.0`会崩，解决方法是设置保留几位小数

| 方法                                              | 返回值     | 说明                 |
| ------------------------------------------------- | ---------- | -------------------- |
| bd.add(BigDecimal bd2)                            | BigDecimal | 加                   |
| bd.subtract(BigDecimal bd2)                       | BigDecimal | 减                   |
| bd.multiply(BigDecimal bd2)                       | BigDecimal | 乘                   |
| bd.divide(BigDecimal bd2)                         | BigDecimal | 除                   |
| bd.divide(BigDecimal bd2, int 精确几位, 舍入模式) | BigDecimal | 除                   |
| bd.doubleValue()                                  | double     | 返回其double类型的值 |





## Date

日期类型，存储时间

### 创建对象

```java
Date d = new Date(); // 存储的时间就是生成对象瞬间的时间
Date d = new Date(long 时间戳); // 设置时间
```



### 常用方法

| 方法                   | 返回值  | 说明                                               |
| ---------------------- | ------- | -------------------------------------------------- |
| d.toString()           | String  | 返回当前时间，格式：`Sun Jan 16 00:07:21 CST 2022` |
| d.getTime()            | long    | 返回当前时间戳                                     |
| d.setTime(long 时间戳) | void    | 用时间戳设置当前对象的时间                         |
| d1.before(Date d2)     | boolean | d1是否在d2之前                                     |
| d1.after(Date d2)      | boolean | d1是否在d2之后                                     |





## SimpleDateFormat

可以对Date对象或时间戳格式化成其他时间形式。

也可以把字符串的时间形式解析成日期对象。

### 创建对象

```java
SimpleDateFormat sdf = new SimpleDateFormat(); // 默认格式
SimpleDateFormat sdf = new SimpleDateFormat(String pattren); // 指定格式
```



### 常用方法

| 方法                    | 返回值 | 说明                                                         |
| ----------------------- | ------ | ------------------------------------------------------------ |
| sdf.format(Date date)   | String | 将Date对象转换格式并返回字符串                               |
| sdf.format(long 时间戳) | String | 将时间戳转换格式并返回字符串                                 |
| sdf.parse(String s)     | Date   | 将字符串解析成日期类型（类存储的格式必须与被解析时间的格式一样） |



### 格式化符号

| 符号 | 代表        |
| ---- | ----------- |
| yyyy | 年          |
| MM   | 月          |
| dd   | 日          |
| HH   | 时          |
| mm   | 分          |
| ss   | 秒          |
| a    | 上午 / 下午 |
| EEE  | 周几        |

示例：

```java
SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日");
Date d = new Date();
String s = sdf.format(d);
System.out.println(s); // 2022年01月16日
```



https://tool.oschina.net/uploads/apidocs/jdk_7u4

## Calendar

Calendar代表了系统此刻日期对应的日历对象。

### 创建对象

Calendar是一个抽象类，不能直接创建对象。但是可以通过静态方法创建对象。

```java
Calendar cld = Calendar.getInstance();
```



### 常用方法

`field`表示字段，比如`Calendar.YEAR`，字段的名称记不住可以通过打印该对象来找

| 方法                           | 返回值 | 说明                     |
| ------------------------------ | ------ | ------------------------ |
| cld.get(int field)             | int    | 取日期中的某个字段信息   |
| cld.set(int field, int value)  | void   | 修改日期中的某个字段信息 |
| cld.add(int field, int amount) | void   | 在某个字段上增加一段时间 |
| cld.getDate()                  | Date   | 返回Date对象             |
| cld.toString()                 | String | 打印所有信息             |
| cld.getTimeInMillis()          | long   | 获取时间戳               |





## 其他时间类型

JDK8 新增​日期类。在Date, SimpleDateFormat, Calendar这几个经典的时间类上拓展了功能且更加灵活。

新增的API严格区分了时刻、本地日期、本地时间，并且，对日期和时间进行运算更加方便。

* 若需要用到查API文档即可，就不写了

| 类型              | 描述               |
| ----------------- | ------------------ |
| LocalDate         | 只包含时分秒相关   |
| LocalTime         | 只包含年月日相关   |
| LocalDateTime     | 包含了日期及时间   |
| Instant           | 时间戳             |
| DateTimeFormatter | 时间格式化和解析   |
| Duration          | 计算两个时间的间隔 |
| Period            | 计算两个日期的间隔 |



## 包装类















