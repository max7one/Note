### XAMPP

  sudo /opt/lampp/lampp startapache  启动apache
  sudo /opt/lampp/lampp startmysql  启动mysql

  更改网站根目录 /opt/lampp/etc/httpd.conf
  修改
    DocumentRoot "D:/xampp/htdocs"
    <Directory "D:/xampp/htdocs">
    重启apache   sudo /opt/lampp/lampp restartapache

### 语法

在开始设置　header("Content-Type: text/html;charset=utf-8");

<?php echo "string" ?>
字符串用`.`来连接

类声明 `class` ,继承 `extends`

echo "\n";  html源代码换行
echo "<br>";　页面显示换行

### 引用

##### require
require("MyRequireFile.php");
这个函数通常放在 PHP 程序的最前面，PHP 程序在执行前，就会先读入 require 所指定引入的文件，使它变成 PHP 程序网页的一部份。常用的函数，亦可以这个方法将它引入网页中。

##### include
使用方法如 include("MyIncludeFile.php");
这个函数一般是放在流程控制的处理部分中。PHP 程序网页在读到 include 的文件时，才将它读进来。这种方式，可以把程序执行时的流程简单化。

##### use 引用模块
`use Phalcon\Mvc\Controller;`

### 关键词　

##### Private

Private是访问控制的最核心部分，因此，在类中被定义成Private的属性（变量）或方法只能在该类内部访问，该类的任何实例（对象）或子类都无法访问，同样，你也不能通过类名直接访问。
##### Protected

Protected的访问级别仅次于Private，被定义为Protected的属性（变量）或方法不仅在本类中可以被访问，在该类的子类中同样可以访问，这是Private属性所不能的。

##### Public

Public具有最大的访问权限，被定义成Public的属性（变量）或方法可以在程序的任何位置、任何时间访问。

##### static

当我们在类中声明一个属性（变量）为static，那么该属性的值在其所有对象中都是可见的，是一个共享变量，因此，static属性值依赖类而非对象。静态属性不能通过对象访问，而是用类名加::符号直接访问。
同样，静态方法也具有对象共享特性，但需要注意如下两点：
1.直接通过类名加::访问静态方法
2.静态方法中不能使用$this关键字
##### Final

如果属性（变量）被Final修饰，那么该属性（变量）值不能被改变，如果是函数，则该函数不能被覆盖或重写。

##### Abstract

定义为Abstract的类不能被实例化。任何一个类，如果它里面至少有一个方法是被声明为Abstract，那么这个类就必须被声明为Abstract。被定义为Abstract的方法只是声明了其调用方式（参数），不能定义其具体的功能实现。

### 异常  exception
`try{}catch{}`

`trｙ`相当于　`if`, `catch`相当于`else`

### 调试

error_log("string"); 输出到`php_error_log`
tail php_error_log -f 在teminal监控

### 连接数据库

    $link1 = mysql_connect('127.0.0.1', 'code1', '');
    $link2 = mysql_connect('127.0.0.1', 'code1', '', true); //开启一个新的连接
    $res = mysql_query('select * from user limit 1', $link1); //从第一个连接中查询数据
