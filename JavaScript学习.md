<p style="font-size: 120px;" align="center">JavaScript</p>

[toc]

# 相关链接

[js插件库](https://www.javascript.fun/) 

[菜鸟教程](https://www.runoob.com/) 

[W3school](https://www.w3school.com.cn/index.html) 









---



# 引入JavaScript

## 行内引入

```html
<h2 onclick="alert('hello!')">hello</h2>
```





## 内部引入

```html
<script type="text/javascript">
	alert('hello!');
</script>
```





## 外部引入

```html
<script src="js路径" type="text/javascript" charset="utf-8"></script>
```









---



# ECMAScript

 JavaScript的基础语法部分

## 输入输出语句

| 方法               | 说明                                     |
| ------------------ | ---------------------------------------- |
| console.log(msg)   | 控制台打印消息，想要输出多个值用逗号隔开 |
| alert(msg)         | 弹出警示框                               |
| prompt(提示信息)   | 弹出输入框，返回输入内容，为字符型       |
| console.error(msg) | 控制台输出一条错误信息                   |
| console.warn(msg)  | 控制台输出一条警告                       |





## 注释

```javascript
//单行注释
/*多行注释*/
```





## 变量

### 变量声明

```js
var 变量名;//最好不要用name做变量名
或
var 变量名 = 值;
```



### 变量类型

使用 `typeof 变量名;`  可以返回变量类型

使用  `变量 instanceof 类名` 判断变量是否为该类型

| 简单数据类型 | 说明       | 默认值    |
| ------------ | ---------- | --------- |
| Number       | 数字型     | 0         |
| Boolean      | 布尔型     | false     |
| String       | 字符串型   | ""        |
| Undefined    | 未定义类型 | undefined |
| Null         | 空值       | null      |
| Array        | 数组       | []        |

* 数值类型：
  二进制：0b开头，八进制：0开头，十六进制：0x开头
  js中数值的最大和最小值：`Number.MAX_VALUE  ; Number.MIN_VALUE`
  无穷大：`Infinity`
  非数值：`NaN`，可以用`isNaN()`函数判断参数是否是非数字
* Undefined类型：
  未初始化的变量类型是`undefined` 



### 数组Array

数组内元素类型可以任意，同python的列表

**创建数组**：

* 利用 new 创建数组： `ver 数组名 = new Array() ;` 

* 利用数组字面量创建数组： `var 数组名 = [初始化列表] ;` 



**数组操作**

| 属性/方法                           | 说明                                                         |
| ----------------------------------- | ------------------------------------------------------------ |
| arr[index]                          | 访问数组元素，若访问越界，只能访问到 `undefined`             |
| arr.length                          | 返回数组元素个数,可以直接修改，改大后会多出undefined元素，改小后会删除多余元素 |
| arr.push()                          | 在数组最后增加元素，返回新数组长度                           |
| arr.pop()                           | 删除数组最后一个元素，返回删除的元素                         |
| arr.unshift()                       | 在数组开头增加元素，返回新数组长度                           |
| arr.shift()                         | 删除数组第一个元素，返回删除的元素                           |
| arr.reverse()                       | 翻转数组                                                     |
| arr.sort()                          | 按照**字符串升序排序**                                       |
| arr.sort(function(a,b){return a-b}) | 按照数字升序排序                                             |
| arr.sort(function(a,b){return b-a}) | 按照数字降序排序                                             |
| arr.indexOf()                       | 查找给定元素的第一个索引，不存在返回-1                       |
| arr.lastIndexOf()                   | 查找给定元素的最后一个索引，不存在返回-1                     |
| arr.toString()                      | 返回数组转换为的字符串，以逗号隔开                           |
| arr.join(分隔符)                    | 返回数组以分隔符分隔成的字符串，默认逗号                     |



### 字符串String

| 属性/方法                                  | 说明                                  |
| ------------------------------------------ | ------------------------------------- |
| str.length                                 | 返回字符串长度                        |
| str + str                                  | 字符串拼接，注意很耗资源              |
| str.indexOf('字符',[起始位置])             | 从起始位置开始查找字符                |
| str.lastIndexOf('字符')                    | 从后往前找                            |
| str.charCodeAt(index)                      | 返回索引处字符的ASCII码               |
| str.substr(start,length)                   | 从start开始截取length长度字符，并返回 |
| str.slice(start,end)                       | 从start到end截取字符，end取不到       |
| str.replace('被替换的字符','替换为的字符') | 替换字符,只替换第一个                 |
| str.split(分隔符)                          | 以分隔符隔开，转换为数组              |



### 类型转换

| 方式                    | 说明             | 举例                 |
| ----------------------- | ---------------- | -------------------- |
| toString()方法          | 转成字符串       | str = num.toString() |
| String()函数强制转换    | 转成字符串       | String(num)          |
| +号 隐式转换为string    | 转成字符串       | 'a' + 12             |
| parseInt(string)函数    | string转为整数型 | parseInt('78')       |
| parseFloat(string)函数  | string转为浮点型 | parseFloat('78.21')  |
| Number()函数强制转换    | string转为数值型 | Number('12')         |
| - , * , / 隐式转换为num | 转为数值型       | '12' - '1'           |
| Boolean()函数           | 转为bool型       | Boolean('true')      |

Boolean()函数会将代表空，否定的值转换为false，如：0，NaN，null，undefined。其余全部转为true





## 运算符

### 算术，关系，赋值运算：

都是和其他语言共通的，这里只写几个特别注意的：

* js的除法是真实除法，如10/3结果是3.333...，整除要使用Math类
* js也有前后缀自增`++`和自减`--`运算
* js也有 `+=,-=,*=,/=,%=` 

* `==`判等号，会转型，如：`18=="18"` 结果为`true` 
* `===`和`!==` ：**全等**，要求值和数据类型都一致



### 逻辑运算：

* 与 `&&` 或`||` 非`!` 



短路：当有多个表达式时，左边的表达式可以确定结果时，就不再继续运算右边的表达式的值；

* 逻辑与的短路：`表达式1 && 表达式2` 
  * 如果表达式1为真，返回表达式2
  * 如果表达式1为假，返回表达式1

* 逻辑或的短路：`表达式1 || 表达式2` 
  * 如果表达式1为真，返回表达式1
  * 如果表达式1为假，返回表达式2



### 条件运算符：

类似C的三目运算符

语法：`variablename=(condition)?value1:value2;`

举例：`result=(age<18)?"年龄太小":"年龄合适";`





## 分支结构

if else 与 c++ 完全一样

三目运算符 ? : 与 c++ 完全一样

switch 与 c++ 完全一样,  **注意case 要求全等** 





## 循环结构

for 循环与 c++ 完全一样，注意计数器变量用 var 声明

while 循环与 c++ 完全一样

do while 循环与 c++ 完全一样

continue 和 break 与 c++ 完全一样





## 函数

* 函数嵌套调用时不要求按顺序定义
* js的函数内部也可以声明函数

### 函数声明

```javascript
function 函数名([形参列表])//形参列表不需要var声明，直接写参数名字
{
    函数体
    [return 返回值;]//return只能返回一个值,不过可以用数组返回多个值
}
若函数没有返回值，则返回undefined
```



### 函数调用

```javascript
函数名([参数列表]);
```

若实参个数多于形参，只按顺序取对应数量的实参，其余值不做传递

```javascript
function getsum(num1,num2){...}
getsum(1,2,3);//只传递1和2
```

若实参个数少于形参，则多余的形参定义为undefined

```javascript
function getsum(num1,num2){...}
getsum(1);//num2为undefined
```



### arguments

arguments是一种伪数组，按照索引(从0开始)存储所有实参，每个函数都内置好了

```javascript
function fn(){
    console.log(arguments);//里面存储了所有传递过来的实参
    console.log(arguments.length)//实参个数
    console.log(arguments[1])//第二个实参
}

fn(1,2,3);
```



### 匿名函数（重要）

没有名字的函数就是匿名函数，它可以让一个变量来接收，也就是用 “函数表达式” 方式创建和接收。

```javascript
定义：
var 变量名 = function([形参列表]){
    函数体
}
调用：
变量名([实参列表])

如：
var fun = function(msg){console.log(msg);}
fun('hello');
//注意：fun是变量名，不是函数名
```



### 立即执行函数

不需要调用，会立即执行。本质是创建匿名函数并立即调用

```javascript
(function(){})();
或者
(function(){}());
```





## 预解析

js解释器运行js分为两步：预解析，代码执行

预解析：在代码执行前，js解释器把所有的 var 和 function 提升到当前作用域的最前面

预解析分为 变量提示 和 函数提升

**变量提升** 就是把所有变量声明提升到当前作用域最前面 **不提升赋值操作** 

**函数提升** 就是把所有函数声明提升到当前作用域最前面 不调用函数





## 面向对象

### 自定义对象

#### 创建对象

方法1：字面量创建

```javascript
var person = {
    uname: '张三丰',
    age: 18,
    sex: '男',
    sayHi: function(){
        console.log('Hi~');
    }
}
```

方法2：创建对象示例

```javascript
var person = new Object();
person.uname = '张三丰';
person.age = 18;
person.sex = '男';
person.sayHi = function(){
    console.log('Hi~');
}
```

方法3：构造函数

```javascript
function 构造函数名(参数列表){
    this.属性 = 值;
    this.方法 = function(参数){...}
}
var 对象名 = new 构造函数名(参数列表);

例：
function Human(uname,age,sex){
    this.uname = uname;
    this.age = age;
    this.sex = sex;
    this.sayHi = function(){
        console.log('Hi~');
    }
}
var person = new Human('张三丰',18,'男');
```



#### 原型prototype

原型的好处是：若干个对象的相同方法只需要开辟一个空间存储，节省空间

```javascript
function Person(name, age) {
    this.name = name;
    this.age = age;
}
// 在Person类的原型对象中添加方法
Person.prototype.sayName = function() {
    console.log(this.name);
};

var person1 = new Person("孙悟空", 18);
```



#### 调用对象属性和方法

调用属性：

```javascript
方法1: 对象名.属性名
person.uname
方法2: 对象名['属性名']
person['uname']
```

调用方法：

```javascript
对象名.方法名()
person.sayHi();
```



#### 检查对象的属性或方法

使用 `in` 运算来检查对象有无某属性或方法

```javascript
属性/方法 in 对象
console.log("age" in Person);
```

使用`hasOwnProperty()` 检查是否包含**(非继承)**属性

```javascript
对象.hasOwnProperty(属性/方法)
Person.hasOwnProperty('age');
```



#### 遍历对象的属性和方法

```javascript
for(变量 in 对象){
    //访问属性：对象[变量]
}
例:
for(k in person){
    console.log(person[k]);
}
```



#### 删除属性

```javascript
delete 对象.属性名
```



#### 回收对象

在js中拥有自动的垃圾回收机制，会自动将这些垃圾对象从内存中销毁，我们只要将不再使用的对象设置null即可。

```javascript
var person1 = new Person("孙悟空", 18);
person1 = null;
```



### 内置对象

查文档：[MDN](https://developer.mozilla.org/zh-CN) 

#### Math对象

该对象不需要new

| 属性/方法          | 说明                   |
| ------------------ | ---------------------- |
| Math.max(参数列表) | 求最大值，参数可以多个 |
| Math.min(参数列表) | 求最小值，参数可以多个 |
| Math.PI()          | 返回常数$\pi$          |
| Math.abs(x)        | 取绝对值               |
| Math.floor(x)      | 向下取整               |
| Math.ceil(x)       | 向上取整               |
| Math.round(x)      | 四舍五入               |
| Math.random()      | 返回[0,1)的随机浮点数  |
| Math.pow(x,y)      | 返回x的y次方           |
| Math.sqrt(x)       | 返回x的平方根          |

```javascript
//生成从a到b的随机整数
Math.floor(Math.random() * (b - a + 1)) + a;
```



#### Data对象

文档：[Date](https://developer.mozilla.org/zh-cn/docs/Web/JavaScript/Reference/Global_Objects/Date) 

实例化：`var date  = new Date();` 

| 属性/方法              | 说明                      |
| ---------------------- | ------------------------- |
| date.getFullYear()     | 返回年                    |
| date.getMonth()        | 返回，取值范围为 0~11     |
| date.getDate()         | 返回几号                  |
| date.getDay()          | 返回星期几，取值范围为0~6 |
| date.valueOf()         | 返回时间戳                |
| date.getTime()         | 返回时间戳                |
| date.getHours()        | 返回当前小时数            |
| date.getMinutes()      | 返回当前分钟数            |
| date.getSeconds()      | 返回当前秒数              |
| date.getMilliseconds() | 返回当前毫秒数            |



#### RegExp对象

正则表达式对象，正则表达式用于定义一些字符串的规则，计算机可以根据正则表达式，来检查一个字符串是否符合规则，获取将字符串中符合规则的内容提取出来。

实例化：`var 变量名 = new RegExp("正则表达式","匹配模式");` 

使用字面量创建：`var 变量名 = /正则表达式/匹配模式;` 

匹配模式：

* i：忽略大小写
* g：全局匹配模式
* ig：忽略大小写且全局匹配
* m：执行多行匹配

| 属性 /方法                      | 说明                                   |
| ------------------------------- | -------------------------------------- |
| regexp.test(str)                | 查看字符串中是否有匹配的子串           |
| str.search(正则表达式)          | 返回第一个匹配内容的下标，没有则返回-1 |
| str.match(正则表达式)           | 返回匹配到的内容                       |
| str.replace(正则表达式, 新内容) | 将匹配到的内容替换为新内容             |

示例：

```javascript
reg = /ab/i; //或var reg = new RegExp("ab", "i")
var str = "Abc";
console.log(reg.test(str));
```



正则表达式的常用操作符:

| 操作符 | 说明                                | 实例                                    |
| ------ | ----------------------------------- | --------------------------------------- |
| .      | 表示任何单个字符                    |                                         |
| [ ]    | 字符集，对单个字符给出取值范围      | [abc]表示a,b,c, [a-z]表示a到z的单个字符 |
| [^ ]   | 非字符集，对单个字符给出排除范围    | [^abc]表示非a或b或c的单个字符           |
| *      | 前一个字符0次或无限次扩展           | abc*表示ab,abc,abcc,abccc等             |
| +      | 前一个字符1次或无限次扩展           | abc+表示abc,abcc,abccc等                |
| ?      | 前一个字符0次或1次扩展              | abc?表示ab,abc                          |
| \|     | 左右表达式任意一个                  | abc\|def表示abc,def                     |
| {m}    | 扩展前一个字符m次                   | ab{2}c表示abbc                          |
| {m,n}  | 扩展前一个字符m至n次(含n)           | ab{1,2}c表示abc,abbc                    |
| ^      | 匹配字符串开头                      | ^abc表示abc且在一个字符串开头           |
| $      | 匹配字符串结尾                      | abc$表示abc且在一个字符串的结尾         |
| ( )    | 分组标记，内部只能使用\|操作符      | (abc)表示abc,(abc\|def)表示abc,def      |
| \d     | 数字，等价于[0-9]                   |                                         |
| \w     | 单词字符，等价于[A-Za-z0-9_]        |                                         |
| *?     | 前一个字符0次或无限次扩展，最小匹配 |                                         |
| +?     | 前一个字符1次或无限次扩展，最小匹配 |                                         |
| ??     | 前一个字符0次或1次扩展，最小匹配    |                                         |
| {m,n}? | 扩展前一个字符m至n次(含n)，最小匹配 |                                         |









---



# DOM

文档对象模型，用来控制网页元素，顶级对象叫document

## DOM树

![image-20211121203729252](C:\Users\29406\AppData\Roaming\Typora\typora-user-images\image-20211121203729252.png) 

* 文档：一个页面就是一个文档，DOM中使用document表示
* 元素：页面中的所有标签都是元素，DOM中使用element表示
* 节点：网页中的所有内容都是节点（标签、属性、文本、注释等），DOM中使用node表示
* DOM把以上都看做对象





## 节点操作

一般地，节点至少拥有nodeType(节点类型)、nodeName(节点名称）和nodeValue(节点值）这三个基本属性。

元素节点：nodeType = 1，属性节点：nodeType = 2，文本节点(包括换行)：nodeType = 3

### 根据节点关系获取节点

| 节点方法/属性               | 说明                                           |
| --------------------------- | ---------------------------------------------- |
| node.parentNode             | 返回父亲节点                                   |
| node.children               | 返回所有**元素类型**孩子节点的列表             |
| node.firstElementChild      | 返回第一个**元素类型**子节点 (ie9以上)         |
| node.lastElementChild       | 返回最后一个**元素类型**子节点 (ie9以上)       |
| node.nextElementSibling     | 返回下一个**元素类型**兄弟节点 (ie9以上)       |
| node.previousElementSibling | 返回上一个**元素类型**兄弟节点 (ie9以上)       |
| node.childNodes             | 返回所有孩子节点的列表，注意包含换行(文本节点) |
| node.firstChild             | 返回第一个子节点，注意包含换行(文本节点)       |
| node.lastChild              | 返回最后一个子节点，注意包含换行(文本节点)     |
| node.nextSibling            | 返回下一个兄弟节点，注意包含换行(文本节点)     |
| node.previousSibling        | 返回上一个兄弟节点，注意包含换行(文本节点)     |



### 创建节点

先创建节点再添加节点

| 方法/属性                          | 说明                               |
| ---------------------------------- | ---------------------------------- |
| document.createElement('typename') | 创建节点，并返回该节点             |
| node.appendChild(节点)             | 为某节点添加儿子节点至**末尾**     |
| node.insertBefore(节点, 指定元素)  | 为某节点添加儿子节点至指定元素前面 |



### 删除节点

| 方法/属性              | 说明                         |
| ---------------------- | ---------------------------- |
| node.removeChild(节点) | 删除指定子节点，并返回该节点 |



### 复制节点

| 方法/属性        | 说明                                                         |
| ---------------- | ------------------------------------------------------------ |
| node.cloneNode() | 返回该节点的克隆, 若参数为空或false，则只复制节点本身，不复制里面的子节点,为true则也复制节点内容 |





## 元素操作

### 获取元素

1.利用DOM提供的方法获取元素

| 指令                                  | 作用                             |
| ------------------------------------- | -------------------------------- |
| document.querySelector(选择器)        | 返回指定选择器的第一个元素对象   |
| document.querySelectorAll(选择器)     | 返回指定选择器的所有元素对象     |
| document.getElementById(id)           | 根据id获取,返回element           |
| document.getElementsByTagName(标签名) | 根据标签名获取，得到的是一个数组 |
| document.getElementsByClassName(类名) | 根据类名获取，得到数组           |
| document.body                         | 返回body对象                     |
| document.documentElement              | 返回html对象                     |

2.利用节点层级关系获取元素

详细参看上面 [根据节点关系获取节点](#根据节点关系获取节点) 的内容

打印元素的详细信息：`console.dir(element)` 



### 元素方法

| 方法                             | 说明                                                 |
| -------------------------------- | ---------------------------------------------------- |
| element.属性                     | 返回元素的某属性，可以直接赋值，但不能获取自定义属性 |
| element.getAttribute('属性')     | 可以获取自定义属性，（一般自定义属性以`data-`开头）  |
| element.setAttribute('属性',值)  | 设置属性值                                           |
| element.removeAttribute('属性')  | 移除属性                                             |
| element.classList.add('类名')    | 添加类名                                             |
| element.classList.remove('类名') | 移除类名                                             |
| element.classList.toggle('类名') | 切换类名：若有该类则移除，若没有该类则添加           |

`a标签`中的`href`填写`javascript:void(0);`或者`javascript:;`可以阻止链接跳转



### 一些特殊的属性

| 特殊的属性 | 说明                                   |
| ---------- | -------------------------------------- |
| innerText  | 文本内容,不识别html标签,去除换行和空格 |
| innerHTML  | 文本内容,识别html标签,保留换行和空格   |
| style      | 行内样式属性(样式采用驼峰命名法)       |
| className  | 当前元素的类名                         |
| classList  | 返回元素的class列表                    |

style属性示例：

```javascript
btn.onclick = function(){
    div.style.backgroundColor = 'pink';
    //注意backgroundColor是驼峰命名法
}
```



### offset系列属性

元素偏移量，可以动态的得到元素的位置（偏移)、大小等。

| 属性                 | 说明                                                         |
| -------------------- | ------------------------------------------------------------ |
| element.offsetParent | 返回作为该元素带有定位的父级元素如果父级都没有定位则返回body |
| element.offsetTop    | 返回元素相对带有定位父元素上方的偏移                         |
| element.offsetLeft   | 返回元素相对带有定位父元素左边框的偏移                       |
| element.offsetWidth  | 返回自身包括padding 、边框、内容区的宽度                     |
| element.offsetHeight | 返回自身包括padding、边框、内容区的高度                      |



### client系列属性

可以获取元素可视区的相关信息，如该元素的边框大小、元素大小等。

| 属性                 | 说明                                         |
| -------------------- | -------------------------------------------- |
| element.clientTop    | 返回元素上边框的大小                         |
| element.clientLeft   | 返回元素左边框的大小                         |
| element.clientWidth  | 返回自身包括padding 、内容区的宽度，不含边框 |
| element.clientHeight | 返回自身包括padding、内容区的高度，不含边框  |



### scroll系列属性

可以动态的得到该元素的大小、滚动距离等。

| 属性                 | 作用                         |
| -------------------- | ---------------------------- |
| element.scrollTop    | 返回被卷去的上侧距离         |
| element.scrollLeft   | 返回被卷去的左侧距离         |
| element.scrollWidth  | 返回自身实际的宽度，不含边框 |
| element.scrollHeight | 返回自身实际的高度，不含边框 |

scrollWidth scrollHeight 和 clientWidth clientHeight 区别是：若内容文字超过了元素大小，scroll返回的大小包含超过的长度，client不包含





## 事件

事件是有三部分组成：事件源(被触发的对象)，事件类型，事件处理程序

### 注册事件

* 传统注册方式：`事件源.事件 = function(){事件处理程序}` 

  ​	该方法对于同一个元素的同一事件只能设置一个处理函数

* 方法监听注册方式：`事件源.addEventListener(事件, 事件处理函数[, useCapture])` 

  ​	注意该方法的事件类型字符串不要带on，如click，mouseover

  ​	第三个参数如果是true，表示在事件捕获阶段调用事件处理程序;如果是false(默认为false )，表示在事件冒 	泡阶段调用事件处理程序。



注册事件示例：

```javascript
var btn = document.getElementById('btn');
//1.传统方式
btn.onclick = function(){
    //按钮被点击后触发的事件
    //this 指向的是事件函数的调用者btn
}
//2.方法监听注册方式
btn.addEventListener('click',function(){
    //按钮被点击后触发的事件
})
```



### 删除事件（解绑事件）

* 传统注册方式：`事件源.事件 = null` 

* 方法监听注册方式：`事件源.removeEventListener(事件, 事件处理函数[, useCapture])` 

  ​	注意该方法的事件类型字符串不要带on，如click，mouseover



### DOM事件流

事件流描述的是从页面中接收事件的顺序。
事件发生时会在元素节点之间按照特定的顺序传播，这个传播过程即DOM事件流。

![image-20211123111656934](C:\Users\29406\AppData\Roaming\Typora\typora-user-images\image-20211123111656934.png) 

注意：

* Js 代码中只能执行捕获或者冒泡其中的一个阶段。
* onclick 只能得到冒泡阶段。
* 有些事件是没有冒泡的，比如onblur、onfocus、onmouseenter、onmouseleave
* addEventListener(type，listener[, usecapture])第三个参数为true，表示在事件捕获阶段调用事件处理程序;为false(默认为false )，表示在事件冒泡阶段调用事件处理程序。
* 我们一般更关注冒泡，很少使用事件捕获
* 可以使用事件对象的stopPropagation()方法阻止冒泡



### 事件对象

在绑定事件时，事件处理函数的小括号里可以加上 事件对象 ，事件对象可以自己命名，会在事件触发后自动创建，里面存储了触发事件的相关信息。

```javascript
var btn = document.getElementById('btn');
btn.onclick = function(event){//event是事件对象
    //在鼠标点击后，event自动创建，存储了如
    //谁绑定了这个事件，触发时鼠标的坐标，等相关信息
}
```

#### 常用的事件对象的属性和方法：

| 属性/方法           | 说明                             |
| ------------------- | -------------------------------- |
| e.target            | 返回触发事件的对象               |
| e.type              | 返回事件类型，如click，mouseover |
| e.preventDefault()  | 该方法阻止默认事件，如链接跳转   |
| e.stopPropagation() | 阻止事件冒泡                     |
| e.keyCode           | 返回按下的键盘的ASCII码          |
| e.pageX  e.pageY    | 返回鼠标相当于文档页面的X和Y坐标 |

示例：

```javascript
document.addEventListener('contextmenu',function(e){
    e.preventDefault();
})//取消右键菜单
document.addEventListener('selectstart',function(e){
    e.preventDefault();
})//禁止鼠标选中
```



### 事件委托

通过委派可以减少事件绑定的次数，提高程序的性能

原理：不需要给每个子节点单独设置事件监听器，而是事件监听器设置在其父节点上，然后利用冒泡原理影响设置每个子节点。

示例：

```javascript
//ul中有几个li,要求点击li时，则改变对应li的背景颜色
<ul>
    <li>li1</li>
    <li>li2</li>
    <li>li3</li>
</ul>

<script>
	var u1 = document.querySelector('ul');
	u1.onclick = function(event) {
		for(var i = 0; i < u1.children.length; i++){
			u1.children[i].removeAttribute('style');
		}
		event.target.style.backgroundColor = 'pink';
	};
</script>
```



### 常见事件

| 事件名                    | 说明                                            |
| ------------------------- | ----------------------------------------------- |
| onclick                   | 鼠标点击                                        |
| onfocus                   | 获得焦点                                        |
| onblur                    | 失去焦点                                        |
| onmouseover               | 鼠标经过                                        |
| onmouseout                | 鼠标离开                                        |
| onmousemove               | 鼠标移动                                        |
| onmouseup                 | 鼠标弹起                                        |
| onmousedown               | 鼠标按下                                        |
| onkeydown                 | 键盘按下                                        |
| onkeyup                   | 松开键盘                                        |
| onkeypress                | 按下并松开键盘(不识别功能键如ctrl,shift,箭头等) |
| document.DOMContentLoaded | DOM加载完成后触发                               |
| onscroll                  | 滚动条开始滚动                                  |









---



# BOM

浏览器对象模型，实现对浏览器进行交互，顶级对象叫window



![image-20211123222456194](C:\Users\29406\AppData\Roaming\Typora\typora-user-images\image-20211123222456194.png) 



## window对象

### window事件

| 事件            | 说明                                              |
| --------------- | ------------------------------------------------- |
| window.onload   | 当文档内容(图像，脚本，CSS等)完全加载完成才会触发 |
| window.onresize | 窗口大小改变                                      |
|                 |                                                   |

**利用onload事件可以将js写在页面上面** 

```javascript
window.addEventListener('load',function(){
    这里写js代码
})
```



### wondow属性

| 属性               | 说明                   |
| ------------------ | ---------------------- |
| window.innerWidth  | 返回当前屏幕的宽度     |
| window.pageYOffset | 返回页面滚动了多少距离 |
|                    |                        |



### window方法

| 方法               | 说明                       |
| ------------------ | -------------------------- |
| window.scroll(x,y) | 滚动窗口至页面中的特点位置 |
| window.open(url)   | 打开一个新窗口并返回       |
| window.close()     | 关闭当前窗口               |
|                    |                            |





## location对象

location对象用来获取和操作url相关内容

### location属性

| 属性              | 说明                           |
| ----------------- | ------------------------------ |
| location.href     | 获取或设置url                  |
| location.host     | 返回主机(域名)                 |
| location.port     | 返回端口号，没有则返回空字符串 |
| location.pathname | 返回路径                       |
| location.search   | 返回参数                       |
| location.hash     | 返回片段，#后面的内容          |



### location方法

| 方法                  | 说明                                             |
| --------------------- | ------------------------------------------------ |
| location.assign(url)  | 跟href一样，可以跳转页面（重定向），可以后退页面 |
| location.replace(url) | 替换当前页面，不能后退页面                       |
| location.reload()     | 重新加载页面，如果参数为true 强制刷新 ctrl+f5    |





## navigator对象

navigator对象包含有关浏览器的信息。

### navigator属性

| 属性                | 说明       |
| ------------------- | ---------- |
| navigator.userAgent | 返回请求头 |





## history对象

与浏览器历史记录进行交互。该对象包含用户访问过的URL。

### history方法

| 方法              | 说明                                      |
| ----------------- | ----------------------------------------- |
| history.back()    | 后退功能                                  |
| history.forward() | 前进功能                                  |
| history.go(n)     | n为正数则前进n个页面，为负数则后退n个页面 |





## screen对象

该对象中存放着有关显示浏览器屏幕的信息

### screen属性

| 属性           | 描述                                       |
| -------------- | ------------------------------------------ |
| availHeight    | 返回显示屏幕的高度 (除 Windows 任务栏之外) |
| availWidth     | 返回显示屏幕的宽度 (除 Windows 任务栏之外) |
| deviceXDPI     | 返回显示屏幕的每英寸水平点数               |
| deviceYDPI     | 返回显示屏幕的每英寸垂直点数               |
| height         | 返回显示屏幕的高度                         |
| width          | 返回显示器屏幕的宽度                       |
| pixelDepth     | 返回显示屏幕的颜色分辨率（比特每像素）     |
| updateInterval | 设置或返回屏幕的刷新率                     |









---



# js执行机制

![image-20211215102836506](D:\笔记\学习笔记\image\image-20211215102836506.png) 

所有任务都分为同步任务和异步任务

* 同步任务都在主线程上执行，形成一个执行栈。
* 异步任务相关回调函数添加到任务队列中(任务队列也称为消息队列)。



1.先执行执行栈中的同步任务。

2.异步任务(回调函数)放入任务队列中。

3.—旦执行栈中的所有同步任务执行完毕，系统就会按次序读取任务队列中的异步任务，被读取的异步任务结束等待状态，进入执行栈，开始执行。



异步任务有以下三类：

* 普通事件，如click.resize等
* 资源加载，如load、error等
* 定时器，包括setlnterval、setTimeout等

```javascript
console.log('1');
setTimeout(function(){
	console.log('2');
},0);
console.log('3');
//此时输出顺序为1 3 2
```









---



# 动画

原理：通过间隔定时器不断改变元素位置

## 定时器

设置定时器：

* 延迟定时器：`var timer1 = window.setTimeout(调用函数[, 延迟的毫秒数]);` 
* 间隔定时器：`window.setInterval(调用函数[, 间隔的毫秒数]);` 



停止计时器：

```javascript
window.clearTimeout(定时器名字);
```





## 封装动画函数

```javascript
function animate(obj,target,itv,cbk){//对象，目标位置，时间间隔，回调函数
    clearInterval(obj.timer);
    obj.timer = setInterval(function(){
        var step = (target - obj.offsetLeft) / 10;//每次移动的步长
        step = step > 0 ? Math.ceil(step) : Math.floor(step);//步长取整
        if(obj.offsetLeft == target){//注意该对象要有定位
            clearInterval(obj.timer);
            cbk && cbk();//调用回调函数
        }
        else{
        	obj.style.left = obj.offsetLeft + step + 'px';
        }
    },itv)
}
```





## 节流阀

防止轮播图按钮连续点击造成潘放过快。

节流阀目的:当上一个函数动画内容执行完毕，再去执行下一个函数动画，让事件无法连续触发。

核心实现思路∶利用回调函数，添加一个变量来控制，锁住函数和解锁函数。

* 开始设置一个变量`var flag =true;` 
* `if(flag){flag= false; do something}` 关闭水龙头
* 利用回调函数动画执行完毕，`flag= true` 打开水龙头









---



# 移动端js

与pc端不同的是，移动端不再有鼠标操作的概念，取而代之的是手指操作

## 触屏事件

| 事件               | 说明               |
| ------------------ | ------------------ |
| element.touchstart | 手指开始触摸到元素 |
| element.touchmove  | 手指在元素上滑动   |
| element.touchend   | 手指离开元素       |





## 触摸事件对象

| 属性                 | 说明                       |
| -------------------- | -------------------------- |
| event.touches        | 当前屏幕的接触点列表       |
| event.targetTuoches  | 当前元素上的接触点列表     |
| event.changedTouches | 接触点状态发生了改变的列表 |









---



# 本地存储

## 本地存储特征

* 数据存储在用户浏览器中
* 设置、读取方便、甚至页面刷新不丢失数据
* 容量较大，sessionStorage约5M、localStorage约20M
* 只能存储字符串，可以将对象JSON.stringify)编码后存储





## sessionStorage

* 生命周期为关闭浏览器窗口
* 存储的数据只能在当前页面使用

| 方法                              | 说明                         |
| --------------------------------- | ---------------------------- |
| sessionStorage.setItem(key,value) | 存储数据，key是键，value是值 |
| sessionStorage.getItem(key)       | 获取数据                     |
| sessionStorage.removeItem(key)    | 删除数据                     |
| sessionStorage.clear()            | 删除所有数据                 |





## localStorage

* 生命周期永久生效，除非手动删除
* 存储的数据是多页面共享的

| 方法                            | 说明                         |
| ------------------------------- | ---------------------------- |
| localStorage.setItem(key,value) | 存储数据，key是键，value是值 |
| localStorage.getItem(key)       | 获取数据                     |
| localStorage.removeItem(key)    | 删除数据                     |
| localStorage.clear()            | 删除所有数据                 |









---



# 开发框架/插件

前端常用的框架有Bootstrap、Vue、Angular、React等。既能开发PC端，也能开发移动端

前端常用的移动端插件有swiper、superslide、iscrol等。

[轮播图插件](https://www.swiper.com.cn/)  









---

