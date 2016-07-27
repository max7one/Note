### Ajax简介
> Asynchronous Javascript And XML（异步JavaScript和XML）

> 通过在浏览器后台与服务器进行少量数据交换，AJAX 可以使网页实现异步更新。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。

### Ajax优缺点
- 优点
  - 无刷新更新数据
  - 异步与服务器通信
  - 界面与应用分离
- 缺点
  - 使页面丧失back和history功能
  - 不利于SEO
  - 浏览器安全性问题
  
### Ajax的运用

```js

var xmlhttp; //声明一个xmlhttp变量
//判断浏览器是否支持 XMLHttpRequest 对象
if (window.XMLHttpRequest) {
  // code for IE7+, Firefox, Chrome, Opera, Safari
  xmlhttp = new XMLHttpRequest(); // 创建一个 XMLHttpRequest对象
} else { // code for IE6, IE5
  xmlhttp = new ActiveXObject("Microsoft.XMLHTTP"); // 创建ActiveXObject对象
}
//每当 readyState 属性改变时，就会调用该函数
xmlhttp.onreadystatechange = function() {
    // 当 readyState 等于 4 且状态为 200 时，表示响应已就绪
  if (xmlhttp.readyState == 4 && xmlhttp.status == 200) {
    // 获得字符串形式的响应数据并渲染dom
    document.getElementById("mydiv").innerHTML = xmlhttp.responseText;
  }
}
  //规定请求类型为POST,url地址为test.html,并且是异步的
xmlhttp.open("POST", "test.html", true);
//将请求发送到服务器
xmlhttp.send("a=1&b=2");

```