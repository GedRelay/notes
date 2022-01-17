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
| Shift + F6                  | 重构同名代码                      |



| 快捷语句   | 生成                                          |
| ---------- | --------------------------------------------- |
| main, psvm | public static void main(String[] args) {    } |
| sout       | System.out.println();                         |
| fori       | for (int i = 0; i < ; i++) {      }           |
| arr.fori   | for (int i = 0; i < arr.length; i++) {    }   |
| arr.for    | for (String s : arr) {     }                  |





## IDEA设置

仅个人喜好，记录用

```
文件 -> 设置 -> 插件
搜索 Chinese，找到中文语言包，安装
搜索 CodeGlance 安装
搜索 Alibaba Java CodingGuidelines，安装。工具 -> 阿里编码规约 ->关闭实时检测功能
搜索 wakatime 安装，工具 -> WakaTime Settings 输入Api key

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





## 命名规范

不要用拼音

类名：每个单词的首字母应该大写（帕斯卡命名法），例如`MyFirstJavaClass` 

方法名：第一个单词小写，后面的单词首字母大写（驼峰命名法），例如`showData()` 

变量名：不要以下划线`_`开头，驼峰命名法

包名：所有字符均小写，不要有特殊字符

源文件名：源文件名必须和类名相同

常量：单词全大写，下划线`_`隔开





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

| 数据类型 |          关键字           |            取值范围            | 默认值 | 内存占用（字节数） |
| :------: | :-----------------------: | :----------------------------: | :----: | :----------------: |
|   整数   |           byte            |       $-2^7 \sim 2^7-1$        |   0    |         1          |
|   整数   |           short           |    $-2^{15} \sim 2^{15}-1$     |   0    |         2          |
|   整数   |        int（默认）        |    $-2^{31} \sim 2^{31}-1$     |   0    |         4          |
|   整数   | long（常量后面要加 l/L）  |    $-2^{63} \sim 2^{63}-1$     |   0L   |         8          |
|  浮点数  | float（常量后面要加 f/F） |  1.401298e-45 ~ 3.402823e+38   |  0.0f  |         4          |
|  浮点数  |      double（默认）       | 4.9000000e-324 ~ 1.797693e+308 |  0.0d  |         8          |
|   字符   |           char            |           0 ~ 65535            | \u0000 |         2          |
|   布尔   |          boolean          |          true, false           | false  |         1          |



### 引用数据类型

* 引用类型变量存储的是堆区域的地址

```java
String
数组
```



### 自动类型转换

整型、实型（常量）、字符型数据可以混合运算。运算中，不同类型的数据先转化为同一类型，然后进行运算。

但是不能对boolean类型进行类型转换。

转换从低级到高级。

```java
低  ------------------------------------>  高
byte,short,char—> int —> long—> float —> double 
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
<<=
>>=
&=
|=
^=
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
&& //与
|| //或
!  //非
```



### 三元运算符

```java
条件表达式 ? 值1 : 值2;
//为真返回值1，为假返回值2
```



### 位运算符

```java
& //按位与
| //按位或
^ //按位异或
~ //按位取反
<< //左移
>> //右移
```



### instanceof运算符

该运算符用于操作对象实例，检查该对象是否是一个特定类型（类类型或接口类型）

```java
String name = "Ged";
name instanceof String //true
name instanceof int //false
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



### 增强for

* 该语句是java5的新特征
* 该循环只读，无法修改数组内元素
* 实现iterable接口的类才能使用增强for

```java
for(数据类型 临时变量名 : 数组/集合名){
    临时变量将会逐次获得数组/集合内的值;
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

为数组内容进行初始化

```java
数据类型[] 数组名 = new 数据类型[]{初始化列表};
数据类型[] 数组名 = {初始化列表}; // 简化形式

int arr[] = new int[] {1, 2, 3};
int arr[] = {1, 2, 3};

int a[][] = new int[][]{{1,2}, {3,4}}; // 二维数组
```



#### 动态初始化数组

只指定数组长度，内容为相应数据类型的默认值

```java
数据类型[] 数组名 = new 数据类型[长度];

int[] arr = new int[3];
String[][] strs = new String[3][4]; // 二维数组
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

