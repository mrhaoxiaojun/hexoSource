---
title: GitHub+Hexo+Next搭建免费独立个人博客
date: 2017-01-04 9:56:29  
categories: hexo
tags: 
	- github
	- hexo
	- next
---

## 前言

—–个人认为不用通篇阅读官方文档，网上很多包括我自己的博文基本可以初步搭建起来自己的博客，然后可能按照你的预想做东西还会有很多坑，再去查阅文档和其他资料，本博客略掉简单的操作步骤，但是会给大家提供一些较全的，零基础的博客地址，我主要是记录自己搭建是绕过的坑

[Hexo官方帮助文档](https://hexo.io/zh-cn/docs/)

[3.0搭建教程](http://opiece.me/2015/04/09/hexo-guide/)

 ![coding](GitHub+Hexo+Next搭建免费独立个人博客/coding.jpg)

<!--more-->

## 准备：配置开发环境

依次下载安装：

- [Node.js](https://nodejs.org/en/download/)
- [Git](http://git-scm.com/downloads)

不要问我怎么安装，傻瓜式安装，下一步下一步，不会找谷歌

## 注册访问[Github](https://github.com/)

Github为广大开发者提供了一个非常好的平台，不仅是代码的开源，同时Github还提供了开发者可以在Github上建立自己的站点。这个功能的局限是只能创建静态的网站。

注册完成后，需要验证邮箱。QQ邮妥妥的

怎么注册？我的个娘，请找度娘

注册完成之后，

创建repository

![repository-01](GitHub+Hexo+Next搭建免费独立个人博客\repository-01.png)

创建时，只需要填写Repository name即可，当然这个名字的格式必须为`youname.github.io`，例如我的为mrhaoxiaojun.github.io

![repository-02](GitHub+Hexo+Next搭建免费独立个人博客\repository-02.png)

## Hexo

- 快速，简单而高效的静态博客框架

### Hexo初始化博客框架

1.安装Hexo

```
$ npm install -g hexo-cli
```

2.初始化框架

```
$ hexo init <yourFolder>
$ cd <yourFolder>
$ npm install
```

初始化完成后，指定文件夹的目录如下

```
.
├── _config.yml //网站的配置信息，您可以在此配置大部分的参数。
├── package.json
├── scaffolds //模版文件夹。当您新建文章时，Hexo 会根据 scaffold 来建立文件。
├── source //资源文件夹是存放用户资源的地方。
| ├── _drafts
| └── _posts
└── themes //主题文件夹。Hexo会根据主题来生成静态页面。
```

3.新建文章（创建一个hello world）

```
$ hexo new "Hello World"
```

会在/source/_post里添加hello-world.md文件，之后新建的文章都将存放在此目录下。编辑hello-world.md文件可修改内容。

4.生成网站

```
$ hexo generate                #简写 hexo g
```

此时会将/source的.md文件生成到/public中，形成网站的静态文件。

5.本地服务器

```
$ hexo server               #简写 hexo s   hexo s --debug
```

输入[http://localhost:4000](http://localhost:4000/) 即可查看网站。
可修改：

```
$ hexo server -p 3000
```

此时，输入[http://localhost:3000](http://localhost:3000/) 查看网站。

6.部署网站

```
$ hexo deploy             #简写 hexo d
```

部署网站之前需要生成静态文件。
可以用$ hexo generate -d直接生成并部署。此时需要在_config.yml中配置你所要部署的站点：

```
deploy: 
  type: git
  repository: http://github.com/mrhaoxiaojun/mrhaoxiaojun.github.io.git
  branch: master
```

到此为止完成网站的雏形。输入yourname.github.io可访问博客主页。例如：[https://mrhaoxiaojun.github.io/](http://mrhaoxiaojun.github.io/) 。
绕坑：
部署的时候有可能会出错，别急，加这一步操作就ok了

```
$ npm install hexo-deployer-git --save
```

## Next主题

NexT 主旨在于简洁优雅且易于使用，所以首先要尽量确保NexT的简洁易用性。

这是一个扩展主题，由一个台湾学生[iissnan](https://github.com/iissnan)开发。主题秉承精于心，简于形的理念。

1. 下载Next主题

   ```
   $ cd your-hexo-site
   $ git clone https://github.com/iissnan/hexo-theme-next themes/next
   ```

2. 启用Next主题

   下载完成后，打开站点配置文件，找到theme字段，并将其值更改为 next。

   ```
   # Extensions
   ## Plugins: http://hexo.io/plugins/
   ## Themes: http://hexo.io/themes/
   theme: next
   ```

3. 验证是否可用
   运行hexo s –debug，并访问[http://localhost:4000](http://localhost:4000/) ，确保站点正确运行。

附：

- [Next官网](http://theme-next.iissnan.com/)–各种功能这里面都有，需要自己去配置，比如，评论，链接，打赏……
- [主题作者iissnan的博客](https://github.com/iissnan)

## Markdown语法

Markdown 是一种「电子邮件」风格的「标记语言]，Hexo支持Markdown。

语法很简单，花十分钟网上找找学一下啊就可以

[Markdown中文网](http://www.markdown.cn/)

[Markdown语法说明（简体中文版）](http://www.appinn.com/markdown/#list)

### Markdown 编辑器

网上搜索一下，网友推荐的Markdown编辑器很多，看个人选择。我对[Typora](https://typora.io/)这个产品比较有好感，所写即所得，就是爽。。。

[Typora](https://typora.io/)