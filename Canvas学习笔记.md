### 简介

> Canvas （画布）是在HTML5中新增的标签用于在网页实时生成图像，并且可以操作图像内容，基本上它是一个可以用JavaScript操作的位图

### Canvas与SVG的比较

1. Canvas 是一个基于 JavaScript 的绘图 API，而 SVG 使用一个 XML 文档来描述绘图。
2. Canvas不支持事件处理器，SVG支持事件处理器
3. Canvas适合图像密集型的游戏，其中的许多对象会被频繁重绘,SVG最适合带有大型渲染区域的应用程序

### Canvas的简单应用

```html
<!--  Canvas对象只有两个属性—— width和height, id属性并不是<canvas>元素所特有的而是全局属性  -->
<canvas id="myCanvas" width="150" height="150"></canvas>   

<script type="application/javascript">
  var canvas = document.getElementById("myCanvas"); //获取canvas元素
  var ctx = canvas.getContext("2d");  //getContext方法指定参数2d，表示该canvas对象用于生成2D图案
  ctx.beginPath(); // 开始路径
  ctx.moveTo(20, 20); // 路径起点，坐标为(20,20)
  ctx.lineTo(200, 20); // 绘制到(200,20)的线
  ctx.lineWidth = 1.0; // 设置线宽
  ctx.strokeStyle = "#CC0000"; // 设置线的颜色
  ctx.stroke(); // 对线进行着色，使线可见
}
</script>
```  

### 注意事项

##### 1.drawImage需要再图片加载完成后才能绘制
```js
img.onload=function(){
  drawImage(img,30,30);
}

//或者事件捕获
window.addEventlistener('load',function () {
  drawImage(img,30,30);
})
```

##### 2.移动canvas的原点(0,0)
```js
//移动canvas原点到(100,100)
ctx.translate(100,100)
```
**`rotate`、`drawImage`是以原点绘制的**   
通过`ctx.save()`,`ctx.restore()`来**还原**原点

##### 3.动画

动画通过`setInterval(function() {},100)`来实现





    






