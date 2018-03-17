---
title: hexo搭建个人博客——搭建
date: 2018-03-17 20:48:48
tags:
---

------

# 安装hexo
```
// 全局安装hexo
cnpm i -g hexo
// 初始化项目
hexo init
```
# 搭桥到github
## 创建仓库
创建一个名为`yourname.github.io`(yourname是github账户名，必须为该格式的仓库名)的仓库
## 配置github账户信息
```
// YourName和YourEmail都是自己github账户名和github邮箱
git config --global user.name 'YourName'
git config --global user.email 'YourEmail'
```
## 创建ssh key并添加到github
1. 生成ssh key
`ssh-keygen -t rsa -C "youremail@example.com`
2. 找到存放ssh key的文件`id_rsa.pub`的内容
`cat id_rsa.pub`
3. 添加到github
github -> Settings -> SSH and GPG keys，添加ssh
4. 测试是否添加成功
ssh -T git@github.com

# 部署项目
## 修改配置信息
打开hexo项目，修改`_config.yml`文件中的一些配置
```
// hexo 3.0以上，type必须指定为git
deploy:
  type: git
  repo: https://github.com/YourGithubName/YourGithubName.github.io.git
  branch: master
```
## 执行hexo命令
```
// 注：hexo 3.0之后把服务器独立成个别模块，需要单独安装：`cnpm i hexo-server`
hexo clean
hexo generate
hexo server
```
## 测试
打开浏览器，输入`http://localhost:4000`，即可看到本地博客了
# 部署到github
## 安装依赖
`cnpm i hexo-deployer-git --save`，安装此依赖，才能将文章部署到github服务器上
## 执行hexo命令
```
// 建议每次都按照该步骤部署
hexo clean
hexo generate
// 执行deploy命令将本地博客部署到github服务器，并自动提交代码到`yourname.github.io`仓库
hexo deploy
```
## 浏览器访问
在浏览器输入`https://yourgithubname.github.io`，就可以看到个人博客了
# 修改及配置主题
修改`_config.yml`文件中的配置项
`theme: next`，推荐使用next主题，主题配置详见 [hexo搭建个人博客——next主题美化](https://shuangmianxiaoq.github.io/2018/03/17/hexo%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2%E2%80%94%E2%80%94next%E4%B8%BB%E9%A2%98%E7%BE%8E%E5%8C%96/)
# 写文章
- 新建文章：`hexo new "文章名"`
- 编辑文章：在`source/ _posts`目录下，采用Markdown语法编写文章

------