---
title: hexo+next主题搭建个人博客记
date: 2017-12-24 20:37:06
tags:
  - Others
comments: true
---

hexo是一个用来生成静态界面的框架，使用hexo搭建静态网页博客，实际上是使用hexo将本地博客内容渲染为静态html页面。运行hexo server可以通过本地4000端口访问这个静态网页，通过将静态网页提交到github pages个人主页后就可以通过 https://gethub_name.github.io 来访问你的静态网站啦

## 基础环境配置
1. 在开始之前，先安装一些过程中必要的组件。
  - 安装 git bash 或者 cygwin，需要用到 git 提交且用到一些命令，所以 linux 风格的shell还是很必要的；
  - 安装 node，windows直接下载 [node 安装程序](https://nodejs.org/en/)，安装好后打开shell使用命令`node -v`，查看一下node版本验证安装是否成功；
  - 安装 hexo ，打开shell使用命令`npm install -g hexo`安装hexo

2. 本文使用的环境如下：
  - Windows 10
  - cygwin
  - git version 2.15.1
  - node version v8.9.3
  - hexo version 3.4.4

## 初始化博客并安装 next 主题
### 安装hexo并初始化博客
在hexo安装的地方新建目录hexo，进入目录后使用命令`npm install -g hexo`安装hexo，并初始化博客
```bash
mkdir hexo
cd hexo
npm install -g hexo
hexo init
```
之后会生成如下目录如下

![hexo目录](/images/hexo+next主题搭建个人博客记/2-1-1.png)

其中_config.yml是hexo的配置文件
package.json描述了hexo版本以及dependencies的版本
source就是博客md文件的位置，source目录树如下

![source目录树](/images/hexo+next主题搭建个人博客记/2-1-2.png)

刚初始化好之后只有_posts/hello-world.md这一篇，图中about、categories和tags是我后来添加的页面，这些页面也是可以在这里编辑内容，_posts目录中就是我们自己的博文md文件了。

themes目录是hexo的主题目录，主题都要安装在这里。

初始化博客后运行命令`hexo s -debug`

![](/images/hexo+next主题搭建个人博客记/2-1-3.png)

在浏览器访问 http://localhost:4000/ 就可以看到使用默认主题landscape的网页如下图

<div style="align: center">
<img src="/images/hexo+next主题搭建个人博客记/2-1-4.png" height="80%" width="80%"/>
</div>


### 安装next主题
在hexo目录位置下载next主题
`git clone https://github.com/iissnan/hexo-theme-next themes/next`

与所有 Hexo 主题启用的模式一样。 当 克隆/下载 完成后，打开 hexo配置文件， 找到 theme 字段，并将其值更改为 next 如 `theme: next`。

验证主题更改成功

`hexo s --debug`

在浏览器访问 http://localhost:4000/ 确保站点正确运行。

### 配置next主题
主题的配置文件在`./themes/next/_config.yml`

配置next主题可以参考[Next官网](http://theme-next.iissnan.com/getting-started.html) ，主要说一些我修改的配置。

选择scheme

```
# Schemes
#scheme: Muse
#scheme: Mist
scheme: Pisces
#scheme: Gemini
```

设置语言

```
language: zh-Hans
```

设置菜单

```
menu:
  home: / || home
  about: /about/ || user
  tags: /tags/ || tags
  categories: /categories/ || th
  archives: /archives/ || archive
  #schedule: /schedule/ || calendar
  #sitemap: /sitemap.xml || sitemap
  #commonweal: /404/ || heartbeat

# Enable/Disable menu icons.
menu_icons:
  enable: true
  home: home
  about: user
  categories: th
  tags: tags
  archives: archive
  #schedule: calendar
```

修改头像

```
# Sidebar Avatar
# in theme directory(source/images): /images/avatar.gif
# in site  directory(source/uploads): /uploads/avatar.gif
avatar: /images/avatar.png
```

验证主题配置成功

`hexo s --debug`

## 上传到github
gitpage 是用来展示个人或项目信息，所以gitpage也分为两类
- 个人或组织
- 项目

我们这里用来展示个人信息
