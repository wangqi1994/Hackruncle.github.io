---
title: "解决bash: hdfs: command not found"
catalog: true
toc_nav_num: true
date: 2020-05-10 12:00:00
subtitle: "拓展"
article_type: 0 # 0 原创，1 转载
tags:
- [Hadoop]
- [HDFS]
- [BUG]
categories:
- [Hadoop]
- [HDFS]
- [BUG]
updateDate: 2020-05-10 12:00:00
top: 0  #置顶
---

在/home/hadoop/app/hadoop文件夹下
执行 hdfs dfs -mkdir /usr/input/hot时
命令需要
bin/hdfs dfs -mkdir /usr/input/hot

如在其他文件夹下运行hdfs dfs -mkdir /usr/input/hot
遇到问题

bash: hdfs: command not found


解决方案：

在/etc/profile下添加hadoop的文件路径
```bash
[hadoop@hadoop001 hadoop]$ vi /etc/profile

export JVA_HOME=/usr/java/jdk1.8.0_181
export PATH=$JVA_HOME/bin:$PATH
# hadoop 
 export HADOOP_HOME=/home/hadoop/app/hadoop/bin # hadoop安装文件
 export PATH=$PATH:$HADOOP_HOME

 [hadoop@hadoop001 etc]$ source profile
 [hadoop@hadoop001 etc]$ which hdfs
~/app/hadoop/bin/hdfs
```
然后source 生效环境变量
which 查看一下是否生效

之后执行bin/hdfs dfs -mkdir /usr/input/hot 即可
