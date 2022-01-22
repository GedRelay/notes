

# AJAX

全称 Asynchronous JavaScript And XML，就是异步的JS和XML

AJAX 最大的优点是在不重新加载整个页面的情况下，可以与服务器交换数据并更新部分网页内容。

## 给服务器发送GET请求

1. 创建xhr对象
2. 使用`open()`方法绑定api
3. 使用`send()`方法发送请求
4. 为xhr绑定`onreadystatechange`事件，当`xhr.readyState`为`4`且响应码为`2`开头时处理结果

```js
const btn = document.getElementById("send");
const resultBox = this.document.getElementById("result");

// 当鼠标点击按钮时，向服务器发送get请求
btn.addEventListener("click",function(){
    // 1.创建对象
    const xhr = new XMLHttpRequest();
    // 2.初始化，设置请求方法和url
    xhr.open("GET","http://127.0.0.1:8000/server?a=100&b=200&c=300");// url后可以带上参数
    // 3.发送
    xhr.send();
    // 4.事件绑定 处理服务端返回的结果
    xhr.onreadystatechange = function(){
        if(xhr.readyState === 4){
            if(xhr.status >= 200 && xhr.status <300){
                //设置result的文本
                resultBox.innerHTML = xhr.response;
            }
            else{
                console.log("响应失败，状态码：" + xhr.status);
            }
        }
    }
});
```

### xhr对象

| 属性/方法                       | 说明                                         |
| ------------------------------- | -------------------------------------------- |
| xhr.status                      | 状态码                                       |
| xhr.statusText                  | 状态字符串                                   |
| xhr.response                    | 响应体                                       |
| xhr.getAllResponseHeaders()     | 返回所有响应头                               |
| xhr.responseType                | 响应体格式，改为"json"可以自动解析为json格式 |
| xhr.timeout                     | 超时时间，规定时间未得到结果则会触发超时事件 |
| xhr.ontimeout = function(){...} | 超时事件                                     |
| xhr.onerror= function(){...}    | 网络异常事件                                 |
| xhr.abort()                     | 取消请求                                     |





## 发送POST请求

```js
// 当鼠标移上resultBox时，发送post请求
resultBox.addEventListener("mouseover", function () {
    const xhr = new XMLHttpRequest();
    xhr.open("POST", "http://127.0.0.1:8000/server");
    xhr.setRequestHeader("Content-Type","application/x-www-form-urlencoded");// 设置请求头
    xhr.send("a=100&b=200&c=300");// 里面写要发送给服务器的数据
    xhr.onreadystatechange = function () {
        if (xhr.readyState === 4) {
            if (xhr.status >= 200 && xhr.status < 300) {
                resultBox.innerHTML = xhr.response;
            }
        }
    }
});
```





## jQuery中的AJAX

```js
// 1.单独写法
$.get(url,[data],[callback],[type]);
$.post(url,[data],[callback],[type]);
url:请求的地址
data:请求携带的参数
callback:载入成功时回调函数
type:设置返回内容的格式,'xml','html','script','json','text','_default'

// 2.通用型方法
$.ajax({
    url: xxx,
    timeout: xxx,
    data: xxx,
    headers:{
        key:val,
    },
    type: xxx,
    dataType: xxx,
    success: function(data){
        ...
    },
    error: function(){
        ...
    }
});
url:请求的地址
timeout:超时时间(毫秒)
data:请求携带的参数
headers:请求头
type:请求类型，"GET","POST"
dataType:返回内容的格式,'xml','html','script','json','text','_default'
success:请求成功后的回调函数
error:请求失败后的回调函数
```

示例：

```js
$('button').eq(0).click(function () {
    $.get("http://127.0.0.1:8000/jquery-server", { a: 100, b: 200 }, function (data) {
        console.log(data);//这是服务器返回的信息
    }, "json");
});
```

```js
$('button').eq(0).click(function () {
    $.ajax({
        url: "http://127.0.0.1:8000/jquery-server",
        data: { a: 100, b: 200 },
        timeout: 2000,
        type: "GET",
        dataType: "json",
        success: function (resdata) {
            console.log(resdata);
        },
        error: function(){
            console.log("出错了");
        }
    });
});
```













