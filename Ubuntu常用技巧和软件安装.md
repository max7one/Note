### Node安装

1. http://fengmk2.com/blog/2014/03/node-env-and-faster-npm.html
2. nvm alias default 4.4.5  

### Mysql安装

1. sudo apt-get install mysql-server

### Nginx安装

1. https://nginx.org/en/download.html 页面下载 .tar.gz
2. `sudo apt-get install libpcre3 libpcre3-dev`安装pcre库
3. `./configure`
4. sudo make && make install
5. sudo vi /usr/local/nginx/conf/nginx.conf 修改配置

### PHP安装以及配置

1. sudo apt-get install php
2. http://www.tecmint.com/install-php7-for-apache-nginx-on-ubuntu-14-04/
3. http://www.2daygeek.com/install-lemp-nginx-mariadb-php-phpmyadmin-on-ubuntu/
4. $ sudo service php7.0-fpm restart
5. $ sudo nginx -s reload

### Sublime安装

1. http://sublimetext.iaixue.com/dl/d

### Sogou输入法安装

1. http://pinyin.sogou.com/linux/

### Browser-Sync安装与使用
```
1. npm install -g browser-sync
2. browser-sync start --server --files *.html  (多个文件类型用`,`隔开)
3. http://www.browsersync.cn/#install
```
### 远程操作

1. 安装openvpn
sudo apt-get install openvpn
2. 运行open
sudo openvpn --config /path/123.ovpn --ca /path/ca.crt
3. 安装sshpass
sudo apt-get install sshpass
4. scp远程操作文件
sshpass -p 'Password' scp /path/123.txt root@10.153.199.66:/path/123.txt 
5. ssh连接远程服务器
sshpass -p 'Password' ssh root@10.153.199.66

解决ssh连接过慢
```
vim ~/.ssh/config
//添加
Host *
  GSSAPIAuthentication no
```

### htop 比top更加人性化

1. sudo apt-get install htop

---
### Ubuntu快捷键

##### 命令行快捷键

`apt-install -f`  安装依赖  
`ctrl-shift-c`  复制到系统剪贴板
`ctrl-shift-v`  粘贴到Terminal
`ctrl-e` 行尾  
`ctrl-a` 行首  
`ctrl-w` 向前删除一个单词
`ctrl-h` 向前删除一个字符
`ctrl-f` 向后移动一个字符
`ctrl-b` 向前移动一个字符
`alt-f` 跳转到后一个单词
`alt-b` 跳转到前一个单词
`ctrl-/` 撤销命令
`ctrl-p` 上一个命令  
`ctrl-n` 下一个命令
`ctrl-r` 历史命令向后搜索  
`ctrl-s` 历史命令向前搜索
`ctrl-l` 清屏  
`ctrl-u` 清除当前命令   
`sudo !!` sudo 上一个命令   
`alt-.` 上一个命令的参数 (或在命令尾部加上 `!$`)
`ctrl-alt-f1～f6` 进入tty1~tty6  
`ctrl-alt-f7`  进入桌面
`sudo passwd root` 改密码     
`sudo su` 切换到root用户

`sudo apt-get -y purge php.*` 完全卸载php
  -y  --yes  执行过程中 yes

##### Terminal快捷键

`ctrl-shift-t` 新建tab   
`alt-1` 切换到第一个tab  
`ctrl-[/]` 左右切换tab  
`ctrl-super-up/down` 最大/最小

##### 引导

vim /etc/default/grub
sudo update-grub