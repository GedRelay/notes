[TOC]

# 绪论

## 注意点

* python属于解释型语言，不需要编译，读到一行执行一行。所以要小心程序运行到一半报错的问题！
* python使用强制缩进来分割代码块，一个缩进一般是**4个空格**的长度，多一个少一个空格都会报错





## 查看指令

可以通过百度或者查阅官方文档来查看指令，这里有两个有用的函数：

`__builtins__ `：查看指令大全

`help(命令)`：告诉你对应的指令有什么用





## 注释：

```python
#单行注释

'''多行
注释'''
```









---



# 数据类型

python的数据类型有：字符串、整型、浮点数、列表、元组、集合、字典、布尔型等等。

其中 字符串、列表、元组、集合和字典 都属于序列类型，这些序列支持几种通用的操作

变量使用时是不需要声明的，但是**变量必须赋值，变量赋值以后才会被创建**。python会自动判断变量的类型

## 注意点

* python的字符和字符串类型没有区别，**单引号和双引号都可以通用** 
* 布尔类型取值是 `True`和`False`，**首字母一定要大写！** 





## 强制类型转换

`list(obj)`：将对象强制转换成列表

`tuple(ojb)`：将对象强制转换成元祖

`int(obj) , float(obj) , str(obj)` 将对象强制转换成整数，浮点数，字符串

示例：

```python
a = '123456'
a = list(a)  # ['1', '2', '3', '4', '5', '6']
a = tuple(a) # ('1', '2', '3', '4', '5', '6')
b = '789'
b = int(b)	 # 789
b = float(b) # 789.0
b = str(b)   # '789.0'
```





## type(参数)

返回参数的数据类型





## isinstance(参数,类型)

判断该参数是否为此类型

```python
a=0.5
isinstance(a,int)
#返回false
```









---



# 操作符

## 算数操作符

`加(+)，减(-)，乘(*)，除(/)，整除(//)，取余(%)，幂(**)`

注意python的除法为真实除法：`10/3 == 3.3333333335`

* `//`：整除

```python
10//3==3
3.0//2==1.0
```

* `**`：幂运算，`a**b`相当于`pow(a,b)` 

```python
3**2==9
```





## 逻辑操作符

`与and，或or，非not` 

* python没有&&, ||, !操作





## 比较操作符

`小于<，大于>，等于==，不等于!=` 

* python还支持连续使用比较符的操作

```python
3<4<5是可行的
```





## 赋值操作符

除了赋值`=`外，python还支持`+=，-=，*=，/=，//=，%=`复合赋值操作





## 三元操作符

`if..else`的简写形式

```python
变量名 = 值1 if 条件表达式 else 值2
#还是挺符合英语语序的
```

例：

```python
x,y=4,5
if x<y:
    small = x
else:
    samll =y
#可以写成
small = x if x < y else y
#等同于c++语言三目运算符
small = x < y ? x : y;
```









---



# 分支控制

## if...else

同c一样，只不过大括号限定域改为了**强制缩进**来表明限定域,**注意冒号！** 

```python
if 逻辑表达式:
    表达式为真执行的语句
else:
    表达式为假执行的语句
```





## if...elif...else

`elif`等同于c语言的`else if`

```python
if 表达式1:
    表达式1为真执行的语句
elif 表达式2：
    表达式2为真执行的语句
elif 表达式3:
    表达式3为真执行的语句
else:
    都为假执行的语句
```









---



# 循环控制

## while 循环

`while`循环同c一样，不过**python没有do while语句**,没有小括号和大括号，使用强制缩进限定范围,**注意冒号！** 

```python
while 条件:
    条件为真执行的语句
```





## for 循环

for循环同c逻辑一样，但是语法差别很大,使用**强制缩进**限定范围,**注意冒号！** 

```python
for 目标 in 表达式:
    循环体

如：
myname = 'GedRelay'
for i in myname:
    print(i,end=' ')
#输出:G e d R e l a y
```

### range([start,] stop[, step=1] )

生成一个从`start`参数的值开始到`stop`参数的值结束（左闭右开），步长为`step`的数字序列

* `start`默认为`0`，`step`默认为`1` 

```python
list(range(5))#[0,1,2,3,4]
```

与for连用

```python
for i in range(2,9):
    print(i)
#2 3 4 5 6 7 8
```





## break和continue

和c一样

* `break`跳出整个循环
* `continue`跳出当前循环









---



# 异常处理

## try...except

若在`try`的范围内出现异常报错，程序不会因此结束，而会转而执行`except`里的语句

* `try`和`except`一定要成对出现，若出现异常后什么都不做，那么`except`里面可以写`pass` 

```python
try:
    <语句块1>
except <异常类型>:#异常类型是python已经定义的
    <语句块2>
```

示例：

```python
try:
    num=eval(input("请输入一个整数:"))
    print(num**2)
except:
    print("输入不是整数")
```





## assert 断言

当这个关键字后边的条件为假的时候，程序自动崩溃并抛出`AssertionError`的异常。

一般来说用它在程序中置入检查点，当需要确保程序中的某条件一定为真才能让程序正常工作的话，`assert`关键字就很有用了

```python
assert 3>4 # 执行到这句时，程序会抛出异常
```









---



# 序列类型通用操作

序列类型包括：字符串、列表、元组、集合和字典，这些序列支持几种通用的操作

* **集合和字典不支持索引、切片、连接和重复操作** 

## 索引

序列都能通过 `序列名[索引]` 来访问索引处的元素





## in， not in

这两个关键词可以测试某元素是否存在于序列中

```python
list1 = [123,['ged','daos'],456]
print(123 in list1) #True
print(798 not in list1) #True
print('ged' in list1) #False
print('ged' in list1[1]) #True

s = 'wtf?'
print('w' in s) #True
print('T' in s) #False
print('f?' in s) #True
```





## 切片操作

