﻿---
title: unity3d中使用git做版本控制的心得体会
date: 2015-07-07 00:39:42
tags: [unity3d,git,版本控制]
description: 提起git，可以说是个程序员都听说过或使用过，我最早接触它是在GITHUB上，用它来下载源代码，后来随着工作的需要，渐渐的用在了工作中，记得某次接盘了一个C++项目，代码一大堆，可是却没有任何文档，要添加新功能却又害怕影响现在的功能，于是在本地建立了git库，进度完成一点就提交一次，这样也不怕改错代码了，大不了重新把之前的签出来就可以了，很是方便。
---
提起git，可以说是个程序员都听说过或使用过，我最早接触它是在GITHUB上，用它来下载源代码，后来随着工作的需要，渐渐的用在了工作中，记得某次接盘了一个C++项目，代码一大堆，可是却没有任何文档，要添加新功能却又害怕影响现在的功能，于是在本地建立了git库，进度完成一点就提交一次，这样也不怕改错代码了，大不了重新把之前的签出来就可以了，很是方便。

后来接触到了unity3d，在小组同事的帮助下渐渐入了门，当时的项目一直用的unity3d自带的asset server做版本控制，这个东西虽然是官方的，但是一点也不好用，每次和同事合并项目，总是出现丢失东西的问题，当时也没有想太多，后来随着项目文件的增多，体积也越来越臃肿，每次合并出现问题，都要花费很多时间去修复，终于大家都受不了了，在一次程序大更新中，我把版本控制换成git了。

在unity3d中使用git，需要注意以下几点


2. 在editor settings中，把asset serialization中的mode项切换成force text
3. 只需要将项目中的Assets和projectsettings文件夹加入到版本库中即可


###另附本人在unity3d中常用的gitignore文件

>[Ll]ibrary/
[Tt]emp/
[Oo]bj/
[Bb]uild/
\# Autogenerated VS/MD solution and project files
*.csproj
*.unityproj
*.sln
*.suo
*.user
*.userprefs
*.pidb
*.booproj
\# Unity3D Generated File On Crash Reports
sysinfo.txt

