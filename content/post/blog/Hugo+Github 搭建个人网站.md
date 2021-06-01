---
slug: 8df2adb7809b41c597eb2efb10ed66db
title: "Hugo+Github 搭建个人网站"
date: 2021-05-31T20:25:48+08:00
# draft: true
---

最近正好整理记录的笔记，之前写的比较随意，不太好整理，而且之前早就想搭建自己的个人博客网站，正好这次刚好又时间折腾折腾。
搭建静态网站的框架网上比较多，文档和教程大部分也比较全，这次就直接选择口碑比较好也容易的 `Hugo` 在 `Github` 下搭建一个。

<!--more-->

## 安装 Hugo

在 Win10 下使用命令安装：

```powershell
PS D:\> scoop install hugo
Updating Scoop...
...
Creating shim for 'hugo'.
'hugo' (0.80.0) was installed successfully!
```

验证安装:

```powershell
PS D:\> hugo version
Hugo Static Site Generator v0.80.0/extended windows/amd64 BuildDate: unknown
```

这里的[Scoop][Scoop Github]是 Win10 平台下的软件包管理工具之一，非常方便，感兴趣可在 [GitHub][Scoop Github]或[CodeChina][Scoop CodeChina] 上查看。  
更多的安装方式和文档可以参看[Hugo 官方安装教程][Hugo Install].

## 新建站点

新建站点项目

```powershell
PS D:\> hugo new site tech-blog
Congratulations! Your new Hugo site is created in D:\tech-blog.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>\<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
```

基本的初始化

```powershell
PS D:\>cd tech-blog
PS D:\>git init
PS D:\>git commit -am "init"
PS D:\>git remote add origin <仓库地址>
PS D:\>git push -u origin master
```

<!-- 参考 -->

[Hugo homepage]: https://gohugo.io "hugo 官网"
[Hugo Install]: https://gohugo.io/getting-started/installing/ "hugo 官方安装教程"
[Hugo Docs]: https://gohugo.io/documentation/ "Hugo 官方文档"
[Hugo Themes]: https://themes.gohugo.io/ "hugo 主题"
[Hugo Config]: https://www.gohugo.org/doc/overview/configuration "Hugo 中文网"
[Scoop Github]: https://github.com/lukesampson/scoop "GitHub Scoop"
[Scoop Codechina]: https://codechina.csdn.net/mirrors/lukesampson/scoop?utm_source=csdn_github_accelerator "Scoop CodeChina 加速"
[Hugo Gitee - Blog]: https://study777.gitee.io/p/hugo-gitee/ "Hugo Gitee - 黄世豪的Blog"
[使用Hugo搭建博客 - Blog]: https://www.dazhuanlan.com/2019/12/27/5e05bb1372559/
