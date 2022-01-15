[toc]



# Requests

Requests用来对网站发起请求，可以根据发送的请求获得相应的数据。

对于爬虫来说，除了发送请求获得数据，剩下的就是提取和分析数据。需要用到其他库来完成，如json库，BeautifulSoup库，正则表达式处理等

## 安装

```powershell
pip install requests
```





## 导包

```python
import requests
```





## 通用代码框架

```python
import requests
def getHTMLText(url):
    try:
        r = requests.get(url,timeout=30)
        r.raise_for_status()
        r.encoding = r.apparent_encoding
        return r.text
    except:
        return "爬取失败"

if __name__ == "__main__":
    url="http://www.baidu.com"
    f = open('Html.txt','w')
    f.write(getHTMLText(url))
    f.close()
```





## Response对象的属性

| 属性                | 说明                                                         |
| ------------------- | ------------------------------------------------------------ |
| r.status_code       | HTTP请求的返回状态，200表示成功                              |
| r.text              | HTTP响应内容的字符串形式，即url对应的页面内容                |
| r.encoding          | 从HTTP header中猜测的响应内容编码方式<br />如果header中不存在charset，则认为编码为ISO-8859-1 |
| r.apparent_encoding | 从内容中分析出的响应内容编码方式（备选编码方式）             |
| r.content           | HTTP响应内容的二进制形式                                     |





## 常用方法

| 方法                                            | 说明                                       |
| ----------------------------------------------- | ------------------------------------------ |
| requests.request(method,url,**kwargs)           | 构造一个请求，支撑以下各方法的基础方法     |
| requests.get(url,params=None,**kwargs)          | 获取html网页的主要方法，对应于http的get    |
| requests.head(url,**kwargs)                     | 获取html网页头信息的方法，对应于http的head |
| requests.post(url,data=None,json=None,**kwargs) | 向html网页提交post请求的方法               |
| requests.put(url,data=None,**kwargs)            | 向html网页提交put请求的方法                |
| requests.patch(url,data=None,**kwargs)          | 向html网页提交局部修改请求                 |
| requests.delete(url,**kwargs)                   | 向html网页提交删除请求                     |

**13个kwargs参数**

```python
params:字典或字节序列，作为参数增加到url中
kv={'key1':'value1','key2':'value2'}
r=requests.request('GET','http://python123.io/ws',params=kv)
print(r.url)
https://python123.io/ws?key1=value1&key2=value2
    
data:字典，字节系列或文件对象，作为Request的内容
kv={'key1':'value1','key2':'value2'}
r=requests.request('POST','http://python123.io/ws',data=kv)
body='主体内容'
r=requests.request('POST','http://python123.io/ws',data=body)

json:JSON格式的数据，作为Request的内容
kv={'key1':'value1'}
r=requests.rquest('POST','http://python123.io/ws',json=kv)

headers:字典，HTTP定制头
hd={'user-agent':'Chrome/10'}
r=requests.request('POST','http://python123.io/ws',headers=hd)

cookies:字典或CookieJar，Request中的cookie
    
auth:元祖，支持HTTP认证功能
    
files:字典类型，传输文件
fs={'file':open('data.xls','rb')}
r=requests.request('POST','http://python123.io/ws',file=fs)

timeout:设定超时时间，秒为单位
r=requests.request('GET','http://www.baidu.com',timeout=10)

proxies:字典类型，设定访问代理服务器，可以增加登录认证
pxs={'http':'http://user:pass@10.10.10.1:1234'
    'https':'https://10.10.10.1:4321'}
r=requests.request('GET','http://www.baidu.com',proxies=pxs)

allow_redirects:True/False,默认为True，重定向开关
    
stream:True/False,默认为True，获取内容是否立即下载开关
    
verify:True/False,默认为True，认证SSL证书开关
    
cert:本地SSL证书路径
```





## HTTP协议对资源的操作

| 方法   | 说明                                                      |
| ------ | --------------------------------------------------------- |
| GET    | 请求获取URL位置的资源                                     |
| HEAD   | 请求获取URL位置资源的响应消息报告，即获得该资源的头部信息 |
| POST   | 请求向URL位置的资源后附加新的数据                         |
| PUT    | 请求向URL位置储存一个资源，覆盖原有URL位置的资源          |
| PATCH  | 请求局部更新URL位置的资源，即改变该出资源的部分内容       |
| DELETE | 请求删除URL位置储存的资源                                 |





## 异常

`r.raise_for_status()`  如果不是`200`，产生异常`requests.HTTPError`