相关链接：[方法重写](#方法重写) 



### 可变参数

JDK 1.5开始，Java支持传递同类型的可变参数给一个方法。

* 一个形参列表中只能有一个可变参数
* 可变参数只能放在形参列表的最后面

```java
类型... 参数名

示例：
public static void show(int... numbers) {// 可变参数
    //可变参数在方法内部其实就是一个数组
	for (int i = 0; i < numbers.length; i++) {
		System.out.println(numbers[i]);
	}
}
show(5, 6, 3, 1, 2, 4);
```





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

当然还可以用[Lambda表达式](#Lambda(箭头函数))进一步简化

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
public class Tiger extends Animal{//需要提前定义一个子类
    @Override
    void eat() {
        System.out.println("吃肉");
    }
}

Animal tiger = new Tiger();
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

作用范围从小到大：(`private`$\to$`缺省`$\to$`protected`$\to$`public`)

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

子类继承父类之后会有父类的所以方法和属性，父类的私有方法是不能被继承的。子类可以**重写**父类的所有方法。

子类又称为派生类，父类又称为基类或超类。

* Java不支持多继承（一个类继承于多个父类），但是支持多层继承
* Java中所有的类都是`Object类`的子类
* 父类中声明为`public`的方法在子类中也必须为`public` 
* 父类中声明为`protected`的方法在子类中要么声明为`protected`，要么声明为`public`，不能声明为`private ` 

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

* 接口里的变量都隐式声明为 `public static final`，而接口里的方法默认情况下访问权限为 `public`，写不写都是

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



# Lambda(箭头函数)

Lambda表达式是JDK8后支持的一种新语法形式。用来简化函数式接口[匿名内部类](#匿名内部类)的代码写法

但是：**Lambda表达式只能简化函数式接口的匿名内部类的写法形式** 

## 使用方法

```java
(匿名内部类被重写方法的形参列表) -> {
    ...;
}

例：
@FunctionalInterface
interface Animal{ // 函数式接口
	void eat();
}

Animal tiger = () ->{ // lambda函数
	System.out.println("吃肉");
};
tiger.eat();
```





## 省略写法

满足规则，则Lambda表达式还可以继续简化！

* 参数类型可以省略

* 如果只有一个参数，同时`()`也可以省略
* 如果Lambda表达式方法体只有一行，大括号`{}`可以省略，同时也要省略分号`;` 
* 如果Lambda表达式只有一行且是`return`语句，可以省略`return`同时省略分号`;` 





## 函数式接口

该接口中有且仅有一个抽象方法

可以在上方添加`@FunctionalInterface`注解





## 简化常见函数式接口

1. [比较器Comparator](#比较器接口) 

```java
new Comparator<Integer>() {
	@Override
	public int compare(Integer o1, Integer o2) {
		...;
	}
}
//---------------------------------------------
(o1, o2) -> {
    ...;
}
```

2. 按钮监听器ActionListener

```java
new ActionListener(){
    @Override
    public void actionperformed(ActionEvent e){
        ...;
    }
}
//---------------------------------------------
e -> {
    ...;
}
```











---



# 泛型

JDK5 中引入的特性，可以在编译阶段约束操作的数据类型，并进行检查。

* **泛型只支持引用数据类型** 
* 泛型在类后面定义叫泛型类
* 泛型在方法声明上定义叫泛型方法
* 泛型在接口后面定义叫泛型接口

## 泛型类

定义类时同时定义了泛型的类就是泛型类

```java
修饰符 class 类名<泛型变量>{...} // 泛型变量一般写E、T、K、V

public class MyArrayList<E> {
	public void add(E e){
		...
	}
}
```





## 泛型方法

定义方法时同时定义了泛型的方法就是泛型方法

* 方法中可以使用泛型接收一切实际类型的参数，方法更具备通用性。

```java
修饰符 <泛型变量> 返回值类型 方法名(形参列表){...}

public <T> void show(T t) {
	System.out.println(t.toString());
}
```





## 泛型接口

使用了泛型定义的接口就是泛型接口

* 泛型接口可以让实现类选择当前功能需要操作的数据类型

```java
修饰符 interface 接口名<泛型变量>{...}

public interface Data<E>{
    void add(E e);
    E getById(int id);
}
```





## 泛型通配符和上下限

通配符：`?` ，可以在使用泛型的时候代表一切类型

泛型上限：`? extends Car`，表示`?`必须是`Car`或者其子类

泛型下限：`? super Car`，表示`?`必须是`Car`或者其父类

示例：

```java
public static void go(ArrayList<? extends Car> cars){
    // 此时只有Car和其子类的ArrayList才能调用次函数
    ...;
}

示例：
interface Car{}
class SmallCar implements Car{}
class BigCar implements  Car{}
class Dog{}

public static void go(ArrayList<? extends Car> cars){
    ...;
}
ArrayList<SmallCar> cars1 = new ArrayList<>();
ArrayList<BigCar> cars2 = new ArrayList<>();
ArrayList<Dog> dogs = new ArrayList<>();
go(cars1);//成功
go(cars2);//成功
go(dogs);//报错，ArrayList<Dog>不能传入此参数
```









---



# Map集合体系

和Collection集合体系是并列关系，数据以键值对的形式存储

<img src="https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20220117234518492.png" alt="image-20220117234518492" style="zoom:67%;" />









---



# Collection集合体系

* 集合支持泛型

* 集合只能支持引用数据类型，**不支持基本数据类型(可以用[包装类](#包装类))** 

![image-20220116222028023](https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20220116222028023.png)



## Collection

### 常用方法

| 方法                     | 返回值  | 说明                         |
| ------------------------ | ------- | ---------------------------- |
| c.add(\<T> val)          | boolean | 添加元素，返回是否头添加成功 |
| c.clear()                | void    | 清空集合                     |
| c.isEmpty()              | boolean | 判断集合是否为空             |
| c.size()                 | int     | 返回集合元素数量             |
| c.contains(\<T> val)     | boolean | 判断集合中是否有指定元素     |
| c.remove(\<T> val)       | boolean | 删除元素，返回是否删除成功   |
| c.toArray()              | Object  | 转换成数组                   |
| c1.addAll(Collection c2) | boolean | 将c2集合中的元素添加至c1     |



### 遍历

1. 使用[迭代器](#Iterator)进行遍历

```java
Collection<String> c = new ArrayList<>();
// 获取迭代器对象
Iterator<String> it = c.iterator();
while(it.hasNext()){
    System.out.println(it.next());
}
```

2. 使用[增强for](#增强for)循环遍历

```java
Collection<String> c = new ArrayList<>();
for(String ele : c){
    System.out.println(ele);
}
```

3. 使用[Lambda表达式](#Lambda(箭头函数))进行遍历

```java
Collection<String> c = new ArrayList<>();
c.foreach(ele -> {
    System.out.println(ele);
});
//了解
c.foreach(System.out::println);
```





## Collections

collections类是一个操作集合的工具类，并不属于collection集合体系

### 常用方法

| 方法                                                  | 返回值  | 说明                 |
| ----------------------------------------------------- | ------- | -------------------- |
| Collections.sort(List ls);                            | void    | 按照默认规则排序     |
| Collections.sort(List ls, 比较器对象);                | void    | 按照比较器的规则排序 |
| Collections.shuffle(List ls)                          | void    | 将ls中元素随机打乱   |
| Collections.addAll(Collection<? super T> c, T... val) | boolean | 给集合批量添加元素   |





## List

特点：有序，可重复，有索引

### 常用方法

| 方法                                   | 返回值   | 说明                               |
| -------------------------------------- | -------- | ---------------------------------- |
| ls.add(int index, \<T> element)        | void     | 在索引处插入元素                   |
| ls.remove(int index)                   | \<T>     | 删除索引处的元素，返回被删除的元素 |
| ls.get(int index)                      | \<T>     | 获取索引处的元素值                 |
| ls.set(int index, \<T> val)            | \<T>     | 修改索引处的值，返回被修改的元素   |
| ls.subList(int fromindex, int toIndex) | List\<T> | 截取子链（左闭右开）               |



### 遍历

在Collection的遍历方式上添加了使用索引的遍历方式

```java
List<String> ls = new ArrayList<>();
for (int i = 0; i < ls.size(); i++) {
	System.out.println(ls.get(i));
}
```





##  ArrayList

ArrayList代表的是集合类，集合是一种容器，与数组类似，不同的是**集合的大小和数据类型是不固定的**。同时ArrayList提供了比数组更好用，更丰富的API给程序员使用。

* ArrayList底层是基于数组实现的
* 第一次创建集合并添加第一个元素的时候，在底层创建一个默认长度为10的数组，若空间不够则会自动扩容为原来的1.5倍并迁移数据

### 创建对象

```java
//1. 默认可以存储任意类型
List list = new ArrayList();

//2. 只能存储特定类型的数据：ArrayList<E>
List<Integer> ls1 = new ArrayList<Integer>();//只能存储整数类型的数据
List<Integer> ls1 = new ArrayList<>();//从JDK 1.7开始，泛型后面的类型申明可以不写
```



### 常用方法

这些方法都是继承下来的

| 方法                         | 返回值  | 说明                                                         |
| ---------------------------- | ------- | ------------------------------------------------------------ |
| ls.add(element)              | boolean | 向数组中添加元素，类型不定。返回是否添加成功                 |
| ls.add(int index, element)   | void    | 向指定下标位置添加元素(超过大小会报错)                       |
| ls.get(int index)            | E       | 返回索引处的元素                                             |
| ls.size()                    | int     | 返回集合中元素的个数                                         |
| ls.remove(int index)         | E       | 删除指定索引的元素，返回被删除的元素                         |
| ls.remove(Object o)          | boolean | 删除指定的第一个元素，返回删除是否成功(若要删除整数则这样写：`(Integer) 数字`) |
| ls.set(int index, E element) | E       | 修改指定索引处的元素，返回被修改的元素                       |





## LinkedList

* 底层数据结构是双链表

### 常用方法

| 方法                                                | 返回值 | 说明                                   |
| --------------------------------------------------- | ------ | -------------------------------------- |
| ls.addFirst(\<T> val)，offerFirst()，push(\<T> val) | void   | 在列表开头插入数据                     |
| ls.addLast(\<T> val)，offerLast(\<T> val)           | void   | 在列表结尾插入数据                     |
| ls.getFirst()                                       | \<T>   | 返回列表的第一个元素                   |
| ls.getLast()                                        | \<T>   | 返回列表的最后一个元素                 |
| ls.removeFirst()，pop()                             | \<T>   | 删除列表第一个元素，并返回删除的元素   |
| ls.removeLast()                                     | \<T>   | 删除列表最后一个元素，并返回删除的元素 |





## Set

特点：无序，不重复，无索引

Set集合的功能基本上与[Collection](#Collection)的API一致





## HashSet

特点：无序，不重复，无索引

* 底层原理是哈希表

功能基本上与[Collection](#Collection)的API一致，元素无序且添加元素会去重而已

### 底层

哈希表数组的默认长度为16，默认加载因子为0.75

采用拉链法，当链表长度超过8时，自动将此链转换为红黑树

当数组存满`长度*加载因子`即16*0.75=12个元素时，就会将长度扩容为原来的两倍

去重判断：先调用hashCode()方法比较哈希值，再调用equals()的比较结果

所以：**类要实现根据内容去重的话，要重写hashCode()和equals()方法** 





## LinkedHashSet

特点：有序，不重复，无索引

* 底层原理是哈希表，只是每个元素又额外的多了一个双链表的机制记录存储的顺序

功能基本上与[Collection](#Collection)的API一致，添加元素会去重而已

<img src="https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20220118002819057.png" alt="image-20220118002819057" style="zoom:50%;" />





## TreeSet

特点：排序(默认升序)，不重复，无索引

功能基本上与[Collection](#Collection)的API一致，添加元素会去重而已

* 底层基于红黑树实现排序

对于数值类型：`Integer` , `Double`，官方默认按照大小进行升序排序。

对于字符串类型：默认按照首字符的编号升序排序。

对于自定义类型：需要制定排序规则

### 自定义排序规则

如果两种方法都用了，按照集合的比较器来排序

* 如果认为第一个数据大于第二个数据返回正整数
* 如果认为第一个数据小于第二个数据返回负整数
* 如果认为第一个数据等于第二个数据返回0

1. 实现`Comparable`接口，重写`compareTo`方法来定制比较规则

```java
class Apple implements Comparable<Apple>{
	double price;
	@Override
	public int compareTo(Apple o) {
		return Double.compare(this.price, o.price);
	}
}
Set<Apple> apples = new TreeSet<>();
```

2. 使用TreeSet的有参构造器，设置`Comparator`接口对应的比较器对象，来定制比较规则

```java
Set<Apple> apples = new TreeSet<>((o1,o2) ->{
	return Double.compare(o1.price, o2.price)
});
//或者
Set<Apple> apples = new TreeSet<>((o1, o2) -> Double.compare(o1.price, o2.price));
```









---



# 其他常用API

## Object

Object类是所有java类的祖宗类，所有类都直接继承或间接继承于它

### 常用方法

| 方法                 | 返回值  | 说明                                                         |
| -------------------- | ------- | ------------------------------------------------------------ |
| obj.toString()       | String  | 默认返回当前对象在堆内存中的地址信息：`类的全限名@内存地址` 如`package1.Student@3b07d329 ` |
| obj.equals(Object o) | boolean | 默认比较当前对象与另一个对象的地址是否相同                   |
| obj.hashCode()       | int     | 获取对象的 hash 值                                           |
| obj.clone()          | Object  | 创建并返回一个对象的拷贝                                     |

`toString`存在的意义就是被重写，由开发者自定义类的返回内容

`equals`存在的意义就是被重写，由开发者自定义对象的比较规则





## Objects

Objects类还是继承于Object，该类从JDK 1.7后才有，提供了更安全的比较相等的方法

### 常用方法

| 方法                               | 返回值  | 说明                                                         |
| ---------------------------------- | ------- | ------------------------------------------------------------ |
| Objects.equals(Object a, Object b) | boolean | 比较两个对象，先进行非空判断避免空指针异常，再进行equals比较 |
| Objects.isNull(Object obj)         | boolean | 判断对象是否为`null`                                         |
| Objects.hash(Object... val)        | int     | 生成若干参数合起来的哈希值                                   |





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
| str.split(String regex)                        | String[] | 以指定分隔符(正则表达式)将字符串分割成数组 |
| str.matches(String regex)                      | boolean  | 判断是否匹配正则表达式                     |
| str.replaceAll(String regex, String newStr)    | String   | 将正则表达式匹配的内容替换为新字符串       |



### 正则表达式常用操作符

| 操作符 | 说明                                | 示例                                    |
| ------ | ----------------------------------- | --------------------------------------- |
| .      | 表示任何单个字符                    |                                         |
| \d     | 数字，等价于[0-9]                   |                                         |
| \w     | 英文数字下划线，等价于[A-Za-z0-9_]  |                                         |
| \s     | 空白字符，等价于[\\t\\n\\x0B\\f\\r] |                                         |
| [ ]    | 字符集，对单个字符给出取值范围      | [abc]表示a,b,c, [a-z]表示a到z的单个字符 |
| [^ ]   | 非字符集，对单个字符给出排除范围    | [^abc]表示非a或b或c的单个字符           |
| *      | 前一个字符0次或无限次扩展           | abc*表示ab,abc,abcc,abccc等             |
| +      | 前一个字符1次或无限次扩展           | abc+表示abc,abcc,abccc等                |
| ?      | 前一个字符0次或1次扩展              | abc?表示ab,abc                          |
| {m}    | 前一个字符正好m次                   | ab{2}c表示abbc                          |
| {m,}   | 前一个字符至少m次                   |                                         |
| {m,n}  | 前一个字符m至n次(含n)               | ab{1,2}c表示abc,abbc                    |
| \|     | 左右表达式任意一个                  | abc\|def表示abc,def                     |
| ( )    | 分组标记，内部只能使用\|操作符      | (abc)表示abc,(abc\|def)表示abc,def      |
| ^      | 匹配字符串开头                      | ^abc表示abc且在一个字符串开头           |
| $      | 匹配字符串结尾                      | abc$表示abc且在一个字符串的结尾         |

举例：

| 正则表达式                                                   | 说明                         |
| ------------------------------------------------------------ | ---------------------------- |
| ^[A-Za-z]+$                                                  | 由26个字母组成的字符串       |
| ^[A-Za-z0-9]+$                                               | 由26个字母和数字组成的字符串 |
| ^-?\d+$                                                      | 整数形式的字符串             |
| ^[0-9]\*\[1-9][0-9]*$                                        | 正整数形式的字符串           |
| [1-9]\d{5}                                                   | 中国境内邮政编码，6位        |
| [\u4e00-\u9fa5]                                              | 匹配中文字符                 |
| \d{3}-\d{8}\|\d{4}-\d{7}                                     | 国内电话号码，010-68913536   |
| (([1-9]?\d\|1\d{2}\|2[0-4]\d\|25[0-5]).){3}([1-9]?\d\|1\d{2}\|2[0-4]\d\|25[0-5]) | IP地址                       |
| http?://[a-zA-Z0-9\.\?/%-_]*                                 | 网址链接                     |





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





## Arrays

数组操作工具类，专门用于操作数组元素。不能创建对象

### 常用方法

| 方法                                    | 返回值 | 说明                                                         |
| --------------------------------------- | ------ | ------------------------------------------------------------ |
| Arrays.toString(类型[] a)               | String | 返回数组内容                                                 |
| Arrays.sort(类型[] a)                   | void   | 对数组进行默认升序排序                                       |
| Arrays.sort(类型[] a, Comparator\<T> c) | \<T>   | 使用比较器对象自定义排序                                     |
| Arrays.binarySearch(int[] a, int key)   | int    | 二分搜索数据(必须排好序)，存在返回索引，不存在返回`-(应该插入的位置+1)` |
| Arrays.fill(int[] a, int val)           | void   | 将指定的值分配给指定 int 型数组指定范围中的每个元素。同样的方法适用于所有其他基本数据类型（Byte，short，Int等） |



### 比较器接口

用来自定义对象的比较方式的接口，需要**重写compare(\<T> o1, \<T> o2)函数** 

注意：比较器对象只能支持引用类型！

compare(\<T> o1, \<T> o2)函数重写规则：

* 如果认为左边数据大于右边数据返回正整数
* 如果认为左边数据小于右边数据返回负整数
* 如果认为左边数据等于右边数据返回0

示例：

```java
Integer[] arr1 = {5,1,2,4,3};
Arrays.sort(arr1);
System.out.println(Arrays.toString(arr1)); // [1, 2, 3, 4, 5] 默认升序排序

Integer[] arr2 = {5,1,2,4,3};
Arrays.sort(arr2, new Comparator<Integer>() {
	@Override
	public int compare(Integer o1, Integer o2) {
		return o2 - o1; // 降序
	}
});
System.out.println(Arrays.toString(arr2)); // [5, 4, 3, 2, 1] 按照比较器对象定义进行排序
```





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

其实就是8种基本数据类型对应的引用类型。原基础类型只能看作是一种符号，而包装类才是对象

集合和泛型只能支持包装类型，不支持基本数据类型。

![image-20220117194056317](https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20220117194056317.png)



| 基本数据类型 | 引用数据类型 |
| ------------ | ------------ |
| byte         | Byte         |
| short        | Short        |
| int          | Integer      |
| long         | Long         |
| char         | Character    |
| float        | Float        |
| double       | Double       |
| boolean      | Boolean      |

### 特点

* 包装类的变量的默认值可以是`null`，容错率更高。
* 基本数据类型和包装类可以相互赋值转换
* 可以通过`.toString()`方法可以转换成字符串类型
* 可以通过`.valueOf(String str)`将字符串转换成对应的类型



###  常用方法

| 方法                     | 返回值 | 说明                     |
| ------------------------ | ------ | ------------------------ |
| type.toString()          | String | 转换成字符串类型         |
| type.valueOf(String str) | type   | 将字符串转换成对应的类型 |





## Iterator

迭代器接口，可以实现集合的遍历

* 实现iterable接口的类才能使用迭代器

### 常用方法

| 方法         | 返回值  | 说明                               |
| ------------ | ------- | ---------------------------------- |
| it.hasNext() | boolean | 判断是否还有下一个元素             |
| it.next()    | E       | 获取下一个元素，同时移向下一个位置 |
| it.remove()  | void    | 删除当前所在元素，并且不会后移     |







