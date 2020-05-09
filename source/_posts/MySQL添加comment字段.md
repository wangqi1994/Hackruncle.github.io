---
title: "MySQL添加comment字段"
catalog: true
toc_nav_num: true
date: 2020-04-29 12:00:00
subtitle: "拓展"
article_type: 0 # 0 原创，1 转载
tags:
- [MySQL]
categories:
- [MySQL]
updateDate: 2020-04-29 12:00:00
top: 0  #置顶
---

在MySQL数据库中， 字段或列的注释是用属性comment来添加。

创建新表的脚本中， 可在字段定义脚本中添加comment属性来添加注释。

示例代码如下：
```sql
create table test( 
    id int(11) not null default 0 comment '用户id' ) 
```
如果是已经建好的表， 也可以用修改字段的命令，然后加上comment属性定义，就可以添加上注释了。

示例代码如下：
```sql
alter table test 
change column id id int(11) not null default 0 comment '测试表id'
```
查看已有表的所有字段的注释呢？
可以用命令：show full columns from table 来查看， 示例如下：
```sql
show full columns from test;
```
创建表的时候写注释
```sql
create table test1 ( 
    field_name int comment '字段的注释' 
)comment='表的注释'; #写不写等号是一样的
```
修改表的注释
```sql
alter table test1 comment '修改后的表的注释';
```
修改字段的注释
```sql
alter table test1 modify column field_name int comment '修改后的字段注释'; 
```
**注意：字段名和字段类型照写就行**

**查看表注释的方法**
-在生成的SQL语句中看 
```sql
    show  create  table  test1; 
```
-在元数据的表里面看
```sql
    use information_schema; 
    select * from TABLES where TABLE_SCHEMA='my_db' and TABLE_NAME='test1' \G
```
**查看字段注释的方法**
-show 
```sql
    show  full  columns  from  test1; 
```
-在元数据的表里面看 
```sql
    select * from COLUMNS where TABLE_SCHEMA='my_db' and TABLE_NAME='test1' \G
```