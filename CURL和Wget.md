## `curl`使用

##### 1. 简介

> `curl`全称是“CommandLine Uniform Resource Locator”  

>  是利用URL语法在命令行方式下工作的开源文件传输工具,它被广泛应用在Unix、多种Linux发行版中，并且有DOS和Win32、Win64下的移植版本

##### 2. 命令行使用技巧

    $ curl www.baidu.com   //查看源码
    $ curl -o index.html www.baidu.com   //输出源码到index.html
    $ curl -i www.baidu.com  // 显示头信息  
    $ curl -i www.baidu.com  // 显示一次http通信的整个过程
    $ curl -X POST www.baidu.com  // 显示一次http通信的整个过程    
    $ curl -x 192.168.0.109:4000 -o index.html www.baidu.com //通过代理
    $ curl -c -O http://cgi2.tky.3wb.ne.jp/~zzh/screen1.JPG  //断点续传
    $ curl -d "user=abc&password=111" www.baidu.com //Post提交
    
##### 3. curl与wget的区别

  - curl支持更多协议
  - curl在指定要下载的链接时能够支持URL的序列或集合，而wget则不能这样
  - curl可以模拟提交web数据，POST/GET请求，调试网页
  - wget支持递归下载，而curl则没有这个功能

