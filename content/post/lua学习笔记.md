﻿---
title: lua学习笔记
date: 2015-07-12 18:14:47
tags: lua
description: lua中的变量名定义规则和大多数编程语言一样，是任何非数字开头的由字母，数字和下划线组成的字符串。
---
##语法约定
lua中的变量名定义规则和大多数编程语言一样，是任何非数字开头的由字母，数字和下划线组成的字符串。
lua是大小写敏感的。
##字符串
字符串是由单引号或双引号或N级中括号定义的，比如 
a = 'dudor' 
a = "dudor" 
a = [[dudor]]
上面三个值是相等的。
其中由N级中括号定义的方式比较特别，在别的语言中很少见到。N级中括号是在两个中括号中插入N个等号定义为第N级中括号。
##注释
注释是用两个横线定义的，单行注释是 -- ，多行注释为 --[  

##类型
lua中有8种类型： nil, boolean, number, string, function, userdata, thread, and table. 

1. nil类似于c中的NULL,通常用来表示一个无意义的值。
2. boolean有false和true两个值。
3. number代表双精度浮点数字。
4. string是上面所说的字符串。
5. userdata用来将任意类型的c数据保存在lua变量中。它不能被lua创建和修改。
6. thread代表了一种线程，当然和C中的线程不由，类似于UNITY3D中的coroutine，它可以在所有的系统中使用，不管系统是否支持多线程。
7. table可以认为是一种字典类型

##变量
在lua中，使用变量是不需要声明的，并且它们默认是全局变量，除非在前面注明了local关键字

##流程控制
1. if ... then ... elseif ... then ... else ... end
2. while ... do ... end
3. repeat ... until ...
4. for 变量=初值,终值,步进 do ... end
5. for 变量1, 变量2, ... 变量n in 表或枚举函数 do ... end

##赋值
a = 1
a,b,c = 1,2,3
局部变量 
local d = 1
##特殊注意事项
1. 在lua中，只有nil和false才计算为假，其它值都是真，包括0
2. ~= 表示不等于
3. 对于function,userdata和table类型，只有==和~=操作符可以用于比较。
