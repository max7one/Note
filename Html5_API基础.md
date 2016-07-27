## HTML5

### 存储类

HTML5本地存储只能存字符串，任何格式存储的时候都会被自动转为字符串，所以读取的时候，需要自己进行类型的转换

#### 1. Web Storage

##### LocalStorage是本地存储

特点
  - 数据持久保存,无论窗口或浏览器是否关闭都一直保存,除非主动删除
  - 存储空间比cookie大的多，有10M甚至更多
  - 存储内容**不会发送到服务器**,节省带宽
  - 更多丰富易用的接口
  
API使用
```js
localStorage.setItem('key','value'); //存入数据

var valueLocal = localStorage.getItem("key");  //读取键名为key的数据

localStorage.key(0);  //读取localStorage内索引为0的数据

localStorage.removeItem('key');  //清除键名为key的数据

localStorage.clear();  //清除所有数据
```

当储存的数据发生变化时，会触发storage事件
```js
Window.addEventlistener('storage',function (e) {
  console.log(e.key);   // 输出保存发生变化的的键名
})
```
`event`对象的属性还包括
  - `oldValue`：更新前的值
  - `newValue`：更新后的值
  - `url`：原始触发storage事件的那个网页的网址

> 如果浏览器同时打开一个域名下面的多个页面，当其中的一个页面改变sessionStorage或localStorage的数据时，其他所有页面的storage事件会被触发，而原始页面并不触发storage事件。可以通过这种机制，实现多个窗口之间的通信

##### sessionStorage是会话存储  

**特点**

同源的同窗口（或tab）中，始终存在的数据  
只要浏览器窗口没有关闭，即使刷新页面或进入同源另一页面，数据仍然存在。  
关闭窗口后，sessionStorage即被销毁。同时“独立”打开的不同窗口，即使是同一页面，sessionStorage对象也是不同的。

sessionStorage的API与localStorage的一致

#### 2. cookie

> cookie指某些网站为了辨别用户身份、进行session跟踪而储存在用户本地终端上的数据（通常经过加密）

特点
  - cookie数据始终在同源的http请求中携带，即cookie在浏览器和服务器间来回传递
  - cookie存储数据不能超过4k 
  - cookie在生存周期内(设置Expire值)之前一直有效，即使窗口或浏览器关闭
  
> 浏览器的同源政策规定，两个网址只要域名相同和端口相同，就可以共享Cookie。

> 注意，这里不要求协议相同。也就是说，`http://example.com`设置的Cookie，> 可以被`https://example.com`读取  
  
#### 3. 离线缓存

1.manifest

> 首先manifest是一个后缀名为minifest的文件，在文件中定义那些需要缓存的文件，支持manifest的浏览器，会将按照manifest文件的规则，像文件保存在本地，从而在没有网络链接的情况下，也能访问页面

> 当我们第一次正确配置app cache后，当我们再次访问该应用时，浏览器会首先检查manifest文件是否有变动，如果有变动就会把相应的变得跟新下来，同时改变浏览器里面的app cache，如果没有变动，就会直接把app cache的资源返回

特点
- 离线浏览: 用户可以在离线状态下浏览网站内容
- 更快的速度: 因为数据被存储在本地，所以速度会更快
- 减轻服务器的负载: 浏览器只会下载在服务器上发生改变的资源

使用
```html
<html manifest=”example.appcache”></html>
```

2.Application Cache

可以通过window.applicationCache 对象来访问浏览器的app cache  
可以查看 status 属性来获取cache的当前状态：

```js
var appCache = window.applicationCache;  
switch (appCache.status) {  
  case appCache.UNCACHED: // UNCACHED == 0  
    return 'UNCACHED';  
    break;  
  case appCache.IDLE: // IDLE == 1  
    return 'IDLE';  
    break;  
  case appCache.CHECKING: // CHECKING == 2  
    return 'CHECKING';  
    break;  
  case appCache.DOWNLOADING: // DOWNLOADING == 3  
    return 'DOWNLOADING';  
    break;  
  case appCache.UPDATEREADY:  // UPDATEREADY == 4  
    return 'UPDATEREADY';  
    break;  
  case appCache.OBSOLETE: // OBSOLETE == 5  
    return 'OBSOLETE';  
    break;  
  default:  
    return 'UKNOWN CACHE STATUS';  
    break;  
};  
```

