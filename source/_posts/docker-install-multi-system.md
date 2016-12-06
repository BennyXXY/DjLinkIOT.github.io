---
title: Docker 安装 & 配置教程 (Windows + Linux + Mac)
date: 2016-12-02 19:48:34
authors:
  - EvanWang
categories:
  - Ops
  - Docker
tags:
  - Docker
  - Ops
  - DevOps
---

# Windows 环境下安装 Docker

如果是在 `Linux` 系统安装 Docker，则比较简单，因为 Docker 就是基于 Linux 内核来进行容器化与资源隔离的，可以直接通过命令安装使用。

对于 `Windows` 来说，稍有些麻烦，但目前 Docker 也提供了支持，且在不断完善。安装之前首先需要看一下你的 `Windows版本`，分两种情况，一种是 `Windows 10 64位专业版`，一种是其他版本（比如很多人仍然推崇的 `Win7`）。

<!-- more -->

`Windows 10 64位专业版` 可以直接支持安装 `Docker原生版`，性能最好，体验最佳。

`其他版本（比如 Win7）` 只能使用 Docker 官方提供的一种过度技术 `Docker ToolBox`，这种技术不得不依赖Oracle的 `Virtualbox` 以在你的系统里创建一个虚拟机用以模拟Linux运行环境，好在封装的比较好，基本可以忽略这个虚拟机的存在，只需专心使用Docker即可。

## 在Windows 10 64位专业版的安装 （建议）

### CPU虚拟化与Hyper-v

安装Docker前，需要确定两个基础环境：

- CPU支持虚拟化（一般都支持，如果在操作系统中没看到，则可以手动到BIOS里打开，如果实在不支持，换台新的电脑吧），具体可以通过任务管理器查看，如图

{% asset_img docker-win10-cpu-virtual.png docker-win10-cpu-virtual %}

你的操作系统需要开启Hyper-V，如图

{% asset_img docker-win10-hyperv.png docker-win10-hyperv %}

### 安装包

然后到官方网站下载安装包直接安装即可

## 非Windows 10 64位专业版（无法使用原生Docker）的安装

# Docker配置

# 参考文档

- [Docker环境在windows系统下的安装与配置](http://www.jianshu.com/p/490884917c4d)