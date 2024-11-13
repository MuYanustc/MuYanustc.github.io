---
title: WSL环境配置
categories: tech.
description: 这是一篇在Windows下配置WSL的笔记
cover: 'https://bu.dusays.com/2024/10/24/671935201b0f2.jpg'
tags:
  - WSL
  - Env.
  - Linux
  - Windows
abbrlink: 33ee5048
date: 2024-11-09 23:24:50
---

# Why WSL?

WSL是Windows Subsystem for Linux的简称，是微软为Windows 10和Windows 11操作系统开发的子系统，允许用户在Windows环境下运行Linux发行版。

作为一个win/mac/linux三修用户，`win`的命令行体验确实是最烂的，而`mac`和`linux`的命令行逻辑基本类似，所以WSL的出现确实大大提升了Windows的命令行体验。

# 配置WSL

## 安装WSL

windows 上安装`WSL`的方法出乎意料的简洁：

```powershell
wsl --install
```

默认是Ubuntu系统，也可以选择别的发行版，比如Debian、OpenSUSE、Kali Linux等。

## 配置WSL

这里遇到的最大问题是`WSL`的网络问题，开了系统代理之后会出现`WSL`无法联网的情况。

### 具体环境以及解决办法

* Windows 11
* WSL 2
* Ubuntu 22.04
* Clash for windows


### 细节区别（相比虚拟机）

* 性能tradeoff，比虚拟机启动更快，空间更小，维护成本更低，但运行速度未必更快。
* 貌似会使用`Windows`的部分环境变量，但不能寄希望于所有都生效，尤其是一些`.exe`文件。
* 有`~`目录，windows下的文件也支持在`WSL`下访问，这点很nice，比如C盘对应的就是`/mnt/c`。


### Linux 配置

具体详细见{% post_link Linux环境配置 %}。
