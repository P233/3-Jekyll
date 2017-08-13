---
layout: post
title: Windows环境给php安装memcached
tags: PHP
---

### 1.php 5.6.15  64位系统
解压压缩包
找到memcached-win64文件夹   复制整个文件夹到指定目的,比如 D:/memcached-win64 （可以自己改掉文件夹名字）
打开 cmd 运行 ： D:\memcached-win64\memcached.exe -d install
回车 没报错
```txt
D:\memcached-win64\memcached.exe -d start
```

回车 没报错
 找到电脑本地服务  memcached 已启动 那就是安装成功了


### 2.找到dll文件夹 里面有php需要的memcache.dll 文件
这里用的是php_memcache-3.0.8-5.6-ts-vc11-x86 文件夹里面的 dll
文件夹里面没有合适的dll   去下载： http://pecl.php.net/package/memcache/3.0.8/windows
把php_memcache-3.0.8-5.6-ts-vc11-x86 解压
拿到里面的 php_memcache.dll 文件
放到php的安装目录的 ext文件夹下
这个文件夹放的都是php的dll文件

### 3.在php配置文件里面添加memcached的扩展
在php的安装目录下找到 php.ini 文件
把    ;extension=php_memcache.dll   的; 去掉

如果没有
在里面添加 
```txt
extension=php_memcache.dll
```
//重启apache

### 4.在Apache环境下 放个 index.php
内容如下：
```php
<?php
phpinfo();
?>
```
5.浏览器访问localhost
在浏览器页面上找到 memcache

找到就成功了  没找到就不知道是是什么鬼了

O(∩_∩)O哈哈~


64位系统安装memcached
