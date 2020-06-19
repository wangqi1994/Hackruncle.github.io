---
title: "解决bash:xx:command not found"
catalog: true
toc_nav_num: true
date: 2020-06-19 12:00:00
subtitle: "bug解决方案"
article_type: 0 # 0 原创，1 转载
tags:

- [BUG]
- [Linux]
  categories:
- [BUG]
- [Linux]
updateDate: 2020-06-19 12:00:00
top: 0 #置顶
---

场景：

在配置java环境变量之后，命令行报bash:…:command not found的解决办法（几乎所有命令）

原因：

由于设置JAVA环境变量时设置PATH属性导致command not found错误

错误设置：

export PATH=JAVA_HOME/bin：PATH

解决方法：

1、在命令行中输入：export PATH=/usr/bin:/usr/sbin:/bin:/sbin 这样可以保证命令行命令暂时可以使用。命令执行完之后先不要关闭终端。

2、在命令行中输入 vi /etc/profile 查看是否自己另外设置了PATH属性。在Vi编辑器中修改正确之后，
：wq保存此文件
在终端输入source profile

3、关闭终端，重新打开终端，输入命令执行，OK，全部正常！


