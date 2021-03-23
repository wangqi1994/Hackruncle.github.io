---
title: "hexo版本问题导致报错“lineno”"
catalog: true
toc_nav_num: true
date: 2021-03-19 12:00:00
subtitle: "备忘"
article_type: 1 # 0 原创，1 转载
tags:
- [软件配置]
categories:
- [软件配置]
updateDate: 2021-03-19 12:00:00
top: 0  #置顶

---



hexo -v出现的问题

```
$ hexo -v
(node:9876) Warning: Accessing non-existent property 'lineno' of module exports inside circular dependency
(Use `node --trace-warnings ...` to show where the warning was created)
(node:9876) Warning: Accessing non-existent property 'column' of module exports inside circular dependency
(node:9876) Warning: Accessing non-existent property 'filename' of module exports inside circular dependency
(node:9876) Warning: Accessing non-existent property 'lineno' of module exports inside circular dependency
(node:9876) Warning: Accessing non-existent property 'column' of module exports inside circular dependency
(node:9876) Warning: Accessing non-existent property 'filename' of module exports inside circular dependency
hexo: 4.2.0
hexo-cli: 3.1.0
os: Windows_NT 10.0.18363 win32 x64
node: 14.0.0
v8: 8.1.307.30-node.30
uv: 1.37.0
zlib: 1.2.11
brotli: 1.0.7
ares: 1.16.0
modules: 83
nghttp2: 1.40.0
napi: 6
llhttp: 2.0.4
openssl: 1.1.1f
cldr: 36.1
icu: 66.1
tz: 2019c
unicode: 13.0
```

hexo d -g 出现的问题

```
$ hexo d -g
(node:3908) Warning: Accessing non-existent property 'lineno' of module exports inside circular dependency
(Use `node --trace-warnings ...` to show where the warning was created)
(node:3908) Warning: Accessing non-existent property 'column' of module exports inside circular dependency
(node:3908) Warning: Accessing non-existent property 'filename' of module exports inside circular dependency
(node:3908) Warning: Accessing non-existent property 'lineno' of module exports inside circular dependency
(node:3908) Warning: Accessing non-existent property 'column' of module exports inside circular dependency
(node:3908) Warning: Accessing non-existent property 'filename' of module exports inside circular dependency
INFO  Start processing
INFO  Files loaded in 94 ms
INFO  0 files generated in 22 ms
INFO  Deploying: git
INFO  Clearing .deploy_git folder...
INFO  Copying files from public folder...
FATAL Something's wrong. Maybe you can find the solution here: https://hexo.io/docs/troubleshooting.html
TypeError [ERR_INVALID_ARG_TYPE]: The "mode" argument must be integer. Received an instance of Object
    at copyFile (fs.js:1890:10)
    at tryCatcher (D:\Blog\node_modules\bluebird\js\release\util.js:16:23)
    at ret (eval at makeNodePromisifiedEval (D:\Node\node_global\node_modules\hexo-cli\node_modules\bluebird\js\release\promisify.js:184:12), <anonymous>:13:39)
    at D:\Blog\node_modules\hexo-fs\lib\fs.js:144:39
    at tryCatcher (D:\Blog\node_modules\bluebird\js\release\util.js:16:23)
    at Promise._settlePromiseFromHandler (D:\Blog\node_modules\bluebird\js\release\promise.js:547:31)
    at Promise._settlePromise (D:\Blog\node_modules\bluebird\js\release\promise.js:604:18)
    at Promise._settlePromise0 (D:\Blog\node_modules\bluebird\js\release\promise.js:649:10)
    at Promise._settlePromises (D:\Blog\node_modules\bluebird\js\release\promise.js:729:18)
    at Promise._fulfill (D:\Blog\node_modules\bluebird\js\release\promise.js:673:18)
    at Promise._resolveCallback (D:\Blog\node_modules\bluebird\js\release\promise.js:466:57)
    at Promise._settlePromiseFromHandler (D:\Blog\node_modules\bluebird\js\release\promise.js:559:17)
    at Promise._settlePromise (D:\Blog\node_modules\bluebird\js\release\promise.js:604:18)
    at Promise._settlePromise0 (D:\Blog\node_modules\bluebird\js\release\promise.js:649:10)
    at Promise._settlePromises (D:\Blog\node_modules\bluebird\js\release\promise.js:729:18)
    at Promise._fulfill (D:\Blog\node_modules\bluebird\js\release\promise.js:673:18)
    at Promise._resolveCallback (D:\Blog\node_modules\bluebird\js\release\promise.js:466:57)
    at Promise._settlePromiseFromHandler (D:\Blog\node_modules\bluebird\js\release\promise.js:559:17)
    at Promise._settlePromise (D:\Blog\node_modules\bluebird\js\release\promise.js:604:18)
    at Promise._settlePromise0 (D:\Blog\node_modules\bluebird\js\release\promise.js:649:10)
    at Promise._settlePromises (D:\Blog\node_modules\bluebird\js\release\promise.js:729:18)
    at Promise._fulfill (D:\Blog\node_modules\bluebird\js\release\promise.js:673:18)

```

出现这些是因为node版本太高，切换成低版本的node来安装Hexo就可以了

原先安装了最新版node14.0，后来装了一个比较稳定的node12.14版本，这个问题就解决了

