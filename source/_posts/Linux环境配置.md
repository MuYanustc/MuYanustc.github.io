---
title: Linux环境配置
categories: tech.
description: 这是一篇Linux基础环境配置。
cover: 'https://bu.dusays.com/2024/10/24/671935201b0f2.jpg'
abbrlink: 3fd5a2ff
date: 2024-11-13 10:20:52
tags:
- Env.
- Linux
---

# Why Linux?

众所周知，Linux 是Unix based sysem, 而万恶的windows是DOS based system。

win相比Linux更加繁重，但好处是日常使用和娱乐更加稳定和方便。但往往我们需要捣鼓一些`tech`的东西，这时候就麻烦了————遇到的问题包括且不限于：

- 莫名其妙的环境问题
- 莫名其妙的各种服务，修改注册表
- 莫名其妙的崩溃
- 莫名其妙的错误
- 莫名其妙的驱动问题
- 莫名其妙的兼容性问题
- 莫名其妙的更新问题

这时候有一个干净好用的Linux环境就显得尤为重要。

# 环境配置

## 1. 安装Linux

这里暂且略过，目前用过的多数是Ubuntu。

## 2. 配置Linux

### 2.1 配置终端

Linux 原生终端是`bash`，但`zsh`更加强大，所以这里选择`zsh`。

这里有一篇总结的很不错的[文章](https://www.haoyep.com/posts/zsh-config-oh-my-zsh/)。

> 一个遗漏点：
使用命令`chsh -s /bin/zsh`修改默认shell为zsh。环境变量的生效需要一次full login才行。在命令行可以使用`su - username`登录。