applicationCache.update()//更新缓存,此操作将尝试更新用户的缓存（前提是已更改清单文件）  

当applicationCache.status 处于 UPDATEREADY 状态时   applicationCache.swapCache() 即可将原缓存换成新缓存。

### 通信类

##### 1. SSE(Server-Sent Event)

Server-Sent 事件 - **单向消息传递**

> Server-Sent 事件指的是网页自动获取来自服务器的更新  
> Server-Sent 事件 - 单向消息传递
Server-Sent 事件指的是网页自动获取来自服务器的更新

```js
//创建一个新的 EventSource 对象，然后规定发送更新的页面的 URL（本例中是 "demo_sse.php"）
var source=new EventSource("demo_sse.php");
//每接收到一次更新，就会发生 onmessage 事件
source.onmessage=function(event)
  {
  //当 onmessage 事件发生时，把已接收的数据推入 id 为 "result" 的元素中
  document.getElementById("result").innerHTML+=event.data + "<br />";
  };
```

服务器端代码

```php
<?php
header('Content-Type: text/event-stream');//把报头 "Content-Type" 设置为 "text/event-stream"
header('Cache-Control: no-cache');//规定不对页面进行缓存

$time = date('r');
echo "data: The server time is: {$time}\n\n";//输出发送日期（始终以 "data: " 开头）
flush();//向网页刷新输出数据
?>
```

##### 2. Websocket

> WebSocket protocol 是HTML5一种新的协议。它实现了浏览器与服务器全双工通信(full-duplex)。一开始的握手需要借助HTTP请求完成

特点
- 浏览器与服务器全双工通信
- Header是很小的-大概只有 2 Bytes
- 服务器的推送，服务器不再被动的接收到浏览器的request之后才返回数据，而是在有新数据时就主动推送给浏览器

应用
```js
// 创建一个Socket实例
var socket = new WebSocket('ws://localhost:8080'); 

// 打开Socket 
socket.onopen = function(event) { 

  // 发送一个初始化消息
  socket.send('I am the client and I am listening!'); 

  // 监听消息
  socket.onmessage = function(event) { 
    console.log('Client received a message',event); 
  }; 

  // 监听Socket的关闭
  socket.onclose = function(event) { 
    console.log('Client notified socket has closed',event); 
  }; 

  // 关闭Socket.... 
  socket.close() 
};
```

##### 3. PostMessage

> PostMessage是Windows API(应用程序接口) 中的一个常用函数，用于将一个消息放入（寄送）到与指定窗口创建的线程相联系消息队列里，不等待线程处理消息就返回，是异步消息模式。消息队列里的消息通过调用GetMessage和PeekMessage取得

### 计算类

##### 1. Web Worker

> 当在 HTML 页面中执行脚本时，页面的状态是不可响应的，直到脚本已完成。  
> web worker 是运行在后台的 JavaScript，独立于其他脚本，不会影响页面的性能。您可以继续做任何愿意做的事情：点击、选取内容等等，而此时 web worker 在后台运行  
> web worker 通常不用于如此简单的脚本，而是用于更耗费 CPU 资源的任务

Web workers可分为两种类型
- 专用线程dedicated web worker  
  Dedicated web worker随当前页面的关闭而结束；这意味着Dedicated web worker只能被创建它的页面访问
- 共享线程shared web worker

运用
1. 创建 web worker 文件 `demo_workers.js`

```js
var i=0;

function timedCount()
{
i=i+1;
postMessage(i);//postMessage() 方法 - 它用于向 HTML 页面传回一段消息
setTimeout("timedCount()",500);
}

timedCount();
```

2. 创建 Web Worker 对象

```js
//检测是否存在 worker，如果不存在，- 它会创建一个新的 web worker 对象，然后运行 "demo_workers.js" 中的代码
if(typeof(w)=="undefined")
  {
  w=new Worker("demo_workers.js");
  }
//向 web worker 添加一个 "onmessage" 事件监听器  
w.onmessage=function(event){
//当 web worker 传递消息时，会执行事件监听器中的代码。event.data 中存有来自 event.data 的数据
document.getElementById("result").innerHTML=event.data;
};
//终止 Web Worker
w.terminate();
```

由于 web worker 位于外部文件中，它们无法访问下例 JavaScript 对象：
- window 对象
- document 对象
- parent 对象

