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

![](/img/centos7.2/c49c1907c26ca17160db644c80d65ef8.png)

点击新建虚拟机，弹出如下窗口，选择自定义，点击下一步

![](/img/centos7.2/34f2cd138e92f790546b6bf4276b32ec.png)

选择workstations 10.x，点击下一步

![](/img/centos7.2/4874f1e625c5190f42280a15f46679f1.png)

选择稍后安装操作系统，下一步

![](/img/centos7.2/85a7c6133f372f0a5bb996020c74f109.png)

选择Linux之后，选择安装版本，此次选择Centos7 64位，点击下一步

![](/img/centos7.2/88d74562a5d04a4c3782847a374acaa9.png)

设置虚拟机的名称以及安装位置，（名称根据个人喜好设置），点击下一步

![](/img/centos7.2/036d0356891341a663803a2a21025370.png)

处理器配置，在不影响电脑流畅度条件下，随意设置

![](/img/centos7.2/a90dd948af4ae6399ed3d0c80c9523a2.png)

配置内存，建议2G以上

![](/img/centos7.2/d729adea26ac58bb4b0afccd2281eda3.png)

网络类型选择默认使用网络地址转换（NAT）

![](/img/centos7.2/5388e62540686c52e0b6277f3601102f.png)

I/O控制器类型默认选择LSI Logic（L）

![](/img/centos7.2/94e0b4abd2e9b917bc24e852dedf4a33.png)

磁盘类型默认选择SCIS

![](/img/centos7.2/cb68f453e1f11ddb2c20e85ca8994713.png)

选择磁盘使用，默认选择创建新虚拟磁盘

![](/img/centos7.2/96c00ef2f294b09950f15df4efed687e.png)

指定磁盘容量，在不影响电脑使用情况下，合理分配内存，建议40G以上

![](/img/centos7.2/99ce7ece3d2a9ef4fcc6471cad209393.png)

磁盘文件命名，默认即可，点击下一步

![](/img/centos7.2/521a7d443ca9667323222739560bf958.png)

点击完成，完成创建，或者选择自定义硬件，编辑相关属性。

![](/img/centos7.2/c35a8e49e1e8078b2387132d5f16a9ed.png)

选中新创建的虚拟机，点击编辑虚拟机设置

![](/img/centos7.2/0d37570407c54b92e4a5e19f0a264429.png)

选择CD/DVD（IDE）后选择使用镜像文件安装，选中提前下载好的镜像文件，点击确定

![](/img/centos7.2/61a14c3bc72f5825e9fd4a71a0e51ee9.png)

### 三、系统安装配置
================

点击开启此虚拟机进行系统安装，选择Install Centos 7,直接回车，开始安装

![](/img/centos7.2/8f646938abe1778660df396875951274.png)

进入配置参数界面，建议选择英文系统，当然选择中文系统也可，看个人喜好。

![](/img/centos7.2/c7e9c8ec2f128503babb862521b5c21e.png)

点击继续，进入具体设置配置界面

![](/img/centos7.2/78f0c1c506574ba088405452b297c778.png)

设置系统时间和时区，选择Asia/Shanghai，注意具体时间可能会差9小时，可以自己进行手动设置。

![](/img/centos7.2/5857c69732bbfc041671039d84ff8c32.png)

至于键盘和辅助语言选择根据个人喜好设置，个人建议英文

选择设置安装software软件，选中software
selection进行自己的定制安装，默认选中最小化安装。

![](/img/centos7.2/9ee752c8ded988102e58a79cb77ed727.png)

此次选择安装桌面版GNOME桌面，右侧可以选择想要安装的软件包。

![](/img/centos7.2/906631cd68755ad7cd23766d1a162991.png)

接下来，最重要的是设置installation destination，选中配置的磁盘（两次点击）

![](/img/centos7.2/a8b8a9f6401359d9268820b64c9fc24a.png)

选择自定义，进行磁盘分配。然后选择Done确定进入磁盘分配

![](/img/centos7.2/72e8498784fac187f5fd408de0b9abf4.png)

选择标准分区后，选择添加按钮进行磁盘分配

![](/img/centos7.2/5a6c7dce4fc5b0fd04ea51a979b1fea1.png)

记得文件系统选择ex4，swap分区最好设置2G往上，设置好boot和swap分区之后，剩余所有磁盘分配给根目录/。点击确认退出磁盘分配

![](/img/centos7.2/597a58f6dfb05cd5520b2d3fcba849fd.png)

关于KDUMP，建议关闭，报错文件看不懂，可以勾选

关于网络和主机名，建议选择打开网络并根据需要自行修改主机名。

配置完成之后点击开始安装。

安装过程中，可以设置root用户和普通用户账号和密码，设置完成之后，等待安装完成。

![](/img/centos7.2/8583314396d4118a861458d98ba471a4.png)

安装完成后，点击reboot重启

![](/img/centos7.2/61735bb11d2346fdae721032f5de150b.png)

会弹出用户协议选择界面，依此输入1-2-c-c即为同意协议

完成安装

输入密码之后，进入欢迎界面，可选择设置系统语言和键盘分布，还有google等用户可选择登录，可以选择跳过。

![](/img/centos7.2/180bee537cf2b314922639e474430ae3.png)

最后，进入Centos 7 桌面。
