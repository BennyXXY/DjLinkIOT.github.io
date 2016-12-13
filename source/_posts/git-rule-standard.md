---
title: Git 使用规范
date: 2016-12-07 21:17:07
authors:
  - EvanWang
categories:
  - Workflow
  - Git
tags:
  - Workflow
  - Git
---

# Git分支管理与提交规范

多人协作开发情况下，每个人都应该了解并理解 **Git分支模型**

这里意见几篇质量极高的文章以供参阅，因此不再赘述。

[git版本控制开发流程小结笔记（一）](http://my.oschina.net/nyankosama/blog/270546?fromerr=0Byh13go)
[git版本控制开发流程小结笔记（二）](http://my.oschina.net/nyankosama/blog/270581)
[一个成功的 Git 分支模型](http://www.oschina.net/translate/a-successful-git-branching-model)

因为Git的操作指令非常灵活，所以这里只给出提交备注的建议：

<!-- more -->

## 1. 提交备注

- 如果使用类似 `$ git commit` 等语句，建议采用以下规范添加完整的提交备注

  标题与内容之间保持一个空行，示例如下：

      Fixed #<此bug在bug管理工具上的索引、路径或其他标识>

      内容部分添加简短描述，如改动原因，主要变动或者一些重要的建议事项。最后如果有需要可以添加对应的网址，如bug地址等。

- 如果使用 `$ git commit -m ""` 等语句，建议采用以下规范添加简短的提交备注

  如果真的没有什么详细内容可以描述，使用简短的提交备注形式，是一种不错的选择，示例如下：

      git commit -m 'Fixed #[issue number]: [Short summary of the change].'

  下面是几个常用提交动词，以供参考：

  - Added ( 新加入的需求 )
  - Removed ( 删除某段代码 )
  - Fixed ( 修复Bug，建议后面加上Bug索引或路径，如：Fixed #[issue number] )
  - Updated ( 完成的任务，或者由于第三方模块变化而做的变化）
  - Completed ( 完成的任务 )
  - Refactored ( 重构代码 )

## 2. 标题尽量不超过50个字符

## 3. 标题的首字母大写（如果你习惯使用一个英文标题的话）

    使用这种标题：
        Accelerate to 88 miles per hour
    而不是：
        accelerate to 88 miles per hour

## 4. 标题不以“句号”作为结尾

    使用这种标题：
        Open the pod bay doors
    而不是：
        Open the pod bay doors.

## 5. 内容描述尽量不要超过72个字符

## 6. 在内容中对此次提交的“Why”以及“How”来进行描述

最后，我们一起来看一看，一个优雅的提交备注是什么样子的：

```text
    Simplify serialize.h's exception handling

    Remove the 'state' and 'exceptmask' from serialize.h's stream implementations, as well as related methods.

    As exceptmask always included 'failbit', and setstate was always called with bits = failbit, all it did was immediately raise an exception. Get rid of those variables, and replace the setstate with direct exception throwing (which also removes some dead code).

    As a result, good() is never reached after a failure (there are only 2 calls, one of which is in tests), and can just be replaced by !eof().

    fail(), clear(n) and exceptions() are just never called. Delete them.
```

# Git 协同守则

- 拉取 dev 分支到本地 Liveneeq 文件夹

  ```shell
  mkdir Liveneeq
  cd Liveneeq
  git init
  git remote add -t dev -f origin git@git.thecampus.cc:onecampus/liveneeq-android.git
  git checkout -b dev origin/dev
  ```

- 每个人建立带下划线的自己全名的分支，例如 _yangfan

  ```shell
  git checkout -b _yangfan
  ```

- 在该分支上进行开发，定期进行 Commit（可使用 tmp 前缀来表示临时提交），确保代码在云端

  ```shell
  git add .
  git commit -m "tmp 3/18 ***"
  git push origin _yangfan

  git add .
  git commit -m "tmp 3/19 ***"
  git push origin _yangfan
  ```

- 完成阶段性功能或页面后，使用 rebase 或者 reset 重建 Commit 历史，确保所有 tmp commit 被合并删除

  ```shell
  git rebase -i <COMMIT_HASH>
  ...
  git rebase --continue
  ```

- 需要提交到 dev 分支时，需要针对 dev 在个人分支上进行 Rebase 操作，并处理冲突

  ```shell
  git fetch
  git rebase origin/dev
  ...
  ```

- rebase 完成后 在本机进行构建和测试，测试通过后使用 -f 参数强制 Push 到远程分支
  ```shell
  git push -f origin _yangfan
  ```

- 在 Gitlab 上提交 Merge Request(/Pull Request) 到 dev 分支，等待 Master 进行 Code Review

# 代码提交规范

- 工作目录要及时更新，不要和服务器有太大的差别
- 提交代码时，如果出现冲突，必须仔细分析解决，不可以强行提交
- 提交代码之前先在本地进行测试，确保项目能编译通过，且能够正常运行，不可盲目提交
- 必须保证服务器上的版本是正确的，项目有错误时，不要进行提交
- 提交之前先更新
- 提交时注意不要提交本地自动生成的文件，比如我们Android Studio项目中的 idea,build文件夹是不需要提交的。
- 不要提交自己不明白的代码
- 提前协调好项目组成员的工作计划，减少冲突
- 对提交的信息采用明晰的标注（写注释）
- 使用git以及github，相信stormzhang的从0开始学习 GitHub 系列会对你有很大的帮助。

# Notice

- 每次 Commit 要保证粒度足够细，包含的更改和描述一致，且可编译运行

- 提交 PR 前如果确保当前分支在 dev 分支 HEAD 处的话可以不进行 Rebase

- dev 分支将处于 protected 状态，非不得已要执行 force push 的话，要提交通知所有开发成员

# 参考

- [Learning Git -- Android](https://source.android.com/source/git-resources.html)