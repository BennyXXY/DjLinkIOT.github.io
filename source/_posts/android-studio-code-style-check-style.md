---
title: Android Studio 配置 CheckStyle 和 CodeStytle
date: 2016-11-26 19:30:38
authors: 
- EvanWang
categories:
- Android
- Android Studio
tags:
- Android
- Android Studio
- Code Style
- Check Style
---

# 概述

在开发中，我们不仅需要单兵作战的全栈型极客，也需要能力普通的团队在一起合作。团队合作的基础之一就是要有一个良好的代码规范。

在Android领域中，我们可以借助两个编码规范的工具 --- CodeSytle & CheckStyle。

<!-- more -->

CodeStyle是IDE（IntelliJ、Eclipse）开发环境自带的一个代码格式化校验设置，包括Tab缩进、空格、括号与对齐、空行、标识符的位置排序、JavaDoc、import等。通过IDE的排版功能调用该格式设置。

CheckStyle主要的功能就是实时检测，代码的规范（Code Style）是否符合我们规定的一个模板，如定义的静态常量是大写，局部参数以m开头，函数名字不超过20个字等。当发现这些不符合这些规范时，它就报一个警告或者错误等提示。


# CheckStyle

## 检验的主要内容

- Javadoc注释
- 命名约定
- 标题
- Import语句
- 体积大小
- 空白
- 修饰符
- 块
- 代码问题
- 类设计
- 混合检查（包活一些有用的比如非必须的System.out和printstackTrace）

## Android Studio 下配置

checkstyle帮助开发者实现常用JAVA代码规范的自动化检查。它的功能比较丰富，相对配置起来比较复杂，你需要根据自己的需求配置你想检查的东西，比如：

- Annotations
- Block Checks
- Class Design
- Coding
- Duplicate Code
- Headers
- Imports
- Javadoc Comments
- Metrics
- Miscellaneous
- Modifiers
- Naming Conventions
- Regexp
- Size Violations
- Whitespace

在Android开发中，也需要我们去定义，Android Studio继承了IDEA的可拓展特性，它也拥有CheckStyle的插件，在Android项目中，使用的Gradle配置。

### 添加Plugin

```groovy
apply plugin: 'checkstyle'
```

### 设置CheckStyle版本

```groovy
checkstyle {
    toolVersion '6.1.1'
    showViolations true
}
```

### 设置配置文件

checkStyle需要我们自定义我们的配置文件，如函数的名字不超过20个字符等，详情可参考 CheckStyle的解释（见文末参考文档）

```groovy
check.dependsOn 'checkstyle'

task checkstyle(type: Checkstyle) {
    source 'src'
    configFile file("config/checkstyle.xml")
    include '**/*.java'
    exclude '**/gen/**'
    ignoreFailures true

    classpath = files()
}
```

我现在用的是华为的CheckStyle（见文末参考文档）

当然了我们也可以自己定义。

### 运行

安装Idea的check Style插件。

那么在我们的列表里，我们会看到多一个CheckStyle的窗口。

{% asset_img android-studio-check-style-window.png android-studio-check-style-window %}

我们可以选择一个文件，Check Current FIle

{% asset_img android-studio-check-style-menu.png android-studio-check-style-menu %}

# CodeStyle

## CodeStyle.xml 源

现在比较好的CodeStyle源就是出自 `Google` 和 `Square`。链接见文末参考文档。

## 设置

IDEA内支持自定义的CodeStyle，那就把Google 提倡的Code Stytle给设置到IDEA（在IDEA上开发的其他IDE如Android Studio也支持这样）

1. 将你的这个文件放到你的 `~/Library/Preferences/IDEA/codestyles` 下。

1. 重启你的IDEA看下，在你的 Prefrence 下的 `Editor ——> Code Stytle ——> Java` 有个 GoogleStyle。哈哈。


# 参考

- [How to improve quality and syntax of your Android code](http://vincentbrison.com/2014/07/19/how-to-improve-quality-and-syntax-of-your-android-code/)

    老外的一篇文章，讲了Android环境下配置CheckStyle、Findbugs、PMD、Android Lint，较为详细

- [CheckStyle官方介绍](http://checkstyle.sourceforge.net/) 及 [具体的配置项](http://checkstyle.sourceforge.net/checks.html) ([Github地址](https://github.com/checkstyle/checkstyle))

    所有详细的CheckStyle配置在这里都能找到

- [华为的CheckStyle](https://gist.github.com/ownwell/c32878440216f1866842)

    华为提供的 CheckStyle 配置文件

- [IntelliJ IDEA 2016.2 Help -- Code Style](https://www.jetbrains.com/help/idea/2016.2/code-style.html)

    IntelliJ IDEA 官方对Code Style的教程

- [google/styleguide](https://github.com/google/styleguide)

    Style guides for Google-originated open-source projects

    Google官方提供的各种语言Code Style 基于不同IDE的 样板配置文件

- [square/java-code-styles](https://github.com/square/java-code-styles)

    IntelliJ IDEA code style settings for Square's Java and Android projects.

    Square团队的基于IntelliJ IDEA 的 code style 配置文件。提供 Java 和 Android 两种规范。