---
title: "Jps命令—使用详解"
catalog: true
toc_nav_num: true
date: 2020-05-08 12:00:00
subtitle: "拓展"
article_type: 1 # 0 原创，1 转载
tags:
- [JAVA]
categories:
- [JAVA]
updateDate: 2020-05-08 12:00:00
top: 0  #置顶
---

**Jps命令—使用详解**

原文：https://blog.csdn.net/wisgood/article/details/38942449

 jps是jdk提供的一个查看当前java进程的小工具， 可以看做是JavaVirtual Machine Process Status Tool的缩写。非常简单实用。

       命令格式：jps [options ] [ hostid ] 

       [options]选项 ：
-q：仅输出VM标识符，不包括classname,jar name,arguments in main method 
-m：输出main method的参数 
-l：输出完全的包名，应用主类名，jar的完全路径名 
-v：输出jvm参数 
-V：输出通过flag文件传递到JVM中的参数(.hotspotrc文件或-XX:Flags=所指定的文件 
-Joption：传递参数到vm,例如:-J-Xms512m

        [hostid]：

[protocol:][[//]hostname][:port][/servername]

        命令的输出格式 ：
lvmid [ [ classname| JARfilename | "Unknown"] [ arg* ] [ jvmarg* ] ]

1）jps

![](/img/jps/jps.png)

2）jps –l:输出主类或者jar的完全路径名

![](/img/jps/jps-l.png)

3）jps –v :输出jvm参数

![](/img/jps/jps-v.png)

4）jps –q ：仅仅显示java进程号

![](/img/jps/jps-q.png)

5)jps -mlv10.134.68.173

![](/img/jps/jps-mlv.png)

       注意：如果需要查看其他机器上的jvm进程，需要在待查看机器上启动jstatd。