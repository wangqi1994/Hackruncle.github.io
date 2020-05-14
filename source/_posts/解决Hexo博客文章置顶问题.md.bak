---
title: "解决Hexo博客文章置顶问题"
catalog: true
toc_nav_num: true
date: 2020-05-01 12:00:00
subtitle: "拓展"
article_type: 1 # 0 原创，1 转载
tags:
- [hexo]

categories:
- [hexo]

updateDate: 2020-05-01 12:00:00
top: 0  #置顶
---

[原文](http://zhwhong.cn/2017/03/23/deal-with-hexo-article-top-problem/)

Hexo默认只提供了按发布日期的排序
```bash
# Home page setting
# path: Root path for your blogs index page. (default = '')
# per_page: Posts displayed per page. (0 = disable pagination)
# order_by: Posts order. (Order by date descending by default)
index_generator:
  path: ''
  per_page: 10
  order_by: -date
```

原理：在Hexo生成首页HTML时，将top值高的文章排在前面，达到置顶功能。

修改Hexo文件夹下的node_modules/hexo-generator-index/lib/generator.js，在生成文章之前进行文章top值排序。

需添加的代码：

```bash
  posts.data = posts.data.sort(function(a, b) {
      if(a.top && b.top) {
          if(a.top == b.top) return b.date - a.date;
          else return b.top - a.top;
      }
      else if(a.top && !b.top) {
          return -1;
      }
      else if(!a.top && b.top) {
          return 1;
      }
      else return b.date - a.date;
  });


```
其中涉及Javascript的比较函数：
```bash
cmp(var a, var b) {
    return  a - b; // 升序，降序的话就 b - a
}
```
修改完成后，只需要在front-matter中设置需要置顶文章的top值，将会根据top值大小来选择置顶顺序
top值越大越靠前。需要注意的是，这个文件不是主题的一部分，也不是Git管理的，备份的时候比较容易忽略。

以下是最终的generator.js内容
```bash
'use strict';
var pagination = require('hexo-pagination');
module.exports = function(locals) {
  var config = this.config;
  var posts = locals.posts.sort(config.index_generator.order_by);
  posts.data = posts.data.sort(function(a, b) {
      if(a.top && b.top) {
          if(a.top == b.top) return b.date - a.date;
          else return b.top - a.top;
      }
      else if(a.top && !b.top) {
          return -1;
      }
      else if(!a.top && b.top) {
          return 1;
      }
      else return b.date - a.date;
  });
  var paginationDir = config.pagination_dir || 'page';
  return pagination('', posts, {
    perPage: config.index_generator.per_page,
    layout: ['index', 'archive'],
    format: paginationDir + '/%d/',
    data: {
      __index: true
    }
  });
};
```