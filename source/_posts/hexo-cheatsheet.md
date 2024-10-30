---
title: hexo-cheatsheet
categories: tech.
description: 搭建hexo博客的一些过程
cover: 'https://bu.dusays.com/2024/10/24/671935201b0f2.jpg'
abbrlink: 1c2fa9ee
date: 2024-10-30 20:04:38
tags:
- hexo
---

# 写在前面

今天是2024年10月30日，经历了换导的挣扎之后，拿到了两边的签字，总算有心情写点东西。搭Blog其实早就搭过，后面因为种种原因，没有坚持下来。经历了一些之后觉得，不管是技术上的事儿，还是生活上的思考，还是需要留下些痕迹，一来为了记录，日后回头看的时候，可以有些许感慨，二来，也算是对过往的一个交代。

# 搭建hexo博客

## blog 目标

一个博客，我觉得起码得做到以下几点才算一个好用的工具：

- [x] 方便写，不用花过多时间在格式编辑上
- [x] 方便管理，可以快速定位到自己想要的notes
- [x] 多端同步，win&mac支持
- [x] diy，可拓展性
- [ ] 多平台，域名
- [ ] 博客框架的更新

捣鼓了大概一周？现在这个方案基本令我满意，至于域名，现在暂时挂在`github pages`上，后面如果买了域名再说。

## 环境配置

这方面我不是特别懂，主要是用轮子。主要用到的环境是

