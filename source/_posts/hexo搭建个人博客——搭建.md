---
title: Hexo 搭建个人博客
description: 使用 Hexo 初次搭建博客
date: 2018-03-17 20:48:48
categories: Hexo
tags: 学习
---

---

## 安装 Hexo CLI 并初始化

```bash
npm install hexo-cli -g
hexo init myblog
cd myblog
yarn
hexo server
```

## 搭桥到 Github

<!-- more -->

### 创建仓库

创建一个名为`yourname.github.io`的仓库（必须为该格式的仓库名）

### 配置 Github 账户信息

```bash
// YourName 和 YourEmail 都是自己 Github 账户名和 Github 邮箱
git config --global user.name 'YourName'
git config --global user.email 'YourEmail'
```

### 添加 ssh key 到 Github

1. 生成 ssh key

```bash
// 生成 ssh key
ssh-keygen
// 找到存放 ssh key 的文件并查看内容
cat ~/.ssh/id_rsa.pub
```

2. 添加到 Github
   `Github` -> `Settings` -> `SSH and GPG keys` -> `New SSH key`

3. 测试是否添加成功

```bash
ssh -T git@github.com
```

## 项目运行

### 修改配置信息

打开 `Hexo` 项目，修改`_config.yml`文件中的部分配置

```
// Hexo 3.0 以上，type 必须指定为 git
deploy:
  type: git
  repo: git@github.com:shuangmianxiaoQ/shuangmianxiaoQ.github.io.git
  branch: master
```

### 使用 Hexo 命令运行项目

注：`Hexo 3.0` 之后把服务器独立成个别模块，需要单独安装：`yarn add hexo-server`

```bash
hexo clean
hexo generate
hexo server
```

打开浏览器访问`http://localhost:4000`，即可查阅本地博客

## 部署到 github

### 安装依赖

`yarn add hexo-deployer-git`，安装该依赖，才能将文章部署到 `Github` 服务器上

### 使用 Hexo 命令部署

```bash
hexo clean
hexo generate
// 执行 deploy 命令将本地博客部署到 Github 服务器，并自动提交代码到`yourname.github.io`仓库
hexo deploy
```

部署完成后，在浏览器输入`https://yourgithubname.github.io`，就可以查看个人博客了

## 修改主题

修改`_config.yml`文件中的配置项，推荐使用 `next` 主题

`theme: next`

主题配置详见 [hexo 搭建个人博客——next 主题美化](https://shuangmianxiaoq.github.io/2018/03/17/hexo%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2%E2%80%94%E2%80%94next%E4%B8%BB%E9%A2%98%E7%BE%8E%E5%8C%96/)

## 写文章

- 新建文章：`hexo new "文章名"`
- 编辑文章：在`source/ _posts`目录下，采用 Markdown 语法编写文章

---
