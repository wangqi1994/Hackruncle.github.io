---
title: "Centos7.2安装部署（图文教程）"
catalog: true
toc_nav_num: true
date: 2020-04-21 12:00:00
subtitle: "备忘流程"
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


Centos7.2安装部署（图文教程）

描述：记录VMware中centos安装部署步骤，包括安装流程和参数配置

### 一、下载CentOSer6.5镜像文件。
=============================

<http://vault.centos.org/7.2.1511/isos/x86_64/>

### 二．虚拟机创建流程:（本次安装使用的VMware版本是15.5）
=====================================================

![](https://i.loli.net/2020/06/11/uZ9XJpS6r4vwAMI.png)

点击新建虚拟机，弹出如下窗口，选择自定义，点击下一步

![](https://i.loli.net/2020/06/11/OKgeS4n1ycDlCm3.png)

选择workstations 10.x，点击下一步

![](https://i.loli.net/2020/06/11/C69zR8mHrp7xBDs.png)

选择稍后安装操作系统，下一步

![](https://i.loli.net/2020/06/11/6YEDstWnmOVvx31.png)

选择Linux之后，选择安装版本，此次选择Centos7 64位，点击下一步

![](https://i.loli.net/2020/06/11/4ZXrEqLOpQseuoy.png)

设置虚拟机的名称以及安装位置，（名称根据个人喜好设置），点击下一步

![](https://i.loli.net/2020/06/11/SdiwrIVGJzxn2yP.png)

处理器配置，在不影响电脑流畅度条件下，随意设置

![](https://i.loli.net/2020/06/11/Va5dg9DlXYCy7zt.png)

配置内存，建议2G以上

![](https://i.loli.net/2020/06/11/5QSTY7MFqp8LwE6.png)

网络类型选择默认使用网络地址转换（NAT）

![](https://i.loli.net/2020/06/11/9t1I2XHKdrbMAQi.png)

I/O控制器类型默认选择LSI Logic（L）

![](https://i.loli.net/2020/06/11/UaELSvOze5xuqX1.png)

磁盘类型默认选择SCIS

![](https://i.loli.net/2020/06/11/ZQikyJDp8q7sMf9.png)

选择磁盘使用，默认选择创建新虚拟磁盘

![](https://i.loli.net/2020/06/11/QdiBONYKrm9h13U.png)

指定磁盘容量，在不影响电脑使用情况下，合理分配内存，建议40G以上

![](https://i.loli.net/2020/06/11/xUdcXn4azQjoGiS.png)

磁盘文件命名，默认即可，点击下一步

![](https://i.loli.net/2020/06/11/eBVv16rcTxy9onX.png)

点击完成，完成创建，或者选择自定义硬件，编辑相关属性。

![](https://i.loli.net/2020/06/11/io8HZ9T16cY5fye.png)

选中新创建的虚拟机，点击编辑虚拟机设置

![](https://i.loli.net/2020/06/11/d2pJltWKPmMX16u.png)

选择CD/DVD（IDE）后选择使用镜像文件安装，选中提前下载好的镜像文件，点击确定

![](https://i.loli.net/2020/06/11/OiqweyvNFPM9suJ.png)

### 三、系统安装配置
================

点击开启此虚拟机进行系统安装，选择Install Centos 7,直接回车，开始安装

![](https://i.loli.net/2020/06/11/qfs3FOugXCkWZK7.png)

进入配置参数界面，建议选择英文系统，当然选择中文系统也可，看个人喜好。

![](https://i.loli.net/2020/06/11/wySMI5LmaJrXxTg.png)

点击继续，进入具体设置配置界面

![](https://i.loli.net/2020/06/11/TlkNRtEPDM1jUah.png)

设置系统时间和时区，选择Asia/Shanghai，注意具体时间可能会差9小时，可以自己进行手动设置。

![](https://i.loli.net/2020/06/11/NC9mr3AencalF2q.png)

至于键盘和辅助语言选择根据个人喜好设置，个人建议英文

选择设置安装software软件，选中software
selection进行自己的定制安装，默认选中最小化安装。

![](https://i.loli.net/2020/06/11/4XKmdb91NVWfwoE.png)

此次选择安装桌面版GNOME桌面，右侧可以选择想要安装的软件包。

![](https://i.loli.net/2020/06/11/v2AcPLE1COihm5y.png)

接下来，最重要的是设置installation destination，选中配置的磁盘（两次点击）

![](https://i.loli.net/2020/06/11/auF7Jt2HNEYxTf5.png)

选择自定义，进行磁盘分配。然后选择Done确定进入磁盘分配

![](https://i.loli.net/2020/06/11/EG6ngOSKJvulH8w.png)

选择标准分区后，选择添加按钮进行磁盘分配

![](https://i.loli.net/2020/06/11/mS5FqJxOa9V13Wp.png)

记得文件系统选择ex4，swap分区最好设置2G往上，设置好boot和swap分区之后，剩余所有磁盘分配给根目录/。点击确认退出磁盘分配

![](https://i.loli.net/2020/06/11/shiamTeWKDRMb4A.png)

关于KDUMP，建议关闭，报错文件看不懂，可以勾选

关于网络和主机名，建议选择打开网络并根据需要自行修改主机名。

配置完成之后点击开始安装。

安装过程中，可以设置root用户和普通用户账号和密码，设置完成之后，等待安装完成。

![](https://i.loli.net/2020/06/11/cuk8XrjGs1p2K5h.png)

安装完成后，点击reboot重启

![](https://i.loli.net/2020/06/11/JFzbrXdSLuIwYxq.png)

会弹出用户协议选择界面，依此输入1-2-c-c即为同意协议

完成安装

输入密码之后，进入欢迎界面，可选择设置系统语言和键盘分布，还有google等用户可选择登录，可以选择跳过。

![](https://i.loli.net/2020/06/11/2XnILJ3FDp7izfv.png)

最后，进入Centos 7 桌面。
