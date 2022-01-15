<p align='center' style="font-size:150px; color:darkblue">css</p>

全称 Cascading Style Sheets (层叠样式表)

[toc]

# 相关链接

[W3school](https://www.w3school.com.cn/index.html) 

[bilibili黑马程序员教学](https://www.bilibili.com/video/BV14J4114768?p=1) 

[菜鸟教程](https://www.runoob.com/) 

[渐变色风格](https://uigradients.com/#Windy) 

https://icomoon.io/

[阿里巴巴矢量图标库](https://www.iconfont.cn/) 

[中国色](http://zhongguose.com/#hehuanhong) 

[配色方案(需要开飞机)](https://colorhunt.co/) 

[Less中文网址](http://lesscss.cn) 

[caniuse查询兼容性问题](https://caniuse.com/) 

<iframe src="//player.bilibili.com/player.html?aid=80149248&bvid=BV14J4114768&cid=137143602&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" style="width: 100%; height: 500px; max-width: 100%；align:center; padding:20px 0;"> </iframe>



# 引入css

显示优先级：就近原则，行内>内嵌>外部

## 行内样式

```html
<p style="color:darkblue">css</p>
```



## 内嵌样式

```html
<style type="text/css">
	p {
		margin: 0;
		padding: 0;
	}
</style>
```



## 外部样式

```html
<link rel="stylesheet" type="text/css" href="css文件"/>
```





# css初始化

不同浏览器对有些标签的默认值是不同的，为了消除不同浏览器对HTML文本呈现的差异，照顾浏览器的兼容，需要对CSS初始化

基础模板：

```css
* {
	margin: 0;
	padding: 0;
}
em,
i {
	font-style: normal;
}
li {
	list-style: none;
}
img {
	border: 0;
	vertical-align: middle;
}
button {
	cursor: pointer;
}
a {
	color: #666;
	text-decoration: none;
}
button,
input {
	font-family: Microsoft YaHei, Heiti SC, tahoma, arial, Hiragino Sans GB, "\5BBB\4F53", sans-serif;
}
body {
	-webkit-font-smoothing: antialiased;/*CSS3 抗锯齿性*/
	background-color: #fff;
	font: 12px/1.5 Microsoft YaHei, Heiti SC, tahoma, arial, Hiragino Sans GB, "\5BBB\4F53", sans-serif;
	color: #666;
}
.hide,
.none {/*隐藏样式*/
	display: none;
}
.clearfix:after {/*清除浮动*/
	visibility: hidden;
	clear: both;
	display: block;
	content: ".";
	height: 0;
}
.clearfix {
	*zoom: 1;
}
```

---





# 注释

快捷键：ctrl + /

```html
/*注释内容*/
```





# Emmet语法

可以帮助快速生成css代码，写上css样式的简写再按`tab键`即可

示例：

```css
w200
width: 200px;

lh100
line-height: 100;

bgc
background-color: #fff;
```





# 选择器

## 基础选择器

### 标签选择器

可以把某一类标签全部选择出来

```css
标签名 {...}
```



### 类选择器

根据class选择标签，一个标签可以有多个class

```css
.类名 {...}
```



### id选择器

根据id选择标签，一个标签只有一个id，id最好是唯一的

```css
#id名 {...}
```



### 通配符选择器

选择所有的标签

```css
* {...}
```



## 复合选择器

复合选择器是建立在基础选择器之上，对基本选择器进行组合形成的。

### 后代选择器

选择元素1里面的所有元素2

```css
元素1 元素2 {...}
```



### 子选择器

选择元素1里面所有的直接子元素2

```css
元素1 > 元素2 {...}
```



### 并集选择器

并集选择器可以选择多组标签,同时为他们定义相同的样式。通常用于集体声明.

选择元素1和元素2

```css
元素1,
元素2 {...}
```



### 伪类选择器

伪类选择器用于向某些选择器添加特殊的效果，比如给链接添加特殊效果，或选择第1个，第n个元素。

```css
元素:伪类 {...}
```



| 选择符      | 说明                 |
| ----------- | -------------------- |
| a:link      | 所有未被访问的链接   |
| a:visited   | 所有已被访问的链接   |
| a:active    | 鼠标按下未弹起的链接 |
| :hover      | 鼠标指针指向的元素   |
| input:focus | 获得焦点的input元素  |

注意link,visited,hover,active要按照LVHA的顺序编写,否则可能不生效



## CSS3新增选择器

### 属性选择器

属性选择器可以根据元素特定属性的来选择元素

```css
元素[属性] {...}
```



| 选择符           | 说明                               |
| ---------------- | ---------------------------------- |
| E[att]           | 具有att属性的E元素                 |
| **E[att="val"]** | 具有att属性且属性值等于val 的E元素 |
| E[att^="val"]    | 具有att属性且值以val开头的E元素    |
| E[att$="val"]    | 具有att属性且值以val结尾的E元素    |
| E[att*="val"]    | 具有att属性且值中含有val的E元素    |



### 结构伪类选择器

结构伪类选择器主要根据文档结构来选择器元素

```css
元素:结构选择器 {...}
```



| 选择符           | 说明                     |
| ---------------- | ------------------------ |
| E:first-child    | E的第一个子元素          |
| E:last-child     | E的最后一个子元素        |
| E:nth-child(n)   | E的第n个子元素(n从1开始) |
| E:first-of-type  | 第一个E元素              |
| E:last-of-type   | 最后一个E元素            |
| E:nth-of-type(n) | 第n个E元素(n从1开始)     |

* `E:nth-child()`的括号里可以填even，odd，表示所有偶数元素和奇数元素



### 伪元素选择器

伪元素选择器可以帮助我们利用CSS创建新标签元素(行内元素)，而不需要HTML标签，从而简化HTMI结构。

文档树中无法找到该元素

```css
元素::伪元素 {...}
```



| 选择符   | 说明                                          |
| -------- | --------------------------------------------- |
| ::before | 在元素内部的前面插入内容，必须有`content`属性 |
| ::after  | 在元素内部的最后插入内容，必须有`content`属性 |



## 总结

| 符号    | 表示           |
| ------- | -------------- |
| 无      | 标签           |
| .       | class          |
| #       | id             |
| [space] | 后代中的       |
| >       | 直接后代中的   |
| ,       | 和             |
| :       | 伪类，结构伪类 |
| []      | 属性           |
| ::      | 伪元素         |





# 样式

## 未分类样式

| 样式   | 样式值                                                       | 说明 |
| ------ | ------------------------------------------------------------ | ---- |
| width  | 像素，百分比，calc()函数                                     | 宽度 |
| height | 像素，百分比，calc()函数                                     | 高度 |
| filter | 滤镜函数 链接：[滤镜函数](https://www.runoob.com/cssref/css3-pr-filter.html) | 滤镜 |



## 字体样式

|    样式     |            样式值             |                 说明                 |
| :---------: | :---------------------------: | :----------------------------------: |
| font-family | 'Microsoft YaHei'，宋体，...  |                 字体                 |
|  font-size  |             像素              | 字体大小，标题比较特殊，需要单独指定 |
| font-weight | nomal，bold，数字100~900，... |               字体粗细               |
| font-style  |         nomal，italic         |           文字风格（斜体）           |



## 文本样式

| 样式            | 样式值                                  | 说明                               |
| --------------- | --------------------------------------- | ---------------------------------- |
| color           | 颜色                                    | 文本颜色                           |
| text-align      | center，left(默认)，right               | 文本水平对齐方式                   |
| vertical-align  | baseline(默认)，top，middle，bottom     | 垂直对齐方式(行内或行内块元素有效) |
| text-decoration | none，underline，overline，line-through | 文本装饰(下划线，上划线，删除线)   |
| text-indent     | em，表示当前元素1个元素的大小如2em      | 段落首行缩进                       |
| line-height     | 像素                                    | 行间距（行高）                     |
| white-space     | normal(自动换行，默认)，nowrap(不换行)  | 文字显示换行                       |
| text-overflow   | ellipsis(溢出部分用省略号代替)          | 文字溢出显示                       |

文字垂直居中：让行高等于容器的高度也可

<img src="https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20211126221101303.png" alt="image-20211126221101303" style="zoom: 67%;" /> 

![image-20211204115413251](https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20211204115413251.png)





## 背景样式

| 样式                  | 样式值                                                       | 说明         |
| --------------------- | ------------------------------------------------------------ | ------------ |
| background-color      | 颜色，transparent(透明)                                      | 背景颜色     |
| background-image      | none，url(图片地址)                                          | 背景图片     |
| background-repeat     | repeat，no-repeat，repeat-x，repeat-y                        | 背景平铺     |
| background-position   | x y坐标，空格隔开，若只有一个参数，另一个默认居中<br/>x和y可以是百分比，像素<br/>也可以是方位名词：top，center，bottom，left，right | 背景图片位置 |
| background-attachment | scroll(滚动，默认)，fixed(固定)                              | 背景图像固定 |

### 背景半透明效果：

```css
background: rgba(a,b,c,d); 其中d是透明度0~1
```

### 背景渐变色：

```css
background: linear-gradient(起始方向, 颜色1, 颜色2, ...);
背景渐变必须添加浏览器私有前缀
background: -webkit-linear-gradient(left, red, blue);
background: -webkit-linear-gradient(left top, red, blue);
```





## 边框样式

边框的关系看盒子模型内容

| 样式          | 样式值                                                       | 说明           |
| ------------- | ------------------------------------------------------------ | -------------- |
| border-width  | 像素                                                         | 边框粗细       |
| border-style  | none，dotted(点线)，dashed(虚线)，solid(实线)，double(双线)<br/>groove(3D凹槽)，ridge(菱形)，inset(3D凹边)，outset(3D凸边) | 边框样式       |
| border-color  | 颜色                                                         | 边框颜色       |
| border        | 粗细 样式 颜色                                               | 复合写法，无序 |
| padding       | 像素，auto<br/>一个值：上下左右<br/>两个值：上下，左右<br/>三个值：上，左右，下<br/>四个值：上，右，下，左 | 内边距         |
| margin        | 像素，auto(块级元素才可以)<br/>一个值：上下左右<br/>两个值：上下，左右<br/>三个值：上，左右，下<br/>四个值：上，右，下，左 | 外边距         |
| border-radius | 像素(表示圆的半径)，百分比                                   | 圆角边框       |

```css
通常css第一句话是这个
* {
    margin: 0;
    padding: 0;
}
```





## 阴影样式

| 样式        | 样式值                                    | 说明     |
| ----------- | ----------------------------------------- | -------- |
| box-shadow  | h-shadow v-shadow blur spread color inset | 盒子阴影 |
| text-shadow | h-shadow v-shadow blur color              | 文字阴影 |
| opacity     | 0~1之间的数字                             | 透明度   |



阴影样式值说明：

| 值       | 描述                           |
| -------- | ------------------------------ |
| h-shadow | 必须。水平阴影的位置，允许负值 |
| v-shadow | 必须。垂直阴影的位置，允许负值 |
| blur     | 可选。模糊距离                 |
| spread   | 可选。阴影尺寸                 |
| color    | 可选。阴影颜色                 |
| inset    | 可选。外部阴影改为内部阴影     |





## 元素显示与隐藏

| 样式       | 样式值                                                    | 说明         |
| ---------- | --------------------------------------------------------- | ------------ |
| display    | block，inline，none(隐藏)                                 | 显示模式     |
| visibility | visible，hidden                                           | 显示隐藏     |
| overflow   | visible，hidden，auto(溢出添加滚动条)，scroll(添加滚动条) | 溢出显示隐藏 |

display隐藏后，不再占有原来的位置

visibility隐藏后，继续占有原来的位置





## 界面样式

| 样式    | 样式值                                                       | 说明     |
| ------- | ------------------------------------------------------------ | -------- |
| cursor  | default(默认)，pointer(小手)，move(十字架)，text($I$形)，not-allowed(禁止) | 鼠标样式 |
| outline | none                                                         | 轮廓线   |
| resize  | none(无法调整)，horizontal(宽度可调)，vertical(高度可调)，both | 调整大小 |





## 样式书写顺序

建议遵循以下顺序：

1. 布局定位属性：display，position，float，clear，visibility，overflow
2. 自身属性：width，height，margin，padding，border，background
3. 文本属性：color，font，text-decoration，text-align，vertical-align，white-space，break-word
4. 其他属性：content，cursor，border-radius，box-shadow，text-shadow 。。。





# 元素类型(元素显示模式)

## 块元素

常见的块元素有`<h1>~<h6>`、`<p>`、`<div>`、`<ul>`、`<ol>`、`<li>`等。

特点：

* 独占一行
* 高度，宽度，外边距以及内边距都可以控制
* 宽度默认是父级宽度的100%
* 里面可以放行内元素或块级元素
* 文字类元素内不能放块级元素



## 行内元素

也称内联元素，常见的行内元素有`<a>`、`<strong>`、`<b>`、`<em>`、`<i>`、`<del>`、`<s>`、`<ins>`、`<u>`、`<span>`等。

特点:

* 相邻行内元素在一行上
* 无法设置高度和宽度
* 宽度默认是本身内容的宽度
* 里面只能放文字或其它行内元素
* a是特殊的行内元素，里面可以放块级元素



## 行内块元素

在行内元素中有几个特殊的标签 `<img />`、`<input />`、`<td>`，它们同时具有块元素和行内元素的特点。

特点：

* 和相邻行内元素(行内块)在一行上，但是他们之间会有空白缝隙。一行可以显示多个(行内元素特点)。
* 宽度默认是它本身内容的宽度(行内元素特点)。
* 高度，行高、外边距以及内边距都可以控制(块级元素特点）。



## 元素显示模式的转换

一个模式需要另一种模式的特性

* 转换为块级元素：`display: block;` 
* 转换为行内元素：`display: inline;` 
* 转换为行内块元素：`display: inline-block;` 

需要更改宽高的一般改成块级元素





# 样式冲突处理

## 继承性

子标签会继承父标签的某些样式



## 优先级

当样式出现冲突时，会检查优先级，若优先级相同则执行层叠性

| 选择器                           | 优先级  |
| -------------------------------- | ------- |
| 继承 或者 *                      | 0,0,0,0 |
| 元素选择器，伪元素选择器         | 0,0,0,1 |
| 类选择器，伪类选择器，属性选择器 | 0,0,1,0 |
| id选择器                         | 0,1,0,0 |
| 行内样式                         | 1,0,0,0 |
| !important                       | 无穷大  |

注意：复合选择器的权重会叠加



## 层叠性

原则：就近原则，哪个样式在后面，就执行哪个样式







# 盒子模型

margin：外边框

border：边框

padding：内边框

![image-20211127135729758](https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20211127135729758.png) 

| 样式       | 样式值                        | 说明     |
| ---------- | ----------------------------- | -------- |
| box-sizing | content-box(默认)，border-box | 盒子类型 |

* content-box 大小为 width + padding + border
* border-box 大小为 width，即padding和border不会撑开盒子







# 浮动

多个块级元素横向排列用浮动

## 添加浮动

float属性用于创建浮动框，将其移动到一边，直到左边缘或右边缘触及包含块或另一个浮动框的边缘。

| 样式  | 样式值                  | 说明 |
| ----- | ----------------------- | ---- |
| float | none(默认)，left，right | 浮动 |

特性：

* 浮动的元素与非浮动元素不在同一层，会与后面的元素重叠

* 浮动的元素会一行内显示并顶部对齐
* 浮动的元素会具有行内块元素的特性



## 清除浮动

由于父级盒子很多情况下，不方便给高度，但是子盒子浮动又不占有位置，最后父级盒子高度为0时，就会影响下面的标准流盒子。

**清除浮动的方法：**

* 额外标签法
  * 在末尾添加一个空标签(必须是块级元素)，如`<div style = "clear:both"></div>` 
* 父级添加overflow属性
* 父级添加after伪元素
* 父级添加双伪元素



| 样式     | 样式值                              | 说明                         |
| -------- | ----------------------------------- | ---------------------------- |
| clear    | left，right，both(同时清除左右浮动) | 清除浮动                     |
| overflow | hidden(隐藏溢出部分)，auto，scroll  | 当内容溢出元素框时发生的事情 |

```css
/*after伪元素清除浮动*/
.clearfix:after {
    content: "";
    display: block;
    height: 0;
    clear: both;
    visibility: hidden;
}
/*双伪元素清除浮动*/
.clearfix:before, .clearfix:after {
    content: "";
    display: table;
}
.clearfix:after {
    clear:both;
}
```







# 定位

定位∶将盒子定在某一个位置，所以定位也是在摆放盒子，按照定位的方式移动盒子。

定位 = 定位模式 + 边偏移

| 样式     | 样式值                                          | 说明                                   |
| -------- | ----------------------------------------------- | -------------------------------------- |
| position | static(默认)，relative，absolute，fixed，sticky | 定位模式：静态，相对，绝对，固定，粘性 |
| top      | 像素                                            | 顶端偏移量，相对于父元素上边线的距离   |
| bottom   | 像素                                            | 底部偏移量，相对于父元素下边线的距离   |
| left     | 像素                                            | 左侧偏移量，相对于父元素左边线的距离   |
| right    | 像素                                            | 右侧偏移量，相对于父元素右边线的距离   |

一般父元素使用相对定位，子元素使用绝对定位

* 行内元素添加绝对或者固定定位，可以直接设置高度和宽度。
* 块级元素添加绝对或者固定定位，如果不给宽度或者高度，默认大小是内容的大小。
* 浮动会压住下面标准流的盒子，但不会压住里面的文字，而绝对定位或者固定定位会压住所有内容



## 静态定位 static

元素默认就是静态定位(无定位)，按照标准流特性摆放位置，没有边偏移。



## 相对定位 relative

相对定位是元素在移动位置的时候，是相对于它原来的位置来说的

* 以原位置为参照点移动元素

* 添加相对定位后，原来的位置还占用(不脱标)



## 绝对定位 absolute

绝对定位是元素在移动位置的时候，是相对于它祖先元素来说的

* 以最近的有定位的父亲为参照点移动元素

* 如果没有祖先元素或者祖先元素没有定位，则以浏览器(Document)为准定位
* 添加绝对定位后，原来的位置不再占用(脱标)



## 固定定位 fixed

固定定位是元素固定于浏览器可视区的位置，不受滚动条影响。

主要使用场景∶可以在浏览器页面滚动时元素的位置不会改变。

* 以浏览器可视窗口为参照点移动元素

* 添加固定定位后，原来的位置不再占用(脱标)



## 粘性定位 sticky

粘性定位可以被认为是相对定位和固定定位的混合。

一般跟页面滚动搭配使用

* 以浏览器的可视窗口为参照点移动元素（固定定位特点)
* 粘性定位占有原先的位置（不脱标，相对定位特点)
* 必须添加top，left，right，bottom其中一个才有效



## 定位叠放次序

当盒子相互重叠时，可以使用z-index来设置层级

* 只有定位的元素才有z-index

* 数字越大，越靠上
* 若层级相同，按书写顺序，后面的在上

| 样式    | 样式值              | 说明    |
| ------- | ------------------- | ------- |
| z-index | 整数(可0可负)，auto | z轴层级 |







# 字体图标

http://icomoon.io

[阿里巴巴矢量图标库](https://www.iconfont.cn/) 

阿里巴巴矢量图库使用步骤：

1.在网站中挑选图标并下载

2.解压后把文件夹中的css和ttf文件放入项目中

3.引入css文件 `<link rel="stylesheet" href="css/iconfont.css"/>` 

4.将css文件中ttf的路径修改正确

5.通过设置元素的class来引用图标 `<span class="iconfont icon-biaoji"></span>` 





# 过渡动画

过渡动画:是从一个状态渐渐的过渡到另外—个状态，通常和`:hover`一起使用

```css
transition: 要过渡的属性 花费时间 运动曲线 何时开始;/*改变过个属性后面加逗号*/
如：
div{
    ...
    transition: width 1s, height .5s;
}
div:hover{
    width:400px;
    height: 200px;
}
```

* 属性：想要变化的css属性，宽度高度背景颜色内外边距都可以。如果想要所有的属性都变化过渡，写一个`all`就可以。
* 花费时间：单位为秒,且必须写单位，如`0.5s` 
* 运动曲线：默认是`ease` （可省略）

![image-20211204181804116](https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20211204181804116.png) 

* 何时开始：延迟触发时间，单位是秒且必须写单位，默认是`0s` （可省略）



# transform样式

css3样式。支持移动，缩放，旋转操作。

* 优点：不会影响其他盒子

| 样式             | 样式值                                     | 说明                           |
| ---------------- | ------------------------------------------ | ------------------------------ |
| transform        | translate(x,y)，scale(x,y)，totate(n)      | 对元素进行平移，旋转，缩放操作 |
| transform-origin | x y空格隔开。可以是 像素，百分比，方位名词 | 改变缩放或旋转的中心           |

综合写法

```css
transform: translate() rotate() scale();
其顺序会影响转换的效果
当同时有位移和其他属性的时候，记得要将位移放到最前
```





## 2D转换

### 移动 translate

让元素在平面内平移

* translate对于行内元素无效

| 函数           | 函数值       | 说明                                                         |
| -------------- | ------------ | ------------------------------------------------------------ |
| translate(x,y) | 像素，百分比 | 向X轴方向移动x像素，向Y轴方向移动y像素。若参数为百分比，则移动的距离以自身大小为参考 |
| translateX(n); | 像素，百分比 | 向X轴方向移动n像素。若参数为百分比，则移动的距离以自身大小为参考 |
| translateY(n); | 像素，百分比 | 向Y轴方向移动n像素。若参数为百分比，则移动的距离以自身大小为参考 |



### 旋转 rotate

让元素在平面内顺时针或逆时针旋转。

* 默认旋转的中心点是元素的中心点(50%, 50%)

| 函数      | 函数值        | 说明                                     |
| --------- | ------------- | ---------------------------------------- |
| rotate(n) | 度数(单位deg) | 角度为正时顺时针旋转，为负时，逆时针旋转 |



### 缩放 scale

让元素放大和缩小

* 默认缩放的中心点是元素的中心点(50%, 50%)

| 函数       | 函数值 | 说明                 |
| ---------- | ------ | -------------------- |
| scale(x,y) | 数字   | 宽放缩x倍，高放缩y倍 |





## 3D转换

### 三维坐标系

* x轴 ：水平向右    右边是正值，左边是负值
* y轴 ：垂直向下    下面是正值，上面是负值
* z轴 ：垂直屏幕    **往外面是正值，往里面是负值** 



### 移动 translate3d

| 函数               | 函数值       | 说明                 |
| ------------------ | ------------ | -------------------- |
| translate3d(x,y,z) | 像素，百分比 | z轴要用像素单位移动  |
| translateZ(n)      | 像素         | 元素向z轴移动n个像素 |



### 透视 perspective

* 如果想要在网页产生3D效果需要透视(理解成3D物体投影在2D平面内)。
* 模拟人类的视觉位置，可认为安排一只眼睛去看
* 透视我们也称为视距∶视距就是人的眼睛到屏幕的距离
* 距离视觉点越近的在电脑平面成像越大，越远成像越小
* 透视的单位是像素
* **透视写在被观察元素的父盒子上面** 

![image-20220110214133759](https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20220110214133759.png)



| 样式        | 样式值 | 说明              |
| ----------- | ------ | ----------------- |
| perspective | 像素   | 视距，如图所标的d |

 

### 旋转 rotate3d

3D旋转指可以让元素在三维平面内沿着x轴，y轴，z轴或者自定义轴进行旋转。

| 函数              | 函数值                           | 说明                |
| ----------------- | -------------------------------- | ------------------- |
| rotateX(n)        | 度数(单位deg)                    | 沿x轴旋转n度        |
| rotateY(n)        | 度数(单位deg)                    | 沿y轴旋转n度        |
| rotateZ(n)        | 度数(单位deg)                    | 沿z轴旋转n度        |
| rotate3d(x,y,z,n) | x,y,z是数字构成空间向量，n是度数 | 沿着自定义轴旋转n度 |



### 3D呈现 transform-style

* 控制子元素是否开启三维立体环境
* **代码写给父级**，但是影响的是子盒子

| 样式            | 样式值            | 说明                                     |
| --------------- | ----------------- | ---------------------------------------- |
| transform-style | flat, preserve-3d | 是否开启三维立体环境，默认是`flat`不开启 |







# 动画

动画( animation）是CSS3中具有颠覆性的特征之一，可通过设置多个节点来精确控制一个或一组动画，常用来实现复杂的动画效果。

相比较过渡，动画可以实现更多变化，更多控制，连续自动播放等效果

## 用keyframes定义动画

* `0%`是动画的开始，`100%`是动画的完成。这样的规则就是动画序列。
* 动画是使元素从一种样式逐渐变化为另一种样式的效果。可以改变任意多的样式任意多的次数。
* 用百分比来规定变化发生的时间，或用关键词"`from`"和 "`to`”，等同于`0%`和`100%`。
* 百分比要是整数

```css
@keyframes 动画名称{
	0%{
		样式描述1
	}
    ...
	100%{
		样式描述2
	}
}
```





## 使用动画

| 样式                      | 样式值                                                       | 说明                                            |
| ------------------------- | ------------------------------------------------------------ | ----------------------------------------------- |
| animation-name            | 动画名称                                                     | 选定要执行的动画，**必要属性**                  |
| animation-duration        | 时间(秒s)                                                    | 设定动画执行时间，**必要属性**                  |
| animation-timing-function | 速度曲线                                                     | 动画的速度曲线，默认是 `ease`                   |
| animation-delay           | 时间(秒s)                                                    | 动画何时开始，默认是`0`                         |
| animation-iteration-count | 数字, infinite                                               | 动画被播放的次数，默认是`1`                     |
| animation-direction       | normal, alternate                                            | 规定动画是否在下一周期逆向播放，默认是 `normal` |
| animation-play-state      | running, pause                                               | 动画是否运行或暂停                              |
| animation-fill-mode       | backwards, forwards                                          | 动画结束后状态(回来或停止)，默认是`backwards`   |
| animation                 | 动画名称 持续时间 运动曲线 何时开始 播放次数 是否反方向 动画结束状态 | 合写形式                                        |









# 移动web

## css初始化

初始化推荐使用 normalize.css

[官网地址](http://necolas.github.io/normalize.css) 





## 视口

视口（viewport ）就是浏览器显示页面内容的屏幕区域。视口可以分为布局视口、视觉视口和理想视口

### 布局视口

一般移动设备的浏览器都默认设置了一个布局视口，用于解决早期的PC端页面在手机上显示的问题。

iOS,Android基本都将这个视口分辨率设置为980px，所以PC上的网页大多都能在手机上呈现，只不过元素看上去很小，一般默认可以通过手动缩放网页。

![image-20220112132810221](D:\笔记\学习笔记\image\image-20220112132810221.png)



### 视觉视口

字面意思，它是用户正在看到的网站的区域。注意∶是网站的区域。

我们可以通过缩放去操作视觉视口，但不会影响布局视口，布局视口仍保持原来的宽度。

![image-20220112133016371](D:\笔记\学习笔记\image\image-20220112133016371.png)

### 理想视口

为了使网站在移动端有最理想的浏览和阅读宽度而设定

理想视口，对设备来讲，是最理想的视口尺寸

需要手动添写meta视口标签通知浏览器操作

meta视口标签的主要目的:布局视口的宽度应该与理想视口的宽度一致，简单理解就是设备有多宽，我们布局的视口就多宽



### meta视口标签

写在head标签里

```css
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0"/>
```

| 属性           | 属性值       | 说明             |
| -------------- | ------------ | ---------------- |
| width          | device-width | 视口宽度         |
| initial-scale  | 数字         | 初始缩放比       |
| maximum-scale  | 数字         | 最大缩放比       |
| minnimum-scale | 数字         | 最小缩放比       |
| user-scalable  | yes, no      | 用户是否可以缩放 |





## 二倍图

**如果直接将图片显示在手机上，则图片会模糊。**

需要准备一个长宽都是两倍的图片再将其长宽缩小至一半来显示。

如：需要一个50px * 50px的图片显示，则需要准备一个100px * 100px的图片，再在样式里修改width为50px，height为50px





##  特殊样式

```css
点击高亮清除
-webkit-tap-highlight-color: transparent;

在移动端浏览器默认的外观在ios上加上这个属性才能给按钮和输入框自定义样式
-webkit-appearance: none;

禁用长按页面时的弹出菜单
-webkit-touch-callout: none;
```





# 媒体查询

媒体查询( Media Query ）是CSS3新语法。

使用@media查询，可以针对不同的媒体类型定义不同的样式。**@media可以针对不同的屏幕尺寸设置不同的样式**

## 语法

```css
@media 媒体类型 and|not|only (媒体特性) {
	CSS-Code;
}

and：可以将多个媒体特性连接到一起
not：排除某个媒体类型
only：指定某个特定的媒体类型

例：
/* 在屏幕上，且最大宽度小于等于800像素时，背景颜色设置为蓝色 */
@media screen and (max-width: 800px) {
	body {
		background-color: blue;
	}
}
```





## 媒体类型

将不同的终端设备划分成不同的类型，称为媒体类型

| 值        | 说明                               |
| --------- | ---------------------------------- |
| all       | 用于所有设备                       |
| print     | 用于打印机和打印预览               |
| **scree** | 用于电脑屏幕，平板电脑，智能手机等 |





## 媒体特性

每种媒体类型都具体各自不同的特性，根据不同媒体类型的媒体特性设置不同的展示风格。

| 值        | 说明                               |
| --------- | ---------------------------------- |
| width     | 定义输出设备中页面可见区域的宽度   |
| min-width | 定义输出设备中页面最小可见区域宽度 |
| max-width | 定义输出设备中页面最大可见区域宽度 |





## 引入资源

当样式比较繁多的时候，我们可以针对不同的媒体使用不同stylesheets

原理：直接在link中判断设备的尺寸，然后引用不同的css文件

```css
<link rel="stylesheet" media="媒体类型 and|not|only (媒体特性)" href="xxx.css"/>
```





# 流式布局（百分比布局）

通过**盒子的宽度设置成百分比来根据屏幕的宽度来进行伸缩**，不受固定像素的限制，内容向两侧填充。

流式布局方式是移动web开发使用的比较常见的布局方式。

为了合理显示，可以设置最大和最小宽度

| 样式      | 样式值 | 说明     |
| --------- | ------ | -------- |
| max-width | 像素   | 最大宽度 |
| min-width | 像素   | 最小宽度 |









# flex布局（弹性布局）

flex是 flexible Box的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性，任何一个容器都可以指定为flex布局。

* 当我们为父盒子设为flex布局以后，子元素的float、clear和vertical-align属性将失效。
* 采用Flex布局的元素，称为Flex容器( flex container )，简称"容器"。它的所有子元素自动成为容器成员，称为Flex项目( flex item )，简称"项目"。

```css
父盒子需要设定布局方式
display:flex;
```

## 常见父属性

| 样式            | 样式值                                        | 说明                                                  |
| --------------- | --------------------------------------------- | ----------------------------------------------------- |
| flex-direction  | [主轴和侧轴](#主轴和侧轴)                     | 设置主轴方向                                          |
| flex-wrap       | nowrap(默认), wrap                            | 设置子元素是否换行                                    |
| justify-content | [主轴上的元素排列方式](#主轴上的元素排列方式) | 设置主轴上的子元素排列方式                            |
| align-content   | [侧轴上的元素排列方式](#侧轴上的元素排列方式) | 设置侧轴上的子元素的排列方式（多行）                  |
| align-items     | [侧轴上的元素排列方式](#侧轴上的元素排列方式) | 设置侧轴上的子元素的排列方式（单行）                  |
| flex-flow       | 主轴方向 和 是否换行                          | 复合属性，相当于同时设置了flex-direction 和 flex-wrap |





## 主轴和侧轴

元素是跟着主轴来排列的

* 默认主轴方向就是x轴方向，水平向右
* 默认侧轴方向就是y轴方向，水平向下

![image-20220112151335119](https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20220112151335119.png)

可以通过`flex-direction`样式改变主轴的方向，剩下的就是侧轴

| 属性值         | 说明             |
| -------------- | ---------------- |
| row            | 从左到右（默认） |
| row-reverse    | 从右到左         |
| column         | 从上到下         |
| column-reverse | 从下到上         |





## 主轴上的元素排列方式

可以通过设置`justify-content`样式来设置主轴上元素的排列方式

| 属性值        | 说明                       |
| ------------- | -------------------------- |
| flex-start    | 从头部开始排列（默认）     |
| flex-end      | 从尾部开始排列             |
| center        | 在主轴居中对齐             |
| space-around  | 平分剩余空间               |
| space-between | 先两边贴边，再平分剩余空间 |





## 侧轴上的元素排列方式

可以通过设置`align-content`和`align-items`样式来设置侧轴上元素的排列方式

| 属性值        | 说明                                          |
| ------------- | --------------------------------------------- |
| flex-start    | 从头部开始排列（align-content默认）           |
| flex-end      | 从尾部开始排列                                |
| center        | 在侧轴居中对齐                                |
| stretch       | 拉伸（align-items默认，注意子盒子不要给高度） |
| space-around  | 平分剩余空间                                  |
| space-between | 先两边贴边，再平分剩余空间                    |





## 常见子属性

| 样式       | 样式值             | 说明                            |
| ---------- | ------------------ | ------------------------------- |
| flex       | 数字               | 定义分配剩余空间的份数          |
| align-self | 在侧轴上的排列方式 | 设置自己在侧轴上的排列方式      |
| order      | 数字(可负)         | 排列顺序（越小越靠前，默认是0） |





# rem适配布局

通过rem + 媒体查询 可以实现元素根据屏幕尺寸的变化动态变化

## rem单位

rem (root em)是一个相对单位，类似于em , em是父元素字体大小。

不同的是**rem的基准是相对于html元素的字体大小**。

比如，根元素( html)设置font-size=12px;非根元素设置width.2rem;则换成px表示就是24px





# 响应式布局

原理：就是使用[媒体查询](#媒体查询)针对不同宽度的设备进行布局和样式的设置，从而适配不同设备的目的。

## 响应式尺寸划分

| 设备划分                 | 尺寸区间       |
| ------------------------ | -------------- |
| 超小屏幕（手机）         | < 768px        |
| 小屏设备（平板）         | 768px ~ 992px  |
| 中等屏幕（桌面显示器）   | 992px ~ 1200px |
| 宽屏设备（大桌面显示器） | \>= 1200px     |

1



## 响应式布局容器

响应式需要一个父级做为布局容器，来配合子级元素来实现变化效果。
原理就是在不同屏幕下，通过[媒体查询](#媒体查询)来改变这个布局容器的大小，再改变里面子元素的排列方式和大小,从而实现不同屏幕下，看到不同的页面布局和样式变化。

| 设备划分                 | 尺寸区间       | 常见宽度设置 |
| ------------------------ | -------------- | ------------ |
| 超小屏幕（手机）         | < 768px        | 100%         |
| 小屏设备（平板）         | 768px ~ 992px  | 750px        |
| 中等屏幕（桌面显示器）   | 992px ~ 1200px | 970px        |
| 宽屏设备（大桌面显示器） | \>= 1200px     | 1170px       |

```css
<div class="container"> </div> 布局容器

.container {
	margin: 0 auto;
}
/* 超小屏幕 */
@media screen and (max-width: 767px) {
	.container {
		width: 100%;
	}
/* 小屏设备 */
@media screen and (min-width: 768px) {
	.container {
		width: 750px;
	}
}
/* 中等屏幕 */
@media screen and (min-width: 992px) {
	.container {
		width: 970px;
	}
}
/* 宽屏设备 */
@media screen and (min-width: 1200px) {
	.container {
		width: 1170px;
	}
}
```







# vw/vh

vw/vh是一个相对单位（类似em和rem相对单位)

vw是：viewport width 视口宽度单位，**1vw = 1/100视口宽度** 

vh是： viewport height 视口高度单位，**1vh = 1/100视口高度** 





# Less

CSS代码冗余度高，不好维护，没有计算能力。于是出现了Less

Less ( Leaner Style Sheets）是一门CSS扩展语言，也成为CSS预处理器。它在CSS的语法基础之上，引入了变量，Mixin(混入），运算以及函数等功能，大大简化了CSS的编写，并且降低了CSS的维护成本。

[Less中文网址](http://lesscss.cn) 

## Less使用

1. 新建一个后缀名为`.less`的文件，在这个less文件里面书写less语句。
2. 把我们的less文件，编译生成为css文件。编译Less需要安装插件 [HBuilderX Less编译插件](https://ext.dcloud.net.cn/plugin?id=2031) 
3. 引入css文件





## Less变量

通常存储颜色或大小，方便后续维护

### 定义

* 大小写敏感
* 不能以数字开头
* 不能包含特殊字符

```less
@变量名:值;

@mainColor:red;
```



### 使用

```less
直接使用 @变量名 即可

body {
    background-color: @mainColor;
}
```





## Less嵌套

子元素的样式可以直接写在父元素的样式里面

* 如果有伪类、伪元素、交集选择器，内层选择器前面需要加`&`符号

例：

html代码：

```html
<div class="header">
	<a href="#">文字</a>
</div>
```

css代码：

```css
.header {
	width: 200px;
	height: 200px;
	background-color: pink;
}

.header a {
	color: red;
}

.header a:hover {
	color: blue;
}
```

less代码：

```less
.header {
	width: 200px;
	height: 200px;
	background-color: pink;
	a {
		color: red;
        &:hover {
            color: blue;
        }
	}
}
```





## Less运算

Less提供了加(`+`)、减(`-`)、乘(`*`)、除(`/` )算术运算。任何数字、颜色或者变量都可以参与运算。

* 运算符左右两侧必须加空格
* 两个数参与运算，单位以第一个的单位为准



# Bootstrap

Bootstrap来自Twitter，是目前最受欢迎的前端框架。Bootstrap是基于HTML、CSS和JAVASCRIPT的，它简洁灵活，使得Web开发更加快捷。

[中文官网](http://www.bootcss.com) 

## 使用

1. 创建文件夹结构（在`index.html`同级目录创建`bootstrap`文件夹）
2. 下载bootstrap，解压后放入`bootstrap`文件夹
3. 引入.css样式（其实还有.js文件）
4. 根据官方文档选择想要的样式添加即可





## 布局容器

Bootstrap需要为页面内容和栅格系统包裹一个`.container`容器，Bootstarp预先定义好了两个这种类，根据需要在容器加上对应的类即可

* `container` ：响应式布局容器，将其平均划分为了**12**等份
* `container-fluid`：流式布局容器，适合单独做移动端开发





## 响应式工具

为了加快对移动设备友好的页面开发工作，利用媒体查询功能，并使用这些工具类可以方便的针对不同设备展示或隐藏页面内容。

只需要在元素上添加相应的类即可

|    类名    | 超小屏 | 小屏 | 中屏 | 大屏 |
| :--------: | :----: | :--: | :--: | :--: |
| hidden-xs  |  隐藏  | 可见 | 可见 | 可见 |
| hidden-sm  |  可见  | 隐藏 | 可见 | 可见 |
| hidden-md  |  可见  | 可见 | 隐藏 | 可见 |
| hidden-lg  |  可见  | 可见 | 可见 | 隐藏 |
| visible-xs |  可见  | 隐藏 | 隐藏 | 隐藏 |
| visible-sm |  隐藏  | 可见 | 隐藏 | 隐藏 |
| visible-md |  隐藏  | 隐藏 | 可见 | 隐藏 |
| visible-lg |  隐藏  | 隐藏 | 隐藏 | 可见 |





## 栅格系统

栅格系统用于通过一系列的行( row )与列( column )的组合来创建页面布局，内容就可以放入这些创建好的布局中

### 类前缀

Bootstrap的`container`容器已经平均划分为了12等份，所以只需要将其分配到子元素上即可，而每个子元素也被分为了12等份

实现列的平均划分需要给列添加**类前缀**：`col-类型-份数` 

* `xs，extra small`：超小
* `sm，small`：小
* `md，medium`：中等
* `lg，large`：大

示例：

```html
<div class="container">
	<div class="row">
		<div class="col-lg-5">1</div>
		<div class="col-lg-3">2</div>
		<div class="col-lg-2">3</div>
		<div class="col-lg-2">4</div>
	</div>
</div>
```



### 列偏移

因为父盒子的分数是从左到右分配的，若要实现中间空一些格子，则需要给元素添加列偏移，即让元素向右移动多少份

* 原理其实就是给元素添加一个左侧的margin值

将需要偏移的元素加上类：`col-类型-offset-偏移份数`即可



### 列排序

可以将元素**向右推**若干份数，**向左拉**若干份数，以此实现调整元素顺序

向右推：`col-类型-push-份数` 

向左拉：`col-类型-pull-份数` 





# 奇技淫巧

## 三角形

### 效果：

![image-20211204114010167](https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20211204114010167.png)

### 代码：

```css
#sjx {
	width: 0;
	height: 0;
	line-height: 0; /*兼容性*/
	font-size: 0;   /*兼容性*/
	border: 50px solid transparent;
	border-left-color: #333333;
}
<div id="sjx"></div>
```



### 效果：

![image-20211204123042742](https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20211204123042742.png)

### 代码：

```css
#sjx {
	width: 0;
	height: 0;
	border-color: transparent red transparent transparent;
	border-style: solid;
	border-width: 22px 8px 0 0;
}
```



## 三角箭头

### 效果：

![image-20220109204948349](https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20220109204948349.png)

### 代码：

```css
#jiantou {
	position: absolute;
	top: 0;
	right: 0;
	width: 10px;
	height: 10px;
	border-right: 1px solid #000;
	border-bottom: 1px solid #000;
	transform: rotate(45deg);
}
```