可以返回列表的一部分，对原列表没有影响

```python
列表名[起始下标:结束下标:步长] # 注意范围是左闭右开的
#起始下标默认为0，结束下标默认为结束，步长默认为1
```

示例：

```python
list1 = [1,2,3,4,5]
list2 = list1[1:4] # [2,3,4]
list2 = list1[:4]  # [1,2,3,4]
list2 = list1[1:]  # [2,3,4,5]
list2 = list1[:]   # [1,2,3,4,5]拷贝一个list1列表,此时list2独立于list1
list3 = list1      # 当list1列表改变时，list3也会改变！！！

s = 'abcd'
print(s[1:3]) # 'bc'
```

### 负下标

python支持下标为负数，即表示倒数第几个，负下标从`-1`开始，同样注意下标越界的问题

![image-20220114002457878](https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20220114002457878.png)

```python
list1 = [0,1,2,3,4,5,6,7,8,9]
list2 = list1[0:-6] # [0,1,2,3]
list2 = list1[-6:-3] # [4,5,6]
list2 = list1[-1:0] # 不允许此操作，返回空列表[]
```





## 连接 +

两个相同类型的序列可以使用`+`号进行连接操作

示例：

```python
list1 = ['a','b','c']
list2 = [1,2,3]
list3 = list1 + list2 # ['a', 'b', 'c', 1, 2, 3]

s1 = "mzy"
s2 = "666!"
s3 = s1 + s2 # "mzy666!"
```





## 重复 *

序列可以使用`*`号与数字进行运算，此时代表的含义是将序列重复若干次

示例：

```python
list1 = ['a', 'b', 'c']
list1 *= 3 # 等同于 list1 = list1 * 3
#['a', 'b', 'c', 1, 2, 3, 'a', 'b', 'c', 1, 2, 3, 'a', 'b', 'c', 1, 2, 3]

s = "-"
print(s * 20) # --------------------
```





## 通用函数/方法

| 函数/方法                      | 描述                                                 |
| ------------------------------ | ---------------------------------------------------- |
| len(s)                         | 返回序列 s 的长度                                    |
| min(s)                         | 返回序列 s 的最小元素，s 中元素需要可比较            |
| max(s)                         | 返回序列 s 的最大元素，s 中元素需要可比较            |
| s.index(x) 或 s.index(x, i, j) | 返回序列 s 从 i 开始到 j 位置中第一次出现元素x的位置 |
| s.count(x)                     | 返回序列 s 中出现x的总次数                           |









---



# 列表

* 列表的数据项不需要具有相同的类型，可以是任意类型，甚至可以列表嵌套

* 列表下标从`0`开始
* 列表的长度能随意变化
* 列表是引用类型，存储的其实是内存地址，所以列表的赋值操作属于浅拷贝

## 创建列表

使用中括号定义：`列表名 = [列表中的值,不同的值用逗号隔开]` 

```python
number = [1,2,3,4,5]#普通列表
mix = [99,'hello',3.14,[1,2,3],true]#混合列表，甚至列表内还能放列表
empty = []#空列表
```





## 访问

使用中括号访问，注意下标不要越界

```python
列表名[下标]
```





## 比较大小

列表支持`<,>,>=,<=,==,!=`等比较大小，但只会比较列表第一个的大小，字符串比较字典序，不同类型比较会出错

```python
list1 = [123,456]
list2 = [456,123]
print(list1 > list2)#False
```





## 列表常用方法

### 添加元素

| 方法                   | 描述                             |
| ---------------------- | -------------------------------- |
| append(element)        | 将元素添加至列表末尾             |
| entend(list)           | 将另一个列表中的每个元素扩展列表 |
| insert(index, element) | 将元素插入到指定下标处           |

示例：

```python
list1 = [1,2,3]
list1.append('a')#[1,2,3,'a']
#list1.append(['x','y'])##[1,2,3,'a'['x','y']]
list1.extend(['x','y'])#[1,2,3,'a','x','y']
list1.insert(1,'first?')#[1,'first?',2,3,'a','x','y']
```



### 删除元素

| 方法            | 描述                                           |
| --------------- | ---------------------------------------------- |
| remove(element) | 将列表中第一个出现的该元素删除                 |
| pop([index])    | 将下标处的元素删除并返回，默认删除最后一个元素 |

另外还有一个`del`语句

```python
list2 = [1,2,3,2,'a','b','c']
list2.remove(2)#[1,3,2,'a','b','c']
aaa = list2.pop()#[1,3,2,'a','b'],aaa='c'
bbb = list2.pop(3)#[1,3,2,'b'],bbb='a'
del list2[2]#[1,3,'b']
del list2#整个列表被删除，并不是变成空列表
```



### 翻转

`reverse()`方法

```python
list1=[1,2,3,4,5,6,7,8]
list1.reverse()#[8, 7, 6, 5, 4, 3, 2, 1]
```



### 排序

`sort()`方法

```python
list1=[2,5,6,9,8,4,1,7,3]
list1.sort()#[1, 2, 3, 4, 5, 6, 7, 8, 9]默认升序
#降序排序：
list1=[2,5,6,9,8,4,1,7,3]
list1.sort(reverse=True)#[9, 8, 7, 6, 5, 4, 3, 2, 1]
```









---



# 元祖

元祖大部分同列表一样，区别就是**元祖内的元素无法被更改**，—旦用一组元素创建一个元组，它就会一直保持不变。所以元祖只能访问

元组存在的价值、意义：保证数据安全

## 创建元祖

使用小括号定义：`元组名 = (元祖中的值)` 

* 注意如果定义一个元组中有且只有一个元素，`(1)`是错误的！`(1,)`才是正确的！

```python
tuple1 = (1,2,3,4,5)
tuple1 = (1,)#定义一个元组中有且只有一个元素,逗号是关键
tuple1 = ()#空元祖
```





