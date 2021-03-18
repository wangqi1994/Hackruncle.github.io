---
title: "Typora自动上传图片配置，集成PicGo-Core"
catalog: true
toc_nav_num: true
date: 2021-03-18 12:00:00
subtitle: "备忘"
article_type: 1 # 0 原创，1 转载
tags:
- [软件配置]
categories:
- [软件配置]
updateDate: 2021-03-18 12:00:00
top: 0  #置顶
---





​         由于markdown上传图片默认是在本地，在其他地方打开时，看不了图片，所以对Typora进行PicGo-Core配置，从而自动上传图片至网络上。

集成步骤如下：

### **一、下载PicGo-Core**

![img](https://i.loli.net/2021/03/18/eaqURYSsPMXHcby.png)

![img](https://i.loli.net/2021/03/18/ZfxmwJOlIFMvP79.png)

![img](https://i.loli.net/2021/03/18/7IfuQbh5zjYaqEM.png)

![img](https://i.loli.net/2021/03/18/DiI58xT6NXgLtlb.png)

![img](https://i.loli.net/2021/03/18/XKPFyvr5TAMwunU.png)



### **二、配置PicGo-Core的图床**

![img](https://i.loli.net/2021/03/18/jrm4RsouKwyt1kP.png)

**注意：**图片中“对网络位置的图片应用上述规则”这个选项。

**如果不勾选**，从其他网站复制的图片，就不会上传至你配置的图床，md文档中会直接显示对应网站图片链接；

**如果勾选了**，就会在本地生成upload文件夹，自动下载图片后，再上传至你配置的图床。

**无论是否勾选**，对于QQ截屏的图片，也会在本地生成upload文件夹，保存图片后，再上传至你配置的图床。

 

具体配置依赖于你选择用什么图床（就是存储到哪里）

**如果准备用gitee作为图床，跳过此步，直接看下方的gitee配置步骤**

配置参考文档：https://picgo.github.io/PicGo-Core-Doc/zh/guide/config.html

![img](https://i.loli.net/2021/03/18/7GFDfuV5JPNLiEa.png)

### **三、验证功能**
上述配置完成后，可以验证下

![img](https://i.loli.net/2021/03/18/uypWdGhqFKUHjoR.png)

![img](https://i.loli.net/2021/03/18/DW5NsXb7FGm1OcE.png)

### **四、gitee配置步骤**
#### 1、gitee账号配置
先有一个gitee账号，官网：https://gitee.com/

创建一个**公有仓库**，用于存储图片

生成一个token用于PicGo操作你的仓库（**生成后的token务必自己保存下，防止丢失**）

访问：https://gitee.com/profile/personal_access_tokens

![img](https://i.loli.net/2021/03/18/3Kz8XRc9TALoSx4.png)

#### 2、安装nodejs
因为使用gitee作为图床，需要下载gitee-uploader插件，而下载插件又需要nodejs的运行时环境

下载地址：https://nodejs.org/en/

安装node-v12.16.2-x64.msi文件，一路next就可以了

#### 3、下载插件
需要下载两个插件

gitee-uploader（用于使用gitee作为图床）

super-prefix（用于上传图片时能自动使用时间戳重命名）

 1.查询之前安装的PicGo执行路径

![img](https://i.loli.net/2021/03/18/uypWdGhqFKUHjoR.png)

![img](https://i.loli.net/2021/03/18/3w91x4ciSHdpYNI.png)

 2.拷贝路径后进入cmd操作

```
cd C:\Users\aji\AppData\Roaming\Typora\picgo\win64
.\picgo.exe install gitee-uploader
.\picgo.exe install super-prefix
```


均下载成功即可（如果执行报错 NPM is not installed，请检查上 #四.2步中的 nodejs 是否已安装成功），如：

![img](https://i.loli.net/2021/03/18/HnXSo1g9vc7wstb.png)

![img](https://i.loli.net/2021/03/18/d7KJ2XtADWbQmeE.png)

#### 4、修改配置文件


修改为如下内容：

```{
{
"picBed": {
    "uploader": "gitee", // 代表当前的上传图床
    "gitee": {
      "repo": "", // 仓库名，格式是 username/reponame 必填
      "token": "", // gitee 私人令牌 必填
      "path": "", // 自定义存储路径，比如 img/ 建议填
      "customUrl": "", // 没有自己的域名的话，可以默认为空就行； 如果自定义域名，注意要加http://或者https://，
      "branch": "" // 分支名，默认是 master
    }
  },
  "picgoPlugins": {
    "picgo-plugin-gitee-uploader": true,
    "picgo-plugin-super-prefix": true
  }, // 为插件预留
  "picgo-plugin-super-prefix": {
    "fileFormat": "YYYYMMDDHHmmss"
  } //super-prefix插件配置
}
```

5、配置完成后验证

![img](https://i.loli.net/2021/03/18/uypWdGhqFKUHjoR.png)

![img](https://i.loli.net/2021/03/18/DW5NsXb7FGm1OcE.png)

***

如果图片上传成功并可以访问，自动上传图片的配置就结束了

参考文档
https://support.typora.io/Upload-Image/#install-prebuilt-binary-of-picgo-core-linux--windows

https://blog.csdn.net/jaymie1023/article/details/105361168/

https://github.com/PicGo/PicGo-Core

https://picgo.github.io/PicGo-Core-Doc/zh/guide/config.html#%E9%BB%98%E8%AE%A4%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6
