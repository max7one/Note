## SUI Mobile学习笔记

#### 页面布局
- 容器 `div.page-group`
  - 页面 `div.page` 
    - 标题栏 `header.bar.bar-nav`
    - 内容区 `.content .content-block`
    - 工具栏 `nav.bar.bar-tab`
      - 子栏 `a.tab-item`
      - 子栏状态 `.active`
    - 其他面板 `.panel.panel-left.panel-reveal`
      - 内容 `.content-block` 
        - 关闭 `a.close-panel`
  
> page-group 为 page集合的容器，里面放多个平行的.page，其他.page作为内联页面由路由控制展示

> 单个page ,第一个.page默认被展示

- 响应式栅格 `div.grid-demo` 
  - 每行 `.row`
  - 行内分区 `col-80` 占据父容器width的80%

#### rem
rem 是相对于 html 元素的 font-size 的一个单位。如果 html 上定义了 font-size: 20px;，则无论在任何地方都是 1rem = 20px 这个大小不会受到父元素的影响。

rem的优势在于实现强大的屏幕适配

#### 路由 
> Router默认开启，会自动拦截所有链接的Touch行为，如果希望一个链接走浏览器原生跳转而不使用router，可以在链接上增加 class="external" 或者自定义属性,如 <a href="xxx" external>xxx</a>.

> 如果需要禁用路由功能,那么可以在 zepto 之后, msui 之前使用 script $.config = {router: false} 来禁用.

路由功能的前提
  - 每个url对应的html文档所展示的内容必须放在`div.page-group`
  - html文档中，每个可以用来切换显示的块都应该有`page`的class
  
在任意链接上增加一个 .back 类，点击就会自动返回到上一页（调用 history.back）

1. 内联页面

> 可以在同一个HTML文件中内联编写多个页面。每一个页面都是一个 .page 容器，如果有多个页面，则需要用 .page-current 标记出第一次进入的时候应该显示的页面。 

> 每一个 .page 容器都应该有一个全局唯一的id，路由器会使用这个id作为唯一标示，如果没有设置id，可能会导致路由出错

2. AJAX加载新页面

注意: ajax 和 pushState 限制了 ajax 加载的页面只能是同域.

> 通过ajax加载新页面和普通的链接写法没有区别，路由器会自动拦截链接的点击事件，并通过ajax请求加载新的页面。

#### 内容区

> 如果希望页面内容所有两边有间距，可以把内容放在 .content-padded 容器中


#### 页面元素

- 按钮 `a.button`
  - 颜色 `.button-light` `.button-warning` 
  - 状态 `.disabled` 不可用
  - 形状 `.button-round` 圆角矩形
  - 大小 `.button-big`
  - 填充 `.button-fill`
- 按钮组 `p.buttons-row`
  - 状态 `.active`
- 列表 `div.list-block`
  - 栅格 `.row.col-50` 容器宽的50%
  - 子项目 `a.item-link.list-button`
- 搜索栏  `div.searchbar`
  - 取消 `.searchbar-cancel` // 自动隐藏的
  - 输入框 `div.search-input`
    - 标签 `label.icon.icon-search`
    - 文本输入 `input[type="search"]`
- 

#### 标签页
- 标签栏 `.buttons-tab`
  - 子标签 `a.tab-link.button` `a[href="#tab1"]`
  - 子标签状态 `.active`
- 关联内容 `div.tabs`
  - 关联 `div#`tab1
  - 单个内容 `div.tab`
  - 状态 `.active`
- 二级标签页 `.button-row`
- fixed标签页 `div.fixed-tab`
  - 位置 `div[data-offset="44"]` 距离页面顶部44px
  
#### 对话框 `Modal`
Modal 是从App的主要内容区域上弹出的一小块内容块,是“临时视图”的一部分   
多个Modal类组件（包括toast）同时被呼起时，会按先后顺序被缓存在队列中，前一个modal关闭后，下一个modal才会打开   
Modals 可以只用JavaScript打开

#### 卡片
- 卡片内容  `div.card`
  - 卡头 `.card-header`
  - 内容 `.card-content .card-content-inner`
  - 卡脚 `.card-footer`

#### popup
通过HTML
  可以通过在链接上使用特定的类和data属性打开和关闭所需的popups：

- 为了打开popup，我们需要添加 "open-popup" 类到任意 HTML 元素上 (最好是链接)
- 为了关闭popup，我们需要添加 "close-popup" 类到任意 HTML 元素上 (最好是链接)
- 如果你的App里有超过一个popups, 你需要指定适当popup，则需添加额外的属性 data-popup=".my-popup" 到这个 HTML 元素上

**a链接 必须去掉href属性,否则页面不能完美打开**