| 异常                      | 说明                                        |
| ------------------------- | ------------------------------------------- |
| requests.ConnectionError  | 网络连接错误异常，如DNS查询失败，拒绝连接等 |
| requests.HTTPError        | HTTP错误异常                                |
| requests.URLRequired      | URL缺失异常                                 |
| requests.TooManyRedirects | 超过最大重定向次数，产生重定向异常          |
| requests.ConnectTimeout   | 连接远程服务器超时异常                      |
| requests.Timeout          | 请求URL超时，产生超时异常                   |









---



# Robots协议：

==不想吃牢饭就给我好好看！==（类人行为可不参考robots协议）

robots协议是一种存放于网站根目录下的ASCII编码的文本文件，它通常告诉网络爬虫，此网站中的哪些内容是不应被爬取的，哪些是可以被爬取的。

robots协议并不是一个规范，而只是约定俗成的，所以并不能保证网站的隐私。类似于君子协议。

## 查看网站的robots协议

```python
url/robots.txt
如:哔哩哔哩的robots协议https://www.bilibili.com/robots.txt
        
User-agent: *
Disallow: /include/
Disallow: /mylist/
Disallow: /member/
Disallow: /images/
Disallow: /ass/
Disallow: /getapi
Disallow: /search
Disallow: /account
Disallow: /badlist.html
Disallow: /m/
```





## robots协议基本语法

```python
# 注释，*代表所有，/代表根目录
User-agent：*
Disallow：/
```

| 语法       | 说明                         |
| ---------- | ---------------------------- |
| User-agent | 规定哪些爬虫应该遵守以下规则 |
| Disallow   | 不能爬取的目录               |
| Allow      | 允许爬取的目录               |
| Sitemap    | 告诉爬虫这个页面是网站地图   |









---



# BeautifulSoup

BeautifulSoup用来对html等代码进行解析，将其解析成一棵树状结构的文档，以便能定位分析到想要的数据

## 安装

```powershell
pip install beautifulsoup4 
```





## 导入和使用

```python
from bs4 import BeautifulSoup
soup = BeautifulSoup(文本,'html.parser')

#举例：
import requests
r = requests.get("http://python123.io/ws/demo.html")
demo = r.text
from bs4 import BeautifulSoup
soup = BeautifulSoup(demo,'html.parser')
print(soup.prettify())
```





## Beautiful Soup库解析器

| 解析器           | 使用方法                            | 条件                 |
| ---------------- | ----------------------------------- | -------------------- |
| bs4的HTML解析器  | **BeautifulSoup(mk,'html.parser')** | 安装bs4库            |
| lxml的HTML解析器 | BeautifulSoup(mk,'lxml')            | pip install lxml     |
| lxml的XML解析器  | BeautifulSoup(mk,'xml')             | pip install lxml     |
| html5lib的解析器 | BeautifulSoup(mk,'html5lib')        | pip install html5lib |



## Beautiful Soup类的基本元素

| 基本元素                           | 获取方法   | 说明                                              |
| ---------------------------------- | ---------- | ------------------------------------------------- |
| Tag 标签                           | soup.tag   | 最基本的信息组织单元，分别用<>和</>标明开头和结尾 |
| Name 标签的名字                    | tag.name   | \<p>.....\</p>的名字是'p'                         |
| Attributes 标签的属性              | tag.attrs  | 字典形式组织                                      |
| NavigableString 标签内非属性字符串 | tag.string | <>......</>中的字符串                             |
| Conmment 标签内字符串的注释部分    |            | 一种特殊的Comment类型                             |





## 标签树的遍历

| 属性               | 说明                                                    |
| ------------------ | ------------------------------------------------------- |
| .contents          | 子节点的列表，将 tag 所有儿子节点存入列表               |
| .children          | 子节点的迭代类型，与.contents类似，用于循环遍历儿子节点 |
| .descendants       | 子孙节点的迭代类型，包含所有子孙节点，用于循环遍历      |
| .parent            | 节点的父亲标签                                          |
| .parents           | 节点先辈标签的迭代类型，用于循环遍历先辈节点            |
| .next_sibling      | 返回按照HTML文本顺序的下一个平行节点标签                |
| .previous_sibling  | 返回按照HTML文本顺序的上一个平行节点标签                |
| .next_siblings     | 迭代类型，返回按照HTML文本顺序的后续所有平行节点标签    |
| .previous_siblings | 迭代类型，返回按照HTML文本顺序的前续所有平行节点标签    |





## bs4库的信息检索方法：

