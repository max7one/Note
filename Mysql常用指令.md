### 安装和启动

    sudo apt-get install mysql-server
    安装过程中会要求输入密码 (输入简单的密码)

    mysql -u root -p  启动mysql

    修复 ctrl-w  向前删除单词的方法
    在 home文件夹下 向 .editrc 插入 bind "^W" ed-delete-prev-word

    安装 mycli
    pip install mycli
    启动
    /home/newday/.local/bin/mycli -h localhost -P 3366 -u "root" -p ""

### 数据类型    

- 数字类型
  - 整数: tinyint、smallint、mediumint、int、bigint
  - 浮点数: float、double、real、decimal
- 日期和时间
  - date、time、datetime、timestamp、year
- 字符串类型
  - 字符串: char、varchar
  - 文本: tinytext、text、mediumtext、longtext
  - 二进制(可用来存储图片、音乐等): tinyblob、blob、mediumblob、longblob

### 常用命令    

    //数据库操作
    show databases;  // 显示所有数据库
    create database 数据库名; //创建数据库mytest1
    create database 数据库名 character set gbk; //显示中文
    alter database 数据库名 character set gb2312; //改变数据库编码
    show variables like 'character_set_database'; //显示当前数据库的编码
    use 数据库名;      // 使用数据库
    drop database 数据库名 //删除数据库

    //表操作
    create table 表名(id int); // 创建表(必须有至少一列);
    create table 表名(name varchar(10)); //varchar要设置长度
    // 整型unsigned禁用负值
    create table students
    (
    id int unsigned not null auto_increment primary key,
    name char(8) not null,
    sex char(4) not null,
    age tinyint unsigned not null,
    tel char(12) null default "-"
    );

    alter table 表名 rename 新表名; //重命名表
    alter table 表名 add primary key(id); //添加主键为id
    show tables;    // 显示当前数据库中的所有table
    drop table 表名;   //删除表
    drop table if exists 表名; // 如果存在表的话删除

    导入 外部sql文件
    先 use database;
    source /path/name.sql

    truncate table 表名
    这样不但将清除数据，而且可以重新位置identity属性的字段

### 表的增删改查

    desc 表名 //查看表结构

    alter table 表名 add 字段名 字段类型(长度); //插入字段
    alter table 表名 drop 字段名; //删除字段

    select 列名称 from 表名称 [查询条件]; //查询表中规定列
    select * from 表名; //查询表中所有列

    insert [into] 表名 (字段) values(值); //插入数据  

    update 表名称 set 列名称=新值 where [条件]; //更新数据

    delete from 表名称 where [条件]; //删除数据
    delete from students where age<20;

### 其他

    SELECT COUNT("栏位名") FROM "表格名"

    select * from table limit m,n
    其中m是指记录开始的index，从0开始，表示第一条记录
    n是指从第m+1条开始，取n条

    select * from tablename limit 2,4
    即取出第3条至第6条，4条记录
    (常用于分页)
