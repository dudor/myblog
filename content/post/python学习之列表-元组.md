---
title: 'python学习之列表,元组'
date: 2016-06-27 10:14:35
tags: python
description: python中内置了四种集合，分别是list，tupple(元组)，set和dict。其中前三种比较类似，只存储了key，而dict字典存储的是key-value键值对。如果学过其它编程语言，就会很容易理解它们。
---
> 学习内容来自[廖雪峰的官方网站](http://www.liaoxuefeng.com)

python中内置了四种集合，分别是list，tupple(元组)，set和dict。
其中前三种比较类似，只存储了key，而dict字典存储的是key-value键值对。
如果学过其它编程语言，就会很容易理解它们。

## list (列表)
list是一个有序的列表，并且可以随时添加修改内部的元素。

```
classmates = ['lilei','xiaoming']
print(classmates)
classmates.append('hanmeimei')
print(classmates)
print(classmates.pop())
print(classmates)
classmates.insert(0,'hanmeimei')
print(classmates)
classmates[2] = 'lucy'
print(classmates)

```
输出结果为
```
['lilei', 'xiaoming']
['lilei', 'xiaoming', 'hanmeimei']
hanmeimei
['lilei', 'xiaoming']
['hanmeimei', 'lilei', 'xiaoming']
['hanmeimei', 'lilei', 'lucy']

```
需要注意的是如果用索引访问会出现数组越界的错误
比如 classmates = ['lilei','xiaoming']，然后访问classmates[2]='hanmeimei'，会出现索引越界，因为索引为2的项不存在。

## tupple (元组)
tupple也是一种有序的列表，它和list非常相似，只是它在初始化之后，内部的元素就不能被修改了。

```
database = ('mysql','mssql','nosql')
print(database[1])
#修改会报错
database[0] = 'oracle'  
```
你只能访问database，而不能修改它。
