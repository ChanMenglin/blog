---
title: "本博客的构建过程"
slug: “build-this-blog”
description: "记录本博客网站的构建过程"
date: 2022-06-25
lastmod: 2022-06-255
image: possessed-photography-M8QfxX2EQXo-unsplash.jpg
archives: 
  - 2022
  - 2022-06
categories:
  - 博客
tags:
  - 博客
  - 博客搭建
links:
  - title: Hugo 官网
    description: Hugo 官网
    website: https://gohugo.io/
    image: https://gohugo.io/safari-pinned-tab.svg
  - title: hugo-theme-stack
    description: Stack 主题仓库 Github 地址
    website: https://github.com/CaiJimmy/hugo-theme-stack
    image: https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png
  - title: Stack 主题文档
    description: Stack 主题文档
    website: https://docs.stack.jimmycai.com/zh/
    
---

## 前言

在几年之前就有自建博客的打算，但一直没有找到心仪的博客搭建方案，最近几个月了解到了 [hugo](https://gohugo.io)，比较符合我的胃口，再加上 [Stack](https://github.com/CaiJimmy/hugo-theme-stack) 主题（感谢 hugo 和 Stack 主题的贡献者），让我下定决心开始搭建自己的博客网址。  
本文为本博客网站搭建过程的记录，也作为本博客的第一篇文章。

## 准备工作

### 安装 hugo

我使用的是 Mac 系统，因此采用 brew 安装

```sh
# 安装 Hugo
brew install hugo
# 查看 HUgo 安装情况
hugo version
```

### 新建站点

hugo 安装完成后就可以开始新建存放博客文件的目录了

```sh
# 新建站点
hugo new site Blog # 会新建名为 Blog 的文件夹，并添加必要的文件
```

### 安装博客主题

本博客网站使用的是 Stack 主题，你也可以选择自己喜欢的主题

```sh
# 下载主题（这里使用的是 Stack 主题）
cd Blog
git init
git submodule add https://github.com/CaiJimmy/hugo-theme-stack/ themes/stack
```

到这里，我们的准备工作就算完成了

### 修改配置文件

按照 Stack 的文档声明，将 Stack 主题下的部分文件复制到博客网站根目录中对应的文件下

```sh
# 拷贝文件（仅限于第一次使用 Stack 主题）
cp -r themes/stack/assets assets
cp themes/stack/config.yaml .
```

删除根目录下的 `config.toml`（会自动替换为从 Stack 主题复制的 `config.yaml` 替代）

```yml
languageCode: zh-cn           # 语言设置为 简体中文
defaultcontentlanguage: zh-cn # 默认语言设置为 简体中文
title: My New Hugo Site       # 网站标题
theme: stack                  # 主题修改为 stack（需要与主题文件夹同名）
```

这里为最小配置，详细的配置可参考：https://docs.stack.jimmycai.com/zh/configuration/

### 启动

```sh
# 启动 HUgo 服务
hugo server -D
```

启动成功后就可以在 http://localhost:1313/ 查看生成的网站了

## 修改网站

在 `./content/` 目录下添加以下目录，丰富网站功能

- `categories`：分类
- `tags`：标签
- `page`
  - `about`：关于
  - `archives` 归档
  - `Search`：搜索

可以在 `./content/post` 目录下写文章了

## 部署

这里采用 Github Page 部署

1. 将项目文件上传到 Github（需要预先建好仓库）
2. 将 public 目录添加到 gh-pages 分支

> 博客搭建还不是很完善，后续会持续更新

> 2022年6月25日 写于湖北武汉