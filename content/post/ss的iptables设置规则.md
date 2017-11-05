---
title: ss的iptables设置规则
date: 2016-07-05 14:34:41
tags: [ss,iptables]
description: 一般情况下，ss服务器只是用来科学上网，所以开几个常用的端口就可以了。这里我们只开放ssh，http，https，dns，ping相关的端口。这里防火墙的原则是进来的流量要审核，而从内部出去的流量不用审核，简单的讲就是外面的流量必须从上面我们开放的几个端口才能连接进来，而内部出去的流量没有限制。
---
搭建好自己的科学上网工具后，如果想要和朋友分享使用，其中的一些安全设置还是很有必要的，不然很可能会被猪一样的队友坑一把哦。

一般情况下，ss服务器只是用来科学上网，所以开几个常用的端口就可以了。这里我们只开放ssh，http，https，dns，ping相关的端口。
这里防火墙的原则是进来的流量要审核，而从内部出去的流量不用审核，简单的讲就是外面的流量必须从上面我们开放的几个端口才能连接进来，而内部出去的流量没有限制。

假设服务器是新开的，以前没有设置过iptables规则。

* 首先清空下规则：
```
	iptables -F
	iptables -X
```

* 启用本地环回网络
```
	iptables -A INPUT -i lo -j ACCEPT
```
* 开放ssh端口
```
	iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```
* 开放http和https端口
```
	iptables -A INPUT -p tcp --dport 80 -j ACCEPT
	iptables -A INPUT -p tcp --dport 443 -j ACCEPT
```
* 开放dns端口
```
	iptables -A INPUT -p udp --dport 53 -j ACCEPT
```
* 开放ping端口
```
	iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
```
* 当然还有ss的端口，不然没法翻墙啊，这里我假设10000~20000之间的端口都可以分配给用户来连接
```
	iptables -A INPUT -p tcp --dport 10000:20000 -j ACCEPT
```
* 屏蔽邮箱端口，以防别人乱发垃圾邮件
```
	iptables -A OUTPUT -p tcp -m multiport --dport 24,25,50,57,105,106,109,110,143,158,209,218,220,465,587 -j REJECT
	iptables -A OUTPUT -p tcp -m multiport --dport 993,995,1109,24554,60177,60179 -j REJECT
	iptables -A OUTPUT -p udp -m multiport --dport 24,25,50,57,105,106,109,110,143,158,209,218,220,465,587 -j DROP
	iptables -A OUTPUT -p udp -m multiport --dport 993,995,1109,24554,60177,60179 -j DROP
```
* 最后我们要禁止其它的端口连接
```
	iptables -P OUTPUT ACCEPT
	iptables -P INPUT DROP
	iptables -P FORWARD DROP
```

以上为个人见解，如有错误，请帮忙指出，谢谢。

> 参考：http://briteming.blogspot.com/2015/10/iptablesshadowsocksshadowsocks.html