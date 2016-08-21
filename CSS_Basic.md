## 伪类和伪元素的区分

- `CSS 伪类`用于向某些选择器添加特殊的效果。
- `CSS 伪元素`用于将特殊的效果添加到某些选择器。

伪类的效果可以通过添加一个**实际的类**来达到

```html
<!--使用伪类-->
<style>
p>i:first-child {color: red}
</style>
<p>
    <i>first</i>
    <i>second</i>
</p>
```
```html
<!--不使用伪类-->
<style>
.first-child {color: red}
</style>
<p>
    <i class="first-child">first</i>
    <i>second</i>
</p>
```

而伪元素的效果则需要通过添加一个**实际的元素**才能达到
```html
<!--使用伪元素-->
<style>
p:first-letter {color: red}
</style>
<p>I am stephen lee.</p>
```
```html
不使wei
<style>
.first-letter {color: red}
</style>
<p><span class='first-letter'>I</span> am stephen lee.</p>
```

`css3` 为了区分两者，已经明确规定了伪类用一个冒号来表示，而伪元素则用两个冒号来表示
```
:Pseudo-classes  伪类
::Pseudo-elements  伪元素
```
但因为兼容性的问题，所以现在大部分还是统一的单冒号   
但是抛开兼容性的问题，我们在书写时应该尽可能养成好习惯，区分两者


## table
`colspan` 跨列; 合并列  
`rowspan` 跨行; 合并行

## 定位

`position:absolute` 包含 `display:block` 不需要再添加`display`属性

## 百分比
1. 根据**自身元素**的宽高来计算的    
    - `transform: translate()`,`transform-origin`
    - `border-radius`  设为50%,相当于椭圆
    - `background-size`

2. 根据**父元素**的宽高计算
    - `width`,`height`
    - `max-width`,`min-width`
    - `margin`, `padding`
    - `left`,`right`

3. 其他
    - `font-size` 相对于直接父元素的font-size
    - `line-height` 相对于元素自身的font-size
    - `vertical-align` 相对于元素自身的line-height
    - `background-position` 方向长度 / 该方向除背景图之外部分总长度 * 100    
    - `position: absolute` 相对于离它最近的那个 position 不为 static 的外层元素
    - `position: fixed` 相对于窗口

## `reset` CSS 文件的作用和使用它的好处

好处：因为各个浏览器默认对CSS的渲染有差异，"reset" CSS 通过重新定义标签样式，对浏览器进行默认样式“清零”重置，样式保持一致
不足:css文件大小增加，许多样式本身就需要重置，多此一举，增加浏览器对CSS 的渲染

## 标准盒模型和怪异盒模型的区别

标准盒模型 box-sizing:content-box
怪异盒模型 box-sizing:border-box

## 响应式布局

@media screen and (max-width:960px){}

## CSS3新特性

- 实现圆角（border-radius）
- 阴影（box-shadow）
- 对文字加特效（text-shadow）
- 线性渐变 (gradient)
- 动画(transform)
- 过度(transition)
- 多列(column-)

## `display: none;`与`visibility: hidden;`的区别

1.display:none;会让元素完全从渲染树中消失，渲染的时候不占据任何空间；
  visibility: hidden;不会让元素从渲染树消失，渲染师元素继续占据空间，只是内容不可见  
2.display: none;是非继承属性，子孙节点消失由于元素从渲染树消失造成，通过修改子孙节点属性无法显示；visibility: hidden;是继承属性，子孙节点消失由于继承了hidden，通过设置visibility: visible;可以让子孙节点显式  
3.修改常规流中元素的display通常会造成文档重排。修改visibility属性只会造成本元素的重绘。  
4.读屏器不会读取display: none;元素内容；会读取visibility: hidden;元素内容

## css权重

 !important > 内联 > id > class > tag

## `z-index`的使用规则

z-index 仅能在定位元素上奏效
  position:relative、position:absolute和position:fixed参与的情况下才有作用，表示层级

从父规则  
  如果 A, B 节点都定义了 position:relative  
  A 节点的 z-index 比 B 节点大, 那么 A 的子节点必定覆盖在 B 的子节点前面

## css中单位`px`和`em`,`rem`的区别

像素px是相对于显示器屏幕分辨率  
em是相对长度单位。相对于当前对象内文本的字体尺寸(em会继承父级元素的字体大小)  
rem相对的只是HTML根元素


## `display:flex`的使用场景以及浏览器的支持

## `display:inline-block`有缺点，怎么解决

移除上下行空格、使用margin-left负值、给父元素使用font-size:0、letter-spacing、word-spacing


## 浏览器CSS选择器匹配顺序

	从右到左

## `link`与`@import`的区别

	link是HTML方式， @import是CSS方式
	页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载;

## 什么是`CSS Sprite`，有什么优点

将多个小图片拼接到一个图片中。通过background-position和元素尺寸调节需要显示的背景图案

优点:
1. 减少HTTP请求数，极大地提高页面加载速度,增加图片信息重复度
2. 提高压缩比，减少图片大小
3. 更换风格方便，只需在一张或几张图片上修改颜色或样式即可实现

缺点:
1. 图片合并麻烦
2. 维护麻烦，修改一个图片可能需要从新布局整个图片，样式


## 如何创建块级格式化上下文(`block formatting context`),BFC有什么用

	创建规则:
	1.根元素
	2.浮动元素(float不是none)
	3.绝对定位元素(position取值为absolute或fixed)
	4.display取值为inline-block,table-cell, table-caption,flex, inline-flex之一
	5.overflow不是visible的元素

	作用:
	1.可以包含浮动元素
	2.不被浮动元素覆盖
	3.阻止父子元素的margin折叠

## 什么是外边距折叠，如何消除外边距折叠

	两个或多个毗邻的普通流中的块元素垂直方向上的margin会折叠
	浮动元素/inline-block元素/绝对定位元素的margin不会和垂直方向上的其他元素的margin折叠
	创建了块级格式化上下文的元素，不会和它的子元素发生margin折叠

## 清除浮动有几种方法

	1.额外标签法，style="clear:both;"
    （缺点：不过这个办法会增加额外的标签使HTML结构看起来不够简洁。）
    2.使用after伪类 content:"."; height:0; visibility:hidden; display:block; clear:both; }
    3.浮动外部元素（BFC）
    4.设置`overflow`为`hidden`或者autoIE 8以下版本的浏览器中的盒模型有什么不同
