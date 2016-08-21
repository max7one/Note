## 前后端数据交互方法

#### 1. HTML赋值

后端(php)直接渲染到HTMl标签的属性,比如`id`、`data-*`  
然后再使用`Javascript`获取

输出到 Element 的 value 或 data-name
```html
<input type="hidden" value="<?php echo $user_avatar;?>" />
<div data-value="<?php echo $user_avatar;?>"></div>
```
渲染结果
```html
<input type="hidden" value="https://avatars1.githubusercontent.com/u/3949015?v=3&s=40" />
<div data-avatar="https://avatars1.githubusercontent.com/u/3949015?v=3&s=40"></div>
```
使用JavaScript或jQurey获取
```js
$('input').val();
// http://jquery.bootcss.com/jQuery.data/
$('div').data('avatar');
```

优点  
不占用全局变量，由 JS 自由获取。

适合传递**简单数据**，也非常适合多个简单数据与 Element 绑定关系


#### 2. 模板引擎

将数据填充到 <script> 的 JavaScript 变量声明中
