# jQuery

jQuery是一个js库，就是为了快速方便的操作DOM，里面基本都是函数(方法)。

* jQuery支持链式编程哦！！！！！

## 安装和引用

1. 去[官方网站](https://jquery.com)将jQuery代码复制保存为js文件
2. 在html中引入js文件 

当然也可以直接引用[在线版本的jQuer](https://staticfile.org/) 

```html
<script src="https://cdn.staticfile.org/jquery/3.4.1/jquery.min.js"></script>
```





## 页面DOM加载完毕再去执行js代码

相当于原生js的DOMContentLoaded事件

```javascript
$(function(){
    js代码;
})
```





## 顶级对象$

\$是jQuery的顶级对象，相当于原生JavaScript中的window。

\$是jQuery的别称，在代码中可以使用jQuery代替\$，但一般为了方便，通常都直接使用\$。

当然也可以自定义前缀：`var ged = $.noConflict();` ，此时就可以用ged来代替$和jQuery





## jQuery对象和DOM对象互转

1. DOM对象转换为jQuery对象：`$(DOM对象)` 
2. jQuery对象转换为DOM对象：
   1. `jQuery对象[index]` 
   2. `jQuery对象.get(index)` 





## jQuery选择器

用来获取元素

```js
$("选择器")
//里面选择器直接写CSS选择器即可，但是要加引号
```

注意：以下选择器都可以混合使用

### css选择器

| 名称       | 用法              |
| ---------- | ----------------- |
| ID选择器   | $("#id")          |
| 全选择器   | $('*')            |
| 类选择器   | $(".class")       |
| 标签选择器 | $("tag")          |
| 并集选择器 | $("tag1,tag2,..") |
| 交集选择器 | $("li.current")   |
| 子代选择器 | $("ul>li")        |
| 后代选择器 | $("div span")     |



### 筛选选择器

| 语法       | 用法           | 说明                     |
| ---------- | -------------- | ------------------------ |
| :first     | $("div:first") | 第一个元素               |
| :last      | $("div:last")  | 最后一个元素             |
| :eq(index) | $("div:eq(2)") | 第index个元素（从0开始） |
| :odd       | $("div:odd")   | 所有奇数位置元素         |
| :even      | $("div:even")  | 所有偶数位置元素         |



### 筛选方法

| 方法                 | 说明                                 |
| -------------------- | ------------------------------------ |
| $.parent()           | 查找父级                             |
| $.children("选择器") | 在下一级元素中选择                   |
| $.find("选择器")     | 在子代中选择                         |
| $.siblings("选择器") | 查找兄弟节点，不包括自己             |
| $.nextAll()          | 查找当前元素之后的所有同辈元素       |
| $.prevAll()          | 查找当前元素之前的所有同辈元素       |
| $.hasClass("类名")   | 检查当前元素是否有特定类，有返回true |
| $.eq(index)          | 第index个$元素（从0开始）            |





## 属性操作

| 方法                                  | 说明                                                  |
| ------------------------------------- | ----------------------------------------------------- |
| $.index()                             | 返回当前元素的下标                                    |
| $.css("样式")                         | 返回该样式的值                                        |
| $.css("样式", "样式值")               | 设置元素样式（值是数字可以不用加引号）                |
| $.css({样式1:值1, 样式2:值2, ...})    | 修改多个样式，样式和值可以不用加引号                  |
| $.addClass("类名")                    | 添加类                                                |
| $.removeClass("类名")                 | 删除类                                                |
| $.toggleClass("类名")                 | 切换类，若有则移除，若没有则添加                      |
| $.prop("固有属性")                    | 返回该固有属性的值                                    |
| $.prop("固有属性", "属性值")          | 设置固有属性值                                        |
| $.attr("属性")                        | 返回属性值                                            |
| $.attr("属性","属性值")               | 设置属性值                                            |
| $.data("数据名","数据值")             | 在元素上存储数据，但并不会显示                        |
| $.data("数据名")                      | 获取数据值                                            |
| $.html()                              | 获取元素内容，相当于innerHTML                         |
| $.html("内容")                        | 设置元素内容                                          |
| $.text()                              | 获取元素文本内容                                      |
| $.text("文本")                        | 设置元素文本内容                                      |
| $("input").val()                      | 获取表单值                                            |
| $("input").val("内容")                | 设置表单值                                            |
| $.width() / height()                  | 获取宽度和高度值 只算width和height                    |
| $.innerWidth() / innerHeight()        | 获取宽度和高度值 包含padding                          |
| $.outerWidth() / outerHeight()        | 获取宽度和高度值 包含padding、border                  |
| $outerWidth(true) / outerHeight(true) | 获取宽度和高度值 包含padding、border、margin          |
| $.offset()                            | 返回元素距离文档的偏移对象，包括left和top             |
| $.offset(包含left或top的对象)         | 设置偏移                                              |
| $.position()                          | 返回相对于带有定位的父级的偏移坐标对象，包括left和top |
| $.scrollTop() / scrollLeft()          | 设置或获取元素被卷去的头部和左侧                      |





## 动画效果

| 方法                                       | 说明                                       |
| ------------------------------------------ | ------------------------------------------ |
| $.show([speed, [easing], [fn]])            | 元素显示                                   |
| $.hide([speed, [easing], [fn]])            | 元素隐藏                                   |
| $.toggle([speed, [easing], [fn]])          | 元素显示切换                               |
| $.slideDown([speed, [easing], [fn]])       | 下拉滑动                                   |
| $.slideUp([speed, [easing], [fn]])         | 上拉滑动                                   |
| $.slideToggle([speed, [easing], [fn]])     | 滑动切换                                   |
| $.hover([over,] out)                       | 事件切换，鼠标移上移出触发函数             |
| $.stop()                                   | 停止动画，写在动画的前面就是停止上一个动画 |
| $.animate(params, [speed], [easing], [fn]) | 自定义动画                                 |

#### 参数说明

`speed`：三种预定速度之一的字符串(“`slow`”,"`normal`",“`fast`”)或表示动画时长的毫秒数值(如:1000)

`easing`：用来指定切换效果，默认是“`swing`”，可用参数“`linear`” 

`fn`：回调函数，在动画完成时执行的函数，每个元素执行一次

`over`：鼠标移到元素上要触发的函数（相当于mouseenter )

`out`：鼠标移出元素要触发的函数（相当于mouseleave )

