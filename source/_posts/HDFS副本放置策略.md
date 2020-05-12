---
title: "HDFS副本放置策略"
catalog: true
toc_nav_num: true
date: 2020-05-11 12:00:00
subtitle: "拓展"
article_type: 0 # 0 原创，1 转载
tags:
- [Hadoop]
- [HDFS]
categories:
- [Hadoop]
- [HDFS]
updateDate: 2020-05-11 12:00:00
top: 0  #置顶
---

![机架](/img/Hadoop/rack.jpg)
机架 rack1 5   rack2 5


生产上读写操作 尽量选择 某个DN节点
第一个副本：
放置在上传的DN节点； (nn和dn放一个副本中，有利于提升速度)
假如是非DN节点，就随机挑选一个磁盘不太慢，cpu不太忙的节点；

第二个副本：
放置在第一个副本不同的机架上的某个DN节点。

第三个副本:
与第二个副本相同机架的不同节点上。

如果副本数设置更多，就随机放。

机架安装考虑用电和机架的安装能力