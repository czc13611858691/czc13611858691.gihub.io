---
title: ubuntu虚拟机+v2ray设置代理
date: 2021-12-25 22:42:30
tags:
- ubuntu
- 虚拟机
categories:
- miscellaneous
---

**实测有效**

[参考文章](https://blog.csdn.net/weixin_45467056/article/details/105956782)

-   windows cmd输入

```
ipconfg
```

-   观察IPv4地址，同时在虚拟机设置中-->网络-->代理-->手动-->socks5设置ipv4地址，同时设置端口

![](https://cdn.jsdelivr.net/gh/czc13611858691/picgoRepo@master/20211225230040.png)

-   windows允许局域网连接

![](https://cdn.jsdelivr.net/gh/czc13611858691/picgoRepo@master/20211225231126.png)

------------

-   vmware虚拟机设置-->网络适配器-->设置桥接模式，复制物理网络连接
-   使用浏览器打开google测试是否成功