`params`：想要更改的样式属性，以对象形式（大括号`{}`）传递。





## 遍历元素

```js
// 1.方法一
$("选择器").each(function (index, domEle){
    //index是索引名称
    //domEle是DOM对象元素
})

// 2.方法二
$.each($("选择器"), function(index, domEle){
    。。。
})

// 3.遍历数组
$.each(arr, function(index, domEle){
    。。。
})

// 4.遍历对象
$.each(对象, function(key, val){
    //key是属性名
    //val是属性值
})
```





## 创建元素

```js
$("完整标签")

例：
$("<li>Hello world</li>")
创建一个<li>
```





## 添加元素

需要先创建一个元素再添加

| 方法                      | 说明                 |
| ------------------------- | -------------------- |
| $(父元素).append(新元素)  | 放入元素内部的最后面 |
| $(父元素).prepend(新元素) | 放入元素内部的最前面 |
| $(元素).after(新元素)     | 放入元素的后面       |
| $(元素).before(新元素)    | 放入元素的前面       |





## 删除元素

| 方法       | 说明             |
| ---------- | ---------------- |
| $.remove() | 将本元素删除     |
| $.empty()  | 将子节点全部删除 |
| $.html("") | 清空元素内容     |





## 事件

### 事件注册

```js
// 1.单个事件注册
$().事件类型(function(){...})

// 2.在元素上绑定一个或多个事件处理函数
$().on("事件类型", [子元素选择器], function(){...}) //写了子元素参数就是事件委托
$().on({事件1:function(){...}, 事件2:function(){...}})

$("div").on("mouseover click", function(){...})

$("div").on({
    mouseover: function(){...},
    click: function(){...}
})

// 3.绑定的事件只触发一次
$().one("事件类型", function(){...})
```



### 解绑

```js
// 1.解绑所有事件
$().off()

// 2.解绑指定事件
$().off("事件")

// 3.解绑事件委托
$().off("事件" ,子元素选择器)
```



### 手动触发事件

```js
// 1.简写形式
$().事件()

// 2.trigger()
$().trigger("事件")

// 3.不会触发元素的默认行为
$().triggerHandler("事件")
```