| 方法                                     | 说明                                                         |
| ---------------------------------------- | ------------------------------------------------------------ |
| bs.fand_all(name,attrs,recursive,string) | 返回一个列表类型，储存查找的结果bs.find_all('div',class_='job-card-item') |
| bs.find()                                | 搜索且只返回一个结果，字符串类型                             |
| bs.find_parents()                        | 在先辈节点中搜索，列表类型                                   |
| bs.find_parent()                         | 在先辈节点中返回一个结果，字符串类型                         |
| bs.find_next_siblings()                  | 在后续平行节点中搜索，列表类型                               |
| bs.find_next_sibling()                   | 在后续平行节点中返回一个结果，字符串类型                     |
| bs.find_previous_siblings()              | 在前序平行节点中搜索，列表类型                               |
| bs.find_previous_sibling()               | 在前序平行节点中返回一个结果，字符串类型                     |

```yaml
find_all()简化形式:
<tag>(...) 等价于 <tag>.find_all(...)
soup(...) 等价于 soup.find_all(...)
参数解释:
name: 对标签名称的检索字符串
attrs: 对标签属性
recursive: 布尔类型，是否对子孙全部检索，默认为True
string: <>...</>中字符串区域的检索字符串
```









---



# Selenium

Selenium是一个用于测试网站的自动化测试工具，可以用于爬虫，操作比request简单，但是速度比request慢。

其原理就是直接控制浏览器自动完成想要的操作。

