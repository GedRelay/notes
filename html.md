<p align='center' style='font-size: 100px; color: darkblue;'>HTML</p>

[toc]

# 相关链接

[模板之家](http://www.cssmoban.com/) 

[dowebok网页素材库](https://www.dowebok.com/) 

[bilibili黑马程序员教学](https://www.bilibili.com/video/BV14J4114768?p=1) 

[菜鸟教程](https://www.runoob.com/) 

[W3school](https://www.w3school.com.cn/index.html) 

[阿里巴巴矢量图库](https://www.iconfont.cn/) 









---



# 注释

快捷键：ctrl + /

```html
<!-- 注释内容 -->
```









---



# Emmet语法

帮助快速生成html代码

* 生成标签直接输入标签名按`tab键`即可比如`div`然后`tab键`，就可以生成`<div></div>` 
* 如果想要生成多个相同标签加上`*`就可以了比如`div*3`就可以快速生成3个`div` 
* 如果有父子级关系的标签，可以用`>`比如`ul > li`就可以了
* 如果有兄弟关系的标签，用`＋`就可以了比如`div+p` 
* 如果生成带有类名或者id名字的，直接写`.demo`或者`#two` `tab键`就可以了
* 如果生成的`div`类名是有顺序的，可以用自增符号`$` 
* 如果想要在生成的标签内部写内容可以用`{}`表示

示例：

```html
div.one#two>p{$}*3+span

<div class="one" id="two">
	<p>1</p>
	<p>2</p>
	<p>3</p>
	<span></span>
</div>
```









---



# 特殊字符

在HTML页面中，一些特殊的符号很难或者不方便直接使用，此时我们就可以使用下面的字符来替代。

| 字符     | 描述          | 代码       |
| -------- | ------------- | ---------- |
| &nbsp;   | 空格符        | `&nbsp;`   |
| &lt;     | 小于号        | `&lt;`     |
| &gt;     | 打一会        | `&gt;`     |
| &amp;    | 和号          | `&amp;`    |
| &yen;    | 人民币        | `&yen;`    |
| &copy;   | 版权          | `&copy;`   |
| &reg;    | 注册商标      | `&reg;`    |
| &deg;    | 摄氏度        | `&deg;`    |
| &plusmn; | 正负号        | `&plusmn;` |
| &times;  | 乘号          | `&times;`  |
| &divide; | 除号          | `&divide;` |
| &sup2;   | 平方（上标2） | `&sup2;`   |
| &sup3;   | 立方（上标3） | `&sup3;`   |









---



# HTML基本框架

输入`!`再按`tab键`即可自动生成

```html
<!DOCTYPE html> 文档类型声明标签
<html lang="zh"> 当前文档的显示语言
<head>
	<meta charset="UTF-8"> 字符集
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge"> 要求当前网页使用IE浏览器最高版本的内核来渲染
	<title></title>
</head>
<body>
	
</body>
</html>
```









---



# favicon图标

网页标签前面的图标

```html
<link rel="shortcut icon" href="favicon.icon" type="image/x-icon"/>
```









---



# 格式标签

| 标签         | 说明                                                 |
| ------------ | ---------------------------------------------------- |
| `<h1> </h1>` | 标题标签，有1到6级，数字越小等级越高，一个标题占一行 |
| `<p> </p>`   | 段落标签                                             |
| `<br />`     | 换行                                                 |
| `<hr />`     | 水平线                                               |









---



# 字体标签

| 标签                             | 说明     |
| -------------------------------- | -------- |
| `<strong> </strong>`或`<b> </b>` | 字体加粗 |
| `<em> </em>`或`<i> </i>`         | 斜体     |
| `<del> </del>` 或 `<s> </s>`     | 删除线   |
| `<ins> </ins>` 或 `<u> </u>`     | 下划线   |
| `<sub> </sub>`                   | 下标     |
| `<sup> </sup>`                   | 上标     |









---



# 容器标签

| 标签                    | 说明                 |
| ----------------------- | -------------------- |
| `<div> </div>`          | 容器，一行只能放一个 |
| `<span> </span>`        | 容器，一行可放多个   |
| `<header> </header>`    | 头部标签             |
| `<nav> </nav> `         | 导航标签             |
| `<article> </article> ` | 内容标签             |
| `<section> </section> ` | 定义文档某个区域     |
| `<aside> </aside> `     | 侧边栏标签           |
| `<footer> </footer>`    | 尾部标签             |









---



# 链接标签

| 标签                    | 说明       |
| ----------------------- | ---------- |
| `<img src="图像url" />` | 图像标签   |
| `<a href='url'> </a>`   | 超链接标签 |
| `<iframe> </iframe>`    | 框架标签   |



## a标签

属性：

| 属性   | 属性值       | 说明                                                         |
| ------ | ------------ | ------------------------------------------------------------ |
| href   | 链接         | 必要属性，填写`javascript:void(0);`或者`javascript:;`可以阻止链接跳转 |
| target | 链接打开方式 | `_self`在本窗口打开，为默认值，`_blank`在新窗口打开          |

锚点：

可以在本页中实现跳转到目标内容

* 设置锚点：在目标位置标签中，添加`id`属性
* 锚点链接：在a标签的href属性中，设置属性值为`#id`的形式，如`<a href="#two">第2集</a>` 





## img标签

属性：

| 属性   | 属性值   | 说明                               |
| ------ | -------- | ---------------------------------- |
| src    | 图片路径 | 必要属性                           |
| alt    | 文本     | 当图片不能显示，则显示这个文本     |
| title  | 文本     | 提示文本，鼠标放在图片上显示的文字 |
| width  | 像素     | 图像的宽度                         |
| height | 像素     | 图像的高度                         |
| border | 像素     | 图像的边框粗细                     |





## ifram标签

属性：

| 属性        | 属性值   | 说明               |
| ----------- | -------- | ------------------ |
| src         | 页面链接 | 可以链接到其他页面 |
| href        | 网页链接 | 可以链接到其他网页 |
| frameborder | 数字     | 边框宽度           |









---



# 表格标签

| 标签               | 说明                       |
| ------------------ | -------------------------- |
| `<table> </table>` | 表格标签                   |
| `<thead> </thead>` | 表头区域                   |
| `<tbody> </tbody>` | 表格主体区域               |
| `<tr> </tr>`       | 行                         |
| `<th> </th>`       | 表头单元格，文字会居中加粗 |
| `<td> </td>`       | 单元格                     |

一般框架：

```html
<table>
	<thead>
		<tr>
			<th>表头</th>
            ...
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>内容</td>
            ...
		</tr>
        ...
	</tbody>
</table>
```



## table标签

属性：

| 属性        | 属性值              | 说明                                  |
| ----------- | ------------------- | ------------------------------------- |
| align       | left，center，right | 表格位置                              |
| border      | 数字                | 边框宽度，默认没有边框                |
| cellpadding | 像素值              | 单元边沿与其内容之间的空白，默认1像素 |
| cellspacing | 像素值              | 单元格之间的空白，默认2像素           |
| width       | 像素值或百分比      | 表格宽度                              |
| height      | 像素值或百分比      | 表格高度                              |





## td标签

属性：

| 属性            | 属性值   | 说明           |
| --------------- | -------- | -------------- |
| rowspan         | 数字     | 单元格所占行数 |
| colspan         | 数字     | 单元格所占列数 |
| border-collapse | collapse | 相邻边框合并   |

以此可以做到合并单元格的效果









---



# 列表标签

根据使用情景不同，列表可以分为三大类：无序列表、有序列表和自定义列表。

| 标签          | 说明           |
| ------------- | -------------- |
| `<ul> </ul>`  | 无序列表标签   |
| `<ol> </ol>`  | 有序列表标签   |
| `<li> </li> ` | 列表项         |
| `<dl> </dl>`  | 自定义列表标签 |
| `<dt> </dt>`  | 自定义列表表头 |
| `<dd> </dd>`  | 自定义列表项目 |

一般框架：

```html
<!-- 无序列表 -->
<ul>
	<li>列表项1</li>
	<li>列表项2</li>
	<li>列表项3</li>
	...
</ul>	
<!-- 有序列表 -->
<ol>
	<li>列表项1</li>
	<li>列表项2</li>
	<li>列表项3</li>
	...
</ol>
<!-- 自定义列表 -->
<dl>
	<dt>名字</dt>
	<dd>描述1</dd>
	<dd>描述2</dd>
    ...
</dl>
```

`li` 的`style`属性改为`none`可以去除黑色圆点









---



# 表单标签

表单可以把它范围内的表单元素信息提交给服务器.

| 标签                     | 说明         |
| ------------------------ | ------------ |
| `<form> </form>`         | 表单域标签   |
| `<input type='类型'/>`   | 输入框       |
| `<select> </select>`     | 下拉列表     |
| `<option> </option>`     | 下拉列表选项 |
| `<textarea> </textarea>` | 文本域标签   |
| `<label> </label>`       | 标签         |

一般框架：

```html
<form action="" method="">
	<input type=""/>
	<select>
		<option value =""></option>
		<option value =""></option>
		...
	</select>
	<textarea rows="" cols="">
		...
	</textarea>
</form>
```



## 表单标签通用属性

| 属性         | 属性值    | 说明                           |
| ------------ | --------- | ------------------------------ |
| required     | required  | 内容不能为空，否则提示错误信息 |
| placeholder  | 提示文本  | 提示信息                       |
| autofocus    | autofocus | 页面加载完成自动聚焦元素       |
| autocomplete | off，on   | 显示之前提交过的内容           |
| multiple     | multiple  | 可以多选文件提交               |





## form标签

属性：

| 属性   | 属性值      | 说明                                            |
| ------ | ----------- | ----------------------------------------------- |
| action | url         | 用于指定接收并处理表单数据的服务器程序的url地址 |
| method | get 或 post | 表单数据的提交方式                              |
| name   | 名称        | 设置表单名称                                    |

下拉列表框架：

```html
<select>
	<option value ="1">1</option>
	<option value ="2" selected="selected">2</option>
	<option value ="3">3</option>
    ...
</select>
```





## input标签

属性：

| 属性      | 属性值         | 说明                                 |
| --------- | -------------- | ------------------------------------ |
| type      | text，button等 | 必选属性，input形态                  |
| name      | 名称           | input的名称                          |
| value     | 自定义         | input内的值                          |
| checked   | checked        | 表示被选中，主要针对于单选框和复选框 |
| maxlength | 正整数         | 输入字段的字符最大长度               |



type属性的属性值：

| type属性值 | 说明                                 |
| ---------- | ------------------------------------ |
| text       | 文本框，默认宽度为20个字符           |
| password   | 密码框，里面的字符被隐藏             |
| button     | 按钮                                 |
| number     | 数字框，只能输入数字                 |
| radio      | 单选框，多个单选框的name属性要相同   |
| checkbox   | 复选框                               |
| file       | 包括输入字段和“浏览按钮”，供文件上传 |
| reset      | 重置按钮，会清除表单中的所有数据     |
| submit     | 提交按钮，会把表单数据发送到服务器   |
| image      | 定义图像形式的提交按钮               |
| hidden     | 定义隐藏的输入字段                   |
| email      | 用户只能输入email类型                |
| url        | 用户只能输入url类型                  |
| date       | 日期选择框                           |
| time       | 时间选择框                           |
| month      | 用户只能输入月                       |
| week       | 用户只能输入周                       |
| number     | 用户只能输入数字                     |
| tel        | 手机号码                             |
| search     | 搜索框                               |
| color      | 颜色选择表单                         |





## label标签

`<label>`标签用于绑定一个表单元素当点击`<label>`标签内的文本时，浏览器就会自动将焦点(光标)转到或者选择对应的表单元素上用来增加用户体验.

`for`属性填写所连接标签的`id` 

示例：

```html
<label for="sex">男</label>
<input type="radio" name="sex" id="sex" />
```





## textarea标签

属性：

| 属性 | 属性值 | 说明           |
| ---- | ------ | -------------- |
| cols | 数字   | 每行中的字符数 |
| rows | 数字   | 显示的行数     |









---



# 媒体标签

| 标签                            | 说明     |
| ------------------------------- | -------- |
| `<audio> </audio>`              | 音频标签 |
| `<video> </video>`              | 视频标签 |
| `<source src="资源"> </source>` | 资源标签 |

一般框架：

```html
<audio controls>
  <source src="" >
  <source src="" >
您的浏览器不支持 audio 元素。
</audio>

<video controls>
  <source src="movie.mp4"  type="video/mp4">
  <source src="movie.ogg"  type="video/ogg">
  您的浏览器不支持 HTML5 video 标签。
</video>
```



## audio标签

属性：

| 属性     | 属性值   | 说明                                    |
| -------- | -------- | --------------------------------------- |
| src      | mp3音频  | 所播放的mp3资源                         |
| autoplay | autoplay | 音频就绪后马上播放                      |
| controls | controls | 向用户显示音频控件（比如播放/暂停按钮） |
| loop     | loop     | 音频结束时重新开始播放                  |
| muted    | muted    | 静音                                    |





## video标签

属性：

| 属性     | 属性值   | 说明                                            |
| -------- | -------- | ----------------------------------------------- |
| src      | mp4视频  | 所播放的mp4资源                                 |
| autoplay | autoplay | 视频就绪后马上播放(谷歌浏览器需要设置muted属性) |
| controls | controls | 向用户显示控件，比如播放按钮                    |
| loop     | loop     | 完成播放后再次开始播放                          |
| muted    | muted    | 静音                                            |
| poster   | 图片     | 视频正在下载时显示的图像，直到用户点击播放按钮  |





## source标签

属性:

| 属性 | 属性值                | 说明     |
| ---- | --------------------- | -------- |
| type | audio/mpeg，video/mp4 | 资源类型 |
| src  | 资源                  | 资源链接 |









---

