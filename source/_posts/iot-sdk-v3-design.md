---
title: 物联SDK3.0 规划
date: 2016-12-13 16:32:10
authors:
  - EvanWang
categories:
  - IOT
  - IOT SDK
tags:
  - IOT
  - IOT SDK
  - IOT SDK 3.0
---

# SDK 3.0 规划

## 整体规划与设计目标

<!-- more -->

- SDK 平台与功能划分

| 平台 | SDK | 说明 |
| --- | --- | --- |
| Android/iOS | -- | 基于v2.x继续优化 |
| Android/iOS | ReactNative SDK | 给混合应用 ReactNative 提供物联通信、物联逻辑、以及一些原生控件的 RN 插件 |
| Android/iOS | Hybrid API（基于Cordova） | 基于v2.x，为 Vue、Ng 提供Cordova 插件 |
| 微信 | H5 SDK | 基于v2.x，提供 React、Vue、Ng 集成插件 |
| 微信 | 小程序 SDK | 提供在小程序环境下操作物联设备的SDK，逻辑部分与H5 SDK共用 |
| 硬件 | WiFi SDK | 基于v2.x继续优化 |
| 硬件 | 蓝牙 SDK | 对接 Djlink BLE 协议 |
| 硬件 | GPRS SDK |  对接 Djlink Cloud 协议|
| 硬件 | 树莓派 SDK | 基于树莓派 系统开发SDK |
| 硬件 | Android Things SDK | 基于Android Things 系统开发SDK |

## Android SDK 3.0

## iOS SDK 3.0

## H5 SDK 3.0
