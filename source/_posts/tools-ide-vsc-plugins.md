---
title: Visual Studio Code 插件大全
date: 2016-11-26 19:43:30
authors: 
- EvanWang
categories: 
- Workflow
- IDE
tags: 
- IDE
- VisualStudioCode
- VSCode
- Plugins
---

# 前言

Visual Studio Code（简称VSCode）是继 Sublime 之后最好用的轻量级跨平台编辑器IDE。其中的核心竞争力就是大量好用的插件。下面整理一下我最近收集的插件，以供参考。

# 主题样式

## 背景

- [background | shalldie | 6k](https://marketplace.visualstudio.com/items?itemName=shalldie.background)

    —— A simple tool to make your vscode's background look better!

    各种萌妹背景，你懂的~

<!-- more -->

## 美化

- [vscode-icons | Roberto Huertas | 632k](https://marketplace.visualstudio.com/items?itemName=robertohuertasm.vscode-icons)

    —— Icons for Visual Studio Code

    看起来很舒服，各种文件类型都标上小图标，一目了然

- [Output Colorizer | IBM | 5k](https://marketplace.visualstudio.com/items?itemName=IBM.output-colorizer)

    —— Syntax highlighting for log output

    彩色输出有助于快速找到输出信息

- [Emoji | Perkovec | 2k](https://marketplace.visualstudio.com/items?itemName=Perkovec.emoji)

    —— Plugin to insert emoji from the command palette

    很好玩的一款插件，可以在代码中插入emoji了，也许是程序猿的娱乐方式吧

# Workflow

## 编辑辅助

- [Vim | vscodevim | 149k](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim)

    —— Vim emulation for Visual Studio Code

    Vim模拟器，编码神器

- [beautify | HookyQR | 330k](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify)

    —— Beautify code in place for VS Code

    这款类似于vscode里格式化代码的功能，不错

- [Rewrap | stkb | 4k](https://marketplace.visualstudio.com/items?itemName=stkb.rewrap)

    —— Re-wraps comments and other text to a given line length.

   长注释/markdown 换行

## Git

- [Git History | Don Jayamanne | 203k](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory)

## Markdown



## 设置同步

- [Visual Studio Code Settings Sync | Shan Khan | 125k](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)

    —— Synchronize Settings, Snippets, launch, keybindings files and extensions Across Multiple Machines using Github GIST.

    可以同步配置插件等到 gist

## 调试辅助

- [Code Runner | Jun Han | 76k](https://marketplace.visualstudio.com/items?itemName=formulahendry.code-runner)

    —— Run code snippet/file for C, C++, Java, JS, PHP, Python, Perl, Ruby, Go, Lua, Groovy, PowerShell, BAT/CMD, BASH/SH, F#, C#, VBScript, TypeScript, CoffeeScript, Scala, Swift, Julia, Crystal, OCaml

    支持多种语言，能直接跑code snippet，非常方便。

## 工作辅助

- [Bookmarks | Alessandro Fragnani | 66k](https://marketplace.visualstudio.com/items?itemName=alefragnani.Bookmarks)

    —— Mark lines and jump to them

    书签没有太大作用，有时候做个标记有点用

- [vscode-todo | MattiasPernhult | 24k](https://marketplace.visualstudio.com/items?itemName=MattiasPernhult.vscode-todo)

    —— Lists todo:s in the project

    todo注释，但是在mac上必须设置语言才可以

- [TODO Parser | minhthai | 22k](https://marketplace.visualstudio.com/items?itemName=minhthai.vscode-todo-parser)

    —— Parse TODOs in your working files.

    和上面的 `scode-todo` 作用一样，推荐使用这个

- [Dash | Budi Irawan | 9k](https://marketplace.visualstudio.com/items?itemName=deerawan.vscode-dash)

    —— Dash integration in Visual Studio Code

    查询API，需要先装Dash软件。应该只能用在mac平台上


# 编程领域

## 前端

- [ESLint | Dirk Baeumer | 372k](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

    —— Integrates ESLint into VS Code.

    流行的 Linter 插件, 平时都是关掉了 VS Code 自带的 Linter, 太慢了.


- [File Peek | abierbaum | 10k](https://marketplace.visualstudio.com/items?itemName=abierbaum.vscode-file-peek)

    —— Allow peeking to file name strings as definitions from javascript and typescript code. Allows peek and goto definition. Great for Angular template and style files)

    预览文件，一般看模块时用到

- [CodeMetrics](https://marketplace.visualstudio.com/items?itemName=kisstkondoros.vscode-codemetrics)

    —— Computes complexity in TypeScript / JavaScript files.

    有助于我重构代码

- [Can I Use | Mahmoud Ali | 20k](https://marketplace.visualstudio.com/items?itemName=akamud.vscode-caniuse)

    —— Compatibility check for HTML5, CSS3, SVG, New JS API based on [caniuse.com](http://caniuse.com/) directly from Visual Studio Code.

    自动检测所写代码能否在相应容器正常编译执行

- [CSScomb | mrmlnc| 13k](https://marketplace.visualstudio.com/items?itemName=mrmlnc.vscode-csscomb)

    —— Coding style formatter for CSS, Less, SCSS or Sass.

    给css排序


### 自动补全

- []()

    —— HTML Snippets，这款插件包含html标签，非常全，很实用；

- [Angular2 TypeScript Snippets | johnpapa | 212k](https://marketplace.visualstudio.com/items?itemName=johnpapa.Angular2)

    —— Angular 2 TypeScript snippets

- [vscode-fileheader | mikey | 2k](https://marketplace.visualstudio.com/items?itemName=mikey.vscode-fileheader)

    —— insert header comment,and automatically update the time.

    自动生成头部注释，自动更新文件更新时间

### ES5/ES6

- [JavaScript (ES6) code snippets | charalampos karypidis | 205k](https://marketplace.visualstudio.com/items?itemName=xabikos.JavaScriptSnippets)

    —— Code snippets for JavaScript in ES6 syntax

- [ECMAScript Quotes Transformer | vilicvane | 2k](https://marketplace.visualstudio.com/items?itemName=vilicvane.es-quotes)

    —— Transform quotes of ECMAScript string literals.

    有时字符串写了一半想转成模板字符串, 或者想从模板字符串转为普通字符串的时候比较顺手

### 模块管理和打包

- [npm | Florian Knop | 42k](https://marketplace.visualstudio.com/items?itemName=fknop.vscode-npm)

    —— npm commands for VSCode

    npm相关命令，集成了终端后，我就很少用了

- [Gulp Snippets | tanato | 12k](https://marketplace.visualstudio.com/items?itemName=fknop.vscode-npm)

    —— Gulp JS Snippets for Visual Studio Code

    写gulp时用到


### Debugger

- [Debugger for Chrome  | Microsoft | 641k](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome)

    —— npm commands for VSCode

    Debugger for Chrome，在Chrome浏览器中调试

- [Debugger for Firefox | Holger Benl | 12k](https://marketplace.visualstudio.com/items?itemName=hbenl.vscode-firefox-debug)

    —— Debug your web application or browser extension in Firefox

    Debugger for Firefox，在Firefox浏览器中调试

### TypeScript

- [TypeScript Toolbox | DSKWRK | 30k](https://marketplace.visualstudio.com/items?itemName=DSKWRK.vscode-generate-getter-setter)

    —— Add and Optimize Imports, Generate Getters / Setters and Constructors

    typescript必备插件

- [TSLint | egamma | 240k](https://marketplace.visualstudio.com/items?itemName=eg2.tslint)

    —— TSLint for Visual Studio Code

    校验ts语法

- [Document This | Joel Day | 55k](https://marketplace.visualstudio.com/items?itemName=joelday.docthis)

    —— Automatically generates detailed JSDoc comments in TypeScript and JavaScript files.

    目前vscode上最好的ts注释插件

- [json2ts | Gregor Biswanger | 2k](https://marketplace.visualstudio.com/items?itemName=GregorBiswanger.json2ts)

    —— Convert a JSON from clipboard to TypeScript interfaces. (Ctrl+Alt+V)

    快速生成一个typescript接口

- [Auto Import | steoates | 15k](https://marketplace.visualstudio.com/items?itemName=steoates.autoimport)

    —— Automatically finds, parses and provides code actions and code completion for all available imports. Works with Typescript and TSX

    自动引入模块

- [TypeLens | Kiss Tamás | 3k](https://marketplace.visualstudio.com/items?itemName=kisstkondoros.typelens)

    —— Shows references to TypeScript methods in the form of codelens

    自动引入模块

## C/C++

- [C/C++ | Microsoft | 582k](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)

    —— Complete C/C++ language support including code-editing and debugging

- [C/C++ Clang | Yasuaki MITANI | 64k](https://marketplace.visualstudio.com/items?itemName=mitaki28.vscode-clang)

    —— Completion and Diagnostic for C/C++/Objective-C using Clang

- [Clang-Format | xaver | 19k](https://marketplace.visualstudio.com/items?itemName=xaver.clang-format)

    —— Use Clang-Format in Visual Studio Code

## Python

- [Python Tools | HPCToolsGuy | 172k](https://marketplace.visualstudio.com/items?itemName=HPCToolsGuy.PythonToolsforVisualStudio)

    —— Python Tools for Visual Studio

    针对python的插件，这是我用过所有python插件中最全的，自动补全功能对有些关键字没有作用，不过还是很好用

- [MagicPython | MagicStack Inc. | 101k](https://marketplace.visualstudio.com/items?itemName=magicstack.MagicPython)

    —— Syntax highlighter for cutting edge Python

    非常好的Python插件


## Go

- [Go | lukehoban| 331k](https://marketplace.visualstudio.com/items?itemName=lukehoban.Go)

    —— Rich Go language support for Visual Studio Code

    

## Docker


# 其他

- [Microsoft/vscode-tips-and-tricks](https://github.com/Microsoft/vscode-tips-and-tricks)
- [学好用好 Visual Studio Code](https://nshen.net/article/2015-11-20/vscode/)
- [用VS Code打造最佳Markdown编辑器](http://www.jianshu.com/p/18876655b452)
- [知乎：Visual Studio Code有哪些你常用的插件？](https://www.zhihu.com/question/40640654)