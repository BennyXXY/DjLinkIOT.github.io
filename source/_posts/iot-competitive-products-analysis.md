---
title: 物联行业竞品分析
date: 2016-12-16 21:20:41
authors:
  - EvanWang
categories:
  - IOT
  - IOT Analysis
tags:
  - IOT
  - IOT Analysis
---


# 横向对比

## App

## SDK

## 云平台

## 大数据

## 人工智能

# 公司分类介绍

## 互联网巨头

### 京东 微联

### 阿里 小智

### 小米 米家

### [QQ 物联](http://iot.open.qq.com/wiki/index.html)

<!-- more -->

### 微信 物联

## 家电巨头

### [海尔 UHome](http://www.haigeek.com/static/information/page1.html)

#### [U+平台概述](http://developer.haigeek.com:9030/selfservice/static/index.html#/devloperDoc//false)

- U+开放平台介绍

  通过U+开放平台提供的 `WiFi模块uPlug`、`设备端SDK`、`应用端uSDK`、`嵌入式开发包uGW`，设备厂商的 **WiFi设备**、**蓝牙设备**、**GPRS设备**，以及 **Zigbee**、**DALI** 等异构类设备，都能便捷快速的实现与U+开放平台的互联和通讯，也能便捷的与不同厂家的不同产品实现互联互通。

