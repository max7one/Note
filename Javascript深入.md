## this关键词

this是js的一个关键字，随着函数使用场合不同，this的值会发生变化。
但是有一个总原则，那就是this指的是调用函数的那个对象。

this一般情况
- 是全局对象Global。 
- 作为方法调用，那么this就是指这个对象
- 构造函数内的this指向 new出来的实例
- 函数用call或者apply调用,fn.call(obj) fn函数内的this指向obj

在函数中this到底取何值，是在函数真正被调用执行的时候确定的，函数定义的时候确定不了  
因为this的取值是执行上下文环境的一部分，每次调用函数，都会产生一个新的执行上下文环境。

## new的作用

1. 创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。
2. 属性和方法被加入到 this 引用的对象中。
3. 新创建的对象由 this 所引用，并且最后隐式的返回 this 。

对象都是通过构造函数通过`new`创建的

```js
var obj = { a: 10, b: 20 };
//等价于
var obj = new Object();
obj.a = 10;
obj.b = 20;
```

构造函数的特点
- 函数体内部使用了this关键字，代表了所要生成的对象实例。
- 生成对象的时候，必需用new命令，调用构造函数。

如果构造函数的return语句返回的是对象，new命令会返回return语句指定的对象  
构造函数默认返回构造后的上下文对象

## 原型和原型链

构造函数中prototype对象有一个constructor属性，默认指向prototype对象所在的构造函数

```js
function P() {}
P.prototype.constructor === P   //true
```

由于constructor属性定义在prototype对象上面，意味着可以被所有实例对象继承

`prototype`和`__proto__`的区别
JavaScript的所有对象，都有自己的继承链。
也就是说，每个对象都继承另一个对象，该对象称为“原型”（prototype）对象。

函数也是一种对象,也是属性的集合
JavaScript默认的给函数一个属性 `prototype`
每个函数都有一个属性叫做`prototype`,这个`prototype`的属性值是一个对象
默认有一个叫做`constructor`的属性，指向`prototype`对象所在的构造函数
和`__proto__`的属性,**指向构造函数的`prototye`**

对象是由Object构造函数通过 new 创建的
每个对象都有一个隐藏的属性  `__proto__`，这个属性引用了创建这个对象的函数的`prototype`

JavaScript默认的给实例对象一个属性`__proto__ ` 
实例对象的`__proto__`属性指向构造函数`obj.constructor`的prototype属性
`obj.constructor`继承自`obj.__proto__.constructor`

```js
obj.__proto__ === Object.prototype
obj.__proto__ === obj.constructor.prototype
```

这里的`__proto__`是`隐式原型`

自定义函数的__proto__指向的就是Object.prototype
但是Object.prototype的__proto__指向的是null

```js
Object.prototype.__proto__ === null;  
Function.prototype.__proto__ === Object.prototype;
Function.__proto__ === Function.prototype
Object.__proto__ === Function.prototype
```

函数是被Function构造的

JavaScript原型链和继承

访问一个对象的属性时，先在基本属性中查找，如果没有，再沿着`__proto__`这条链向上找，这就是原型链
`hasOwnProperty`可以判断一个属性到底是基本的还是从原型中找到的

在JavaScript中，每一个对象都有一个对应的原型对象，被称为prototype对象。
定义在原型对象上的所有属性和方法，都能被派生对象继承。这就是JavaScript继承机制


获取实例对象obj的原型对象，有三种方法
```js
- obj.__proto__
- obj.constructor.prototype
- Object.getPrototypeOf(obj)
```
