---
title: "MapReduce2.x 架构设计"
catalog: true
toc_nav_num: true
date: 2020-05-17 12:00:00
subtitle: "mapreduce架构设计"
article_type: 0 # 0 原创，1 转载
tags:
- [ruozedata]
- [Hadoop]
categories:
- [ruozedata]
- [Hadoop]
updateDate: 2020-05-17 12:00:00
top: 0  #置顶
---

### MapReduce2.x 架构设计 

又可以称为 
* mr on yarn提交流程 
* yarn的架构设计  

#### 1 container 容器  
首先明确一个container容器的概念，这是一个虚拟的概念，其实是一组memory+cpu vcore资源的组合
Container 是 YARN 中的资源抽象，它封装了某个节点上的多维度资源，
如内存、 CPU、磁盘、网络等，当 AM 向 RM 申请资源时，RM 为 AM 返回的资源便是用 Container 表示的。
YARN 会为每个任务分配一个 Container，且该任务只能使用该 Container 中描述的 资源。
容器是一个动态划分资源。

在内存够的情况下，适当增加cpu vcore带来计算效率的提升
![](/img/Hadoop/container.png)

#### 2 架构
mapreduce也是主从架构
Resourcemanager是主，简称 rm ，包含：
* ApplicationsManager  应用管理器 作业和程序等提交到的地方

* ResourceScheduler    资源调度器  

NodeManager是从，简称nm

工作流程
![](/img/Hadoop/MR架构设计.png)

1.client向rm提交应用程序（jar） 其中已经包含ApplicationMaster主程序和启动命令
2.ApplicationsManager  会为job分配第一个container，并与对应的nodemanager通信，要求他
在这个container中启动ApplicationMaster
3.Applicationmaster向 ApplicationsManager注册，用户就可以在yarn的web界面看到这个job的运行状态
4.Applicationmaster采取轮询的方式，通过【RPC】协议向ResourceScheduler申请和领取资源列表
（信息包括哪台nm 多少内存 多少cpu vcore）
5.一旦app master拿到资源列表，就和对应的nm进程通信，要求启动任务task 计算代码
6.NM为任务设置好运行环境(container容器 包含jar包等资源) ，将任务启动命令写在一个脚本里，并通过该脚本
启动任务task
7.各个任务task通过【RPC】协议向app master汇报自己的进度和状态，以此让app master随时掌握task的运行状态。
当task运行失败，会在另外一个container容器中重启任务。
8.当所有task运行完成后，app master向 apps manager申请注销和关闭作业
---------------------

这时可以在web页面查看任务状态，包含两种状态：
* 是不是完成的   
* 完成的是成功还是失败的
---------------------