* [npm](https://www.npmjs.com/)
* [node.js](https://nodejs.org/)

`npm`是node.js的包管理工具，`node.js`是js的运行环境。
[npm install](https://nodejs.org/en/download/package-manager)的界面挺好的，给出了各个环境的安装方法。win & mac 可以通过包管理工具安装，也提供了prebuild的安装包。

> notice: 如果是老版本的mac， brew 有点拉稀，建议还是用prebuild的安装包。如果是windows，那么可能需要配置环境变量。

测试是否安装成功：

```shell
node -v
npm -v
```

## 安装hexo

```shell
npm install -g hexo-cli
```

`-g` 是全局安装，安装完之后，就可以在任何地方使用hexo命令。

## 基本的hexo指令

* hexo init \<folder\> 初始化一个hexo博客
* hexo new \<layout\> \<title\> 创建一篇题为\<title\>的\<layout\>文章
* hexo generate 生成静态文件
* hexo server 启动本地服务器
* hexo deploy 部署博客

运行`hexo init blog-demo`之后，会在当前目录下生成一个文件夹，里面包含了一些基本的文件。基本的结构如下（有一些详略，butterfly主题是后面安装的 ）：

```
blog-demo/
├── source/
│   ├── _posts/
│   └── _drafts/
├── themes/
│   └── butterfly/
├── node_modules/
├── scaffolds/
│   ├── tech.md
│   └── life.md
├── _config.yml
├── _config.butterfly.yml
├── package.json
└── package-lock.json
```

其中`source`文件夹下包含`_posts`和`_drafts`两个文件夹，分别用于存放草稿和文章。`themes`文件夹下包含主题文件夹，`node_modules`是node.js的包管理文件夹，`scaffolds`是post的模板文件夹，`_config.yml`是全局配置文件，`_config.butterfly.yml`是主题配置文件，`package.json`是项目配置文件（npm包管理）。

## 主题安装

hexo的主题可以到[hexo主题](https://hexo.io/themes/)查看，选择一个自己喜欢的主题，然后按照主题的说明进行安装。这里用的是[butterfly](https://github.com/jerryc127/hexo-theme-butterfly)主题。

```shell
git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
```
这样下载下来的主题文件夹会放在`themes`文件夹下。

然后在`_config.yml`文件中，将`theme`设置为`butterfly`。

```yaml
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: butterfly
```

一些需要安装的插件(在`package.json`中)：

```json
"dependencies": {
    "hexo": "^7.3.0",
    "hexo-abbrlink": "^2.2.1",
    "hexo-browsersync": "^0.3.0",
    "hexo-deployer-git": "^4.0.0",
    "hexo-deployer-shell": "^0.2.3",
    "hexo-generator-archive": "^2.0.0",
    "hexo-generator-category": "^2.0.0",
    "hexo-generator-feed": "^3.0.0",
    "hexo-generator-index": "^4.0.0",
    "hexo-generator-sitemap": "^3.0.1",
    "hexo-generator-tag": "^2.0.0",
    "hexo-renderer-ejs": "^2.0.0",
    "hexo-renderer-jade": "^0.5.0",
    "hexo-renderer-pandoc": "^0.4.0",
    "hexo-renderer-pug": "^3.0.0",
    "hexo-renderer-stylus": "^3.0.1",
    "hexo-server": "^3.0.0",
  }
```

这里是直接从`package.json`中复制过来的，日后可能会有更新改动，如果有更新请以最新的为准。一般来说，执行：

``shell
npm install
``

会自动查询当前目录下的`package.json`文件，安装所有需要的插件。如果安装某个特定的插件，可以执行：

```shell
npm install <plugin-name>
```

> notice: hexo-renderer-pandoc 需要提前安装pandoc，pandoc的安装可以参考[pandoc的文档](https://pandoc.org/installing.html)。windows 别忘了环境变量。



## 额外的美化/优化配置

偷懒略一下，大多数的配置都在`_config.yml`文件中，主题配置在`_config.butterfly.yml`文件中。`_config.butterfly.yml`文件中，有非常多的配置项，可以参考[butterfly的文档](https://butterfly.js.org/posts/21cfbf15/)进行配置。如果没有`_config.butterfly.yml`文件，可以复制`/themes/butterfly/`文件夹下的`_config.yml`文件，然后重命名为`_config.butterfly.yml`。后者会自动覆盖前者。

> notice: 需要修改`_config.yml`中的`language`为`zh-CN`，否则中文标点会显示在中间。

## 部署

部署用到了`hexo-deployer-git` 和 `hexo-deployer-shell` 两个插件。

`hexo-deployer-git` 是用来将博客部署到github的，`hexo-deployer-shell` 是用来在部署前预执行一些shell命令的。

```yaml
# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
  - type: shell
    command: git add -A && git commit --allow-empty -m "raw file update" && git push -u origin main
  - type: git
    repository: git@github.com:MuYanustc/MuYanustc.github.io.git
    branch: gh-pages
```

因为`hexo-deployer-git` 的作用是将编译过后的文件同步到github，看不到原始的文档。所以用`hexo-deployer-shell` 在部署前执行一些shell命令，将原始的文档推送到github。

> notice: 基础的git配置在这里略去了。github仓库的名字需要是`<username>.github.io`, 以及在github repository settings中，设置github pages的source为`gh-pages`分支。

## 图床方案

使用[7bu](https://7bu.top/login)，可以自动同步图片到github，并且可以生成markdown的图片链接。配合[Piclist](https://github.com/Kuingsmile/PicList)和其vscode/cursor插件，可以方便的将图片插入到markdown中。
## 一些现存的问题/可能改进的方向

### 主题的更新

`themes/butterfly` 是作为一个git仓库存在的，如果不额外设置，那么外层仓库的操作无法同步到`themes/butterfly`。这意味着我自己的修改也无法同步到远程仓库中。

可能的解决方案：

* submodule/tree 一种git 子仓库的管理方法
* 每次进入butterfly目录，执行`git pull`（这个方法不清楚能否实现自己修改，也许需要先fork主题仓库，github不支持一个仓库里的文件夹作为source）

目前的解决方案是：

删除`.git`文件夹，自己修改。如果未来需要更新主题，再重新设置git仓库（？未测试）。


### 多平台部署

将blog部署到多个平台，这就需要修改`github actions`的配置。将仓库推到别的平台。

### 多平台的操作流

现在如果有更改，那么需要先

```shell
git pull origin main
```

然后继续修改，是否有更好的方法？（怕忘记了）

忘记了的标准流程应该是？：

```shell
git stash
git pull origin main
git stash pop
```

