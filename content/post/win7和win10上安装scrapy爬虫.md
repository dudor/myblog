---
title: win7和win10上安装scrapy爬虫
date: 2016-07-19 14:40:08
tags: [python,scrapy,win7,win10]
description: 64位win7和win10上安装scrapy爬虫的过程
---
我在自己的win7和win10电脑上安装成功了，具体环境是：

win7-64位/win10-64位 + python2.7-32

但是python3.5中没有安装成功(好像不支持)。

以下用到的所用文件我都在百度网盘中做了备份，有需要的可以直接用我分享的文件。

百度盘：<http://pan.baidu.com/s/1qYIPIYK>

## 安装32位的python2.7
* 下载地址 <https://www.python.org/downloads/>
* 更新环境变量,可以直接把下面的代码添加到环境变量的path中

  ```
  C:\Python27\;C:\Python27\Scripts\;
  ```
  或者直接运行python自带的脚本自动更新

  ```
  c:\python27\python.exe c:\python27\tools\scripts\win_add2path.py
  ```
## 安装 pywin32

  * 下载地址：<https://sourceforge.net/projects/pywin32/files/pywin32/Build%20220/>

    pywin32的版本要和python的一致，所以要选 pywin32-220.win32-py2.7.exe
	
## 安装 Microsoft Visual C++ Compiler for Python 2.7

  * 下载地址 : <https://www.microsoft.com/en-us/download/details.aspx?id=44266>

## 安装pip

  * 下载地址 : <https://pip.pypa.io/en/latest/installing/>
	   
    下载页而上的get-pip.py脚本，然后在本机上运行

	```
	python get-pip.py
	```

## 安装lxml

  * 下载地址 : http://www.lfd.uci.edu/~gohlke/pythonlibs/#lxml
  这个也需要和python版本对应，所以在页面上搜索**lxml-3.4.4-cp27-none-win32.whl**，下载并用下面的命令安装。

    ```
	pip install lxml-3.4.4-cp27-none-win32.whl
    ```

## 最后安装scrapy

  ```
  pip install scrapy

  ```




> 参考： http://doc.scrapy.org/en/1.1/intro/install.html