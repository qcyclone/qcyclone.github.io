---
title: phpmyadmin更改MySQL密码
date: 2017-03-15 17:30:48
tags:
---
## 环境
* XAMPP 
* macOS 10.12.3

## 问题
在电脑上安装了XAMPP环境，可以连接phpmyadmin。不过写的php代码无法连接到MySQL。
XAMPP默认安装MySQL的Root账户密码为空。
## 方法
在phpmyadmin中选择mysql-user表
`UPDATE user SET password=PASSWORD('123456') where USER='root'`

刷新一下，可能会出现错误

进入phpmyadmin文件夹找到config.inc.php文件
`$cfg['Servers'][$i]['password'] = '123456';`
改成你刚才设置的密码。

如果还有问题，重启MySQL就好了。

## 结尾

* 2017/3/15 完成