- U+接入方案介绍

  ![U+开放平台技术架构图](http://uhome.haier.net/download/resource/selfService/ueditor/image/1461727797518056433.jpg)

#### 接入流程

- 硬件接入流程

- APP接入流程

- 轻应用接入流程

- Open API接入流程


#### 移动端SDK

- 概要介绍

  uSDK 是一种可以配置、搜索和控制物联网家电的手机软件开发中间件。它对硬件资源要求小，运行稳定。目前支持的手机平台包括Android和iOS。现在已经被众多APP厂商使用，并开发出多款智能家电的手机应用。

- 功能介绍

  uSDK应用结构图如下所示：

  ![uSDK应用结构图](http://uhome.haier.net/download/resource/selfService/ueditor/image/1462258403416015147.jpg)

  功能列表
  1. 家庭内U+类设备搜索
  1. U+类家电入网配置
  1. 家庭内控制U+类家电
  1. U+类家电状态和报警上报
  1. 通知类消息推送
  1. 远程控制U+类家电
  1. 支持U+开放平台第三方APP管理

- 优势介绍

  uSDK 具有如下优点：

  1. 提供快捷和方便的配置智能家电入网方式，目前支持 `softap` 和 `smartconfig` 两种
  1. 提供 `Android` 和 `iOS` 平台的 API，屏蔽了复杂的协议解析和网络通讯
  1. 长期改进用户体验和优化性能
  1. 专职的技术支持人员帮助开发者完成智能硬件手机应用的开发

- 发展规划

  uSDK 以用户为中心，以不断改进用户体验和优化性能为目标，打造成一种简单易用、 功能强大、运行稳定的手机软件中间件。

  发展规划思路如下：

  1. 支持更多协议类型的设备，例如AllSeen
  1. 不断提升用户体验，为满足手机开发者的需求，提供简单和功能强大的API接口和开发文档
  1. 软件功能迭代，随着市场需求的变化，uSDK 会不断开发新版本，以满足各种需求


#### 网关SDK（uGW）

- 简介

  uGW 为u+网关中间件，提供管理设备操作的接口，应用开发者通过接口很方便操控u+下的设备；并为第三方设备厂商提供u+的接入标准及对应API接口，方便第三方设备接入U+。

  uGW是基于Linux系统开发的，提供c语言及JAVA语言两种API。功能包括设备入网配置、搜索、控制、查询状态、设备状态变化上报、报警上报等操作接口。

- 开发包

  - uGW_client.so（应用开发者使用该库提供的管理接口集中管理设备(接入U+的设备)）
  - uGW_server（uGW主服务程序）
  - uGW_br.so（设备接入库，设备接入者可以使用该库提供的接口将设备接入u+）

- 系统框架图

  ![系统框架图](http://uhome.haier.net/download/resource/selfService/ueditor/image/1462784077137082140.jpg)

  支持功能：
  - uGW支持所有海尔白电设备（uwt）的管控
  - uGW支持新标准海尔设备（CAE）的管控
  - uGW支持第三方设备以标准方式的接入管控
  - uGW支持接入设备的远程管控（U＋云）
  - uGW支持与手机端uSDK的互联互通

- 应用开发者API
  - 设备配置入网API
  - 设备列表获取API
  - 设备上下线通知API
  - 设备操作API
  - 设备状态改变上报API
  - 设备报警上报API
  - 设备能力集获取API

- 设备接入者API
  - 设备注册API
  - 设备属性注册API
  - 设备操作API
  - 设备状态上报API
  - 设备报警上报API

- 发布
  - UGW可以运行在多种嵌入式平台，需要运行平台或者接入设备厂商提供对应的工具链交叉编译。
  - 设备开发文档及接口说明文档发布在海极网，需要开发者注册账号下载需要的开发文档进行开发

#### 蓝牙SDK

蓝牙SDK是一种支持经典蓝牙、低功耗（BLE）蓝牙设备的软件开发中间件。可运行在 POSIX 标准系统上，例如 Android、iOS、Linux 等。

- 优势介绍

  蓝牙SDK 具有如下优点：

  1. 设计轻量化
  1. 接口定义简单
  1. 支持品类众多，目前已支持Bong、欧姆龙、时云、微智电子等厂家的蓝牙设备
  1. 占用资源小，可以在嵌入式设备上运行
  1. 长期改进用户体验和优化性能

- 发展规划

  蓝牙SDK以用户为中心，以不断改进用户体验和优化性能为目标，打造成一种简单易用、 功能强大、运行稳定、支持品类众多的软件中间件。

#### Open API


### [美的 M·Smart](https://iot.midea.com/index.php)

#### [概述](http://smartbbs.midea.com/thread-2327-1-1.html)

整个系统从上至下分为四层。业务逻辑层开放给事业部进行二次开发，事业部可以根据自己的需求定制不同的功能。应用框架、应用协议和系统调度为研究院对M-Smart协议的完整实现，包括系统控制、家电端串口通信，网络端通信三大部分。适配层接口为研究院针对不同Wi-Fi芯片定制的一套统一接口。该接口是上层应用与芯片模块沟通的桥梁。

![美的SDK分层架构图](http://m-bbs.oss-cn-shenzhen.aliyuncs.com/forum/201602/17/105001sni8k4oio4r8tr44.png)

采用这层种分层架构设计使得M-Smart Wi-Fi系统具备跨平台性和可移植性。这为M-Smart系统的推广起到了很好的推动作用；此外，采用适配层接口的设计，减轻了上层应用、协议开发的维护成本，利于提高整个系统的稳定性和可靠性。总体而言，M-Smart SDK相较于市场上现有的物联网解决方案，具备以下几大优势：

- 通用性 —— 一套代码适配多家芯片方案
- 开发便利性 —— 只需修改一行代码即可切换芯片平台
- 系统非耦合性 —— SDK的功能模块之间相互独立，用户可以自由裁剪
- 系统可移植性 —— 由于采用适配层接口设计，可以方便移植到Linux、Android平台
- 多云平台支持 —— 除了支持美的云之外，还支持包括京东云、阿里云、Homekit等其他云平台
- 低成本优势 —— M-Smart SDK支持的Wi-Fi模块均具备高性价比

![M-Smart SDK](http://m-bbs.oss-cn-shenzhen.aliyuncs.com/forum/201602/17/105001dz7gr1aah091a6rz.png)

M-Smart SDK是沟通底层芯片硬件与云平台之间的桥梁。M-Smart SDK完美地实现了“多对多”方案，极大地丰富了家电厂商对于云平台、Wi-Fi芯片的可选择性。

#### [App SDK 介绍](https://iot.midea.com/index.php/develop/index?pid=206&cid=207)

![M-Smart SDK](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/image/20160617/sw2.png)

#### 开发者注册及应用相关流程文档

- [M-Smart 开发者注册](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160617/M-Smart%E5%BC%80%E5%8F%91%E8%80%85%E6%B3%A8%E5%86%8C.pdf)
- [M-Smart 应用发布申请](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160617/M-Smart_%E5%BA%94%E7%94%A8%E5%8F%91%E5%B8%83%E7%94%B3%E8%AF%B7.pdf)
- [M-Smart 应用开发申请](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160617/M-Smart_%E5%BA%94%E7%94%A8%E5%BC%80%E5%8F%91%E7%94%B3%E8%AF%B7.pdf)

#### SDK集成调用说明

- [SDK 应用集成调用整体流程](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160621/001---SDK_%E5%BA%94%E7%94%A8%E9%9B%86%E6%88%90%E8%B0%83%E7%94%A8%E6%95%B4%E4%BD%93%E6%B5%81%E7%A8%8B.pdf)
- [简化版SDK对接流程](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160621/%E7%AE%80%E5%8C%96%E7%89%88SDK%E5%AF%B9%E6%8E%A5%E6%B5%81%E7%A8%8B.pdf)
- [云对接方案说明](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160621/005---%E7%AC%AC%E4%B8%89%E6%96%B9%E4%BA%91%E5%AF%B9%E6%8E%A5%E6%96%B9%E6%A1%88%E8%AF%B4%E6%98%8E(%E7%AC%AC%E4%B8%89%E6%96%B9%E4%BA%91%E7%AB%AF%E9%9C%80%E8%A6%81%E5%AE%9E%E7%8E%B0%E7%9A%84%E6%8E%A5%E5%8F%A3)-1.5.pdf)
- [家电功能属性](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160621/004---%E5%AE%B6%E7%94%B5%E5%8A%9F%E8%83%BD%E5%B1%9E%E6%80%A7--%E7%94%A8%E4%BA%8EAndroid%E7%BB%84MAP%E5%8C%85.xlsx)

#### 接口说明文档以及错误码

- [SDK Android底层接口说明](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160621/002---SDK_%E5%BA%95%E5%B1%82%E6%8E%A5%E5%8F%A3%E8%AF%B4%E6%98%8E-Android.pdf)  
—— 用户管理接口，家电管理接口，数据传输接口
- [SDK Android应用接口说明](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160621/003---SDK_%E5%BA%94%E7%94%A8%E6%8E%A5%E5%8F%A3%E8%AF%B4%E6%98%8E1.1.6_.pdf)  
—— 设备控制接口，语音识别接口（控制、合成）
- [SDK iOS底层接口说明](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160622/iOS_SLK_家庭组接口文档.zip)
- [语音SDK集成接口](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160617/%E8%AF%AD%E9%9F%B3SDK2.0%E8%AF%AD%E9%9F%B3%E9%9B%86%E6%88%90%E6%8E%A5%E5%8F%A3.pdf)
- [SDK错误码说明](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160621/%E9%94%99%E8%AF%AF%E7%A0%81%E8%AF%B4%E6%98%8E_20160102.pdf)  
—— 通用错误，用户相关，设备相关，插件相关，家庭相关，SDK状态码

#### SDK示例Demo

- [Android底层SDK（SLK）](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160621/SLK_2.62_1045_pro.zip)
- [Android 应用层SDK（SSK）](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160622/SSK_1.2.9_201604192021.zip)
- [Android SLK Demo](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160622/Android_SLKDemo_20160614.zip)
- [Android SSK Demo](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160622/SSKDemoProguard_20160616.zip)
- [iOS 底层SDK附带Demo（SLK）](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160622/SLK_iOS_V2.4.3(family).zip)
- [iOS 应用层SDK附带Demo（SSK）](http://test-smartbbs.oss-cn-hangzhou.aliyuncs.com/openplatform/editor/file/20160622/SSKProtocol库-Demo-文档.zip)

### [苏宁 智能开发平台](http://opensh.suning.com/shsys-web/openPlatform/account/ptjs.htm)

#### [平台概况](http://opensh.suning.com/shsys-web/openPlatform/account/jszc.htm#help1)

智能家居产品体系以智能家居云平台和各种智能家庭终端为服务载体。具备以下优势：

1. 云平台基于云计算和大数据技术，通过苏宁云服务框架整合公司优势资源，搭建起来的云服务的开放平台。
1. 开放平台面向家庭用户、家电厂商、创新企业、各种电器设备提供服务。
1. 云平台开放的能力包括：基础设施云平台、大数据分析、苏宁IT系统和完整的供应链。

![](http://opensh.suning.com/shsys-web/webstatic/smartHomeOpen2.0v/openHome-help/temp/d_p1.png)

#### [开发平台系统架构](http://opensh.suning.com/shsys-web/openPlatform/account/jszc.htm#help2)

为智能家居合作伙伴提供对接苏宁智能家居的服务平台，通过苏宁智能家居云平台的支撑，使合作伙伴简单、快速的完成设备与平台的对接。

![](http://opensh.suning.com/shsys-web/webstatic/smartHomeOpen2.0v/openHome-help/temp/d_p2.png)

平台优势
- **安全性高**：  
采用2048位非对称加密算法进行密匙传递， 设备模块与云端数据交互，均使用密匙加解密，保证设备通讯安全。
- **稳定性好**：  
系统使用云端部署，可根据使用情况进行动态扩充。采用及时消息与普通消息分离的系统设计，提升系统性能。
- **接入速度快**：  
系统自动生成固件代码及控制面板原型，用户仅需提交设备通讯协议及选择的无线模块型号，双方技术沟通确认后，即可通过系统生成相关资料。
- **提供用户定制操作面板能力**：  
系统提供功能供用户自己上传开发的面板，提升交互的积极性与参与感。
- **提供用户定制APP能力**：  
用户根据需要提交需调用的api接口申请，根据接口说明，开发自己的应用程序。

#### [合作伙伴申请](http://opensh.suning.com/shsys-web/openPlatform/account/jszc.htm#help3)

#### [合作流程](http://opensh.suning.com/shsys-web/openPlatform/account/jszc.htm#help4)

#### [技术学习](http://opensh.suning.com/shsys-web/openPlatform/account/jszc.htm#help5)

- 家电配网详解

  ![家电配网流程](http://opensh.suning.com/shsys-web/webstatic/smartHomeOpen2.0v/openHome-help/temp/d_p66.jpg)

  1. 苏宁智能APP扫描设备上的配网二维码；
  1. 苏宁智能APP分析二维码信息，从中获取到设备的PID和配网模式；
  1. 苏宁智能APP根据设备PID信息，从苏宁云端获取设备图片、配网引导等；
  1. 手动触发设备进入配网模式；
  1. 设备通知wifi模块进入配网模式；
  1. wifi模块启动配网监听服务，监听配网广播包；
  1. 苏宁智能APP将用户输入的WIFI账号、密码信息通过广播发送给wifi模块；
  1. wifi模块接收到WIFI账号、密码信息后，进行联网；
  1. wifi模块联网成功后，通知苏宁智能APP配网成功，并返回设备MAC信息；
  1. 苏宁智能APP接收到配网成功的消息后，调用苏宁云端接口进行设备绑定；

- APP操作详解

  ![App操作详解](http://opensh.suning.com//shsys-web/webstatic/smartHomeOpen2.0v/openHome-help/temp/d_p77.jpg)

  命令发送过程：

  1. 用户在苏宁智能APP控制面板上控制设备，比如开机；
  1. 苏宁智能APP将控制设备的命令进行加密，将命令信息发送给苏宁云；
  1. 苏宁云端收到苏宁智能APP发送的命令后，判断用户是否登录，判断用户是否具有控制该设备的权限，对命令进行解密；
  1. 苏宁云端根据设备型号将命令信息做必要的转换，进行加密，发送给智能设备；
  1. 智能设备接收到命令信息，对信息进行解密，判断信息的有效性；
  1. 智能设备执行命令；

  状态数据上报过程：

  1. 智能设备状态发生变化时，智能设备将最新状态进行加密，将最新状态数据上报给苏宁云端；
  1. 苏宁云端接收到设备上报的数据，进行解密，根据设备型号解析数据，得到上报的状态数据；
  1. 苏宁云端将解析后的状态数据发送给苏宁智能APP；
  1. 苏宁智能APP接收到最新的状态数据，使用状态数据刷新控制面板，APP呈现设备最新的状态；

#### [APP SDK下载](http://opensh.suning.com/shsys-web/openPlatform/account/jszc.htm#help6)

  SDK提供功能

  1. 设备配网：让智能设备连上指定的路由器；
  1. 设备绑定：让智能设备连接到苏宁云；
  1. 设备删除：从苏宁云删除智能设备；
  1. 用户设备查询：查询用户下已经绑定的智能设备；
  1. 用户设备分享：将设备分享给另一个用户；
  1. 修改设备名称：修改用户下显示的设备名称；
  1. 设备查询：查询智能设备的信息和状态；
  1. 设备控制：控制智能设备；
  1. 接收状态推送：收取智能设备上报的状态变化；

#### [API 说明](http://opensh.suning.com/shsys-web/openPlatform/account/jszc.htm#help7)

  需要成为合作伙伴

#### [通用面板下载](http://opensh.suning.com/shsys-web/openPlatform/account/jszc.htm#help8)

  需要成为合作伙伴

## 其他云提供商

### [机智云](http://docs.gizwits.com/zh-cn/overview/overview.html)

未开放SDK

### [氦氪云](http://docs.hekr.me/v4/index.html)

需要申请合作账号，才能开发SDK

### [智城云](http://dev.machtalk.net/intro/regist)

### [云智易](http://www.xlink.cn/guide.html)

### [涂鸦智能](http://www.tuya.com/)

未开放SDK

### [AbleCloud](https://www.ablecloud.cn/)

### [Yeelink](http://www.yeelink.net/developer)

### [深智云](http://www.dtston.com/developer.php)

### [开发快](http://developer.kaifakuai.com/)

### [妙联](http://www.miotlink.com/index.php)

未开放SDK

### [控客](http://www.ikonke.com/index.php)

未开放SDK

### [司南物联](http://www.scinan.com/)

未开放SDK

### [艾拉物联](http://www.ayla.com.cn/)

未开放SDK