## Zepto

#### 1. 简介

	Zepto是一个轻量级的针对现代高级浏览器的JavaScript库， 它与jquery有着类似的api

#### 2. 核心模块
  
- 选择器
	- `$('div')` 标签选择器
	- `$('#foo')` ID选择器
	- `$(".foo")` 类选择器
	- `$("div p")` 后代选择器
	- `$("input[type=text]")` 属性选择器
	- `$("<p>Hello</p>")` 创建元素
	- `$("<p />", { text:"Hello", id:"greeting", css:{color:'darkblue'} })`  创建带有属性的元素

- 属性
	- `attr` 读取或设置dom的属性。如果没有给定value参数，则读取对象集合中第一个元素的属性值。当给定了value参数。则设置对象集合中所有元素的该属性的值
	- `prop` 要读取DOM的属性如 checked和selected,它在读取属性值的情况下优先于 attr，因为这些属性值会因为用户的交互发生改变
	- `addClass` `removeClass`添加删除类名
	- `html` `text` 获取或设置对象集合中元素的HTML内容。当没有给定content参数时，返回对象集合中第一个元素的innerHtml。当给定content参数时，用其替换对象集合中每个元素的内容
	- `val` 获取匹配元素的value值

- 文档处理
	- 元素添加	`append` `after` `insertAfter`
	- 元素删减  `empty` `remove`
	- 替换 `replaceAll` `replaceWith`
	- 克隆 `clone`

- CSS
	- `css` 读取或设置DOM元素的css属性。当value参数不存在的时候，返回对象集合中第一个元素的css属性。当value参数存在时，设置对象集合中每一个元素的对应css属性
	- `positon` 获取对象集合中第一个元素的位置
	- `scrollLeft` `scrollTop` 获取或设置页面上的滚动元素或者整个窗口向右滚动的像素值,获取或设置页面上的滚动元素或者整个窗口向下滚动的像素值
	- `width` `height`获取对象集合中第一个元素的宽高；或者设置对象集合中所有元素的宽高

- 筛选
	- 索引 `eq()` `first()`
	- 查找 `find()`
	- 子父级 `children` `parent`
	- 前后 `prev` `next`

- 效果 
	- 显示隐藏 `show()` `hide()` `toggle()`
	- 自定义动画 `animate()`


- 判断
	- `$.isArray`
	- `$.isFunction`
	- `$.isPlainObject` 测试对象是否是“纯粹”的对象，这个对象是通过 对象常量（"{}"） 或者 new Object 创建的
	- `$.isWindow ` 如果object参数是否为一个window对象，那么返回true


- 工具
	- JSON解析  (接受一个标准格式的 JSON 字符串，并返回解析后的 JavaScript 对象) `$.parseJSON(string)`
	- 删除字符串首尾的空白符
		`$.trim(string)`
	- 遍历 `$.each` 
	- $(function)(){} dom加载玩执行

#### 3. 事件处理

- `$.Event` <br>
创建并初始化一个指定的DOM事件。如果给定properties对象，使用它来扩展出新的事件对象。默认情况下，事件被设置为冒泡方式；这个可以通过设置bubbles为false来关闭
- `on` 添加事件处理程序到对象集合中得元素上
- `off` 移除通过 on 添加的事件.移除一个特定的事件处理程序
- `one` 添加一个处理事件到元素，当第一次执行事件以后，该事件将自动解除绑定，保证处理函数在每个元素上最多执行一次
- `trigger` 在对象集合的元素上触发指定的事件
	

#### 4. Ajax

- $.ajax(options)  
	- `type`(默认： “GET”)：请求方法 (“GET”, “POST”, or other)
	- `url` (默认： 当前地址)：发送请求的地址
	- `data`(默认：none)：发送到服务器的数据；如果是GET请求，它会自动被作为参数拼接到url上。非String对象将通过 $.param 得到序列化字符串。
	- `contentType `(默认： “application/x-www-form-urlencoded”)： 发送信息至服务器时内容编码类型
	- `dataType` (默认： none)：预期服务器返回的数据类型(“json”, “jsonp”, “xml”, “html”, or “text”)
	- `async`(默认：true): 默认设置下，所有请求均为异步。如果需发送同步请求，请将此设置为 false
	- `Ajax 回调函数`
		- `beforeSend(xhr, settings)`：请求发出前调用，它接收xhr对象和settings作为参数对象。如果它返回 false ，请求将被取消。
		- `success(data, status, xhr)`: 请求成功之后调用。传入返回后的数据，以及包含成功代码的字符串
		- `error(xhr, errorType, error)`: 请求出错时调用。 (超时，解析错误，或者状态码不在HTTP 2xx)。
		- `complete(xhr, status)`：请求完成时调用，无论请求失败或成功

#### 5. Zepto与JQuery的区别

- Zepto比JQuery体积小，加载比JQuery块
- 对移动端的浏览器支持好
- Zepto把代码拆分为核心模块和其他模块
- 对选择器的支持不一样，Zepto核心模块选择器支持的很少，需要引入selector模块
- Zepto的touch模块对移动端的操作支持很完善，支持`tap` `singTap单击` `doubleTap双击` `longTap长按` `swipe 元素划过时触发`
- gesture模块支持pinch手势
- `clone()深度克隆来复制集合中的所有元素` Zepto此方法不会将数据和事件处理程序复制到新的元素,jquery会利用一个参数来确定是否复制数据和事件处理不相同
- `concat()`为Zepto特有api,添加元素到一个Zepto对象集合形成一个新数组
- `data()`Zepto只能存储字符串，如果要存储任意对象，需要引入`data.js`模块
- `forEach()遍历集合中每个元素` Zepto特有的方法
