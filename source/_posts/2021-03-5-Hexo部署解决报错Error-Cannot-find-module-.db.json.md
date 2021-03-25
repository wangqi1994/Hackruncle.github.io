---
title: "Hexo部署解决报错Error: Cannot find module './db.json'"
catalog: true
toc_nav_num: true
date: 2021-03-5 12:00:00
subtitle: "备忘流程"
article_type: 0 # 0 原创，1 转载
tags:
- [hexo]
categories:
- [hexo]
updateDate: 2021-03-5 12:00:00
top: 0  #置顶

---

```
Error: Cannot find module './db.json'
at Function.Module._resolveFilename (module.js:336:15)
at Function.Module._load (module.js:286:25)
at Module.require (module.js:365:17)
at require (module.js:384:17)
at Object. (/user/XXX/node_modules/hexo-server/node_modules/compression/node_modules/accepts/node_modules/mime-types/node_modules/mime-db/index.js:11:18)
at Module._compile (module.js:434:26)
at Object.Module._extensions..js (module.js:452:10)
at Module.load (module.js:355:32)
at Function.Module._load (module.js:310:12)
at Module.require (module.js:365:17)
at require (module.js:384:17)
at Object. (/user/XXX/node_modules/hexo-server/node_modules/compression/node_modules/accepts/node_modules/mime-types/index.js:15:10)
at Module._compile (module.js:434:26)
at Object.Module._extensions..js (module.js:452:10)
at Module.load (module.js:355:32)
at Function.Module._load (module.js:310:12)
at Module.require (module.js:365:17)
at require (module.js:384:17)
at Object. (/user/XXX/node_modules/hexo-server/node_modules/compression/node_modules/accepts/index.js:16:12)
at Module._compile (module.js:434:26)
at Object.Module._extensions..js (module.js:452:10)
at Module.load (module.js:355:32)
at Function.Module._load (module.js:310:12)
at Module.require (module.js:365:17)
at require (module.js:384:17)
at Object. (/user/XXX/node_modules/hexo-server/node_modules/compression/index.js:17:15)
at Module._compile (module.js:434:26)
at Object.Module._extensions..js (module.js:452:10)
at Module.load (module.js:355:32)
at Function.Module._load (module.js:310:12)
at Module.require (module.js:365:17)
at require (module.js:384:17)
at Object. (/user/XXX/node_modules/hexo-server/lib/middlewares/gzip.js:3:16)
at Module._compile (module.js:434:26)
at Object.Module._extensions..js (module.js:452:10)
at Module.load (module.js:355:32)
at Function.Module._load (module.js:310:12)
at Module.require (module.js:365:17)
at require (/user/XXX/node_modules/hexo/lib/hexo/index.js:213:21)
at /user/XXX/node_modules/hexo-server/index.js:24:50
at /user/XXX/node_modules/hexo/lib/hexo/index.js:229:12
at tryCatcher (/user/XXX/node_modules/hexo/node_modules/hexo-fs/node_modules/bluebird/js/release/util.js:11:23)
at Promise._settlePromiseFromHandler (/user/XXX/node_modules/hexo/node_modules/hexo-fs/node_modules/bluebird/js/release/promise.js:489:31)
at Promise._settlePromise (/user/XXX/node_modules/hexo/node_modules/hexo-fs/node_modules/bluebird/js/release/promise.js:546:18)
at Promise._settlePromise0 (/user/XXX/node_modules/hexo/node_modules/hexo-fs/node_modules/bluebird/js/release/promise.js:591:10)
at Promise._settlePromises (/user/XXX/node_modules/hexo/node_modules/hexo-fs/node_modules/bluebird/js/release/promise.js:674:18)
at Promise._fulfill (/user/XXX/node_modules/hexo/node_modules/hexo-fs/node_modules/bluebird/js/release/promise.js:615:18)
at Promise._resolveCallback (/user/XXX/node_modules/hexo/node_modules/hexo-fs/node_modules/bluebird/js/release/promise.js:416:57)
at Promise._settlePromiseFromHandler (/user/XXX/node_modules/hexo/node_modules/hexo-fs/node_modules/bluebird/js/release/promise.js:502:17)
at Promise._settlePromise (/user/XXX/node_modules/hexo/node_modules/hexo-fs/node_modules/bluebird/js/release/promise.js:546:18)
at Promise._settlePromise0 (/user/XXX/node_modules/hexo/node_modules/hexo-fs/node_modules/bluebird/js/release/promise.js:591:10)
at Promise._settlePromises (/user/XXX/node_modules/hexo/node_modules/hexo-fs/node_modules/bluebird/js/release/promise.js:674:18)
INFO Deleted database.
INFO Deleted public folder.
```

```
发生这种情况是因为mime-db模块中缺少db.json文件
1.可以创建db.json文件或将mime-db模块安装在其他位置，然后从那里复制db.json
2.把node-modules 删除之后重装
```