### 常用命令

    ls *    列出当前目录下所有非隐藏文件
    ls t*   列出当前目录中所有以“t”开头的目录的详细内容
    ls -l   长数据串列出，包含文件的属性与权限等等数据

    /dev/null 黑洞设备 (用来删除文件)

    more / less  
    通过shell查看文本，more只能往下，less可上可下

    history  查看历史

    touch -t 201211142234.50 log.log
    设定文件的时间

    cat主要有三大功能：
        1.一次显示整个文件:cat filename
        2.从键盘创建一个文件:cat > filename 只能创建新文件,不能编辑已有文件.
        3.将几个文件合并为一个文件:cat file1 file2 > file

    tac (反向列示)  tac log.txt
      cat 是由第一行到最后一行连续显示在萤幕上
      tac 则是由最后一行到第一行反向在萤幕上显示出来

    header 头　
    tail 显示指定文件末尾内容，不指定文件时，作为输入信息进行处理。常用查看日志文件
      -f 循环读取，监控

    nl 123.log  (-b 空白行加上行号)
    用 nl 列出文件内容(空白行不会加上行号)

    diff 命令 比较两个文件

### 进程

    ps aux | grep nginx  
    ps -ef | grep mysqld
    把进程中包含nginx的信息列出来

    sudo kill -9 [pid]  进程停止

    top  查看cpu,内存占用

### 网络    

    netstat -tnl | grep 9000
    查看端口是否被占用

    ifconfig -a  查看IP地址

    ping   查看连接延迟

### 查找文件

    which   查看可执行文件的位置
    whereis 用于程序的所在目录查找
    locate  配合数据库查看文件位置
    sudo updatedb  升级库

    find    实际搜寻硬盘查询文件名称
    find . -name "*.log"      # 在当前目录查找 以.log结尾的文件
    find /opt/soft/test/ -perm 777    查找/opt/soft/test/目录下 权限为 777的文件
    find . -type f -name "*.log"      查找当目录，以.log结尾的普通文件
    find . -type d | sort         查找当前所有目录并排序
    find . -size +1000c -print    查找当前目录大于1K的文件
    find / -name '*mysql*'      在根目录查找文件名包括mysql的文件

### 权限

    权限范围：
    u ：目录或者文件的当前的用户
    g ：目录或者文件的当前的群组
    o ：除了目录或者文件的当前用户或群组之外的用户或者群组
    a ：所有的用户及群组

    权限代号：
    r ：读权限，用数字4表示
    w ：写权限，用数字2表示
    x ：执行权限，用数字1表示
    - ：删除权限，用数字0表示
    s ：特殊权限

    chmod 777  /www  创建一个 /www 目录设置为 777 权限
    chmod -R 777 dir  改变dir下所有文件的权限  
    0表示没有权限，1表示可执行权限，2表示可写权限，4表示可读权限
    sudo chmod -R a+x test 对所有用户可执行

    1、Linux使用User和Group控制使用者对文件的存取权限 
    2、用户使用账号和口令登录Linux 
    3、每个文件都有owner,并且owner属于某个Group 
    4、每个程序都有owner和Group 


    1、每个用户都有一个唯一的User  ID 
    2、User的信息存储在/etc/passwd中 
      1)存储用户名和home目录等信息 
      2)/etc/shadow 
    3、每个User都有一个home目录 
    4、User未经授权将禁止读写或执行其他User的文件 
    5、root用户解读 
      1)超级管理员账号,具有至高无上的权限 
      2)一般不要随便用root登录并操作系统 

     1、每个User都属于一个Group,具有唯一的标识符gid 
     2、Group信息存储于/etc/group中 
       1)gid、成员等 
       2)/etc/gshadow 
     3、系统会为每个User关联一个和User同名的Group 
       1)每个User至少存在于自己同名的Group中 
       2)User也可以加入其他的Group 
     4、在同一个Group中的成员可以共享其他成员的文件 

    1、只读权限,用r表示(read) 
     可以读取文件或者列出目录的内容(ls) 
    2、可写权限,用w表示(write) 
     可以写、删除文件或者目录 
    3、可执行权限,用x表示(execute) 
     1)可以执行可执行文件 
     2)可以进入目录并使用cd切换进入目录 
    4、没有任何权限,用-表示 

### 系统信息    

    uname -a    显示系统信息
    df -h     显示硬盘空间
    free -h   显示内存空间

### 操作文件和文件夹    

    mkdir -p  123/123  递归的创建多个目录
          -m 777 text  创建权限为777的目录
                        777 ； rwxrwxrwx
          -v  显示创建信息
    mkdir -vp 123/{a,b}
                递归创建目录 123/a/ , 123/b/

    tree 以树形显示目录结构(需要安装)
        -d     只显示目录,不显示内容
        -L 1   只显示第一层目录和文件
        -f     在每个文件或目录之前，显示完整的相对路径名称
        -t     用文件和目录的更改时间排序

    ls -l | grep "^-"|wc -l
    列出当前文件夹的个数

### 检索文件内字符串

    grep pattern files – 搜索 files 中匹配 pattern 的内容
    grep -r pattern dir – 递归搜索 dir 中匹配 pattern 的 内容
     -i 不区分大小写
     -n 显示行号
     -r 递归

### 压缩解压

    tar zxvf  xxx.tar.gz             解压
    tar vcf file.tar files           创建包含 files 的 tar 文件 file.tar
    tar vxf file.tar                 从 file.tar 提取文件
    tar vczf file.tar.gz files       使用 Gzip 压缩创建 tar 文件
    tar vxzf file.tar.gz             使用 Gzip 提取 tar 文件
    tar vcjf file.tar.bz2            使用 Bzip2 压缩创建 tar 文件
    tar vxjf file.tar.bz2            使用 Bzip2 提取 tar 文件

### 后台切换

    jobs      查看当前有多少在后台运行的命令
    ctrl-z    放到后台  suspend(挂起)
    Ctrl+c    终止前台进程
    bg        查看后台 的job
    fg        把后台任务放到前台
    &         加在一个命令的最后，可以把这个命令放到后台执行
    nohup COMMAND    
             如果让程序始终在后台执行，即使关闭当前的终端也执行
             关闭中断后，在另一个终端jobs已经无法看到后台跑得程序了，此时利用ps

### 其他

    rename  批量修改文件名
    echo $SHELL 查看当前Shell
    chsh -s /bin/zsh 切换为zsh
