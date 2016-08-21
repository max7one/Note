## 常见命令

#### 设置登录源

- 通过config命令
```
npm config set registry https://registry.npm.taobao.org
npm info underscore （如果上面配置正确这个命令会有字符串response）
```
- 命令行指定
```
npm --registry https://registry.npm.taobao.org info underscore
```
- 编辑 ~/.npmrc 加入下面内容
```
registry = https://registry.npm.taobao.org
```

## 其它

在行尾写入 字符串
```js
fs.appendFile('message.txt','data to append',function(err){});
```

不要声明arguments变量  
这样将覆盖函数作用域的arguments对象,导致无法访问函数作用域的arguments


`JSON.stringify` 不能解析环形json  (尤其对于dom对象)  
用 node 中的 util.inspect();


文件内的 var a = 1;并不是全局变量,而是模块内的局部变量
a = 1  为全局变量
global为最外层

在浏览器 JavaScript 中，通常 window 是全局对象  
而 Node.js 中的全局对象是 global，所有全局变量（除了 global 本身以外）都是 global 对象的属性。

## NPM Package

- `browser-sync` 浏览器自动刷新
- `Anywhere` 随启随用的静态文件服务器
- `gulp` 前端自动化
