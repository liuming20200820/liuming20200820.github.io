---
title: 用hexo 搭建博客
date: 2022-01-08 19:11:50
tags:
---
## 什么是 Hexo？
Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 [Markdown](https://daringfireball.net/projects/markdown/)（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

## 安装
安装 Hexo 相当简单，只需要先安装下列应用程序即可：

+ [Node.js](https://nodejs.org/en/) (Node.js 版本需不低于 10.13，建议使用 Node.js 12.0 及以上版本)
+ [Git](http://git-scm.com/)

```
npm install hexo-cli -g
hexo init blog
cd blog
npm install
hexo server
```
新建完成后，指定文件夹的目录如下：
```
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```
#### _config.yml
网站的 配置 信息，您可以在此配置大部分的参数。
#### package.json
应用程序的信息。EJS, Stylus 和 Markdown renderer 已默认安装，您可以自由移除。
```
{
  "name": "hexo-site",
  "version": "0.0.0",
  "private": true,
  "scripts": {
    "build": "hexo generate",
    "clean": "hexo clean",
    "deploy": "hexo deploy",
    "server": "hexo server"
  },
  "hexo": {
    "version": "6.0.0"
  },
  "dependencies": {
    "hexo": "^6.0.0",
    "hexo-deployer-git": "^3.0.0",
    "hexo-generator-archive": "^1.0.0",
    "hexo-generator-category": "^1.0.0",
    "hexo-generator-index": "^2.0.0",
    "hexo-generator-tag": "^1.0.0",
    "hexo-renderer-ejs": "^2.0.0",
    "hexo-renderer-marked": "^4.0.0",
    "hexo-renderer-stylus": "^2.0.0",
    "hexo-server": "^3.0.0",
    "hexo-theme-landscape": "^0.0.3"
  }
}

```
#### scaffolds
模版 文件夹。当您新建文章时，Hexo 会根据 scaffold 来建立文件。

Hexo的模板是指在新建的文章文件中默认填充的内容。例如，如果您修改scaffold/post.md中的Front-matter内容，那么每次新建一篇文章时都会包含这个修改。
#### source
资源文件夹是存放用户资源的地方。除 _posts 文件夹之外，开头命名为 _ (下划线)的文件 / 文件夹和隐藏的文件将会被忽略。Markdown 和 HTML 文件会被解析并放到 public 文件夹，而其他文件会被拷贝过去。
#### themes
主题 文件夹。Hexo 会根据主题来生成静态页面。
修改主题：
下载
```
git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
or
npm i hexo-theme-butterfly

```
修改本地配置
```
_config.yml文件下
theme: butterfly
```
## Hexo部署博客到Github和Coding
#### Github和Coding又是什么？
+ Github是国外免费的Git代码托管平台。利用Github Page服务可以免费创建一个静态网站。
+ Coding则是国内Git代码托管平台。国内首个Git代码托管平台GitCafe已被Coding收购。也提供page服务

#### 本地部署Hexo
+ 输入hexo s 启动博客
```
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/ . Press Ctrl+C to stop.
```
+ 打开浏览器输入 http://localhost:4000/ 即可访问

#### 将博客托管到Github和Coding上
```
npm i hexo-deployer-git --save
修改_config.yml配置文件
deploy:
  type: git
  repository: https://github.com/liuming20200820/liuming20200820.github.io.git
  branch: main
--------------------------------------------------------------------------------------------------
hexo g 生成静态网页
hexo d 开始部署
```