## 访问

同列表一样使用下标索引访问





## 添加元素(不推荐！)

虽然不能直接给元祖直接添加新元素，但是因为元祖支持切片和拼接的操作，所以有以下方法更新元祖以给元祖添加元素

```python
tuple1 = ('a','b','c','d')
tuple1 = tuple1[:2] + ('e',) + tuple1[2:] # ('a', 'b', 'e', 'c', 'd') 注意逗号-->('e',)<--
```





## 删除元祖

1. 使用del 删除元祖
2. 当某个元祖失去所有名称标签指针，那么该元祖会被自动回收

```python
tuple1 = (1,2,3,4)
del tuple1 # 直接用del删除该元祖
tuple1 = tuple1[:2] # (1,2,3,4)失去标签，将会被回收
```









---



# 集合

集合是一个元素无序且不重复的序列

## 创建集合

可以使用大括号`{}`或者`set()`函数

但是创建一个空的集合必须要用`set()`而不是`{}`，因为`{}`是用来创建一个空字典的

```python
A = {"python",123,a4}
B = set("pypy123") # {"y",3,2,"p",1} 顺序是不定的!
C = set([1,2,3,4,5,6]) #{1,2,3,4,5,6}
empty = set() #创建空集合
```





## 集合运算

| 操作符      | 名称 | 描述                                       |
| ----------- | ---- | ------------------------------------------ |
| S\|T        | 并集 | 返回一个新集合，包括在集合S和T中的所有元素 |
| S-T         | 差集 | 返回一个新集合，包括在集合S但不在T中的元素 |
| S&T         | 交集 | 返回一个新集合，包括同时在集合S和T中的元素 |
| S^T         | 补集 | 返回一个新集合，包括集合S和T中的非相同元素 |
| S<=T 或 S<T | 子集 | 返回True/False，判断S和T的子集关系         |
| S>=T 或 S>T | 包含 | 返回True/False，判断S和T的包含关系         |

示例：

```python
A = {1,2,3}
B = {3,4,5}

print(A | B) #{1, 2, 3, 4, 5}
print(A - B) #{1, 2}
print(A & B) #{3}
print(A ^ B) #{1, 2, 4, 5}
print(A < B) #False
print(A > B) #False
```





## 集合常用方法

### 添加元素

| 方法           | 描述                                                    |
| -------------- | ------------------------------------------------------- |
| s.add(element) | 向集合中添加元素                                        |
| s.update(x)    | 参数可以是列表，元组，字典等，且x可以有多个，具体看示例 |

示例：

```python
s = set((1,2,3))
s.add(4) # {1, 2, 3, 4}
s.update({1,5}) # {1, 2, 3, 4, 5}注意会去重
s.update(["a","b"],[6,7],"c") # {1, 2, 3, 4, 5, 'a', 6, 7, 'c', 'b'}
```





### 删除元素

| 方法               | 描述                                              |
| ------------------ | ------------------------------------------------- |
| s.remove(element)  | 移除s中元素,如果元素不在集合中，产生KeyError异常  |
| s.discard(element) | 移除s中元素,如果元素不在集合中，不会报错          |
| s.clear()          | 移除s中所有元素                                   |
| s.pop()            | 随机移除一个元素并返回，若s为空，产生KeyError异常 |





### 复制

| 方法     | 描述                |
| -------- | ------------------- |
| s.copy() | 返回集合s的一个副本 |









---



# 字典

字典是另一种可变容器模型，且可存储任意类型对象。

## 创建字典

使用大括号`{}`或者`dict()`来创建，键值对用冒号`:`表示

```python
字典名 = {键1:值1,键2:值2,键3:值3,.....,键n:值n}#定义

dic = {'a': 1, 'b': [2, 3], 'c': 4}
dic = {} # 空字典
```





## 访问

1. 通过`字典名[键名]`来访问特定键的值，若不存在此键，则会报错
2. 通过`字典名.get(键名)`来访问，若不存在此键，则会返回`None` 

```python
dic = {'a': 1, 'b': [2, 3], 'c': 4}
print(dic['b']) # [2, 3]
```





## 添加元素

* 注意如果键重复，则最后的一个键值对会替换前面的

直接使用`字典名[键] = 值`即可向字典中添加数据

```python
dic = {'a':1}
dic['b'] = 2
print(dic) # {'a': 1, 'b': 2}
```





## 字典常用方法

### 删除元素

| 方法             | 描述                                               |
| ---------------- | -------------------------------------------------- |
| del d[k]         | 删除字典d中键k对应的键值对                         |
| d.pop(k,default) | 若键k存在，则移除并返回相应值，不存在返回default值 |
| d.popitem()      | 随机从字典d中移除一个键值对，以元祖形式返回        |
| d.clear()        | 删除所有的键值对                                   |



### 查看字典

| 方法       | 描述                                                |
| ---------- | --------------------------------------------------- |
| k in d     | 判断键k是否在字典d中，如果在返回True，否则返回False |
| d.keys()   | 返回字典d中所有的键信息                             |
| d.values() | 返回字典d中所有的值信息                             |
| d.items()  | 返回字典d中所有的键值对信息                         |









----



# 字符串

字符串是 Python 中最常用的数据类型。

## 创建字符串

可以使用引号`''`或`""`来创建字符串。

```python
s = 'hello'
s = "world" # 单双引号是一样的
s = "" # 空字符串
```





## 原始字符串

所有的字符串都是直接按照字面的意思来使用，没有转义特殊或不能打印的字符。 原始字符串除在字符串的第一个引号前加上字母`r`或`R`以外，与普通字符串有着几乎完全相同的语法

```python
s = r'a\nb'
s = R'a\nb'
print(s) # a\nb 不会转义\n为换行
```





## 三引号

Python 三引号`''' '''`允许一个字符串跨多行，字符串中可以包含换行符、制表符以及其他特殊字符。

