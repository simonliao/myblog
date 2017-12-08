---
title: Hexo搭建Github博客配置
date: 2017-12-08T10:49:50.000Z
tags:
  - Hexo
  - Github Pages
---

## 1、配置自定义域名

在Hexo工程下，创建文件：

```
/source/CNAME
```

文件的内容添加上你的域名即可，例如：

```
liao-xi.com
```

## 2、自定义404页面

参考：[Creating a custom 404 page for your GitHub Pages site](https://help.github.com/articles/creating-a-custom-404-page-for-your-github-pages-site/)

1. 进入Github个人网站仓库，例如github.com/username/username.github.io。

2. 在在Github个人网站仓库根目录中新建一个404.html，或者404.md文件。

3. 在该404文件头部的[YAML前页](http://jekyllrb.com/docs/frontmatter/)，添加如下内容，告诉系统该自定义404文件作为404文件使用。

  ```
  ---
  permalink: /404.html
  ---
  ```

4. 在404文件中添加内容，推荐使用[公益404-腾讯](http://www.qq.com/404/)。

5. 如果是使用Hexo，那么将该404文件放在/source/目录下。

## 3、googleapi导致页面加载缓慢
默认的主题里面使用了google相关的资源，由于总所周知的原因，在国内这个网站根本就不存在，所以需要更换一下资源：
1. 查找哪些文件使用了google资源。在工程目录全局搜索googleapis。
2. 替换掉这些资源。可以采用其他网站的url替换，或者直接将相关资源下载之后放在当前工程都可以。

例如针对默认主题(landscape)，将themes/landscape/layout/\_partial/head.ejs文件中的：
``` html
<link href="//fonts.googleapis.com/css?family=Source+Code+Pro" rel="stylesheet" type="text/css">
```
修改为：（googlefonts.css的存放路径：themes/landscape/source/css）
``` html
<link href="/css/googlefonts.css" rel="stylesheet" type="text/css">
```
将themes/landscape/layout/\_partial/after-footer.ejs文件中的：
``` html
<script src="//ajax.googleapis.com/ajax/libs/jquery/2.0.3/jquery.min.js" ></script>
```
修改为：（jquery.min.js的存放路径：themes/landscape/source/js）
``` html
<script src="/js/jquery.min.js"></script>
```
