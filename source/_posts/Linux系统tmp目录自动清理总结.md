---
title: "Linux系统tmp目录自动清理总结"
catalog: true
toc_nav_num: true
date: 2020-05-11 12:00:00
subtitle: "拓展"
article_type: 0 # 0 原创，1 转载
tags:
- [Linux]

categories:
- [Linux]

updateDate: 2020-05-11 12:00:00
top: 0  #置顶
---



在Centos7.2系统中/tmp文件夹下的文件是会被清理、删除的.

根据网上的调查，存在两种方式
1.主要是因为作业里面会调用tmpwatch命令删除那些一段时间没有访问的文件。
/etc/cron.daily/tmpwatch
但是在我的系统中没有找到这个文件和tmpwatch这个命令
```bash
[root@hadoop001 tmpfiles.d]# tmpwatch 30d /tmp/
bash: tmpwatch: command not found...
```
2.在 /usr/lib/tmpfiles.d/tmp.conf文件进行定义
```bash
[root@hadoop001 tmpfiles.d]# vi tmp.conf

#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.

# See tmpfiles.d(5) for details

# Clear tmp directories separately, to make them easier to override
v /tmp 1777 root root 10d #自动清理根目录的tmp文件夹
v /var/tmp 1777 root root 30d #自动清理var目录的tmp文件夹

# Exclude namespace mountpoints created with PrivateTmp=yes
x /tmp/systemd-private-%b-*
X /tmp/systemd-private-%b-*/tmp
x /var/tmp/systemd-private-%b-*
X /var/tmp/systemd-private-%b-*/tmp
```
 
参数后加时间，默认是hours。也可以使用30d表示30天，但是有些版本只支持hours。 

 
如果想将强制删除30天没有访问的文件改为7天，
只需修改以下两处
```bash
# Clear tmp directories separately, to make them easier to override
v /tmp 1777 root root 10d #自动清理根目录的tmp文件夹
v /var/tmp 1777 root root 30d #自动清理var目录的tmp文件夹
```

 
