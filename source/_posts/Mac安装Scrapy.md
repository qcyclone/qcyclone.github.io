---
title: Mac安装Scrapy
date: 2017-03-17 17:30:48
tags:
---

## 平台
* macOS 10.12.3
* Python 2.7.10
* XAMPP

## 安装pip
这里有两种方法

1. 直接这样 
	`sudo easy_install pip`
2. 安装Homebrew 
`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

	安装wget
	```brew install wget```
	安装pip
	```wget https://bootstrap.pypa.io/get-pip.py```
	```sudo python get-pip.py```
	
## 安装Scrapy
```sudo pip install Scrapy```

运行发现错误
 ```AttributeError: 'module' object has no attribute 'OP_NO_TLSv1_1'```
原因是自带安装的Twisted-17.1.0版本过高。

我们这里安装较低的版本

```sudo pip install Twisted==16.4.1```
## 各种包的安装
* requests  ```sudo pip install requests```
* MySQLdb  
  **利用pip安装**
  
 	 ```pip install MySQL-python```
  
 	 发现错误 ```EnvironmentError: mysql_config not found```
  
 	 执行 ```export PATH=$PATH:/Applications/XAMPP/bin```
 	 
 	 然后安装```pip install MySQL-python```
  
  **手工安装**
  
  <http://sourceforge.net/projects/mysql-python/files/>这里下载，解压缩
  
	然后找到site.cfg文件，
  	更改
  	```mysql_config = /Applications/MAMP/Library/bin/mysql_config```
  	
  	执行
  	```sudo python setup.py build```
  
***
  
### 走到这里又出现了错误
  
```  
_mysql.c:44:10: fatal error: 'my_config.h' file not found
	#include "my_config.h"
         ^
1 error generated.
error: command 'cc' failed with exit status 1
```


找了很长时间终于找到了解决方法<http://www.sunnyos.com/article-show-38.html>
  
  
  这个错误意思是找不到头文件，原因是MySQL不是单独装的。而是用的XAMPP集成环境。XAMPP中PHP和MySQL的头文件都是没有的，所以会报出这个错误。
  
  一种解决方法是安装mysq-connector-c
  
  ```brew install mysql-connector-c```
  
  OK，终于解决了
  ***
  
   安装 ```pip install MySQL-python```
   
   	 
   如果手动，则需要:
   
   ```sudo python setup.py build```
   
   ```sudo python setup.py install```
   
   
* PIL
 ```sudo easy_install -f http://www.pythonware.com/products/pil/ Imaging```
  ```sudo pip install -U Pillow```
  
## Mysql连接问题
  ```OperationalError: (2002, "Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)")```
  执行
  ```ln -s /applications/xampp/xamppfiles/var/mysql/mysql.sock /tmp/mysql.sock``` 
## 结尾
  至此，终于全部安装完成。愉快的抓取了。
  
*  2017/3/16 完成
  

  
  
	

	

