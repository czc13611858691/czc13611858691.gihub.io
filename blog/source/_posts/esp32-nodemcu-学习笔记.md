---
title: esp32_nodemcu_学习笔记
date: 2021-12-11 20:16:54
tags:
- 物联网
- esp32
- nodemcu
categories:
- 软硬结合——从零打造物联网-学习
---



## 学习目标

通过网页或者手机app点个灯

这篇笔记的记录方式采用时间顺序的记录方式。



## 学习资源&材料

-   硬件:esp32开发板

-   服务器

-   生子当如哈士奇的个人博客



## **操作步骤&实验现象**

### 服务器配置

购买服务器，安装*CentOS 8.0*系统

设置密码(输入时密码不可见)

```
sudo passwd root
```



#### 远程登陆

下载[PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

1.  打开软件
2.  设置公网ip地址(Host Name)
3.  设置Port端口
4.  设置连接方式SSH
5.  save
6.  open
7.  login as: root
8.  输入密码

**报错**

```
sudo vi /etc/ssh/sshd_config

```

修改内容如下

```
PermitRootLogin yes
PasswordAuthentication yes
```

重启ssh服务

```
service sshd restart
```

**密钥登陆**

[Putty使用密钥自动登陆SSH](https://www.laozuo.org/2811.html)

使用云服务器生成公钥，下载

使用puttygen打开，生成私钥，可以不设置密码

设置auto-login username root

save

下次直接点击就可以登陆

**注意**

1.putty自动断开

![](https://cdn.jsdelivr.net/gh/czc13611858691/picgoRepo@master/20211211221520.png)

2.使用腾讯云绑定密钥时会关机，然后里面的设置都清空了

可以备份一下镜像下次恢复