```python
s = '''hello!
world'''

print(s)
#hello!
#world
```





## 字符串格式化

这些内容同c语言一模一样

### 字符串格式化符号含义

| **符号** | **说明**                                   |
| -------- | ------------------------------------------ |
| %c       | 格式化字符及其 ASCII 码                    |
| %s       | 格式化字符串                               |
| %d       | 格式化整数                                 |
| %o       | 格式化无符号八进制数                       |
| %x       | 格式化无符号十六进制数                     |
| %X       | 格式化无符号十六进制数（大写）             |
| %f       | 格式化浮点数字，可指定小数点后的精度       |
| %e       | 用科学计数法格式化浮点数                   |
| %E       | 作用同 %e，用科学计数法格式化浮点数        |
| %g       | 根据值的大小决定使用 %f 或 %e              |
| %G       | 作用同 %g，根据值的大小决定使用 %f 或者 %E |



### 格式化操作符辅助命令

| **符号** | **说明**                                                   |
| -------- | ---------------------------------------------------------- |
| m.n      | m 是显示的最小总宽度，n 是小数点后的位数                   |
| -        | 用于左对齐                                                 |
| +        | 在正数前面显示加号（+）                                    |
| #        | 在八进制数前面显示 '0o'，在十六进制数前面显示 '0x' 或 '0X' |
| 0        | 显示的数字前面填充 '0' 取代空格                            |

示例：

```python
print('%c %c'%(97,99))	#a c
print('%s'%('hello world'.title()))	#Hello World
print('%o'%(8))	#10
print('%x'%(160))	#a0
print('%x'%(160))	#A0
print('%.4f'%(1.123456))	#1.1235
```



### format()方法格式化

<img src="https://cdn.jsdelivr.net/gh/GedRelay/imgs/rXbVsUQz3ngw6LZ.png"  width="500" />

<img src="https://cdn.jsdelivr.net/gh/GedRelay/imgs/M83TsOgWEJ5GilX.png" width="500" />

示例：

```python
a = 1
b = 2
print("a的值是 {}，b的值是 {} !".format(a,b)) # a的值是 1，b的值是 2 !
```





## 字符串常用方法

加粗为比较常用

| 方法                                      | 描述                                                         |
| ----------------------------------------- | ------------------------------------------------------------ |
| **split(sep=None, maxsplit=-1)**          | **以sep为分隔符，不带参数默认是以空格为分隔符切片字符串，如果 maxsplit 参数有设置，则仅分隔 maxsplit 个子字符串，返回切片后的子字符串拼接的列表。** |
| **count(sub[, start[, end]])**            | **返回 sub 在字符串里边出现的次数，start 和 end 参数表示范围，可选。** |
| **find(sub[, start[, end]])**             | **检测 sub 是否包含在字符串中，如果有则返回索引值，否则返回 -1，start 和 end 参数表示范围，可选。** |
| **upper()**                               | **转换字符串中的所有小写字符为大写。**                       |
| **lower()**                               | **转换字符串中所有大写字符为小写。**                         |
| **istitle()**                             | **如果字符串是标题化（所有的单词都是以大写开始，其余字母均小写），则返回 True，否则返回 False。** |
| **title()**                               | **返回标题化（所有的单词都是以大写开始，其余字母均小写）的字符串。** |
| **replace(old, new[, count])**            | **把字符串中的 old 子字符串替换成 new 子字符串，如果 count 指定，则替换不超过 count 次。** |
| center(width)                             | 将字符串居中，并使用空格填充至长度 width 的新字符串          |
| index(sub[, start[, end]])                | 跟 find 方法一样，不过如果 sub 不在 string 中会产生一个异常。 |
| isalnum()                                 | 如果字符串至少有一个字符并且所有字符都是字母或数字则返回 True，否则返回 False。 |
| isalpha()                                 | 如果字符串至少有一个字符并且所有字符都是字母则返回 True，否则返回 False。 |
| isdecimal()                               | 如果字符串只包含十进制数字则返回 True，否则返回 False。      |
| isdigit()                                 | 如果字符串只包含数字则返回 True，否则返回 False。            |
| islower()                                 | 如果字符串中至少包含一个区分大小写的字符，并且这些字符都是小写，则返回 True，否则返回 False。 |
| isnumeric()                               | 如果字符串中只包含数字字符，则返回 True，否则返回 False。    |
| isspace()                                 | 如果字符串中只包含空格，则返回 True，否则返回 False。        |
| endswith(sub[, start[, end]])             | 检查字符串是否以 sub 子字符串结束，如果是返回 True，否则返回 False。start 和 end 参数表示范围，可选。 |
| isupper()                                 | 如果字符串中至少包含一个区分大小写的字符，并且这些字符都是大写，则返回 True，否则返回 False。 |
| s.join(sub)                               | 以字符串作为分隔符，插入到 sub 中所有的字符s之间。           |
| ljust(width)                              | 返回一个左对齐的字符串，并使用空格填充至长度为 width 的新字符串。 |
| encode(encoding='utf-8', errors='strict') | 以 encoding 指定的编码格式对字符串进行编码。                 |
| lstrip()                                  | 去掉字符串左边的所有空格                                     |
| partition(sub)                            | 找到子字符串 sub，把字符串分成一个 3 元组 (pre_sub, sub, fol_sub)，如果字符串中不包含 sub 则返回 ('原字符串', '', '') |
| rfind(sub[, start[, end]])                | 类似于 find() 方法，不过是从右边开始查找。                   |
| rindex(sub[, start[, end]])               | 类似于 index() 方法，不过是从右边开始。                      |
| rjust(width)                              | 返回一个右对齐的字符串，并使用空格填充至长度为 width 的新字符串。 |
| rpartition(sub)                           | 类似于 partition() 方法，不过是从右边开始查找。              |
| rstrip()                                  | 删除字符串末尾的空格。                                       |
| capitalize()                              | 把字符串的第一个字符改为大写                                 |
| splitlines(([keepends]))                  | 在输出结果里是否去掉换行符，默认为 False，不包含换行符；如果为 True，则保留换行符。。 |
| startswith(prefix[, start[, end]])        | 检查字符串是否以 prefix 开头，是则返回 True，否则返回 False。start 和 end 参数可以指定范围检查，可选。 |
| strip([chars])                            | 删除字符串前边和后边所有的空格，chars 参数可以定制删除的字符，可选。 |
| swapcase()                                | 翻转字符串中的大小写。                                       |
| expandtabs([tabsize=8])                   | 把字符串中的 tab 符号（\t）转换为空格，如不指定参数，默认的空格数是 tabsize=8。 |
| translate(table)                          | 根据 table 的规则（可以由 str.maketrans('a', 'b') 定制）转换字符串中的字符。 |
| zfill(width)                              | 返回长度为 width 的字符串，原字符串右对齐，前边用 0 填充。   |
| casefold()                                | 把整个字符串的所有字符改为小写                               |









