---
title: cmake构建单片机工程
date: 2021-12-22 09:16:57
tags:
- cmake
categories:
- miscellaneous
---

## 1.CMake下载安装

- [官网cmake](https://cmake.org/)

```
$ cmake --version
```

- [gcc-arm-none-eabi工具链](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads)

```
$ arm-none-eabi-gcc --version
```

- [tdm-gcc编译器](https://jmeubank.github.io/tdm-gcc/)

```
 mingw32-make.exe --version
```

还需要**stm32cubemx**

## 2.参考文章

文章：[STM32 上的 CMake](https://dev.to/younup/cmake-on-stm32-the-beginning-3766)

**stm32cubemx**生成的文件目录不同版本有点不同，我使用的是6.2.1

[我的github工程例子](https://github.com/czc13611858691/stm32_cmake_example)