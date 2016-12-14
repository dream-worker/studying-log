# Node ——part 1：

##   node 响应浏览器请求 **三步走**       

## 1. require('http') 获取 http 核心模块  

（1）获取http 核心模块

（2）然后才能通过http模块创建服务（实现第2步）  

（3）创建服务后，才能监听  

  

代码部分：  

```js 
// 1. 获得http核心模块
var http = require('http')
// 2.创建http 服务 server
var server = http.createServer(function  (request, response) {
	// 浏览器发出请求时，服务器可以获取到访问的url:指的是端口后面的部分URL
	// 服务器可以根据端口后面的数据，返回给浏览器相应的数据（页面）
	console.log(request.url)
	// 浏览器访问服务器设置的固定端口和IP时，服务器返回给浏览器以下内容
	response.end('这里是浏览器')
})
// 3. 监听
server.listen(3000,'127.0.0.1',function  () {
	// 不从浏览器发送请求时，也可以打印（旨在表明服务器正常开启）
	console.log('服务器正常开启')
})
```

##  2. request.url   '/xx.html?a=1&=2'   



http 服务部分的`request.url`获得用户请求时URL中端口号后的部分   

服务部分的request.url获得用户请求时URL中端口号后的部分     

浏览器访问如下地址：

![request.url1](E:\360data\重要数据\桌面\node\request.url1.png)  



服务器响应：  

![request.url2](E:\360data\重要数据\桌面\node\request.url2.png)  

当浏览器访问的地址，端口号后面没有数据时，服务器默认返回"/";

否则，返回端口号后面内容，如：“/xx.html”;   

## 3. request.headers  

   `request.headers`获得请求头信息       

代码部分：

```js  
var http = require('http')
var server = http.createServer(function( request, response ){
console.log(request.headers)
// node 中显示了请求头的信息
	response.end('浏览器中显示')
	// 只在浏览器中显示response的内容。node 服务器中没有显示内容
	
})
server.listen(3000)  
```

如图：  

![request.headers](E:\360data\重要数据\桌面\node\request.headers.png)

## 4. require('url') url 核心模块   

代码部分：  

```js  
//1.得到http对象
var http = require('http')
var url = require('url')

// 2.创建服务
var server = http.createServer(function(request, response){
    // 只要是请求，都会在这里接收
    console.log(url)
   
    response.end('你好!')
})

// 3.监听
// 后面的ip可以默认省略！
// // 省略的话，可以用127.0.0.1,或者localhost或者本机ip访问！
server.listen(1201,'127.0.0.1')
```

服务器响应如图：  

![url](E:\360data\重要数据\桌面\node\url.png)



如图所示：

url 模块具有五个方法属性 ： `parse/resolve/resolveObject/format/Url`  

## 5. 一幅图涉及到的ndoe 知识   

假如我们访问这个地址：

http://127.0.0.1:1201/xx.html?a=1&b=2

代码部分： 

```js 
// request.url 得到path即： xx.html

//1.得到http对象
var http = require('http')
var url = require('url')

// 2.创建服务
var server = http.createServer(function(request, response){
// var url = require('url')得到的url核心模块中有parse方法，第二个参数为true,
//将第一个参数path+search = '/xx.html?a=1&=2'转化为对象
    var obj = url.parse(request.url, true)
    console.log(obj)
})

// 3.监听
server.listen(1201,'127.0.0.1')


```

图示： 核心模块Url的parse()

![oneUrl](E:\360data\重要数据\桌面\node\oneUrl.png)





图示：核心模块Url.parse () +  request.header  :



![url.parse](E:\360data\重要数据\桌面\node\url.parse.png)  



- Url 对象中的内容包括：  `slashes/auth/host/port/hostname/search/query/pathname/path/href/...`

- Url:  是一个对象

  如图：

  ![two Urls](E:\360data\重要数据\桌面\node\two Urls.png)

   

  - 第一个Url 是浏览器访问时的数据  

  - 第二个Url 是浏览器请求favicon时的请求数据  

    所以，上图共有两条数据  

      

- `host`: "127.0.0.1:1201"是浏览器发送请求的字符串形式的url  

- `search`:"?a=1&b=2":是浏览器发送请求时，url上携带的字符串数据（包含问号部分）  

- `query`:{a:'1',b:'2'}:是浏览器请求时，携带的数据的对象形式，其中，属性值是字符串  

- `pathname`:“/xx.html”:端口号后面到问号前面的部分  字符串类型

  - 请求图标的是"/favicon.ico";且pathname = path = href  

- `path`: “/xx.html?a=1&b=2” : 端口号后面到url结束  

- `href`: "/xx.html?a=1&b=2"  

  一个小小的地址，竟包含如此多内容： 

  http://127.0.0.1:1201/xx.html?a=1&b=2

  - 协议：//host+pathname+search  

  - 协议:// host+path  

  - 协议：//host+pathname+query（对象形式，转成字符串）

    ​

  ​