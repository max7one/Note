### for的用法

    for(initialize; test; increment) {
      statement
    }
    // initialize 循环的初始值，只在循环开始时执行一次
    // test   检查循环条件，只要为真就进行后续操作
    // increment 完成后续操作，然后返回上一步，再一次检查循环条件

    `break` 和 `continue`不能再函数内用,会报错

    `for...in` 可以用来遍历对象,不建议用来遍历数组(会把数组对象的键遍历出来)

> 当变量之前设定过，`initialize` 可以为空

### 三元运算符

    (contidion) ? expression1 : expression2

    如果contidion为true，则返回expression1的值，否则返回expression2的值

可以把三元运算的返回值再赋值给一个变量    

    var a = (contidion) ? expression1 : expression2

    执行顺序：先执行三元运算，后执行赋值

### 回调函数    

> 函数A作为参数(函数引用)传递到另一个函数B中，并且这个函数B执行函数A。我们就说函数A叫做回调函数。如果没有名称(函数表达式)，就叫做匿名回调函数

```js
function A(){};
function B(A){
  console.log("hello");
  A();
}
```

### 作用域和变量提升

> 作用域分为两种，全局作用域和函数作用域  
> 函数作用域内定义的变量和方法不能在外部使用

在作用域内使用`var` 声明的变量和函数声明会被提升至作用域顶部

### apply和call

`apply`和`call`可以改变函数调用时`this`的指向
第一个参数为`this`所指向的对象
`apply`后面的参数为包含所有参数的数组 Array ~ apply
`call`后面的参数为多个参数

如果call方法没有参数，或者参数为null或undefined，则等同于指向全局对象。
a.call(window)

### bind

`bind`方法用于将函数体内的`this`绑定到某个对象，然后返回一个新函数

```js
var print = console.log;
print(2); // log内的this指向window
// TypeError: Illegal invocation

// var print1 = console.log.bind(console);
// print1(2);  bind方法将log方法内部的this绑定到console对象
// 2

```

### `top`    

top.onclick=function(){};
相当于给window.top绑定click事件

###  Math

```js
function getRandomNumber(min, max){
    return Math.floor(Math.random() * (max - min + 1)) + min;
}

getRandomNumber(15, 20);

Math.max.apply(null, array)

Math.pow(2,53) === Math.pow(2,53) + 1  //true
```

###  Array

Array.prototype.indexOf();   
判断数组是否存在某值 不存在返回-1

slice()就是对应String的substring()版本，它截取Array的部分元素，然后返回一个新的Array

数组末尾添加 `push` 删除 `pop`
数组头部添加 `unshift` 删除 `shift`

splice()方法是修改Array的“万能方法”，它可以从指定的索引开始删除若干元素，然后再从该位置添加若干元素
```js
var arr = ['Microsoft', 'Apple', 'Yahoo', 'AOL', 'Excite', 'Oracle'];
// 从索引2开始删除3个元素,然后再添加两个元素:
arr.splice(2, 3, 'Google', 'Facebook'); // 返回删除的元素 ['Yahoo', 'AOL', 'Excite']
arr; // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']
// 只删除,不添加:
arr.splice(2, 2); // ['Google', 'Facebook']
arr; // ['Microsoft', 'Apple', 'Oracle']
// 只添加,不删除:
arr.splice(2, 0, 'Google', 'Facebook'); // 返回[],因为没有删除任何元素
arr; // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']
```

```js
//for循环
Array.apply(null, Array(5)).forEach(function(){
// ...
});

Array.prototype.slice.call({ 0: 'a', 1: 'b', length: 2 })

var arr1=new Array("1","2","3");   
var arr2=new Array("4","5","6");   
Array.prototype.push.apply(arr1,arr2);   

var str= "hello world"
String.prototype.spa=function () {
  return this.split('').join(' ');
}
str.spa(); // "h e l l o   w o r l d"
```

### 执行时间

```js
function test(func){
 var start = new Date().getTime();//起始时间
 func();//执行待测函数
 var end = new Date().getTime();//接受时间
 return (end - start)+"ms";//返回函数执行需要时间
}

var time = test(myfunc);
console.log(time);
```

### ParseInt

全局函数 parseInt(string, radix) 的参数radix必须介于2~36之间   
**radix为进制 默认10进制**  

而且字符串string中的数字**不能大于radix**才能正确返回数字结果值

```js
 ["1", "2", "3"].map(parseInt)  
 // [1,NaN,NaN]

 parseInt("1",0); // 1
 parseInt("2",1); // NaN
 parseInt("3",2); // NaN
```

### String

```js
String('123') === '123'; // true  
new String('123') === '123'; //false  左边为对象
```
'(111)'.slice(1,-1); // '111'

### 构造函数  

1. 为了保证构造函数必须与new命令一起使用
一个解决办法是在构造函数内部使用严格模式，即第一行加上use strict。

2. 在构造函数内部
if (!(this instanceof Fubar)) {
  return new Fubar(foo, bar);
}

### setInterval

setInterval,setTimeout 内部 `this`指向Window

```js
function func(){
  setInterval(function () {
    //loop
  },time)
}

function func() {
  //loop
  setTimeout(func,time)
}
```

### canvas

ctx.beginPath();重置路线
