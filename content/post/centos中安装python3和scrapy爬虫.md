---
title: centos中安装python3和scrapy爬虫
date: 2016-07-22 16:55:31
tags: [centos,python3,scrapy,爬虫]
description: centos中安装python3和scrapy爬虫，折腾了一天，总算是安装好了。必须得记录下，不然下次说不准还得再折腾一天。
---
折腾了一天，总算是安装好了。必须得记录下，不然下次说不准还得再折腾一天。。。

虚拟机环境是centos6.5，系统自带python2.6。

我先要安装个python3.5，然后再安装scrapy。

### 先更新下系统
```
yum update -y
```

### 安装依赖包

```
yum groupinstall 'Development Tools'
yum install gcc gcc-devel -y
yum install libxml2 libxml2-devel -y
yum install libxslt libxslt-devel -y
yum install openssl openssl-devel -y
yum install libffi libffi-devel -y
yum install sqlite sqlite-devel -y
```

### 安装python3.5
下载地址：<https://www.python.org/ftp/python/3.5.2/Python-3.5.2.tgz>

```
tar zxvf Python-3.5.2.tgz
cd Python-3.5.2
./configure --prefix=/usr/local/python3.5.2
make && make install
```
### 重新设置python命令链接
```
cd /usr/bin
mv python python2_old
ln -s /usr/local/python3.5.2/bin/python3 python
ln -s /usr/local/python3.5.2/bin/python3 python3
ln -s /usr/local/python3.5.2/bin/pip3 pip
ln -s /usr/local/python3.5.2/bin/easy_install-3.5  easy_install
```
### 检验python是否安装成功

```
python

Python 3.5.2 (default, Jul 22 2016, 16:45:39) 
[GCC 4.4.7 20120313 (Red Hat 4.4.7-17)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```
### 修复yum的python版本
```
vi /usr/bin/yum
```
### 安装Twisted
```
wget https://pypi.python.org/packages/c0/7c/c1e5b61e30b7ffc96576d2a922615c8068e6996a622be813fc626cef07aa/Twisted-16.3.0.tar.bz2#md5=e044af844623e9fbcbe29f578db6053a
tar jxvf Twisted-16.3.0.tar.bz2
cd Twisted-16.3.0
python setup.py install
```

### 安装scrapy爬虫
```
pip install lxml
pip install scrapy
```

### 检验scrapy是否安装成功
```
ln -s /usr/local/python3.5.2/bin/scrapy   /usr/bin/scrapy
scrapy -v

Scrapy 1.1.1 - project: demo1

Usage:
  scrapy <command> [options] [args]

Available commands:
  bench         Run quick benchmark test
  check         Check spider contracts
  commands      
  crawl         Run a spider
  edit          Edit spider
  fetch         Fetch a URL using the Scrapy downloader
  genspider     Generate new spider using pre-defined templates
  list          List available spiders
  parse         Parse URL (using its spider) and print the results
  runspider     Run a self-contained spider (without creating a project)
  settings      Get settings values
  shell         Interactive scraping console
  startproject  Create new project
  version       Print Scrapy version
  view          Open URL in browser, as seen by Scrapy

Use "scrapy <command> -h" to see more info about a command
```

到此，python3和scrapy就算安装成功了。


> 参考：https://clasense4.wordpress.com/2015/11/25/how-to-install-scrapy-on-centos-7/