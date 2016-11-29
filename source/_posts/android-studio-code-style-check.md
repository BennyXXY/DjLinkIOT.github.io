---
title: android-studio-code-style-check
date: 2016-11-26 19:30:38
authors: 
- EvanWang
categories:
tags:
---
概述
在开发中，我们需要不仅仅是个人的超强的能力（学习能力、解决问题能力等），我们也需要团队合作能力，我们要明白，我们的成功来自于我们的团队（一个英雄是很难自靠自己的能力来创造一个时代的）。今天我们就介绍一种，在团队开发中遵守某些编码规范的工具---CheckStyle。

CheckStyle主要的功能就是实时检测，代码的规范（Code Style）是否符合我们规定的一个模板，如定义的静态常量是大写，局部参数以m开头，函数名字不超过20个字等。当发现这些不符合这些规范时，它就报一个警告或者错误等提示。

CheckStyle检验的主要内容
Javadoc注释
命名约定
标题
Import语句
体积大小
空白
修饰符
块
代码问题
类设计
混合检查（包活一些有用的比如非必须的System.out和printstackTrace）
Android和Check Style
checkstyle帮助开发者实现常用JAVA代码规范的自动化检查。它的功能比较丰富，相对配置起来比较复杂，你需要根据自己的需求配置你想检查的东西，比如Annotations，Block Checks，Class Design，Coding，Duplicate Code，Headers，Imports，Javadoc Comments，Metrics，Miscellaneous，Modifiers，Naming Conventions，Regexp，Size Violations，Whitespace。

在Android开发中，也需要我们去定义，Android Studio继承了IDEA的可拓展特性，它也拥有CheckStyle的插件，在Android项目中，使用的Gradle配置。

添加Plugin
apply plugin: 'checkstyle'
设置CheckStyle版本
checkstyle {
    toolVersion '6.1.1'
    showViolations true
}
设置配置文件
checkStyle需要我们自定义我们的配置文件，如函数的名字不超过20个字符等，详情可参考 CheckStyle的解释。

check.dependsOn 'checkstyle'

task checkstyle(type: Checkstyle) {
    source 'src'
    configFile file("config/checkstyle.xml")
    include '**/*.java'
    exclude '**/gen/**'
    ignoreFailures true

    classpath = files()
}
我现在用的是华为的CheckStyle：

当然了我们也可以自己定义。

运行
安装Idea的check Style插件。

那么在我们的列表里，我们会看到多一个CheckStyle的窗口。


image
我们可以选择一个文件，Check Current FIle。


image
参考：

How to improve quality and syntax of your Android code

CheckStyle及具体的配置

文／cyning（简书作者）
原文链接：http://www.jianshu.com/p/fc2f45a9ee37
著作权归作者所有，转载请联系作者获得授权，并标注“简书作者”。