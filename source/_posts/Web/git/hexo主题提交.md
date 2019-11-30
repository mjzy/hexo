---
title: hexo主题无法提交 -- 隐藏文件.git 嵌套导致提交出错
date: 2019-11-28 17:26:50
categories:
  - 前端
tags:
  - git
---

## git add 无法添加项目下的文件夹

搭建hexo博客时，遇到一个问题，git add 添加文件时发现主题文件夹始终无法添加

后查证是由于主题文件夹内有 .git 隐藏文件【下载主题时自带】，因此导致了项目.git 文件嵌套，文件无法提交

解决方案：

git rm --cached 【目录地址】，例如：

```
$ git add E:/Demo/GitHub/hexo/themes/pure
```

如果执行中报 `fatal: Unable to create 'xx/.git/index.lock': File exists.`

可以使用 `rm -f xx/.git/index.lock` 解决

成功后再使用 git 命令添加，例如：
```
$ git add E:/Demo/GitHub/hexo/themes/pure
```