---



# 函数

## 定义,调用

```python
def 函数名([参数列表]):	#其实函数名可以用中文，并不推荐!
    函数体
    [return 返回值]

def pr_hen():
    print('哼！')
pr_hen()#调用
```





## 关键字参数

在调用时，传递的参数前指定关键字，避免参数排序错误

```python
def func(name,words):
    print(name + '->' +words)
    
func('Ged','Haha!')	#Ged->Haha!
func('Haha!','Ged')	#Haha!->Ged
func(words='Haha',name='Ged')	#Ged->Haha!
```





## 默认参数(可选参数)

在函数定义时，给参数加上默认值，如果调用时没有提供值，则对应参数会使用默认值

```python
def func(name='Ged',words='Haha!'):
    print(name + '->' +words)
    
func()	#Ged->Haha!
func(words='What?')	#Ged->What?
```





## 收集参数 (可变参数)

定义函数时，参数前加一个*号则此参数变为收集参数，调用时所有参数默认属于收集参数

```python
def func(*a1,a2='100'):
    print(a1)
    print(a2)
    
func('1','2','3')	#('1', '2', '3')  100
```





## 全局变量与局部变量

同c++

如果要在函数内改变全局变量的值，要使用`global关`键字

```python
a = 5
def func():
    global a # 此时a是全局变量
    a = 10
```





## 内嵌函数

python允许函数内定义另外的函数，但是只能用于此函数内

```python
a=10
def f1(x):
    def f2(x):	#在f1()中定义函数f2()
        return x+1
    return f2(x)+1

print(func(a))	#12
```





## 闭包

我们可以将闭包理解为一种特殊的函数，这种函数由两个函数的嵌套组成，且称之为外函数和内函数，外函数返回值是内函数的引用，此时就构成了闭包。

```python
def 外层函数(参数):
    def 内层函数():
        print("内层函数执行", 参数)
    return 内层函数

内层函数的引用 = 外层函数("传入参数")
内层函数的引用()
```

例子：

```python
def func(a, b):
    def line(x):
        return a * x - b
    return line

line = func(2, 3)
print(line(5))	#7
```

在这个案例中，外函数func有接收参数 a=2，b=3，内函数line接收参数x=5，在内函数体中计算了a*x-b 即 2×5-3的值作为返回值，外函数返回内函数的引用，这里的引用指的是内函数line在内存中的起始地址，最终调用内函数line()得到返回值7

如果想要在内函数中修改外函数的值，需要使用 nonlocal 关键字声明变量

```python
def func(a, b):
    def line(x):
        nonlocal a
        a = 3
        return a * x - b
    return line

line = func(2, 3)
print(line(5))	#12
```





## lambda函数

就是匿名函数，没有名字的函数。减少了代码的冗余，快速地实现某项功能。一般lamda函数功能简单且单一

```python
<变量名> = lambda <参数>:<表达式>
#等价于：
def <函数名>（<参数>）:
    <函数体>
    return <返回值>
```

示例：

```python
add = lambda x,y:x+y # 注意add是变量不是函数！所以add还可以做其他用
print(add(1,2)) # 3
```





## 常用函数

python提供了许多好用的函数

### 函数列表

