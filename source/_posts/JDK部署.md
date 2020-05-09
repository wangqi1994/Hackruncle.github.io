---
title: "JDK部署"
catalog: true
toc_nav_num: true
date: 2020-04-26 12:00:00
subtitle: "JDK部署备忘流程"
article_type: 0 # 0 原创，1 转载
tags:
- [ruozedata]
- [Linux]
- [JAVA]
categories:
- [ruozedata]
- [Linux]
- [JAVA]
updateDate: 2020-04-26 12:00:00
top: 0  #置顶
---

### 环境：
OS：CentOS7.2 （虚拟机）
JDK版本：jdk-8u45-linux-x64.gz （百度下载)

### 1.安装准备
windows下载安装包，通过rz上传到Linux系统中

### 2.解压JDK程序包
jdk文件建议放在/usr/java,没有则创建
```bash
[root@ruozedata001 ~]# mkdir  /usr/java
[root@ruozedata001 ~]# tar -xzvf jdk-8u45-linux-x64.gz -C /usr/java/
 # -C 解压到那个文件夹 /usr/java
 # tar.gz解压储来之后建议习惯性查看一下所属用户和用户组有没有变化
 # 可能存在权限问题：那是解压一瞬间的用户和用户组，导致用户错误，可能会报错莫名其妙
[root@hadoop001 java]# ll
total 4
drwxr-xr-x. 8 10 143 4096 Apr 11  2015 jdk1.8.0_45
[root@hadoop001 java]# chown -R root:root jdk1.8.0_45
[root@hadoop001 java]# ll
total 4
drwxr-xr-x. 8 root root 4096 Apr 11  2015 jdk1.8.0_45
 #修改用户权限
 ```
### 3.配置环境变量
```bash
[root@ruozedata001 java]# vi /etc/profile
#ruozedata env
export JAVA_HOME=/usr/java/jdk1.8.0_45
export PATH=$JAVA_HOME/bin:$PATH
```
### 4.source生效环境变量
```bash
[root@ruozedata001 ~]# source /etc/profile
[root@ruozedata001 ~]# which java
/usr/java/jdk1.8.0_45/bin/java
```
export 生效，路径必须是/usr/java
保存，生效
### 5.测试
```bash
[root@hadoop001 ~]# which java
/usr/java/jdk1.8.0_45/bin/java
[root@hadoop001 ~]# java -version
java version "1.8.0_45"
Java(TM) SE Runtime Environment (build 1.8.0_45-b14)
Java HotSpot(TM) 64-Bit Server VM (build 25.45-b02, mixed mode)
```
完成JDK部署
