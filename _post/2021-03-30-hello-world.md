---
title: Gitee和GitHub生成/添加SSH公钥的詳細教程
date: 2022-07-01 15:34:00 +0800
categories: [技術][linux]
tags: [生活]
pin: true
author: 西土公民

toc: true
comments: true
typora-root-url: ../../jilefo.github.io
math: false
mermaid: true#
---

## 前言

　　现如今将代码开源已经成为软件开发行业的一种趋势，而现在比较有名的代码托管平台有GItHub、Gitee、Gitlab等相关平台。而我们在使用代码托管平台最为常见的就是如何将自己本地的代码推送到远程托管平台中的仓库中，现如今各大托管平台基本上都提供了基于SSH协议的GIt服务，因此我们常见的方式就是使用SSH协议访问代码托管中的仓库。

## Git Bash生成并找到SSH Key

### 输入以下命令：

```
ssh-keygen -t rsa -C ``"xxxxx@xxxxx.com"
```

按照提示完成三次回车（注意如果说想要以后能够免密提交的话直接按三次空格即可），即可生成 ssh key。

### 通过查看 ~/.ssh/id_rsa.pub 文件内容，获取到你的 public key：

```
cat ~/.ssh/id_rsa.pub
```

![img](/_posts/2021-03-30-hello-world.assets/1336199-20200608004510101-677258405.png)



###  或者直接到C盘中找到id_rsa.pub文件：

![img](/_posts/2021-03-30-hello-world.assets/1336199-20200608004625070-443191610.png)

 

## GitHub添加公钥

复制生成后的 ssh key，通过Settings => SHH and GPG keys=> New SHH key 添加生成的 SSH key 添加到仓库中，如下图所示：

![img](/_posts/2021-03-30-hello-world.assets/1336199-20200608004729823-483691268.png)

 

### 添加完成后，在Git Bash终端验证 SSH Key是否添加成功:

```
ssh -T git@github.com
```

输出以下消息则表示成功：Hi YSGStudyHards! You've successfully authenticated, but GitHub does not provide shell access.

![img](/_posts/2021-03-30-hello-world.assets/1336199-20200608004834128-1826141120.png)

##  Gitee添加公钥：

复制生成后的 ssh key，通过仓库主页 管理=>部署公钥管理=>添加部署公钥，添加生成的 public key 添加到仓库中，如下图所示：

![img](/_posts/2021-03-30-hello-world.assets/1336199-20200608005052516-1535781759.png)

 

 

 

### 添加完成后，在Git Bash终端验证 SSH Key是否添加成功:

```
ssh -T git@gitee.com
```

输出以下消息则表示成功：You've successfully authenticated, but GITEE.COM does not provide shell access.

![img](/_posts/2021-03-30-hello-world.assets/1336199-20200608005110610-1610820714.png)