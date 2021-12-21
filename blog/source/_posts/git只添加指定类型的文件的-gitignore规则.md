---
title: git只添加指定类型的文件的.gitignore规则
date: 2021-12-21 09:40:07
tags:
- git
categories:
- miscellaneous
---

```
#忽略根目录下的所有文件
*
 
#忽略子目录下的所有文件
/*
#包含目录
!*/

#指定不忽略的文件
!*.c
!*.h

```

