#### 伪类和伪元素的区分

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
<style>
.first-letter {color: red}
</style>
<p><span class='first-letter'>I</span> am stephen lee.</p>
```

`css3` 为了区分两者，已经明确规定了伪类用一个冒号来表示，而伪元素则用两个冒号来表示
```
:Pseudo-classes
::Pseudo-elements
```
但因为兼容性的问题，所以现在大部分还是统一的单冒号   
但是抛开兼容性的问题，我们在书写时应该尽可能养成好习惯，区分两者


## table
`colspan` 跨列; 合并列
`rowspan` 跨行; 合并行
