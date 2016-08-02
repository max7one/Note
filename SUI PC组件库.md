## SUI组件库

### 1. 布局

- 响应式布局 `class="sui-container"`

	> 会自动左右居中，并且根据页面的宽度来调整自身宽度，左右两边有合理的边距。很合适作为整个页面内容的容器

- 表格
	- 默认样式`class="sui-table"`
	- 带边框 `class="sui-table table-bordered"`
	- 不带边框 `class="sui-table table-nobordered"`
	- 只有内边框的表格`class="sui-table table-bordered-simple"`
	- 表头在侧边 `class="sui-table table-sideheader"`
	- 斑马线 `class="sui-table table-zebra"`
	- 首要表格 `class="sui-table table-primary"`
	- 二维表格 `class="sui-table table-bordered table-sideheader"`

- 栅格
	- 默认栅格系统

	> 默认栅格系统每一栏是定宽的，并且宽度可以根据屏幕宽度在几个固定值之间变化，区别于流式栅格系统的百分比宽度

	```html
	<div class="grid-demo">
		<div class="sui-row"></div>
	</div>
	```

	- 流式栅格系统

	> 流式栅格系统每一栏的宽度都是其容器的百分比，因此会随着屏幕宽度的变化而不断变化，没有一个固定的宽度像素值

	```html
	<div class="grid-demo">
		<div class="sui-row-fluid"></div>
	</div>
	```

- layout

	> 左右宽度固定中间自适应的布局，默认宽度会铺满整个屏幕。非常适合用在有侧边栏的全屏页面布局。默认的两边宽度是150px，可以根据需要自己重载

	两栏布局

    ```html
	<h2>2 col layout</h2>
	<div class="sui-layout">
	  <div class="sidebar">sidebar</div>
	  <div class="content">content</div>
	</div>
    ```
	三栏布局

    ```html
	<h2>3 col layout</h2>
	<div class="sui-layout layout3">
	  <div class="sidebar">sidebar</div>
	  <div class="content">content</div>
	  <div class="sidebar">sidebar</div>
	</div>
    ```

### 2. 功能样式

- 导航
	- 普通导航 `class="sui-navbar"`
	- 深色导航 `class="sui-navbar navbar-inverse"`
	- 固定在顶部 `class="sui-navbar navbar-fixed-top"`
	- 固定在底部 `class="sui-navbar navbar-fixed-bottom"`

- 分页
	- 普通分页 `class="sui-pagination"`
	- 小型分页 `class="sui-pagination pagination-small"`
	- 大型分页 `class="sui-pagination pagination-large"`
	- 非主流分页 `class="sui-pagination pagination-naked"`

- 文字
	- 全局文本 `sui-text--`
	- label `class="sui-label label--"`
	- tag `class="sui-tag tag-selected"`

- 标签页
	- 默认标签页 `class="sui-nav nav-tabs"`
	- 垂直标签页 `class="sui-nav nav-tabs tab-vertical"`
	- 首要标签页 `class="sui-nav nav-tabs nav-primary"`
	- 胶囊标签页 `class="sui-nav nav-tabs nav-pills"`c
	- 导航条标签 `class="sui-nav nav-tabs tab-navbar"`
	- 包裹标签页 `class="sui-nav nav-tabs tab-wraped"`

- 提示消息
	- 错误信息提示 `class="sui-msg msg-error"`
	- 禁止信息提示 `class="sui-msg msg-stop"`
	- 成功信息提示 `class="sui-msg msg-success"`
	- 警示信息提示 `class="sui-msg msg-warning"`
	- 公告信息提示 `class="sui-msg msg-notice"`
	- 提示信息提示 `class="sui-msg msg-tips"`
	- 提醒信息提示 `class="sui-msg msg-info"`
	- 疑问信息提示 `class="sui-msg msg-question"`
	- 大尺寸提示 `class="sui-msg msg-large msg-error"`
	- 块级提示 `class="sui-msg msg-block msg-error"`
	- 清除提示 `class="sui-msg msg-clear msg-error"`

		> 清除模式区别于成块级模式，Msg内联状态独占一行，常用于表单校验
	- 去边框和底色 `class="sui-msg msg-naked msg-error"`
	- 带关闭按钮提示 `class="sui-msg msg-info msg-block"`

		> 1.4.1版本 增加了一个记忆功能，只需要给 .sui-msg 加上一个id并且增加一个class remember，就可以自动记住当前消息的关闭状态（即关闭之后刷新页面也不会再显示出来）。注意这个功能是使用localStorage实现的

   	 ```html
		<div class="sui-msg msg-info msg-block">
		  <div class="msg-con">通知：特色中国页面自13年４月上线以来，业务整合了更多的地域营销资源
  		  <button type="button" data-dismiss="msgs" class="sui-close">×</button>
		  </div>
		  <s class="msg-icon"></s>
		</div>
  	  ```

- 步骤条
	> `steps-auto`适用于步骤条内容不能过长的情景，极端情况下请自行修改每个step的宽度
	- 定宽步骤条 `class="sui-steps"`
	- 自适应步骤条 `class="sui-steps steps-auto"`
	- 前台定宽步骤条 `class="sui-steps-round"`
	- 前台自适应步骤条 `class="sui-steps-round steps-round-auto"`

- 面包屑
	> `class="sui-breadcrumb"`

- 动画效果
