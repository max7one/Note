## nginx的使用以及与apache的区别

##### 1. 简介

> Nginx ("engine x") 是一个高性能的HTTP和反向代理服务器
> 因它的稳定性、丰富的功能集、示例配置文件和低系统资源的消耗而闻名

##### 2. 使用指南

    ubuntu安装    
      $ sudo apt-install nginx
    
    命令行使用     
      $ sudo nginx  //启用nginx 
      $ sudo ./sbin/nginx
      $ sudo nginx -s quit  //退出nginx
      $ sudo nginx -s reload  //重载
      
     配置文件   /etc/nginx/sites-available/default
                  
##### 3. 区别                

- nginx优点
  - 轻量级，同样起web 服务，比apache 占用更少的内存及资源
  - 抗并发，nginx 处理请求是异步非阻塞的，而apache 则是阻塞型的，在高并发下nginx 能保持低资源低消耗高性能
  - 配置相对简单

- apache优点
  - 稳定
  - 模块多
  - 处理动态有优势
  - rewrite相对更好

