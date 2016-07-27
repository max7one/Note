## 单例模式 Singleton

> 一个类能返回一个对象的引用（并且永远是同一个）和一个获得该实例的方法（静态方法，通常使用 getInstance 名称）  
那么当我们调用这个方法时，如果类持有的引用不为空就返回该引用，否者就创建该类的实例，并且将实例引用赋值给该类保持的那个引用再返回  
同时将该类的构造函数定义为私有方法，避免其他函数使用该构造函数来实例化对象，只通过该类的静态方法来得到该类的唯一实例

单例在JavaScript的有多种用途，它用来划分**命名空间**  
- 可以减少网页中全局变量的数量(在网页中使用全局变量有风险)
- 可以在多人开发时避免代码的冲突(使用合理的命名空间)

**对象字面量单例**  

缺点:没有什么封装性，所有的属性方法都是暴露的

```js
var singleton= {
	name : 'abc',
	method : function () {
		return this.name;
	},
	init:function () {
		//code
	}
}

var t1 = singleton ;
var t2 = singleton ;
t1 === t2; //返回true
```
**构造函数内部判断**

缺点:构造函数的unique属性是暴露的

```js
function SingletonFunc(){
	// 确保只有一个实例
	if( SingletonFunc.unique !== undefined ){
			return SingletonFunc.unique;   //函数内部到return停止执行
	}
	// 其他代码
	this.name = "abc";
	SingletonFunc.unique = this;
}

var t1 = new SingletonFunc() ;
var t2 = new SingletonFunc() ;
t1 === t2; //返回true
```

**闭包方式**
```js
var single = (function(){
  var unique;
  function Construct(){
    // 生成单例的构造函数的代码
  }
  unique = new Construct();
  return function(){
    return unique;
  } 
})();

var t1 = single();
var t2 = single();
t1 === t2; //返回true
```

## 工厂模式 Factory

工厂模式定义一个用于创建对象的**接口**，这个接口由**子类**决定实例化哪一个类   
该模式使一个类的实例化延迟到了子类,而子类可以重写接口方法以便创建的时候指定自己的对象类型。

```js
var product = {};
product.createA = function () {
	console.log("A");
}
product.createB = function () {
	console.log("B");
}
product.factory = function (type) {
	return new product[type];
}

product.factory('createA');
```

## 观察者模式

观察者模式又叫发布订阅模式（Publish/Subscribe），它定义了一种一对多的关系，让多个观察者对象同时监听某一个主题对象，这个主题对象的状态发生变化时就会通知所有的观察者对象，使得它们能够自动更新自己

优点
- 支持简单的广播通信，自动通知所有已经订阅过的对象
- 页面载入后目标对象很容易与观察者存在一种动态关联，增加了灵活性
- 目标对象与观察者之间的抽象耦合关系能够单独扩展以及重用

```js
//定义一个Observable对象，其内部包含了2个方法：订阅add方法与发布fire方法
var Observable = {
  callbacks: [],
  add: function(fn) {
    this.callbacks.push(fn);
  },
  fire: function() {
    this.callbacks.forEach(function(fn) {
      fn();
    })
  }
}

//使用add开始订阅
Observable.add(function() { console.log(1) })
Observable.add(function() { console.log(2) })

//使用fire开始发布
Observable.fire(); // 1, 2
```