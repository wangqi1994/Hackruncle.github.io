---
title: "CentOS6.5配置静态IP和可访问外网"
catalog: true
toc_nav_num: true
date: 2020-04-21 12:00:00
subtitle: "备忘"
article_type: 0 # 0 原创，1 转载
tags:
- [ruozedata]
- [系统配置]
categories:
- [ruozedata]
- [系统配置]
updateDate: 2020-04-21 12:00:00
top: 0  #置顶
---


**CentOS6.5**配置静态**IP**和可访问外网

**1.**关闭**Windos7**防火墙

路径：控制面板\\系统和安全\\Windows Defender防火墙，选择启用或关闭防火墙，将防火墙关闭。

![](https://i.loli.net/2020/06/11/NoRIlr9a1HLWyAi.jpg)

**2.**关闭**CentOS6.5**防火墙

在centos系统中关闭防火墙，terminal输入以下命令回车
```bash
service iptables stop
chkconfig iptables off
```

**3.**开启两个服务

Windows系统打开以下两个服务，默认是开启的。路径windows键+x，选择计算机管理，选择服务，将以下两个服务开启并设置为自动启动。

VMware DHCP Service

VMware NAT Service

![](https://i.loli.net/2020/06/11/Nedu7oDgtPEqAFV.png)

**4.**无线网卡的网络(或者插网线的网络)上设置网络共享，选择VM8。

路径：设置网络-更改适配器配置-选中网络-属性-高级属性-共享-将VM8加入共享。

![](https://i.loli.net/2020/06/11/tYo1n6ebjFKGDPa.png)

**5.**使用**ipconfig -all**命令查看**DNS**、**IPv4**等信息

Windows键+R-cmd

![](https://i.loli.net/2020/06/11/EyQgeUz7FZbAfjN.png)

![](https://i.loli.net/2020/06/11/n3K4tJArBXEDHPF.png)

记住现在所连网络的DNS，以及VMnet8的Ipv4地址和子网掩码

**6.**配置**VM8**的选择 使用配置**ip**

路径：设置网络-更改适配器配置-选中VMnet8-属性-选中Internet协议Ipv4（TCP/Ipv4）-修改IP地址和子网掩码

![](https://i.loli.net/2020/06/11/iDhbZSIMdLoKgGs.png)

**7.**进入vm,单击菜单栏的编辑--\>虚拟网络编辑器

![](https://i.loli.net/2020/06/11/SA8LQtOmKyMUYNw.png)

![](https://i.loli.net/2020/06/11/1fCBs6XIZdLbAqu.png)

![](https://i.loli.net/2020/06/11/21WKeadNR9MV6CI.png)

**子网IP最后一个为0**
**NAT设置中网关IP最后一位2**
**DHCP设置中范围128-254**

Centos7.2安装之后可以不需要设置静态IP，在安装时直接选择开启网络即可（安装配置可参照<https://wangqi1994.github.io/2020/04/21/centos7.2/>）

**8.**hadoop001配置**NAT**网络
在虚拟机设置中，确认网络适配器是选择的NAT模式

![](https://i.loli.net/2020/06/11/MU9DhYSCGj4tbKz.png)

**9.**进入hadoop001,编辑ifcfg-eth0

```bash
vi /etc/sysconfig/network-scripts/ifcfg-eth0
```
![](https://i.loli.net/2020/06/11/FOScUk6CY4TJfGu.jpg)
IPADDR即IP地址，最后一位在设置范围内即可128-254
NETMASK即子网掩码

GATEWAY即网关IP
DNS即外部网络DNS
注意不要打错单词，否则无法设置成功

**10.** 进入hadoop001,重启网络
执行命令：

```bash
service network restart
```
![](https://i.loli.net/2020/06/11/H8tPbAyMwG4I9Ns.jpg)
**11.** 进入hadoop001,检查网络

![](https://i.loli.net/2020/06/11/arKObktAYL6ychd.png)


