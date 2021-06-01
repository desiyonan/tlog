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

配置一款主题

Hugo主题提供了大量模板，这里用的主题是 [PaperMod][Theme PaperMod]，详细文档(安装、配置)可以在[Github][PaperMod - Github]上查看。

更多的主题可以在 [Hugo 主题][Hugo Themes] 上查看

```powershell
PS D:\>cd tech-blog
PS D:\>git init
PS D:\>git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod --depth=1
PS D:\>git submodule update --init --recursive
```

修改配置文件 `config.toml` 或者 `config.yaml`，`.toml`格式配置可参考官方文档，`.\config.yaml`基本内容如下

```yml
baseurl: "http://tlog.desiyonan.tech"
title: "DnF's Zone"
defaultContentLanguage: zh
hasCJKLanguage: true
theme: PaperMod # 主题
params:
  AuthorName: "DnF"
  GitHubUser: "desiyonan"
```

启动本地服务器

```powershell
PS D:\>hugo server -D
Start building sites … 

                   | EN
-------------------+-----
  Pages            | 12
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  1
  Processed images |  0
  Aliases          |  2
  Sitemaps         |  1
  Cleaned          |  0

Built in 35 ms
Watching for changes in D:\tech-blog\{archetypes，content，data，layouts，static，themes}
Watching for config changes in D:\tech-blog\config.yaml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

现在可以直接访问 `http://localhost:1313/` 查看站点，不过要看文章具体效果可以先新建测试文章

```powershell
PS D:\>hugo new post/test.md
D:\tech-blog\content\post\test.md created
PS D:\>'## Test' | out-file -a -e utf8 .\content\post\test.md
```

访问 `http://localhost:1313/post/test` 就可以看到测试效果

最后基本仓库的初始化

```powershell
PS D:\>git commit -am "init"
PS D:\>git remote add origin <仓库地址>
PS D:\>git push -u origin master
```

## 配置 Github Pages

打开对应 `Github` 仓库页面，找到 `Setting` 页签，然后可以在侧边栏看到 `Pages` 设置

![Github Pages](https://raw.desiyonan.tech/img/2021/06/github_pages.png)

需要配置的主要是 `Source` 选择分支和目录，自定义域名可以通过 `Custom domain` 配置，域名配置不是必须，所以这里不再做过多赘述。

<!-- 参考 -->

[Hugo homepage]: https://gohugo.io "hugo 官网"
[Hugo Install]: https://gohugo.io/getting-started/installing/ "hugo 官方安装教程"
[Hugo Docs]: https://gohugo.io/documentation/ "Hugo 官方文档"
[Hugo Themes]: https://themes.gohugo.io/ "hugo 主题"
[Theme PaperMod]: https://themes.gohugo.io/hugo-papermod "hugo papermod 主题"
[PaperMod - Github]: https://github.com/adityatelange/hugo-PaperMod "adityatelange/hugo-PaperMod"
[Hugo Config]: https://www.gohugo.org/doc/overview/configuration "Hugo 中文网"
[Scoop Github]: https://github.com/lukesampson/scoop "GitHub Scoop"
[Scoop Codechina]: https://codechina.csdn.net/mirrors/lukesampson/scoop?utm_source=csdn_github_accelerator "Scoop CodeChina 加速"
[Hugo Gitee - Blog]: https://study777.gitee.io/p/hugo-gitee/ "Hugo Gitee - 黄世豪的Blog"
[使用Hugo搭建博客 - Blog]: https://www.dazhuanlan.com/2019/12/27/5e05bb1372559/
[Deploy Action]: https://zhuanlan.zhihu.com/p/109057290 "折腾Hugo | GitHub Pages | Github Actions自动构建发布免费个人网站"
