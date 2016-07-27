## Bootstrap

#### Bootstrap简介

- 什么是Bootstrap<br>
	- Bootstrap是一个用于快速开发Web应用程序和网站的前端框架，Bootstrap是基于HTML、CSS、JAVASCRIPT开发的
- 为什么使用Bootstrap
	- 对移动设备支持优先
	- 所有主流浏览器都支持Bootstrap
	- 容易上手
	- 响应式设计
	- 包含功能强大的组件，易于定制
	- 开源
- Bootstrap所包括的内容
	- 基本结构：Bootstrap 提供了一个带有网格系统、链接样式、背景的基本结构
	- CSS: 全局的CSS设置、定义基本的HTML元素样式、可扩展的class、以及一个先进的网格系统
	- 组件：包含了十几个可重用的组件，用于创建图像、下拉菜单、导航、警告框、弹出框等
	- JavaScript插件：包含了十几个自定义的jQuery插件

#### Bootstrap CSS
- 网格系统
	- 响应式的
	- 移动设备优先的
	- 不固定，随着设备或视口大小的增加而适当地扩展到12列
- 代码 
	- 内联显示代码 `<code>`
	- 多行代码 `<pre>`
- 表格
	- 表格类 `.table` 
	- 条纹表格 `.table-striped`
	- 边框表格 `.table-bordered`
	- 悬停表格 `.table-hover`
	- 精简表格 `.table-condensed`
	- 响应式表格 `.table-responsive`
- 表单
	- 垂直表单
		- 向父`<form>`元素添加`role="form"`
		- 把标签和控件放在一个带有`form-group`的 `<div>`中
		- 向所有的文本元素 `<input>`、`<textarea>` 和 `<select>` 添加`.form-control`
	- 内联表单
		- 向 `<form>` 标签添加 `.form-inline`
	- 水平表单
		- 向父 `<form>` 元素添加`.form-horizontal`
		- 把标签和控件放在一个带有 `.form-group` 的 `<div>` 中
	 	- 向标签添加`.control-label`
- 辅助类
	- 文本 `.text-`
	- 背景 `.bg-`

#### Bootstrap 布局组件
- 字体图标 `.glyphicon`
- 下拉菜单 `.dropdown`
- 导航栏   `.navbar` `.navbar-default`
- 分页     `.pagination`
- 标签 	   `.lable`
- 徽章	   `.badge`
- 超大屏幕 `.jumbotron`
- 警告	   `.alert` `.alert-success` `.alert-warning`
- 进度条   `.progress`
- 多媒体对象  `.media` `.media-list`
- 列表组  	`.list-group` `.list-group-item`
- 面板 		`.panels`
