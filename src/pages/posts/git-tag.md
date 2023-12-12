---
title: Git tag
date: Thu Dec 07 2023 11:19:31 GMT+0800 (中国标准时间)
lang: zh
duration: 5min
---

### 打轻量级标签

轻量级标签是一个简单的标签，它只是一个特定提交的引用。创建轻量级标签的命令是

```bash
git tag tagname
```

例如，要创建一个名为 `v1.0.0` 的轻量级标签，你可以执行：

```bash
git tag v1.0.0
```

### 打注释标签

注释标签是存储了额外信息的标签，如标签的创建者、日期、附加信息等。创建注释标签的命令是：

```bash
git tag -a tagname -m "<message>"
```

例如，创建一个名为 `v1.0.0` 的注释标签，并附加一条消息：

```bash
git tag -a v1.0.0 -m "Release version 1.0.0"
```

### 打标签到特定的提交

默认情况下，标签是应用于当前的 `HEAD`，即你最后一次提交的状态。如果你想要给历史中的某个特定提交打标签，你需要提供该提交的哈希值：

```bash
git tag <tagname> <commit-hash>
```

例如：

```bash
git tag v1.0.0 9fceb02
```

### 将标签推送到远程仓库

创建的标签默认是只保存在本地的。如果你想要与他人共享这些标签，你需要将它们推送到远程仓库：


```bash
git push origin <tagname>
```

要推送所有的本地标签到远程仓库，可以使用：

```bash
git push origin --tags
```
