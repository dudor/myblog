---
title: python学习之字典
date: 2016-06-27 11:52:39
tags: python
description:  dict (字典) 是一个存储了许多key=value键值对的集合，就像新华字典一样，查找数据很快。
---
> 学习内容来自[廖雪峰的官方网站](http://www.liaoxuefeng.com)

## dict (字典)

dict (字典) 是一个存储了许多key=value键值对的集合，就像新华字典一样，查找数据很快。
比如查找班级中某个同学的成绩，用list来实现的话，可能是这样：
```
students = ['lilei','hanmeimei','lucy']
scores = [55,56,57]

name = input('请输入学生的名字>')
for i in range(len(students)):
	if(students[i] == name):
		print(scores[i])
```

而用dict来实现会更简单：

```
students = {'lilei':55,'hanmeimei':56,'lucy':57}
name = input('请输入学生的名字 >')
print(students[name])
```
由于字典是根据key来查找value的，所以它的key必须是不能改变的，也就是常量。

## set (集合)

set 和 dict类似，只是set只存储key，而不存储value，它是一个无序的并且内部无重复元素的集合。
要创建一个set，需要提供一个list作为输入集合：
```
s = set([1, 2, 3])
```