

# Node.js

Node.js是一个基于Chrome V8引擎的JavaScript运行环境。

* 浏览器是JavaScript的前端运行环境
* Node.js是JavaScript的后端运行环境
* Node.js中无法调用DOM和BOM等浏览器内置API

[官方网站](https://nodejs.org/zh-cn/) 

## 在Node.js环境中执行JS代码

使用cmd执行

```powershell
node js文件的路径
```









---



# 内置模块

## 导入模块

使用`require(模块)`来导入模块。

如果省略了文件的扩展名，则Node.js 会按顺序分别尝试加载以下的文件：

1. 按照确切的文件名进行加载
2. 补全`.js`扩展名进行加载
3. 补全`.json`扩展名进行加载
4. 补全`.node`扩展名进行加载
5. 加载失败，终端报错





## fs文件系统模块

用来操作文件的模块

### 导入fs

```js
const fs = require('fs');
```



### 读取文件

使用`fs.readFile(path[, encoding], callback)`读取文件

* `path`是文件路径，`__dirname`是当前js文件的路径
* `encoding`是读取的编码格式，默认是`utf8` 
* `callback`是回调函数，一般编写读取后执行的代码
* 回调函数有两个参数，`err`是读取失败的信息，`dataStr`是读取成功后文件的文本信息

示例：

```js
const fs = require('fs');
fs.readFile(__dirname + '/test.txt', 'utf8', function(err, dataStr){
	if(err){ // 如果读取成功，err 值为 null
		console.log("读取文件失败！" + err.message);
	}
	else{ // 如果读取失败，dataStr 值为 undefined
		console.log("读取文件成功！" + dataStr);
	}
})
```



### 写文件

使用`fs.writeFile(path, data[, encoding], callback)`写文件（覆盖写）

* `path`是文件路径，`__dirname`是当前js文件的路径
* `data`是写入的内容
* `encoding`是写入文件的编码，默认是`utf8` 
* `callback`是回调函数
* 回调函数有一个参数，`err`表示写入失败的信息

示例：

```js
const fs = require('fs');
fs.writeFile(__dirname + '/test.txt', 'abcd', function(err) {
	if(err){
		console.log("写入失败！" + err.message);
	}
	else{
		console.log("写入成功！");
	}
})
```





## path路径模块

用来处理路径的模块。它提供了一系列的方法和属性，用来满足用户对路径的处理需求。

### 导入path

```js
const path = require('path');
```



### 路径拼接

使用`path.join(path1,path2,...)`来拼接路径，使用`+`来拼接的话可能会出现问题

*  路径中的`../`会抵消前面一层路径
* `__dirname`表示当前js文件的路径

示例：

```js
const path = require('path');
var pathStr = path.join('/a', '/b/c', '../', './d', 'e'); // \a\b\d\e
```



### 解析文件名

使用`path.basename(path[, ext])`方法，可以获取路径中的最后一部分，经常通过这个方法获取路径中的文件名

* `path`是文件路径
* `ext`表示文件扩展名

示例：

```js
const fpath = 'a/b/c/index.html';
var fullName = path.basename(fpath); // index.html
var nameWithoutExt = path.basename(fpath, 'html'); // index
```



### 解析文件扩展名

使用`path.extname(path)`获取文件扩展名

* `path`是文件路径

示例：

```js
var fext = path.extname('a/b/c/index.html'); // .html
```





## http模块

用来创建web服务器的模块

步骤：

1. 导入http模块
2. 创建web服务器实例
3. 为服务器示例绑定request事件，监听客户端的请求
4. 启动服务器

### 导入

```js
const http = require('http');
```



### 创建web服务器实例

```js
const server = http.createServer();
```



### 绑定request事件

```js
server.on('request',(req, res) => {
    // 只要有客户端来请求服务器，就会触发该事件
})
```

#### req

req是请求对象，包含了与客户端相关的数据和属性

| 属性       | 说明                   |
| ---------- | ---------------------- |
| req.url    | 客户端请求的url地址    |
| req.method | 客户端的method请求类型 |

#### res

res是响应对象，可以访问与服务器相关的数据或属性

| 属性/方法              | 说明                                             |
| ---------------------- | ------------------------------------------------ |
| res.end(内容)          | 向客户端发送指定的内容，并结束这次请求的处理过程 |
| res.setHeader(字段:值) | 设置响应头字段信息                               |

```js
// 解决中文乱码问题
res.setHeader("Content-Type","text/html; charset=utf-8");
```



### 启动服务器

```js
// .listen(端口号，回调函数)
server.listen(80,() => {
    //启动服务器后执行的代码
})
```



### 示例

```js
const http = require('http');
const server = http.createServer();

server.on('request',(req, res) => {
    var url = req.url; // 请求的页面地址
	res.setHeader("Content-Type", "text/html; charset=utf-8");
	let econtent = "<h1>404 Not found</h1>"; // 默认的错误页面提示信息
	
	if(url ==="/" || url === "/index.html"){// 首页
		content = "<h1>首页<h1/>";
	}
	else if(url == "/about.html"){// 关于页面
		content = "<h1>关于页面<h1/>";
	}
	res.end(content);//返回页面
})

server.listen(80,() => {
    console.log("server running at http://127.0.0.1");
})
```









---



# 自定义模块

## module对象

在每个.is自定义模块中都有一个module对象，它里面存储了和当前模块有关的信息

```js
console.log(module);

Module {
  id: '.',
  path: 'D:\\0program\\HTML网页开发\\20220109test\\js',
  exports: {},
  filename: 'D:\\0program\\HTML网页开发\\20220109test\\js\\nodeLearn.js',
  loaded: false,
  children: [],
  paths: [
    'D:\\0program\\HTML网页开发\\20220109test\\js\\node_modules',        
    'D:\\0program\\HTML网页开发\\20220109test\\node_modules',
    'D:\\0program\\HTML网页开发\\node_modules',
    'D:\\0program\\node_modules',
    'D:\\node_modules'
  ]
}
```

### exports

在自定义模块中，可以使用module.exports对象，将模块内的成员共享出去，供外界使用。

外界用require()方法导入自定义模块时，得到的就是module.exports所指向的对象。

```js
exports.username = "Ged";
exports.sayHello = function(){
    console.log("Hello!");
}
```





## 包结构

一个规范的包，它的组成结构，必须符合以下3点要求:

* 包必须以单独的目录而存在
* 包的顶级目录下要必须包含`package.json`这个包管理配置文件
* package.json中必须包含`name`，`version`，`main`这三个属性，分别代表包的名字、版本号、包的入口。

$myTool文件夹\begin{cases}\ package.json & （包管理配置文件） \\ index.js & （包的入口文件） \\ README.md & （包的说明文档） \end{cases}$ 

```json
package.json文件内容示例,使用npm init -y可以自动生成

{
    "name": "myFirstTool",
    "version": "1.0.0",
    "main": "index.js",
    "description": "我的第一个工具包",
    "keywords": ["tool", "study", "js"]
    "license": "ISC"
}
```









---



# 第三方模块

搜包：[全球最大的包共享平台](https://www.npmjs.com/) 

下包：在cmd中执行：`npm install 包的完整名字`或者`npm i 包的完整名字`即可下载安装相应的包

卸载包：在cmd中执行：`npm uninstall 包的完整名字` 

查看当前的下包镜像源：`npm config get registry` 

切换下包镜像源：`npm config set registry=https://registry.npm.taobao.org/` 



初次装包完成后，在项目文件夹下多一个叫做`node_modules` 的文件夹和`package-lock.json`的配置文件。

`node modules` 文件夹：用来存放所有已安装到项目中的包。require()导入第三方包时，就是从这个目录中查找并加载包。

`package-lock.json`配置文件：用来记录node_modules目录下的每一个包的下载信息，例如包的名字、版本号、下载地址等。









---



# Express

Express是基于Node.js 平台，快速、开放、极简的Web开发框架。

Express 的作用和Node.js内置的http模块类似，是专门用来创建Web服务器的。

Express本质就是一个npm上的第三方包，提供了快速创建Web 服务器的便捷方法。

[Express中文官网](https://www.expressjs.com.cn/) 

## 安装

```powershell
npm install express
```