| 函数                       | 功能                                                         |
| -------------------------- | ------------------------------------------------------------ |
| eval(参数)                 | 将参数最外侧引号去除并执行余下语句 [示例](#eval())           |
| round（x[,d]）             | 对x四舍五入，d是小数的截取位数,默认是0                       |
| abs(x)                     | 绝对值                                                       |
| divmod(x,y)                | 商余，同时输出商和余数，如divmod(10,3)结果为(3,1)            |
| pow(x,y[,z])               | 输出结果：(x**y)%z                                           |
| max(x1,x2....xn)，min(...) | 返回最大最小值                                               |
| enumerate(obj)             | 生成下标和元素值组成的元祖 [示例](#enumerate(obj))           |
| zip(obj1 , obj2)           | 将两个对象的元素一 一对应组成元祖，长度取最小的那个 [示例](#zip(obj1 , obj2)) |
|                            |                                                              |



### 函数使用示例

#### eval()

```python
eval("1") # 数字1
eval("'1'") # 字符串1
eval("1+2") # 数字3
eval("print("hello")") # 打印出hello字符串
```



#### enumerate(obj)

```python
a = [1,2,3,4,5,6,7,8,9]
b = [4,5,6,7,8]
print(list(enumerate(a)))	# [(0, 1), (1, 2), (2, 3), (3, 4), (4, 5), (5, 6), (6, 7), (7, 8), (8, 9)]
print(list(enumerate(b)))	# [(0, 4), (1, 5), (2, 6), (3, 7), (4, 8)]
```



#### zip(obj1 , obj2)

```python
a = [1,2,3,4,5,6,7,8,9]
b = [4,5,6,7,8]
print(list(zip(a,b)))	# [(1, 4), (2, 5), (3, 6), (4, 7), (5, 8)]
```









---



# 文件操作

## 打开文件

```python
<变量名> = open(<文件路径和文件名>,<打开模式>)
#源文件同目录可省略路径
#打开模式包括文本打开或者二进制打卡，读入或者写入
```

### 文件打开模式

| 文件的打开模式 | 描述                                                        |
| -------------- | ----------------------------------------------------------- |
| 'r'            | 只读模式，默认值，如果文件不存在，返回FileNotFoundError异常 |
| 'w'            | 覆盖写模式，文件不存在则创建，存在则完全覆盖                |
| 'x'            | 创建写模式，文件不存在则创建，存在则返回FileExistsError     |
| 'a'            | 追加写模式，文件不存在则创建，存在则在文件最后追加内容      |
| 'b'            | 二进制文件模式                                              |
| 't'            | 文本文件模式，默认值                                        |
| '+'            | 与r/w/x/a/一同使用，在原功能基础上增加同时读写能力          |





## 读取文件内容

| 操作方法             | 描述                                                         |
| -------------------- | ------------------------------------------------------------ |
| f.read(size=-1)      | 读入全部内容，如果给出参数，读入前size长度                   |
| f.readline(size=-1)  | 读入一行内容，如果给出参数，读入改行前size长度               |
| f.readlines(hint=-1) | 读入文件所有行，以每行为元素写成列表<br/>如果给出参数，读入前hint行 |

```python
fname = input("请输入要打开的文件的名字")
fo = open(fname,"r")
---------------------------------------
遍历全文本：方法一
txt = fo.read()
#对全文进行处理
fo.close()
---------------------------------------
方法二
txt = fo.read(2)
while txt !="":
    #对txt进行处理
    txt = fo.read(2)
fo.close()
---------------------------------------
逐行遍历文件：方法一
for line in fo.readlines():
    #对文本进行处理
fo.close()
---------------------------------------
方法二
for line in fo:
    #对一行文本进行处理
fo.close()
```





## 写入数据

| 操作方法            | 描述                                                         |
| ------------------- | ------------------------------------------------------------ |
| f.write(s)          | 将文件写入一个字符串或字节流                                 |
| f.writelines(lines) | 将一个元素全为字符串的**列表**写入文件<br/>例：ls=['a','b','c']<br/>f.writelines(ls)<br/>文件内容：abc |
| f.seek(offset)      | 改变当前文件操作指针的位置，offset含义如下：<br/>0 - 文件开头 ; 1 - 当前位置 ; 2 - 文件结尾<br/>如：f.seek(0) #将指针指向文件开头 |









---



# 面向对象

**类(Class):** 用来描述具有相同的属性和方法的对象的集合。它定义了该集合中每个对象所共有的属性和方法。对象是类的实例。

**方法：**类中定义的函数。

**类变量：**类变量在整个实例化的对象中是公用的。类变量定义在类中且在函数体之外。类变量通常不作为实例变量使用。

**局部变量：**定义在方法中的变量，只作用于当前实例的类。

## 类的定义

```python
class Car():
    pass
##    
class Car():
    gasoline = 100 #属性
    __price = 50000#私有属性
    def run(self):#方法
      print('runing')
#self不是必须的可以自己定义
```





## 类的实例化

```python
myCar = Car()
print(myCar.gasoline)
myCar.run()
```





## 构造函数:

```python
class Car():
      def __init__(self):
        self.a = 1
#####
class Car():
      def __init__(self,destination):
        print(destination)
        self.destination = destination
        self.a = 1
```





## 继承:

### 单继承

```python
#类定义
class People:
    name = ''
    age = 0
    def __init__(self,n,a):
        self.name = n
        self.age = a
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
class Student(People):
    grade = ''
    def __init__(self,n,a,g):
        #调用父类的构函
        People.__init__(self,n,a)
        self.grade = g
    #覆写父类的方法
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级"%(self.name,self.age,self.grade))
      
a = Student('xiaohong',11,6) 
super(Student,a).speak() #用子类对象调用父类已被覆盖的方法
```





### 多继承

```python
#类定义
class People:
    name = ''
    age = 0
    def __init__(self,n,a):
        self.name = n
        self.age = a
    def speak(self):
        print("%s 说: 我 %d 岁。" %(self.name,self.age))
class Student():
    def __init__(self，g):
        self.grade = g
    #覆写父类的方法
    def speak(self):
        print("我在读 %d 年级"%(self.grade))
class Me(People,Student)
  def __init__(self,n,a,g):
    People.__init__(self,n,a)
    Student.__init__(self,g)
   
a = Me('xiaowang',10,5)
a.speak()#方法名同，默认调用的是在括号中排前地父类的方法
```









---



# 库引用

```python
import 库名
#使用函数：
库名.函数名（）

#也可以:
from 库名 import *
#使用函数：此时不需要加库名前缀
函数名()

#还可以
import 库名 as 库别名
#使用函数：
库别名.函数名()
```









---



# 官方标准库

## 海龟turtle绘图库

### 导包

```py
import turtle
```



### 画布位置设置

<img src="https://cdn.jsdelivr.net/gh/GedRelay/imgs/7BOdZfIaxgDGn9v.png" width="400" height="230"/>

```python
设置绘图窗口的大小，单位为像素px
显示器左上角坐标点为（0,0）
turtle.setup(width,height,startx,starty)
后两个参数可选,默认在屏幕正中心
```



### 坐标系

#### 空间坐标系

<img src="https://cdn.jsdelivr.net/gh/GedRelay/imgs/3rDoO7YWIyKhiSC.png" width="400" height="230" />

#### 海龟坐标系

<img src= "https://cdn.jsdelivr.net/gh/GedRelay/imgs/J7rXYaIduxkiHUR.png" width="400" height="230" />

```python
turtle.left(angle)左转角度
trutle.right(angle)右转角度
trutle.fd(d)前进长度
trutle.bk(d)后退长度
```

#### 角度坐标系

<img src="https://cdn.jsdelivr.net/gh/GedRelay/imgs/6VyTDWsqE1F57OY.png" width="400" height="230"/>





### 画笔控制

```python
turtle.penup()画笔抬起
turtle.pendown()画笔落下
turtle.pensize(参数)设置画笔宽度，单位px
turtle.pencolor(参数)设置画笔颜色，可以用英语单词或RGB参数
turtle.write('字符串',font=(字体),大小，"normal")#绘制字符串
```





## os库

### 导包

```python
import os.path#引用os.path子库
```



### 路径操作

| 函数                      | 描述                                                         |
| ------------------------- | ------------------------------------------------------------ |
| os.path.abspath(path)     | 返回path在当前操作系统中的绝对路径<br />os.path.abspath("file.txt")<br />"C:\\\\Users\\\\Tian Song\\\\Python36-32\\\\file.txt" |
| os.path.normpath(path)    | 归一化path的表示形式，统一用\\\\分隔路径<br />os.path.normpath("D://PYE//file.txt")<br />"D:\\\\PYE\\\\file.txt" |
| os.path.relpath(path)     | 返回当前程序与文件之间的相对路径(relative path)<br />os.path.relpath("C://PYE//file.txt")<br />"..\\\\..\\\\..\\\\..\\\\..\\\\PYE\\\\file.txt" |
| os.path.dirname(path)     | 返回path中的目录名称<br />os.path.dirname("D://PYE//file.txt")<br />"D://PYE" |
| os.path.basename(path)    | 返回path中最后的文件名称<br />os.path.basename("D://PYE//file.txt")<br />"file.txt" |
| os.path.join(path,*paths) | 组合path与paths，返回一个路径字符串<br />os.path.join("D:/" , "PYE/file.txt")<br />"D:/PYE/file.txt" |
| os.path.exists(path)      | 判断path对应文件或目录是否存在，返回True或False              |
| os.path.isfile(path)      | 判断path所对应是否为已存在的文件，返回True或False            |
| os.path.isdir(path)       | 判断path所对应是否为已存在的目录，返回True或False            |
| os.path.getatime(path)    | 返回path对应文件或目录上一次的访问时间                       |
| os.path.getmtime(path)    | 返回path对应文件或目录最近一次的修改时间                     |
| os.path.getctime(path)    | 返回path对应文件或目录的创建时间                             |
| os.path.getsize(path)     | 返回path对应文件的大小，以字节为单位                         |
| os.mkdir(path)            | 创建path目录                                                 |



### 进程管理

| 函数            | 描述                                                         |
| --------------- | ------------------------------------------------------------ |
| os.system(path) | 打开path路径下的文件或程序<br />os.system("C:\\Windows\\System32\\calc.exe")<br />将会打开系统自带的计算器 |



### 环境参数

| 函数           | 描述                                            |
| -------------- | ----------------------------------------------- |
| os.chdir(path) | 修改当前程序操作的路径                          |
| os.getcwd()    | 返回程序的当前路径                              |
| os.getlogin()  | 获得当前系统登录用户名称                        |
| os.cpu_count() | 获得当前系统的CPU数量                           |
| os.urandom(n)  | 获得n个字节长度的随机字符串，通常用于加解密运算 |





## time库

### 导包

```python
import time
```



### 时间获取

| 函数     | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| time()   | 获取当前时间戳，浮点数. <br>如1586194618.740861              |
| ctime()  | 获取当前时间以易读方式表示，字符串.  <br>如'Tue Apr  7 01:36:10 2020' |
| gmtime() | **获取当前时间，表示为计算机可处理的时间格式                 |



### 时间格式化

| 函数             | 描述                                                         |
| ---------------- | ------------------------------------------------------------ |
| strftime(tpl,ts) | tpl是格式化模板字符串，用来定义输出效果，<br>ts是计算机内部时间类型变量。<br>t=time.gmtime()<br>time.strftime("%Y-%m-%d %H:%M:%S",t)<br>'2020-04-06 17:54:27' |
| strptime()       | 将字符串转换成时间格式<br>str是字符串形式的时间值<br>tpl是格式化模板字符串，用来定义输入效果<br>timestr="2020-04-07 02:04:56<br>time.strptime(timestr,"%Y-%m-%d %H:%M:%S") |

#### 格式化字符串

| 格式化字符串 | 日期/时间说明 | 值范围和实例                   |
| ------------ | ------------- | ------------------------------ |
| %Y           | 年份          | 0000~9999，例如1900            |
| %m           | 月份          | 01~12，例如：10                |
| %B           | 月份名称      | January~December，例如：April  |
| %b           | 月份名称缩写  | Jan~Dec，例如：Apr             |
| %d           | 日期          | 01~31，例如25                  |
| %A           | 星期          | Monday~Sunday，例如：Wednesday |
| %a           | 星期缩写      | Mon~Sun，例如：Wed             |
| %H           | 小时（24h制） | 00~23，例如：12                |
| %I           | 小时（12h制） | 01~12，例如：7                 |
| %p           | 上/下午       | AM，PM，例如：PM               |
| %M           | 分钟          | 00~59，例如：26                |
| %S           | 秒            | 00~59，例如：25                |



### 程序计时

| 函数 | 描述 |
| -------------- | ------------------------------------------------------------ |
| perf_counter() | 返回一个时间，这个时间的起点不确定，所以调用差值才有意义，单位为秒 |
| sleep(t)   | 程序休眠t秒时间，可以是浮点数                            |





## random库

### 导包

```python
import random#库引用
```



### 基本随机函数

| 函数         | 描述                                       |
| ------------ | ------------------------------------------ |
| seed(a=None) | 初始化给定的随机数种子，默认为当前系统时间 |
| random()     | 生成一个[0.0,1.0)之间的随机小数            |



### 扩展随机函数

| randint(a,b)       | 生成一个[a,b]之间的整数              |
| ------------------ | ------------------------------------ |
| randrange(m,n[,k]) | 生成一个[m,n)之间以k为步长的随机整数 |
| getrandbits(k)     | 生成一个k比特长的随机整数            |
| uniform(a,b)       | 生成一个[a,b]之间的随机小数          |
| choice(列表)       | 从列表中随机选取一个元素             |
| shuffle(列表)      | 将列表中的元素打乱，返回打乱后的序列 |





## Re库

正则表达式库，是用来简洁表达一组字符串特征的表达式。最主要应用在字符串匹配中。

### re库主要函数

| 函数                                        | 说明                                                         |
| ------------------------------------------- | ------------------------------------------------------------ |
| re.search(pattern,string,falgs=0)           | 在一个字符串中搜索匹配正则表达式的第一个位置，返回match对象  |
| re.match(pattern,string,falgs=0)            | 从一个字符串的开始位置起匹配正则表达式，返回match对象        |
| re.findall(pattern,string,falgs=0)          | 搜索字符串，以列表类型返回全部能匹配的子串                   |
| re.split(pattern,string,maxsplit=0,falgs=0) | 将一个字符串按照正则表达式匹配结果进行分割，返回列表类型     |
| re.finditer(pattern,string,falgs=0)         | 搜索字符串，返回一个匹配结果的迭代类型，每个迭代元素是match对象 |
| re.sub(pattern,repl,string,count=0,falgs=0) | 在一个字符串中替换所有匹配正则表达式的子串，返回替换后的字符串 |
| regex = re.compile(pattern,flags=0)         | 将正则表达式的字符串形式编译成正则表达式对象                 |

```yaml
参数解释：
pattern: 正则表达式的字符串或原始字符串
string: 待匹配字符串
flags: 正则表达式使用时的控制标记
	re.I: 忽略正则表达式的大小写，[A-Z]能够匹配小写字母
	re.M: 正则表达式中的^操作符能够将给定字符串的每行当做匹配开始
	re.S: 正则表达式中的.操作符能够匹配所有字符串，默认匹配除换行外的所有字符
maxsplit: 最大分割数，剩余部分作为最后一个元素输出
repl: 替换匹配字符串的字符串
count: 匹配的最大替换次数

Re库的另一种等价用法
rst = re.search(r'[1-9]\d{5}','BIT 100081')
等价于
pat = re.compile(r'[1-9]\d{5}')
rst = pat.search('BIT 100081')
```



### Match对象的属性及方法

| 属性      | 说明                                |
| --------- | ----------------------------------- |
| .string   | 待匹配的文本                        |
| .re       | 匹配时使用的pattern对象(正则表达式) |
| .pos      | 正则表达式搜索文本的开始位置        |
| .endpos   | 正则表达式搜索文本的结束位置        |
| **方法**  | **说明**                            |
| .group(0) | 获得匹配后的字符串                  |
| .start()  | 匹配字符串在原始字符串的开始位置    |
| .end()    | 匹配字符串在原始字符串的结束位置    |
| .span()   | 返回(.start(),.end())               |



### 正则表达式的常用操作符

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

**举例：**

| 正则表达式                                                   | 说明                         |
| ------------------------------------------------------------ | ---------------------------- |
| P(Y\|YT\|YTH\|YTHO)?N                                        | PN,PYN,PYTN,PYTHN,PYTHON     |
| PYTHON+                                                      | PYTHON,PYTHONN,PYTHONNN,,,   |
| PY[TH]ON                                                     | PYTON,PYHON                  |
| PY\[^TH]?ON                                                  | PYON,PYaON,PYbON,PYcON,,,    |
| PY{:3}N                                                      | PN,PYN,PYYN,PYYYN            |
| ^[A-Za-z]+$                                                  | 由26个字母组成的字符串       |
| ^[A-Za-z0-9]+$                                               | 由26个字母和数字组成的字符串 |
| ^-?\d+$                                                      | 整数形式的字符串             |
| ^[0-9]\*\[1-9][0-9]*$                                        | 正整数形式的字符串           |
| [1-9]\d{5}                                                   | 中国境内邮政编码，6位        |
| [\u4e00-\u9fa5]                                              | 匹配中文字符                 |
| \d{3}-\d{8}\|\d{4}-\d{7}                                     | 国内电话号码，010-68913536   |
| (([1-9]?\d\|1\d{2}\|2[0-4]\d\|25[0-5]).){3}([1-9]?\d\|1\d{2}\|2[0-4]\d\|25[0-5]) | IP地址                       |
| http?://[a-zA-Z0-9\.\?/%-_]*                                 | 网址链接                     |









---



# 第三方库

python第三方库搜索网站:www.pypi.org

## 安装第三方库

需要打开`cmd`或者`powershell`来安装第三方库！

| 指令                        | 描述                                 |
| --------------------------- | ------------------------------------ |
| pip install <第三方库名>    | 安装第三方库                         |
| pip install -U <第三方库名> | 更新已安装的指定第三方库             |
| pip uninstall <第三方库名>  | 卸载指定的第三方库                   |
| pip download <第三方库名>   | 下载但不安装指定的第三方库           |
| pip show <第三方库名>       | 列出某个指定第三方库的详细信息       |
| pip search <关键词>         | 根据关键词在名称和介绍中搜索第三方库 |
| pip list                    | 列出当前系统已经安装的第三方库       |



## 第三方库使用

第三方库的使用方法以及爬虫的笔记在另一个笔记中！[python第三方库](D:\笔记\学习笔记\python第三方库.md) 









---

