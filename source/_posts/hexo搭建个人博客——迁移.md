---
title: Hexo 搭建个人博客之迁移
description: 使用 Hexo 搭建博客后，利用 Github 来管理博客迁移
date: 2018-03-17 20:19:13
categories: Hexo
tags: 学习
---

---

> 由于使用 `Hexo` 搭建的是博客属于静态博客，如果更换电脑或是在多台电脑同时更新博客，就不能很方便的管理了
> 此时，借助 `Github` 来管理 `Hexo` 项目源代码同时更新是个不错的选择

## 创建仓库

在 `Github` 创建一个仓库，用来存放 `Hexo` 项目的核心代码

<!-- more -->

## 上传代码

上传如下图所示的文件到 `Github`：

![git上传代码目录](/images/hexo迁移/代码提交目录.png)

- 使用 `.gitignore` 文件忽略部分文件的提交

```
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
```

## 向 github 中添加 ssh key

参照 [hexo 搭建个人博客——搭建](https://shuangmianxiaoq.github.io/2018/03/17/hexo%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2%E2%80%94%E2%80%94%E6%90%AD%E5%BB%BA/) 中如何添加`ssh key`到`github`

## 使用

```bash
git clone https://github.com/shuangmianxiaoQ/myblog.git

yarn

node_modules/.bin/hexo clean
node_modules/.bin/hexo g
node_modules/.bin/hexo s
node_modules/.bin/hexo d
```

---
