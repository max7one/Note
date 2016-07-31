- thead tbody 会被浏览器自动解析

- a[title] 当鼠标放在上面的时候会显示出title

- form要放在table里面 会有像素的差别

- bgcolor 是 html标签属性  
  background-color 是css属性

- CSS3用法
1. 容器内部元素(块级和行内都行)水平垂直居中
```html
<style>
    .box {
        display: flex;
        align-items: center; /*垂直居中*/
        justify-content: center;/*水平居中*/
        width: 300px;
        height: 300px;
        border: 1px solid #0000ff;
    }
    .inner{
        width: 100px;
        height: 100px;
        border: 1px solid #ff0000;
    }
</style>
<div class="box">
    <div class="inner"></div>
    <!-- <span>slkjf</span>  -->  行内元素
</div>
```

- 元素自适应

    浮动元素的宽度是随内容变化的
    父容器设为 float:left或者 display:inline-block
    子元素 width:100% 也会自适应



- 刷新当前页

    windows.history.go(0); 从缓存里读取
    windows.location.reload(); 重新向服务器发起请求,相当与F5
