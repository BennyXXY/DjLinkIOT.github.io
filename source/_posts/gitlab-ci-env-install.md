---
title: Gitlab CI Runner 打包机环境搭建
date: 2016-11-28 11:08:02
author:
- EvanWang
categories: 
- Workflow
- Gitlab CI
tags: 
- Gitlab
- Gitlab CI
- Gitlab CI Runner
- CI
---
# Gitlab CI Runner 打包机环境搭建（Ubuntu）

## 基本配置

### 1. 系统版本

#### Ubuntu

- 推荐版本: 14.04LTS

- 查看Ubuntu版本号

> sudo lsb_release -a

<!-- more -->

### 2. 内核版本

- 推荐版本: > 4.4

- 查看Ubuntu版本号

> uname -r

- 升级内核方法

> sudo apt-get dist-upgrade

### 3. Git

- 设置最新Git源

> sudo apt-add-repository ppa:git-core/ppa  
> sudo apt-get update

- 安装Client：

> sudo apt-get install git

- 升级

> sudo apt-get dist-upgrade

### 4. Shell (Zsh)

- 配置与安装：[参考文章](http://www.jianshu.com/p/9189eac3e52d)

### 5. JDK

#### 检查JDK

> java -version

#### 安装SDK

- Installing default JRE/JDK

> sudo apt-get install default-jdk

- Installing Oracle JDK

> sudo apt-get install python-software-properties  
> sudo add-apt-repository ppa:webupd8team/java  
> sudo apt-get update

- Oracle JDK 6 (旧版本)

> sudo apt-get install oracle-java6-installer

- Oracle JDK 7 (较新的稳定版本)

> sudo apt-get install oracle-java7-installer

- Oracle JDK 8 (最新版本)

> sudo apt-get install oracle-java8-installer

#### 管理JDK

- 通过update-alternatives，选择默认使用的JDK

> sudo update-alternatives --config java  
> sudo update-alternatives --config javac

#### 配置 JAVA_HOME 环境变量

- 根据设置时所选项来确定path

> sudo update-alternatives --config java  
> 得到安装路径：  
> /usr/lib/jvm/java-6-openjdk-amd64  
> /usr/lib/jvm/java-7-oracle  
> /usr/lib/jvm/java-8-oracle

- 我是用默认的java8，所以path为：

> "/usr/lib/jvm/java-8-oracle"

- 编辑环境配置文件

> sudo vim /etc/environment

- 在文件最后添加上：

> JAVA_HOME="/usr/lib/jvm/java-8-oracle"

- reload 配置文件

> source /etc/environment

- 检查是否安装成功

> echo $JAVA_HOME

- 参考文章：

1. [how-to-install-java-on-ubuntu-with-apt-get](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get)
1. [ubuntu 14.04 下通过apt-get 安装jdk](https://segmentfault.com/a/1190000001703180)

### 其他常用软件

#### 翻墙

- 蓝灯
- ShandowSocks

#### 通信

- WebQQ
- TeamViewer

#### 工具

- 监控网速CPU：[indicator-sysmonitor](http://blog.sina.com.cn/s/blog_1312684690101e7ur.html)


-----------

## CI 环境搭建

### GitLab CI

- [官网指导](https://gitlab.com/gitlab-org/gitlab-ci-multi-runner)

- Shell 安装

> curl -L <https://packages.gitlab.com/install/repositories/runner/gitlab-ci-multi-runner/script.deb.sh> | sudo bash  
> sudo apt-get install gitlab-ci-multi-runner

- Docker 安装

详见：[这里](https://gitlab.com/gitlab-org/gitlab-ci-multi-runner/blob/master/docs/install/docker.md)

- 注册Runner

```Shell
sudo gitlab-ci-multi-runner register Please enter the gitlab-ci coordinator URL (e.g. https://gitlab.com )  
https://gitlab.com  
Please enter the gitlab-ci token for this runner  
xxx  
Please enter the gitlab-ci description for this runner  
my-runner
INFO[0034] fcf5c619 Registering runner... succeeded
Please enter the executor: shell, docker, docker-ssh, ssh?  docker Please enter the Docker image (eg. ruby:2.1):
ruby:2.1  
INFO[0037] Runner registered successfully. Feel free to start it, but if it's running already the config should be automatically reloaded!
```

### Jenkins

-----------

## Android 环境搭建

### 1. Android studio

- 下载地址（官网）
  - [官网](https://developer.android.com/studio/index.html)
  - [国内镜像](http://www.androiddevtools.cn/)

- 配置

### 2. SDK

- 配置代理

> 参考Bugly提供的代理仓库 <https://dsx.bugly.qq.com/repository/1>

- 直接在AndroidStudio中下载

> File -> Settings -> Appearance & Behavior -> System Settings -> Android SDK

- SDK Platorms : 下载最新的三个SDK

- SDK Tools：
  - 必选：Build-Tools, SDK Platform-Tools, SDK Tools, Support Repository
  - 可选：CMake, NDK, LLDB


### 3. Gradle

- 网盘

> <http://pan.baidu.com/s/1pLEkm4F#list/path=%2F>

- 下载最新的三个版本

> 解压到~/.gradle/wrapper/dists/

- 或者用sdkman安装（推荐）

> curl -s <https://get.sdkman.io> | bash

- 打开一个新 terminal，安装 Gradle

> sdk install gradle {version}

-----------

## Node.js 环境搭建

### NVM

- 前置条件

> sudo apt-get update  
> sudo apt-get install build-essential libssl-dev

- 安装脚本

> curl -o- <https://raw.githubusercontent.com/creationix/nvm/v0.32.0/install.sh> | bash

最新脚本参考 <https://github.com/creationix/nvm>

- 判断是否成功

> command -v nvm

- 查看可安装node版本

> nvm ls-remote

- 安装某一版本

> nvm install {version}

- 查看已安装的版本

> nvm ls

- 指定默认版本

> nvm alias default {version}

- 使用默认版本

> nvm use default

- 查看Node版本，检查是否安装成功

> node -v

### NPM

- 修改淘宝NPM源

> npm config set registry <http://registry.cnpmjs.org>  //临时替换

- 替换CNPM

> npm install -g cnpm --registry=<http://registry.npm.taobao.org>  
> 参考官网：<https://npm.taobao.org/>

-----------

## J2EE 环境搭建

### Maven

- 用sdkman安装（推荐）

> $ curl -s <https://get.sdkman.io> | bash

- 打开一个新 terminal，安装 maven

> $ sdk install maven {version}

### Gradle

- 参考Android

-----------

## Python 环境搭建

-----------

## Ruby 环境搭建

-----------

## PHP 环境搭建

-----------

## Go 环境搭建