[教程](https://blog.csdn.net/weixin_36279318/article/details/79475388) 

## 安装

```cmd
pip install Selenium
除此之外还要下载一个chromedriver，添加至系统path环境变量
```





## 导包

```python
from selenium import webdriver
```





## 获取页面

```python
from selenium import webdriver
browser = webdriver.Chrome('E:\\chromeDriver\\chromedriver.exe')

browser.get('http://www.baidu.com') #访问网站
html = browser.page_source #获取返回页面
cookies = browser.get_cookies() #获取cookies
bs = BeautifulSoup(html,'html.parser') #解析
print(bs.prettify())
```





## 定位元素

| 定位一个元素(定位多个元素则换成elements) | 含义                  |
| ---------------------------------------- | --------------------- |
| find_element_by_id                       | 通过元素id定位        |
| find_element_by_name                     | 通过元素name定位      |
| find_element_by_xpath                    | 通过xpath表达式定位   |
| find_element_by_link_text                | 通过完整超链接定位    |
| find_element_by_partial_link_text        | 通过部分链接定位      |
| find_element_by_tag_name                 | 通过标签定位          |
| find_element_by_class_name               | 通过类名进行定位      |
| find_elements_by_css_selector            | 通过css选择器进行定位 |

**示例：**

```python
inputbox = browser.find_element_by_class_name("kw")#根据class名称找到元素
```





## 元素控制

| 方法                        | 说明                   |
| --------------------------- | ---------------------- |
| browser.set_window_size()   | 设置浏览器的大小       |
| browser.back()              | 控制浏览器后退         |
| browser.forward()           | 控制浏览器前进         |
| browser.refresh()           | 刷新当前页面           |
| element.clear()             | 清除文本               |
| element.send_keys (value)   | 模拟按键输入           |
| element.click()             | 单击元素               |
| element.submit()            | 用于提交表单           |
| element.get_attribute(name) | 获取元素属性值         |
| element.is_displayed()      | 设置该元素是否用户可见 |
| element.size                | 返回元素的尺寸         |
| element.text                | 获取元素的文本         |

**示例**：

```python
browser.refresh()#刷新页面
inputbox = browser.find_element_by_class_name("kw")#根据class名称找到元素
inputbox.clear()#清空输入框
inputbox.send_keys('python')#将输入框内容变为python
```





## 鼠标控制

```python
from selenium.webdriver.common.action_chains import ActionChains#调库
```

| 方法                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ActionChains(browser)                                        | 构造ActionChains对象                                         |
| act.context_click(element)                                   | 鼠标右键操作                                                 |
| act.move_to_element(element)                                 | 执行鼠标悬停操作                                             |
| act.double_click()                                           | 双击                                                         |
| act.drag_and_drop()                                          | 拖动                                                         |
| act.perform()                                                | **执行所有 ActionChains 中存储的行为，可以理解成是对整个操作的提交动作** |
| act.click(element)                                           | 鼠标单击元素                                                 |
| act.click_and_hold(element)                                  | 点击鼠标左键，不松开                                         |
| act.drag_and_drop(source, target)                            | 拖拽到某个元素然后松开                                       |
| act.drag_and_drop_by_offset(source, xoffset, yoffset)        | 拖拽到某个坐标然后松开                                       |
| act.move_by_offset(xoffset, yoffset)                         | 鼠标从当前位置移动到某个坐标                                 |
| act.move_to_element_with_offset(to_element, xoffset, yoffset) | 移动到距某个元素（左上角坐标）多少距离的位置                 |
| act.release(element)                                         | 在某个元素位置松开鼠标左键                                   |

**示例**：

```python
from selenium.webdriver.common.action_chains import ActionChains
#定位到要悬停的元素
element= driver.find_element_by_link_text("设置")
#对定位到的元素执行鼠标悬停操作
ActionChains(browser).move_to_element(element).perform()
```





## 键盘控制

```python
from selenium.webdriver.common.keys import Keys#调库
```

| 模拟键盘按键                | 说明                |
| --------------------------- | ------------------- |
| send_keys(Keys.BACK_SPACE)  | 删除键（BackSpace） |
| send_keys(Keys.SPACE)       | 空格键(Space)       |
| send_keys(Keys.TAB)         | 制表键(Tab)         |
| send_keys(Keys.ESCAPE)      | 回退键（Esc）       |
| send_keys(Keys.ENTER)       | 回车键（Enter）     |
| send_keys(Keys.CONTROL,‘a’) | 全选（Ctrl+A）      |
| send_keys(Keys.CONTROL,‘c’) | 复制（Ctrl+C）      |
| send_keys(Keys.CONTROL,‘x’) | 剪切（Ctrl+X）      |
| send_keys(Keys.CONTROL,‘v’) | 粘贴（Ctrl+V）      |
| send_keys(Keys.F1…Fn)       | 键盘 F1…Fn          |

**示例**：

```python
from selenium.webdriver.common.keys import Keys#调库
inputbox = browser.find_element_by_class_name("kw")#根据class名称找到元素
inputbox.clear()#清空输入框
inputbox.send_keys('python')#将输入框内容变为python
inputbox.send_keys(Keys.ENTER)#对输入框按回车
```





## cookie操作

| 方法                                      | 说明                                                         |
| ----------------------------------------- | ------------------------------------------------------------ |
| browser.get_cookies()                     | 获得所有cookie信息                                           |
| browser.get_cookie(name)                  | 返回字典的key为“name”的cookie信息                            |
| browser.add_cookie(cookie_dict)           | 添加cookie。“cookie_dict”指字典对象，必须有name 和value 值   |
| browser.delete_cookie(name,optionsString) | 删除cookie信息。“name”是要删除的cookie的名称，“optionsString”是该cookie的选项，目前支持的选项包括“路径”，“域” |
| browser.delete_all_cookies()              | 删除所有cookie信息                                           |





## 获取断言信息

不管是在做功能测试还是自动化测试，最后一步需要拿实际结果与预期进行比较。这个比较的称之为断言。通过我们获取title 、URL和text等信息进行断言。

| 属性                | 说明                   |
| ------------------- | ---------------------- |
| browser.title       | 用于获得当前页面的标题 |
| browser.current_url | 用户获得当前页面的URL  |
| element.text        | 获取搜索条目的文本信息 |





## 切换frame/iframe

在Web应用中经常会遇到frame/iframe表单嵌套页面的应用，WebDriver只能在一个页面上对元素识别与定位，对于frame/iframe表单内嵌页面上的元素无法直接定位。这时就需要通过switch_to.frame()方法将当前定位的主体切换为frame/iframe表单的内嵌页面中。

| 方法                                | 说明                                                         |
| ----------------------------------- | ------------------------------------------------------------ |
| browser.switch_to.frame()           | 将当前定位的主体切换为frame/iframe表单的内嵌页面中,默认可以直接取表单的id 或name属性,若没有id或name属性则可以先用各种find函数先找到frame元素再作为参数值 |
| browser.switch_to.default_content() | 跳回最外层的页面                                             |

**示例**：

```python
browser.switch_to.frame('x-URS-iframe')#切换到frame
#这里对副窗口进行操作
browser.switch_to.default_content()#返回
```





## 切换窗口

在页面操作过程中有时候点击某个链接会弹出新的窗口，这时就需要主机切换到新打开的窗口上进行操作。WebDriver提供了switch_to.window()方法，可以实现在不同的窗口之间切换。

| 方法                             | 说明                                                         |
| -------------------------------- | ------------------------------------------------------------ |
| browser.current_window_handle    | 获得当前窗口句柄                                             |
| browser.window_handles           | 返回所有窗口的句柄到当前会话                                 |
| browser.switch_to.window(handle) | 用于切换到相应的窗口，与上一节的switch_to.frame()类似，前者用于不同窗口的切换，后者用于不同表单之间的切换。 |
| browser.close()                  | 关闭单个窗口                                                 |
| browser.quit()                   | 关闭所有窗口                                                 |





## 警告框处理

在WebDriver中处理[JavaScript](https://so.csdn.net/so/search?from=pc_blog_highlight&q=JavaScript)所生成的alert、confirm以及prompt十分简单，具体做法是使用 switch_to.alert 方法定位到 alert/confirm/prompt，然后使用text/accept/dismiss/ send_keys等方法进行操作。

| 方法                    | 说明                                   |
| ----------------------- | -------------------------------------- |
| browser.switch_to.alert | 切换至警告框                           |
| text                    | 返回 alert/confirm/prompt 中的文字信息 |
| accept()                | 接受现有警告框                         |
| dismiss()               | 解散现有警告框                         |
| send_keys()             | 发送文本至警告框。                     |





## 下拉框选择操作

```python
from selenium.webdriver.support.select import Select#调库
```

Select类的方法

| 方法                              | 说明                      |
| --------------------------------- | ------------------------- |
| select_by_value(“选择值”)         | select标签的value属性的值 |
| select_by_index(“索引值”)         | 下拉框的索引              |
| select_by_visible_testx(“文本值”) | 下拉框的文本值            |

**示例**：

```python
sel = driver.find_element_by_class_name('slc')
Select(sel).select_by_value('50')  #选择50
```









---



# xlrd

可以对`excel`进行**读取**操作

## 安装

```powershell
pip install xlrd
```





## 导包

```python
import xlrd
```





## 使用

| 方法/属性                         | 说明                                 |
| --------------------------------- | ------------------------------------ |
| xlrd.open_workbook(excel文件路径) | 打开excel文件，返回excel对象         |
| excel.sheets()                    | 返回excel文件的sheet列表             |
| excel.get_sheet(n)                | 获取第`n`个表单(从0开始)             |
| excel.sheet_by_name(u'sheet名')   | 根据sheet名返回sheet (table)         |
| table.name                        | 返回表格的名称                       |
| table.nrows                       | 返回表格的行数                       |
| table.nrows                       | 返回表格的列数                       |
| table.row_values(row)             | 返回表格的第`row`行(从0开始)         |
| table.col_values(col)             | 返回表格的第`col`列(从0开始)         |
| table.cell(i ,j).value            | 返回表格的第`i`行，第`j`列的数据     |
| table.cell_value(i,j)             | 返回表格的第`i`行，第`j`列的数据     |
| table.cell(i,j).ctype             | 返回表格的第`i`行，第`j`列数据的类型 |

示例：

```python
import xlrd              #导入模块
data = xlrd.open_workbook('电影.xlsx')    #打开电影.xlsx文件读取数据
table = data.sheets()[0]       #读取第一个（0）表单
#或者通过表单名称获取 table = data.sheet_by_name(u'Sheet1')
print(table.nrows)            #输出表格行数
print(table.ncols)            #输出表格列数
print(table.row_values(0))    #输出第一行
print(table.col_values(0))    #输出第一列
print(table.cell(0,2).value)  #输出元素（0,2）的值
```

原Excel表格情况：

![image](https://cdn.jsdelivr.net/gh/GedRelay/imgs/1176700-20170925151650901-1405911679.png)

输出结果：

![image](https://cdn.jsdelivr.net/gh/GedRelay/imgs/1176700-20170925151648214-182571950.png)



## 数据类型

xlrd的数据类型有：

0 empty
1 string
2 number
3 date
4 boolean
5 error

**数字一律按浮点型输出，日期输出成一串小数，布尔型输出0或1，所以我们必须在程序中做判断处理转换成我们想要的数据类型**









---



# xlwt

可以对`excel`进行**创建和写入**操作

## 安装

```powershell
pip install xlwt
```





## 导包

```python
import xlwt
```





## 使用

| 方法/属性                    | 说明                            |
| ---------------------------- | ------------------------------- |
| xlwt.Workbook()              | 创建一个新的excel并返回         |
| excel.add_sheet(表单名)      | excel创建一个新的表单并返回     |
| table.write(row,col,'value') | 在第`row`行`col`列写入值`value` |
| excel.save(保存路径)         | 保存excel文件                   |

示例：

```python
import xlwt                             #导入模块
wb = xlwt.Workbook(encoding = 'ascii')  #创建新的Excel（新的workbook），建议还是用ascii编码
ws = wb.add_sheet('test')               #创建新的表单test
ws.write(0, 0, label = 'hello')         #在（0,0）加入 hello
ws.write(0, 1, label = 'world')         #在（0,1）加入 world
ws.write(1, 0, label = '你好')           #在（1,0）加入 你好
wb.save('test.xls')                     #保存为test.xls文件
```









---



# xlutils

可以对原有的`excel`进行**修改**操作，常和`xlrd`一起使用

## 安装

```powershell
pip install xlutils
```





## 导包

```python
from xlutils.copy import copy
```





## 使用

| 方法/属性                    | 说明                                        |
| ---------------------------- | ------------------------------------------- |
| copy(excel)                  | 将excel拷贝一份变成可写的 xlwt 对象，并返回 |
| table.write(row,col,'value') | 在第`row`行`col`列写入值`value`             |
| excel.save(保存路径)         | 保存excel文件                               |

示例：

```python
import xlrd                             #导入模块
from xlutils.copy import copy           #导入copy模块
excel1 = xlrd.open_workbook('weng.xls') #打开weng.xls文件
excel2 = copy(excel1)                   #利用xlutils.copy下的copy函数复制
table = excel2.get_sheet(0)             #获取表单0
table.write(0, 0, 'changed!')           #改变（0,0）的值
table.write(8,0,label = '好的')          #增加（8,0）的值
excel2.save('weng.xls')                 #保存文件
```









---



# PyMySQL

可以使python连接数据库，对mysql数据库进行操作

## 安装

```powershell
pip install PyMySQL
pip install cryptography
```





## 导包

```python
import pymysql
```





## 连接数据库

1. 通过ODBC连接数据库
2. 生成游标
3. 通过游标对数据库进行操作
4. 关闭游标
5. 关闭连接

```python
import pymysql
db = pymysql.connect(host = '127.0.0.1' # 连接名称，默认127.0.0.1
,user = 'root' # 用户名
,passwd = 'password' # 密码
,port = 3306 # 端口，默认为3306
,db = 'test' # 数据库名称
,charset = 'utf8' # 字符编码
)

cur = db.cursor() # 生成游标对象

cur.execute("select * from student") # 执行SQL语句
data = cur.fetchall() # 通过fetchall方法获得数据

for i in data: # 打印输出数据
    print (i)

cur.close() # 关闭游标
db.close() # 关闭连接
```





## 游标方法

对游标cursor进行操作

| 方法                    | 说明                                                       |
| ----------------------- | ---------------------------------------------------------- |
| cursor.execute(sql语句) | 执行sql语句，除了查询语句，其他都要`db.commit()`提交才执行 |
| cursor.fetchone()       | 获取mysql返回的单条数据                                    |
| cur.fetchall()          | 获取mysql返回的所有数据                                    |
| cursor.close()          | 关闭游标                                                   |





## 数据库方法

对数据库db进行操作

| 方法          | 说明                   |
| ------------- | ---------------------- |
| db.cursor()   | 创建一个游标对象并返回 |
| db.commit()   | 提交sql语句            |
| db.rollback() | 回滚                   |
| db.close()    | 关闭连接               |





## 错误处理

| 异常              | 描述                                                         |
| :---------------- | :----------------------------------------------------------- |
| Warning           | 当有严重警告时触发，例如插入数据是被截断等等。必须是 StandardError 的子类。 |
| Error             | 警告以外所有其他错误类。必须是 StandardError 的子类。        |
| InterfaceError    | 当有数据库接口模块本身的错误（而不是数据库的错误）发生时触发。 必须是Error的子类。 |
| DatabaseError     | 和数据库有关的错误发生时触发。 必须是Error的子类。           |
| DataError         | 当有数据处理时的错误发生时触发，例如：除零错误，数据超范围等等。 必须是DatabaseError的子类。 |
| OperationalError  | 指非用户控制的，而是操作数据库时发生的错误。例如：连接意外断开、 数据库名未找到、事务处理失败、内存分配错误等等操作数据库是发生的错误。 必须是DatabaseError的子类。 |
| IntegrityError    | 完整性相关的错误，例如外键检查失败等。必须是DatabaseError子类。 |
| InternalError     | 数据库的内部错误，例如游标（cursor）失效了、事务同步失败等等。 必须是DatabaseError子类。 |
| ProgrammingError  | 程序错误，例如数据表（table）没找到或已存在、SQL语句语法错误、 参数数量错误等等。必须是DatabaseError的子类。 |
| NotSupportedError | 不支持错误，指使用了数据库不支持的函数或API等。例如在连接对象上 使用.rollback()函数，然而数据库并不支持事务或者事务已关闭。 必须是DatabaseError的子类。 |









---



# sqlite3

一个轻量级的数据库，不需要登录，一个`.db`文件即可存储数据

## 导包

python2.5以后的安装包已经自带SQLite3的软件包了，所以直接导入使用即可

```cmd
添加至系统path环境变量
import sqlite3
```

创建数据库：新建.db文件即可





## 连接数据库

```python
import sqlite3
con = sqlite3.connect('D:\\mysql_db\\ttt.db')#建立连接
cur = con.cursor()#游标
con.close()#关闭连接
```





## 数据库方法

| 方法          | 说明                   |
| ------------- | ---------------------- |
| db.cursor()   | 创建一个游标对象并返回 |
| db.commit()   | 提交事务               |
| db.rollback() | 事务回滚               |
| db.close()    | 关闭数据库连接         |





## 游标方法

| 方法                        | 说明                                                       |
| --------------------------- | ---------------------------------------------------------- |
| cursor.execute(sql语句)     | 执行sql语句，除了查询语句，其他都要`db.commit()`提交才执行 |
| cursor.executemany(sql语句) | 执行多条sql语句                                            |
| cursor.fetchone()           | 获取mysql返回的单条数据                                    |
| cursor.fetchall()           | 获取mysql返回的所有数据                                    |
| cursor.scroll()             | 用于游标滚动                                               |
| cursor.close()              | 关闭游标                                                   |

使用占位符“`?`”，**规避sql注入** 

```python
cur.execute('insert into student VALUES (?,?,?)',('xuehao','name2',28))
```

使用`executemany()`执行多条sql语句，使用executmany()比循环使用excute()执行多条sql语句效率高。

```python
cur.executemany('INSERT INTO person VALUES (?,?,?)',[(3,'name3',19),(4,'name4',26)])
```









---



# cv2(OpenCV)

可以对图像进行数字图像处理

[教程](https://www.cnblogs.com/silence-cho/p/10926248.html) 

## 安装

```powershell
pip install opencv-python
```





## 导包

```python
import cv2
```





## 基础知识

### 读取图片，写入图片

```python
imread("图片路径",flag) #读取图片，返回图片对象
imwrite("写入路径.jpg",img) #将图片写入文件
参数说明：
flag：
	cv2.IMREAD_COLOR #默认，读取彩色图片，图片透明性会被忽略，也可以传入1
	cv2.IMREAD_GRAYSCALE #按灰度模式读取图像，也可以传入0
	cv2.IMREAD_UNCHANGED #读取图像，包括其alpha通道，也可以传入-1
```



### 展示图片

```python
imshow(window_name,img) #显示图片，窗口自适应图片大小
参数说明：
    window_name: 指定窗口的名字
    img：显示的图片对象
    可以指定多个窗口名称，显示多个图片
    
waitKey(millseconds)  #键盘绑定事件，阻塞监听键盘按键，返回一个数字（不同按键对应的数字不同）
    millseconds: 传入时间毫秒数，在该时间内等待键盘事件；传入0时，会一直等待键盘事件
    
destroyAllWindows(window_name) #关闭图片显示窗口
    window_name: 需要关闭的窗口名字，不传入时关闭所有窗口
```

**示例：**

```python
my_img = cv2.imread('C:\\Users\\29406\\Desktop\\img\\xxx.jpg',0)#按灰度读取图像
cv2.imshow('图片',canny)
cv2.waitKey(0)
```









---



# PyInstaller

可以将程序打包成`.exe`文件

* 该模块是在`cmd`或者`powershell`中使用的

## 安装

```powershell
pip install pyinstaller
```





## 打包

在`cmd`中执行以下命令：

```powershell
pyinstaller 文件位置.py 命令参数(可选)
默认将在C:\Windows\System32\dist中生成exe文件
```

### 常用命令参数:

| 参数                                      | 功能                                            |
| :---------------------------------------- | :---------------------------------------------- |
| -h, --help                                | 帮助                                            |
| --distpath DIR                            | 生成exe程序的位置，默认在当前目录的dist文件下   |
| --workpath WORKPATH                       | 生成临时文件的位置，默认在当前目录的build文件下 |
| --clean                                   | 清除生成的文件（重新生成前先清除）              |
| -D, --onedir                              | 打包成一个包含exe程序的文件夹                   |
| -F, --onefile                             | 打包成一个独立的exe程序（运行起来会慢很多）     |
| --hidden-import MODULENAME                | 有些依赖包是动态导入的需手动导入告诉pyinstaller |
| -d {all,imports,bootloader,noarchive}     | 生成debug版本                                   |
| -w, --windowed, --noconsole               | 隐藏命令行窗口                                  |
| -i <FILE.ico or FILE.exe,ID or FILE.icns> | 为程序添加ico图标                               |
| -n NAME, --name NAME                      | 为exe程序指定名称，默认和py程序名一样           |



### 参考代码

* pyside2文件打包需要加上`--hidden-import PySide2.QtXml` 

```powershell
生成一个单独的.exe文件
pyinstaller 代码位置.py --distpath .exe文件目标位置 -F -w -n 程序名字 -i 图标文件位置.ico

生成一个包含.exe文件的文件
pyinstaller 代码位置.py --distpath .exe文件目标位置 -D -w -n 程序名字 -i 图标文件位置.ico
```









---



# jieba

将中文句子根据语义进行分词

## 安装

```powershell
pip install jieba
```





## 使用

jieba分词有三种模式：

* 精确模式：把文本精确的切分开，不存在冗余单词
* 全模式：把文本中所有可能的词都扫描出来，有冗余
* 搜索引擎模式：在精确模式基础上，对长词再次切分

| 函数                       | 描述                                                         |
| -------------------------- | ------------------------------------------------------------ |
| jieba.lcut(s)              | 精确模式，返回一个列表类型的分词结果<br />jieba.lcut("中国是一个伟大的国家")<br/>['中国', '是', '一个', '伟大', '的', '国家'] |
| jieba.lcut(s,cut_all=True) | 全模式，返回一个列表类型的分词结果，存在冗余<br/>jieba.lcut("中国是一个伟大的国家",cut_all=True)<br/>['中国', '国是', '一个', '伟大', '的', '国家'] |
| jieba.lcut_for_search(s)   | 搜索引擎模式，返回一个列表类型的分词结果，存在冗余<br/>jieba.lcut_for_search("中华人民共和国是伟大的")<br/>['中华', '华人', '人民', '共和', '共和国', '中华人民共和国', '是', '伟大', '的'] |
| jieba.add_word(w)          | 向分词词典增加新词w<br/>jieba.add_word("蟒蛇语言")           |









---



# wordcloud

根据传入的一系列词语，根据词语出现的频率生成词云

示例：

<img src="https://cdn.jsdelivr.net/gh/GedRelay/imgs/image-20220114145153928.png" alt="image-20220114145153928" style="zoom: 33%;" />

## 安装

```powershell
pip install wordcloud
```





## 使用

```python
定义一个词云对象:
w = wordcloud.WordCloud([参数1][,参数2].....[,参数n])
```

### 词云对象方法

| 方法                | 描述                                                         |
| ------------------- | ------------------------------------------------------------ |
| w.generate(txt)     | 向WordCloud对象w中加载文本txt<br>如：w.generate("Python and wordcloud") |
| w.to_file(filename) | 将词云输出为图像文件，.png或.jpg格式<br>如：w.to_file("outfile.png") |



### 词云对象参数

| 参数             | 描述                                                         |
| ---------------- | ------------------------------------------------------------ |
| width            | 指定词云对象生成图片的宽度，默认400像素<br/>如：w=wordcloud.WordCloud(width=600) |
| height           | 指定词云对象生成图片的高度，默认200像素<br/>如：w=wordcloud.WordCloud(height=400) |
| min_font_size    | 指定词云对象中字体的最小字号，默认4号<br/>如：w=wordcloud.WordCloud(min_font_size=10) |
| max_font_size    | 指定词云对象中字体的最大字号，根据高度自动调节<br/>如：w=wordcloud.WordCloud(max_font_size=20) |
| font_step        | 指定词云中字体字号的步进间隔，默认为1<br/>如：w=wordcloud.WordCloud(font_step=2) |
| font_path        | 指定字体文件路径，默认None<br/>如：w=wordcloud.WordCloud(font_path="msyh.ttc") |
| max_words        | 指定词云显示的最大单词数量，默认200<br/>如：w=wordcloud.WordCloud(max_words=20) |
| stop_words       | 指定词云的排列词列表，即不显示的单词列表<br/>如：w=wordcloud.WordCloud(stop_words={"Python"}) |
| mask             | 指定词云形状，默认为长方形，需要引用imread()函数<br/>如：from scipy.misc import imread<br/>mk = imread("pic.png")<br/>w = wordcloud.WordCloud(mask=mk) |
| background_color | 指定词云图片的背景颜色，默认为黑色<br/>如：w=wordcloud.WordCloud(background_color="white") |









---

