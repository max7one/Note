<!DOCTYPE html>
<!--<html manifest='item.manifest'>-->
<html lang="en">
<head>
    <meta charset="utf-8">
    <link rel="shortcut icon" href="/favicon.ico">
    <title>爱用商品</title>
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black">
    <meta name="format-detection" content="telephone=no">
    <link rel="stylesheet" href="//g.alicdn.com/msui/sm/0.6.2/css/sm.min.css">
    <link rel="stylesheet" type="text/css" href="css/itemlist.css"/>
    <script src="js/suport/phoneWidth.js"></script>
</head>

<body>
<div class="page-group">
    <!-- 单个page ,第一个.page默认被展示-->
    <div class="page page-current" id="itemlist">
        <style>
            .itemcard{
                margin: 0 0 .5rem;
            }
            .itemcard .card-footer {
                background: #e8e8e8;
                padding: 0;
            }

            .itemcard .row{
                text-align: center;
            }

            .itemcard .col-33{
                font-size: 1rem;
                font-weight: bold;
                border: 1px solid #bbb;
                height: 2.2rem;
                line-height: 2.2rem;
            }

        </style>
        <header class="bar bar-nav">
            <a href="" class="button button-link button-nav pull-left">
                <span class="icon icon-menu"></span>
            </a>
            <a href="" class="button button-link button-nav pull-right">
                <span class="icon icon-search"></span>
            </a>
            <a href="javascript:;">
                <h1 class="title">
                    <span>售出中(123)</span>
                    <span class="icon icon-down"></span>
                </h1>
            </a>
        </header>
        <!-- 这里是页面内容区 -->
        <div class="content">
            <!-- <script id="itemlist_template" type="text/x-dot-template"> -->
            <!-- </script> -->

            <!-- 宝贝列表 -->
            <div class="card itemcard">
                <div class="card-content">
                    <div class="list-block media-list">
                        <ul>
                            <li>
                                <a href="#" class="item-content">
                                    <div class="item-media">
                                        <img src="http://gqianniu.alicdn.com/bao/uploaded/i4//tfscom/i3/TB10LfcHFXXXXXKXpXXXXXXXXXX_!!0-item_pic.jpg_250x250q60.jpg" width="80">
                                        <div style="background:#22cd6d;width:80px;position:absolute;margin-top: 2.4rem;margin-left: -3.19rem;height:20px;color:white;text-align:center;font-size:12px;">已推荐</div>
                                    </div>
                                    <div class="item-inner">
                                        <div class="item-title">标题</div>
                                        <div class="item-title-row">
                                            <div class="item-title">日期</div>
                                            <div class="item-after">件数</div>
                                        </div>
                                        <div class="item-title-row">
                                            <div class="item-title">价格</div>
                                            <div class="item-after">到期时间</div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                        </ul>
                    </div>
                </div>
                <div class="card-footer row no-gutter">
                    <div class="col-33">重发</div>
                    <div class="col-33 no-gutter">橱窗推荐</div>
                    <div class="col-33 no-gutter">删除</div>
                </div>
            </div>
            <div class="card itemcard">
                <div class="card-content">
                    <div class="list-block media-list">
                        <ul>
                            <li>
                                <a href="#" class="item-content">
                                    <div class="item-media">
                                        <img src="http://gqianniu.alicdn.com/bao/uploaded/i4//tfscom/i3/TB10LfcHFXXXXXKXpXXXXXXXXXX_!!0-item_pic.jpg_250x250q60.jpg" width="80">
                                        <div style="background:#22cd6d;width:80px;position:absolute;margin-top: 2.4rem;margin-left: -3.19rem;height:20px;color:white;text-align:center;font-size:12px;">已推荐</div>
                                    </div>
                                    <div class="item-inner">
                                        <div class="item-title">标题</div>
                                        <div class="item-title-row">
                                            <div class="item-title">日期</div>
                                            <div class="item-after">件数</div>
                                        </div>
                                        <div class="item-title-row">
                                            <div class="item-title">价格</div>
                                            <div class="item-after">到期时间</div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                        </ul>
                    </div>
                </div>
                <div class="card-footer row no-gutter">
                    <div class="col-33">重发</div>
                    <div class="col-33 no-gutter">橱窗推荐</div>
                    <div class="col-33 no-gutter">删除</div>
                </div>
            </div>
            <p id="showlist"></p>
        </div>
        <!-- 默认必须要执行$.init(),实际业务里一般不会在HTML文档里执行，通常是在业务页面代码的最后执行 -->
    </div>
</div>
<script type='text/javascript' src='//g.alicdn.com/sj/lib/zepto/zepto.min.js' charset='utf-8'></script>
<script type='text/javascript' src='//g.alicdn.com/msui/sm/0.6.2/js/sm.min.js' charset='utf-8'></script>
<script src="js/item-top.js"></script>
<script src="js/suport/Dot_Layload_Beacon.js"></script>
</body>
</html>
