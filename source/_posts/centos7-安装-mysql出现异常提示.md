---
title: "centos7 安装 mysql出现异常提示"
catalog: true
toc_nav_num: true
date: 2020-06-20 12:00:00
subtitle: "bug解决方案"
article_type: 0 # 0 原创，1 转载
tags:

- [Linux]
- [MySQL]
  categories:
- [Linux]
- [MySQL]
updateDate: 2020-06-20 12:00:00
top: 0 #置顶

---

场景：

centos7 安装 MySQL出现异常提示

 TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details

解决办法：

首先说明，不需要任何更改。
这些非标准行为仍然是TIMESTAMP的默认行为，但自MySQL 5.6.6起已弃用，并且此警告在启动时出现
现在，如果要去掉这个警告，则必须在my.cnf配置文件中增加

```shell
[mysqld]

explicit_defaults_for_timestamp=true
```

my.cnf（或其他配置文件）的位置因系统而异。 如果找不到，请参阅https://dev.mysql.com/doc/refman/5.7/en/option-files.html