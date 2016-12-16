---
title: 物联SDK2.0 规划
date: 2016-12-13 16:29:17
authors:
  - EvanWang
categories:
  - IOT
  - IOT SDK
tags:
  - IOT
  - IOT SDK
  - IOT SDK 2.0
---

# SDK 1.x 现状

## 概述

目前 Djlink SDK，只是在内部使用，没有形成文档化，没有对外发布的能力。而且包括架构设计，API设计都有很多东西需要优化。下面对当下 Android、iOS、H5 等几大部分SDK做一个概述。

## Android SDK 1.x

- 采用 Android 模块化依赖管理方案 `Gradle`，依赖于 `Maven` 仓库

- 项目代码托管在公司自己搭建的 `Gitlab` 服务器上（ [链接: IOTSDKAndroidV1](https://git.djlink.cn/djlink.dev.iot.android/IOTSDKAndroidV1) ），打完的 `.aar` 包托管到 [公司 Maven 服务器](http://maven.djlink.cn:8081/nexus/) 上。

<!-- more -->

- SDK 包含内容：
  - 通用API —— 封装了一套完整的API，`SkySDK`
  - 通用UI —— 基本控件（`SweetDialog`、`ActionSheet`），网络异常弹框，`BaseActivity`，`BaseFragment`
  - 物联逻辑 —— 配网，发指令，大小循环过滤，MCU数据编解码（注解）
  - 业务接口 —— 所有接口的封装
  - 底层通信 —— 外网推送长连接 `MQTT`，内网 `Socket` 通信
  - 底层支撑 —— 日志系统，工具类，线程池，持久化层

- 存在的问题：
  - 耦合性太强，不应该包含 UI
  - HTTP 接口 耦合性略强，抽象成独立服务
  - MQTT 服务不稳定
  - SDK 接口设计不太合理

## iOS SDK 1.x

- 采用 iOS 模块化依赖管理方案 `CocoaPods`，依赖于 `Git` 仓库。

- 项目代码托管在 `Github`，开源形式（ [链接: SkywareUI](https://github.com/lixiao7215981/SkywareUI) ）。由于其中包含公司接口，极其危险，现已着手迁移到公司自己搭建的 `Gitlab` 服务器上。

- SDK 包含内容：
  - UI —— 除了设备详情页，个人中心，大部分页面及其相关业务逻辑
  - 物联逻辑 —— 配网，长连接MQTT，发指令
  - 接口 —— 所有接口的封装

- 存在的问题：
  - 代码开源，应该尽快迁移到公司自己的 `Git` 服务器
  - 没有打成包，直接依赖源码，不方便对外提供
  - 耦合性太强，不应该包含UI
  - SDK 接口设计不合理

## Hybrid API （H5）

- 采用最基础的 `Hybrid` 方案，`Android` 和 `iOS` 分别通过 `WebView` 与 前端 `JavaScript` 进行交互
- API 包含内容
  - UI相关 —— js 渲染完成，滑动手势
  - 推送 —— MQTT 状态上报
  - 接口 —— 天气接口、设备信息接口
  - 原生相关 —— 打电话

- 存在的问题：
  - 接口设计过于随意，零散
  - 缺乏 `JavaScript` 层面的基本封装

## 微信 SDK

- 目前微信端尚未抽象出SDK

## OpenAPI

- 服务器目前没有严格意义上的 `OpenApi`，接口只有对内接口，接口本身校验机制薄弱，极易被攻破。

## 硬件SDK —— WiFi / 蓝牙

- 目前硬件端尚未抽象出SDK

# SDK 2.0 规划

## 整体规划与设计目标

### 设计目标

- 形成类似竞争对手的 SDK 产品，将开发能力转移给第三方。加速开发，降低开发成本。
- 封装核心逻辑 —— 物联大小循环、协议处理相关逻辑，屏蔽平台细节，保证平台安全性，降低开发难度。
- 业务App与SDK解耦，方便各自独立维护。SDK交给核心团队维护，保证质量。
- 一套业务代码，可兼容各种其他厂商的SDK（海尔 uSDK，美的 M-Smart，...）

### 核心优势

- 降低开发成本
- 加快开发速度
- 保证平台安全
- SDK独立维护升级
- 兼容其他平台SDK

### SDK 平台分布与功能划分

| 平台 | SDK | 说明 |
| --- | --- | --- |
| Android/iOS | CoreSDK-Common | 封装 抽象的设备数据、设备属性数据点、用户数据的模型，对上层抽象的Api与回调 |
| Android/iOS | CoreSDK-Djlink | 封装 Djlink Cloud 接口、Mqtt 推送、内网 Socket 通信、蓝牙通信、协议解析工具类 |
| Android/iOS | CoreSDK-Haier | 封装海尔uSDK（将来可拓展为美的, ...） |
| Android/iOS | IOTSDK | 基于CoreSDK，提供常用的物联逻辑，统一封装 |
| Android/iOS | HybridSDK | 给嵌入在原生 App 中的H5网页提供物联通信、物联逻辑、接口数据、操作原生系统的能力 |
| Android/iOS/H5 | BigDataSDK | 提供大数据采集与统计的SDK |
| 微信 | H5 SDK | 将 微信AirKiss、WebSocket、Ajax、以及一些物联逻辑 封装成 js SDK |
| 硬件 | WiFi SDK | 对接 Djlink Cloud 协议（基于ESP8266） |

### SDK 与 相关协议 的整体架构图

{% asset_img iot-sdk-v2-framework.svg SDK与相关协议整体架构图 %}

> 其中：  
`B` 代表 `BlueTooth`，App 与 蓝牙模块 之间的 `蓝牙` 协议  
`D` 代表 `Device`，MCU 与 WiFi模块/蓝牙模块/GPRS模块 之间的 `串口` 协议  
`T` 代表 `Transmit`，云平台 与 WiFi模块/GPRS模块 之间的 `TCP/UDP` 传输层协议  
`L` 代表 `Local`，App 与 WiFi模块 之间的 `TCP/UDP` 传输层协议（局域网）  
`S` 代表 `Server`，App 与 云平台 之间的 `HTTP/MQTT` 协议

> 注：以上这五种协议都是双向协议，全双工

## Android SDK 2.0


### 设计概述

#### 设计思想

- 将SDK分 `CoreSDK` 和 `IOTSDK` 的原因：
  - 将 涉及到物联通信协议细节的 ***CoreSDK*** 和 涉及物联上层逻辑的 ***IOTSDK*** 解耦，各自关注各自的核心逻辑
  - ***CoreSDK*** 作为一层 `Wrapper`，可以将 其他家的SDK（比如海尔的 `uSDK`） 封装进来，对上层的 ***IOTSDK*** 提供统一的接口，这样可以做到一个App无缝切换对 底层物联系统的依赖
  - 物联协议升级（ WiFi大小循环、蓝牙、HTTP接口、MQTT ） 或者 第三方SDK升级 （比如 uSDK），接口大体保持不变，***IOTSDK*** 几乎可保持代码不变
- `CoreSDK` 和 `IOTSDK` 之间通过 `CoreSDK-Common` 解耦：
  - 两者之间是俩个独立的 `module`，之间通过一层中间 module —— ***CoreSDK-Common*** 来解耦
  - ***CoreSDK-Common*** 用来封装对上层暴露的 ***Common-Api*** 和 封装的基本数据模型 ***Common-DTO***
  - 每个 ***CoreSDK-XXX*** 依赖 ***CoreSDK-Common***，后者基本保持Api和数据结构的稳定。
- `Hybrid SDK` 

#### 整体架构图

{% asset_img iot-android-sdk.svg Android SDK 整体架构图 %}

### CoreSDK

#### 概述

- **CoreSDK-Common**
  - 封装基本通信数据模型 `DeviceDTO`、 `UserDTO`、 `DevAttrDTO`、 `DevCmdDTO` 等
  - 封装 `Core-Api` 和 `Core-DTO`
  - 提供 `RxJava`、`Eventbus` 和 `常规回调` 三种数据上报方式
- **CoreSDK-Djlink**
  - 协议上需要支持 `B` （蓝牙与App）`L` （WiFi与App）和 `S` （服务器与App）三个协议
  - 三个协议需要相互解耦，可以各自根据协议版本迭代独自升级
  - 实现 `CoreSDK-Common` 的 Api 和 Model
  - 封装 `MQTT`信道 与 `Socket`信道 的包过滤机制
  - 封装 配网逻辑 `Smartlink` 和 `SmartConfig`
- **CoreSDK-Haier**
  - 封装 `uSDK` 的大小循环部分，获取设备列表
  - 封装 `openAPI` 的部分，所有业务接口

#### 设计思路

- 

#### 依赖结构

{% asset_img iot-android-core-sdk-hierarchy.svg Android CoreSDK 依赖结构 %}

#### 概要设计


### AbleSDK

#### 概述

- 能力层SDK，封装一些和业务无关的数据接口
- 包含 接口层 + 数据解析

#### 概要设计

- **WeatherAPI**：天气接口
- **Pm25API**：PM2.5接口
- **ProvCityAPI**：省市区数据
- **FileAPI**：文件存取接口

### IOTSDK

#### 概述

#### 概要设计

- **IOT-Service**：将IOT服务封装成一个`Service`
- **IOT-PublicAPI**：将IOT服务封装成对外的 `公共API`，并开放文档
- **IOT-BasicLogic**：将常用的物联逻辑封装，包括 `控制设备逻辑（超时）`，`设备状态流的分发`，`设备配网流程`
- **IOT-ExtLogic**：扩展的物联逻辑封装，包括 `连续点击假值替换`，`设备状态机管理`
- **IOT-DebugUtils**：提供联调工具，方便设备联调
- **IOT-FakeDevice**：**假设备** 逻辑，方便市场展示，用户试体验等场合

### HybridSDK

#### 设计思想

- 
#### 架构图

#### 


## iOS SDK 2.0

## Hybrid SDK 2.0

## BigData SDK 1.0


# 参考
