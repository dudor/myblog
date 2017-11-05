---
title: centos一键安装开发工具包
date: 2016-07-22 10:56:22
tags: [centos,python]
description: centos一键安装开发工具包
---
今天在centos上升级python3.5，提示缺少编译工具gcc等

如果一个个的手动下载安装太慢了，可以用系统自带的命令一键安装

```
yum groupinstall 'Development Tools'
```

这个命令会安装几十个工具，如git,gcc,perl,zip，svn，rsync等等，太方便了。
