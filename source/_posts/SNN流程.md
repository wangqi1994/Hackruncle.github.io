---
title: "SNN流程"
catalog: true
toc_nav_num: true
date: 2020-05-13 12:00:00
subtitle: "拓展"
article_type: 0 # 0 原创，1 转载
tags:
- [Hadoop]
- [HDFS]
categories:
- [Hadoop]
- [HDFS]
updateDate: 2020-05-13 12:00:00
top: 0  #置顶
---

**SNN流程**

```bash
#SNN
[hadoop@hadoop001 current]$ pwd
/home/hadoop/tmp/dfs/namesecondary/current
[hadoop@hadoop001 current]$ ll
total 197948
-rw-rw-r--. 1 hadoop hadoop        42 May 13 08:09 edits_0000000000001114471-0000000000001114472
-rw-rw-r--. 1 hadoop hadoop        42 May 13 09:09 edits_0000000000001114473-0000000000001114474
-rw-rw-r--. 1 hadoop hadoop        42 May 13 10:09 edits_0000000000001114475-0000000000001114476
-rw-rw-r--. 1 hadoop hadoop      2364 May 13 09:09 fsimage_0000000000001114474
-rw-rw-r--. 1 hadoop hadoop        62 May 13 09:09 fsimage_0000000000001114474.md5
-rw-rw-r--. 1 hadoop hadoop      2364 May 13 10:09 fsimage_0000000000001114476
-rw-rw-r--. 1 hadoop hadoop        62 May 13 10:09 fsimage_0000000000001114476.md5
-rw-rw-r--. 1 hadoop hadoop       205 May 13 10:09 VERSION
[hadoop@hadoop001 current]$ 
#NN
[hadoop@hadoop001 current]$ pwd
/home/hadoop/tmp/dfs/name/current
[hadoop@hadoop001 current]$ ll
total 198980
-rw-rw-r--. 1 hadoop hadoop        42 May 13 08:09 edits_0000000000001114471-0000000000001114472
-rw-rw-r--. 1 hadoop hadoop        42 May 13 09:09 edits_0000000000001114473-0000000000001114474
-rw-rw-r--. 1 hadoop hadoop        42 May 13 10:09 edits_0000000000001114475-0000000000001114476
-rw-rw-r--. 1 hadoop hadoop   1048576 May 13 10:09 edits_inprogress_0000000000001114477
-rw-rw-r--. 1 hadoop hadoop      2364 May 13 09:09 fsimage_0000000000001114474
-rw-rw-r--. 1 hadoop hadoop        62 May 13 09:09 fsimage_0000000000001114474.md5
-rw-rw-r--. 1 hadoop hadoop      2364 May 13 10:09 fsimage_0000000000001114476
-rw-rw-r--. 1 hadoop hadoop        62 May 13 10:09 fsimage_0000000000001114476.md5
-rw-rw-r--. 1 hadoop hadoop         8 May 13 10:09 seen_txid
-rw-rw-r--. 1 hadoop hadoop       205 May 11 15:32 VERSION
[hadoop@hadoop001 current]$ 
```
![](/img/Hadoop/SNN.png)

1.SNN将NN的日志文件edits475-476（图中487-488） 和镜像文件fsimage474（图中486） 接收

2.SNN将接收文件进行合并为镜像文件fsimage476（图中488）

3.SNN返回镜像文件fsimage476给NN
NN自身进行edit操作，写入edit477 inprogress （图中489）
