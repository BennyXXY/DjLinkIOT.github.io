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

# Git 协同守则

- 拉取 dev 分支到本地 Liveneeq 文件夹

  ```shell
  mkdir Liveneeq
  cd Liveneeq
  git init
  git remote add -t dev -f origin git@git.thecampus.cc:onecampus/liveneeq-android.git
  git checkout -b dev origin/dev
  ```
<!-- more -->

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

# Notice

- 每次 Commit 要保证粒度足够细，包含的更改和描述一致，且可编译运行

- 提交 PR 前如果确保当前分支在 dev 分支 HEAD 处的话可以不进行 Rebase

- dev 分支将处于 protected 状态，非不得已要执行 force push 的话，要提交通知所有开发成员

