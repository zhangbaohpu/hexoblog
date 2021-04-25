---
title: VMWare12+centos7安装
date: 2019-06-08 21:12:39
categories: linux
tags:
    - 虚拟机
    - linux
---

# 1.打开并创建虚拟机

![](https://uploader.shimo.im/f/1ano9KF3kckTQbaW.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 2.自定义安装

![](https://uploader.shimo.im/f/KFoPFp3ttWcvknVi.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

![](https://uploader.shimo.im/f/oVZNRFVs2L0tlmDB.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 3.选择稍后安装操作系统

![](https://uploader.shimo.im/f/q5JnyTZBxSkGbUpL.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 4.操作系统的选择

![](https://uploader.shimo.im/f/Mu5UnMEGq58zd7ln.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 5.虚拟机位置与命名

![](https://uploader.shimo.im/f/qmIq2YTQBZIj1wdl.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 6.根据设备配置高低，自行设置资源

在使用过程中CPU不够的话是可以再增加的

![](https://uploader.shimo.im/f/PdbysypfcWwwtu8V.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 7.设置内存

内存也是要根据实际的需求分配。我的宿主机内存是16G所以我给虚拟机分配2G内存。

后期可再添加

![](https://uploader.shimo.im/f/QJUPLh2SNzEjfdgX.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 8.选择网络连接类型

网络连接类型一共有桥接、NAT、仅主机。

桥接：选择桥接模式的话虚拟机和宿主机在网络上就是平级的关系，相当于连接在同一交换机上。

NAT：NAT模式就是虚拟机要联网得先通过宿主机才能和外面进行通信。

仅主机：虚拟机与宿主机直接连起来

这里选择NAT模式

![](https://uploader.shimo.im/f/wJsw16catcM9fUR1.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 9.其余两项默认

![](https://uploader.shimo.im/f/HuL1kwd9McElksoZ.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

![](https://uploader.shimo.im/f/griqzlyF6X0KpD2d.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

![](https://uploader.shimo.im/f/s0slwjcrMTQ3W6fT.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 10.磁盘容量

磁盘容量暂时分配20G即可后期可以随时增加，不要勾选立即分配所有磁盘，否则虚拟机会将20G直接分配给CentOS，会导致宿主机所剩硬盘容量减少。

勾选将虚拟磁盘拆分成多个文件，这样可以使虚拟机方便用储存设备拷贝复制。

![](https://uploader.shimo.im/f/YWz1LT1qJaQVmEzb.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 11.磁盘名称，默认即可

![](https://uploader.shimo.im/f/nDUWcM39QzsP6zGd.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 12.删除不必要的硬件

声卡和打印机可以不要

![](https://uploader.shimo.im/f/arElxVkIkLAVOsfG.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

可将声卡和打印机删除，如果可以删除的话，然后关闭

![](https://uploader.shimo.im/f/Y3RQ7FWyvmwL7Vn0.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 13.点击完成，即可创建虚拟机

![](https://uploader.shimo.im/f/5Fd5WpeAzEceYzn1.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

完成之后

![](https://uploader.shimo.im/f/l8S7o65XklkQjorj.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 14.安装镜像

选择使用ISO映像文件，最后选择浏览找到下载好的镜像文件

[https://mirrors.aliyun.com/centos/7/isos/x86_64/CentOS-7-x86_64-DVD-2003.torrent](https://mirrors.aliyun.com/centos/7/isos/x86_64/CentOS-7-x86_64-DVD-2003.torrent?fileGuid=F0YrE8Munk42DYQC)

![](https://uploader.shimo.im/f/OjUGKQEVhIUsWVJM.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 15.开启虚拟机

![](https://uploader.shimo.im/f/WevaeYBfCpA4NXjZ.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

![](https://uploader.shimo.im/f/be72iJwWcvYefB82.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

![](https://uploader.shimo.im/f/WKtKQHPy5SMf2AYe.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 16.选择语言

这里选择英文、键盘选择美式键盘。点击Continue

![](https://uploader.shimo.im/f/swE5W1YJX8IQWnZh.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 17.设置时间

![](https://uploader.shimo.im/f/JeMdwdy97TkOwjGN.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

![](https://uploader.shimo.im/f/5HlLgbk7LHsS8ZNx.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 18.选择安装软件

![](https://uploader.shimo.im/f/SHRaYBxZAooUiGbF.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

这里我选择Minimal install（最小安装），然后点击Done

![](https://uploader.shimo.im/f/U3eOPqVWxbcdQyWD.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 19.选择安装位置，进行磁盘划分

![](https://uploader.shimo.im/f/1Z4q860n8mEdNR5d.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

选择I will configure partitioning（我会自己配置分区），然后Done

![](https://uploader.shimo.im/f/pdaE3rt1QHURnlfd.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

选择/boot，给boot分区分200M。最后点击Add

![](https://uploader.shimo.im/f/JskwktfIfwsmd2yM.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

按同样方法给其他区分配好空间，然后点击Done

![](https://uploader.shimo.im/f/t2c3yApy9j42XtB2.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

会弹出摘要信息，点击Accept Changes

![](https://uploader.shimo.im/f/QQwVjs7R9Jsdw7Xe.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 20.设置主机名与网卡信息

登录系统后也可以更改

![](https://uploader.shimo.im/f/PTl5JIDEGeUg8dj8.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

![](https://uploader.shimo.im/f/wgi7zsUbSZkEqOpc.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 21.最后选择Begin Installation（开始安装）

![](https://uploader.shimo.im/f/TanoxBc0B9oL6AzN.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 22.设置root用户密码

password：123456

![](https://uploader.shimo.im/f/nSW5z3LfkYEjDDt4.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

![](https://uploader.shimo.im/f/c22C5en6Ai8H5wBT.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 23.点击USER CREATION 创建管理员用户

![](https://uploader.shimo.im/f/495AX4GfI18syRzk.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

![](https://uploader.shimo.im/f/ObUP6xNexBQ5uih7.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 24.Finish  configure

![](https://uploader.shimo.im/f/B7UDfziJz8wQmKZz.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

![](https://uploader.shimo.im/f/QwmVcC5W4K0Zb1yE.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 25.reboot（重启）

![](https://uploader.shimo.im/f/MSz5EooosoAeRdDb.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

![](https://uploader.shimo.im/f/ou8rFnavRKoEzgBA.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

![](https://uploader.shimo.im/f/hG7m4b1gyVA4owBA.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 25.修改ip及网络

1.查看虚拟机网络配置

![](https://uploader.shimo.im/f/MrEpn6GYWQMgwLtn.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

节点ip及网段设置要根据这个同步，ip要和下面子网ip在同一网段，比如：192.168.245.22,192.168.245.30等，子网掩码及网关跟下面的相同

![](https://uploader.shimo.im/f/gt3IJ3JIr80Mt9Uq.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

登录后执行以下命令

[root@node002 ~]# vi /etc/sysconfig/network-scripts/ifcfg-ens33

![](https://uploader.shimo.im/f/X1dFXEIXqpQKTxPF.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 26.修改resolv.conf

在配置文件中添加两个nameserver![](https://uploader.shimo.im/f/2zx9LRPIBC8oJy24.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

[root@node002 ~]# vi /etc/resolv.conf

![](https://uploader.shimo.im/f/PgeaWLyH7mofWrXh.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 27.重启网络连接

[root@node002 ~]# service network restart![](https://uploader.shimo.im/f/oxjoOpuiKkEwXnLl.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

# 28.ping百度

![](https://uploader.shimo.im/f/CoiXChthQSI6yOV6.png!thumbnail?fileGuid=F0YrE8Munk42DYQC)

关闭防火墙

查看防火墙状态

```plain
firewall-cmd --state
```
停止firewall
```plain
systemctl stop firewalld.service
```
禁止firewall开机启动
```plain
systemctl disable firewalld.service
```

