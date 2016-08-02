## 浏览器同源

- 协议相同  (`http`)
- 域名相同    
    `http://www.abc.com`  
    `http://www.abc.com/html/index.html` 同源  
    `http://abc.com` 不同源  
    `http://www1.abc.com` 不同源
- 端口相同 (`80`)

如果非同源，共有三种行为受到限制
- Cookie、LocalStorage 和 IndexDB 无法读取。
- DOM 无法获得。
- AJAX 请求不能发送。

#### 规避方式

jsonp

网页通过添加一个`<script>`元素，向服务器请求JSON数据，这种做法不受同源政策限制  
服务器收到请求后，将数据放在一个指定名字的回调函数里传回来

首先，网页动态插入`<script>`元素，由它向跨源网址发出请求  
**带有src属性的标签都是跨域的**

```
function addScriptTag(src) {
  var script = document.createElement('script');
  script.setAttribute("type","text/javascript");
  script.src = src;
  document.body.appendChild(script);
}

window.onload = function () {
  addScriptTag('http://example.com/ip?callback=foo');
}

function foo(data) {
  console.log('Your public IP address is: ' + data.ip);
};
```

上面代码通过动态添加`<script>`元素，向服务器example.com发出请求  
注意，该请求的查询字符串有一个callback参数，用来指定回调函数的名字，这对于JSONP是必需的
