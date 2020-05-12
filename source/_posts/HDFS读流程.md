---
title: "HDFS读流程"
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

**HDFS读流程**
```bash
[hadoop@hadoop001 ~]$ hdfs dfs -cat  /1.log
20/05/12 09:51:19 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... \
using builtin-java classes where applicable
ruozedata
[hadoop@hadoop001 ~]$ 
```
![HDFS读流程图](/img/Hadoop/HDFS读流程.png)

读取流程对用户操作是无感知的 

1.Client调用FileSystem的open(filePath)方法,与NN进行RPC通信，
返回该文件的部分或者全部的block列表
也就是返回【FSDataInputStream】对象

2.Client调用【FSDataInputStream】对象的read方法
去与第一个块的最近的DN进行读取，读取完成后，会check，假如ok，就关闭与DN通信。
假如读取失败，会记录DN+block信息，下次就不会从这个节点读取。那么就从第二个节点读取。

然后去与第二个块的最近的DN进行读取，以此类推。

假如当block列表全部读取完成，文件还没读取结束，就调用FileSystem从nn获取下一批次的block列表。

3.Client调用【FSDataInputStream】对象close方法，关闭输入流。