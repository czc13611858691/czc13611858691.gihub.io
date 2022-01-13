---
title: git子模块
date: 2022-01-13 11:51:54
tags:
- git
categories:
- 工作笔记
---



### 1.拉取别人的仓库

**示例**

```bash
$ git submodule add https://github.com/chaconinc/DbConnector
```

### 2.克隆含有子模块的项目

**示例**

```bash
$ git submodule init
$ git submodule update
```

### 3.移动子模块的位置

**示例**

```bash
$ git mv old/submod new/submod
```

