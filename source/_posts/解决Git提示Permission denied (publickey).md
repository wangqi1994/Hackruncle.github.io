---
title: "解决Git提示Permission denied (publickey)"
catalog: true
toc_nav_num: true
date: 2020-05-10 12:00:00
subtitle: "bug"
article_type: 1 # 0 原创，1 转载
tags:
- [BUG]
- [Git]
categories:
- [BUG]
- [Git]
updateDate: 2020-05-10 12:00:00
top: 0  #置顶
---

```bash
$ git clone https://github.com/wangqi1994/wangqi1994.github.io qiblog
Cloning into 'protobuf'...
The authenticity of host 'github.com (13.229.188.59)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'github.com,13.229.188.59' (RSA) to the list of known hosts.
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```
github中自己账户settings-SSH and GPG keys-new ssh key 
名字自己定，key有以下步骤提取。

回到需要下载源码的机器终端

```bash
ssh-keygen -t rsa  #敲入命令，一路回车
cd /root/.ssh/
cat id_rsa.pub 
ssh-rsa AAAAB3AAABIwAAAQEAzVPno/Cm5ApGGMP8YjituJGegOCq7TVKVECehWog9hTfC0Z5PMsf
5OWkWvUZ85nFJBuwhMszxkjFSd7e6INYJ42WfGKxPXm7ZoOQxkBZAetUUaNvDhCKZCdLNHWGde8gaX84
i39JKWgwYrzX9Y1T+bDI1cJiUuNN6Xr8x4ZkMm4e+LugYtVSKGZKz7zLcp1mXQszh9mWM08/yyRq/CdT
Ely1ghojUDUNFTzyk6VQz/rzMFoiVuwbYlQasqdR4xIzvnIjfBrtSP4z+qdD+wZFvSABnFClXH0nJEaa
KX9EdJpi2ezvLvAblDg371J
#取出公钥，复制粘贴github中的key中，保存
ssh -T git@github.com  # 测试是否成功
```
