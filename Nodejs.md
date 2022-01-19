

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

## nodemon

可以将node命令替换为nodemon命令，使用nodemon xxx.js 来启动项目。这样做的好处是：代码被修改之后，会被nodemon监听到，从而实现自动重启项目的效果。

### 安装

```js
npm install -g nodemon
```



### 使用

```js
nodemon js文件
```









---



# Express

Express是基于Node.js 平台，快速、开放、极简的Web开发框架。

Express 的作用和Node.js内置的http模块类似，是专门用来创建Web服务器的。

Express本质就是一个npm上的第三方包，提供了快速创建Web 服务器的便捷方法。

[Express中文官网](https://www.expressjs.com.cn/) 

## 安装

```powershell
npm install express@4.17.1
```





## 创建基本的web服务器

```js
const express = require("express");
// 创建web服务器
const app = express();

//调用app.listen(端口号，启动成功后的回调函数)，启动服务器
app.listen(80,() => {
    console.log("express服务器运行于 http://127.0.0.1");
})
```





## 监听请求

通过`app.get()`方法，可以监听客户端的GET请求

通过`app.post()`方法，可以监听客户端的POST请求

```js
//req:请求对象
//res:响应对象
app.get("请求url", function(req, res){
    //处理代码
})


app.get("/user", (req, res) => {
    res.send({ name: "GED", age: 20, gender: "男" })
})

app.post("/user", (req, res) => {
    res.send("请求成功")
})
```

### req

req是请求对象，包含了与客户端相关的数据和属性

| 属性       | 说明                              |
| ---------- | --------------------------------- |
| req.url    | 客户端请求的url地址               |
| req.method | 客户端的method请求类型            |
| req.query  | 发送到服务器的附在url上的静态参数 |
| req.params | url中通`:`匹配到的动态参数        |
| req.body   | 客户端发来的请求体数据            |

```js
// 获取静态参数
app.get("/", (req, res) => {
    // 客户端使用 ?name=Ged&age=20 这种查询字符串形式，发送到服务器的参数
    // 可以通过 req.query.name req.query.age 获取
    console.log(req.query);
})

// 获取动态参数
app.get("/user/:id/:name", (req, res) => {
    // 访问地址：http://127.0.0.1/user/1/Ged
    console.log(req.params);// { id: '1', name: 'Ged' }
})
```



### res

res是响应对象，可以访问与服务器相关的数据或属性

| 属性/方法              | 说明                                             |
| ---------------------- | ------------------------------------------------ |
| res.end(内容)          | 向客户端发送指定的内容，并结束这次请求的处理过程 |
| res.setHeader(字段:值) | 设置响应头字段信息                               |





## 托管静态资源

通过`express.static()`方法可以非常方便地创建一个静态资源服务器

```js
//通过如下代码就可以将public目录下的图片、CSS文件、JavaScript 文件对外开放访问了
app.use(express.static("./public"));

挂载路径前缀
//要访问public文件，则需要在网页路径加上/p才能访问
app.use("/p", express.static("./public"));
```





## 路由

路由指的是客户端的请求与服务器处理函数之间的映射关系。

Express 中的路由分3部分组成，分别是请求的类型、请求的URL地址、处理函数

* 按照定义的先后顺序进行匹配
* 请求类型和请求的URL同时匹配成功，才会调用对应的处理函数

```js
格式
app.METHOD(PATH, HANDLER);
```

### 模块化路由

为了方便对路由进行模块化的管理，Express 不建议将路由直接挂载到app上，而是推荐将路由抽离为单独的模块。

1. 创建路由模块对应的`.js`文件
2. 调用`express.Router()`函数创建路由对象
3. 向路由对象上挂载具体的路由
4. 使用`module.exports`向外共享路由对象
5. 使用`app.use()`函数注册路由模块

示例：

```js
// router.js
// 1.导入express
const express = require("express");

// 2.创建路由对象
const router = express.Router();

// 3.挂载路由
router.get("/user", (req, res) => {
    res.send({ name: "GED", age: 20, gender: "男" });
})

router.post("/user/:id/:name", (req, res) => {
    console.log(req.params);
    res.send(req.params);
})

// 4.向外导出路由对象
module.exports = router;
```

```js
// test.js
const express = require("express");
const app = express();

// 1.导入路由模块
const router = require("./router");
// 2.注册路由模块
app.use(router);

app.use(express.static("./Page"));

//调用app.listen(端口号，启动成功后的回调函数)，启动服务器
app.listen(80, () => {
    console.log("express服务器运行于 http://127.0.0.1");
})
```





## 中间件

中间件(Middleware ) 指业务流程的中间处理环节。

Express的中间件，本质上就是一个function处理函数

中间件函数的形参列表中，**必须包含`next`参数**。而路由处理函数中只包含`req`和`res`。

`next`函数是实现多个中间件连续调用的关键，它表示把流转关系转交给下一个中间件或路由。

**多个中间件之间，共享同一份`req`和`res`**。基于这样的特性，我们可以在上游的中间件中，统一为`req`或`res`对象添加自定义的属性或方法，供下游的中间件或路由进行使用。

<img src="https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20220119163828972.png" alt="image-20220119163828972" style="zoom: 67%;" />

### 定义中间件

```js
const mw = function (req, res, next) {
    console.log("这是一个最简单的中间件函数");
    next();// 中间件业务处理完毕后，必须调用 next() 函数
}
```



### 全局中间件

客户端发起的任何请求，到达服务器之后，都会触发的中间件，叫做全局生效的中间件。

中间件函数在请求的回调函数之前执行

使用`app.use(中间件函数)`注册中间件，可以多次使用`.use()`注册多个中间件，**按照定义的顺序依次调用** 

```js
app.use(function (req, res, next) {
    console.log("这是一个最简单的中间件函数");
    next();// 中间件业务处理完毕后，必须调用 next() 函数
});
```



### 局部生效的中间件

不使用`app.use()`定义的中间件，叫做局部生效的中间件，该中间件只会影响特定路由，不会影响所有路由

```js
app.get("url路径", 中间件函数1, 中间件函数2, ..., 路由函数);

示例：
const mw = function (req, res, next) {
    console.log("这是一个最简单的中间件函数");
    next();// 中间件业务处理完毕后，必须调用 next() 函数
}
app.get("/", mw, function(req, res){
    res.send("Home Page");
});
```



### 监听req的data和end事件

在中间件中，需要监听req对象的data 事件，来获取客户端发送到服务器的数据。

* 如果数据量比较大，无法一次性发送完毕，则客户端会**把数据切割后，分批发送到服务器**。所以data事件可能会触发多次，每一次触发data事件时，获取到数据只是完整数据的一部分，需要**手动对接收到的数据进行拼接**。
* 当请求体数据接收完毕之后，会自动触发req的end事件，因此，可以在req的end事件中，拿到并处理完整的请求体数据。

```js
app.use(function (req, res, next) {
    // 定义变量，原来存储客户端发送过来的请求体数据
    let str = "";
    
    // 监听 req 对象的 data 事件
    req.on("data", (chunk) => {
        str += chunk; //手动拼接数据
    })
    
    // 监听 req 对象的 end 事件
    req.on("end", () => {
        //此时 str 中存放的是完整的请求体数据
        console.log(str);
        req.body = str;// 将数据挂载到req的body属性，给下一个中间件使用
        next();
    })
});
```



### 错误级别中间件

专门用来捕获整个项目中发生的异常错误，从而防止项目异常崩溃的问题

函数的形参有四个，分别是(`err`, `req`, `res`, `next`)

* **错误级别的中间件必须注册在所有路由之后** 
* `next()`可以不调用

```js
app.get("/", (req, res) => {
    throw new Error("服务器内部发生了错误！");// 人为抛出异常
    res.send("Home Page");
});

app.use((err, req, res, next) => {
    console.log("发生了错误" + err.message);
    res.send("Error: " + err.message);
})
```



### Express内置中间件

1. `express.static()`：[快速托管静态资源](#托管静态资源) 
2. `express.json()`：解析 JSON 格式的请求体数据（仅在4.16.0版本之后使用）
3. `express.urlencoded()`：解析 URL-encoded 格式的请求体数据（仅在4.16.0版本之后使用）

#### express.json

```js
app.use(express.json());
app.post("/", (req, res) => {
    console.log(req.body);// 获取JSON格式的表单数据
});
```



#### express.urlencoded

```js
app.use(express.urlencoded({ extended: false }));// 固定格式
app.post("/", (req, res) => {
    console.log(req.body);// 获取URL-encoded格式的表单数据
});
```





## cros跨域资源共享

cors 是 Express的一个第三方中间件。通过安装和配置cors 中间件，可以很方便地解决跨域问题

### 安装中间件

```powershell
npm insatll cors
```



### 使用

```js
const cors = require("cors");
app.use(cors());// 在路由之前配置全局中间件 
```



### 响应头部

CORS 由一系列HTTP响应头组成，这些HTTP响应头决定浏览器是否阻止前端JS代码跨域获取资源。

浏览器的同源安全策略默认会阻止网页“跨域”获取资源。但如果接口服务器配置了CORS相关的HTTP响应头，就可以解除浏览器端的跨域访问限制。

```js
// 1.Access-Control-Allow-Origin 可以指定允许访问该资源的外域URL
res.setHeader("Access-Control-Allow-Origin", "http://abcdef.cn");// 只允许来自http://abcdef.cn的请求
res.setHeader("Access-Control-Allow-Origin", "*");// 任何网站都可以访问

// 2.Access-Control-Allow-Headers 默认情况下，CORS仅支持客户端向服务器发送特定的9个请求头，通过这个可以对其他的请求头进行声明
res.setHeader("Access-Control-Allow-Headers", "Content-Type, X-Custom-Header");

// 3.Access-Control-Allow-Methods 默认情况下，CORS仅支持客户端发起GET、POST、HEAD请求，通过这个可以声明其他请求方式
res.setHeader("Access-Control-Allow-Methods", "POST, GET, DELETE, HEAD");
res.setHeader("Access-Control-Allow-Methods", "*");
```





