---
title: "mysql报错收集"
catalog: true
toc_nav_num: true
date: 2020-05-09 12:00:00
subtitle: "mysql报错解决方案"
article_type: 0 # 0 原创，1 转载
tags:
- [BUG]
- [MySQL]
categories:
- [BUG]
- [MySQL]
updateDate: 2020-05-09 12:00:00
top: 1 #置顶
---

### mysql报错
#### 1.Can't connect to local MySQL server through socket '/usr/local/mysql/mysql/mysql.sock' (2)
```bash
#查看3306端口是否被占用
lsof -i:3306 # lsof -i:port
[root@hadoop001 java]# lsof -i:3306
COMMAND   PID       USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
mysqld  60782 mysqladmin   35u  IPv6 673904      0t0  TCP *:mysql (LISTEN)
[root@hadoop001 java]# netstat -nlp |grep 3306
tcp6       0      0 :::3306                 :::*                    LISTEN      60782/mysqld        
[root@hadoop001 java]# 

#启动mysql
service mysql start
```
#### 2.Starting MySQL.. ERROR! The server quit without updating PID file (/usr/local/mysql/data/hostname.pid).
在root用户下，可以停止数据库，但是利用service mysql start命令启动mysql数据库时出现报错
需要切换到对应用户下，才可以启动数据库
```bash 
su - xxx
service mysql start 
```