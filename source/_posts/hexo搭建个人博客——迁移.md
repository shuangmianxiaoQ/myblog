---
title: hexo搭建个人博客——迁移
date: 2018-03-17 20:19:13
tags:
---

------
**由于hexo构建的是静态博客（博客项目代码都存放在本地），如果当更换电脑或是想在多台电脑同时更新博客就有点麻烦了，而通过github来管理hexo项目源代码同时更新是个不错的选择。**

# 创建仓库
在github创建一个仓库，用来存放hexo项目的核心源代码
# 上传代码
上传如下图所示的文件到github：
![git上传代码目录](/images/hexo迁移/git上传目录.png)
**注意**：.gitignore和package.json文件内容如下
## .gitignore
```
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
```
## package.json
``` json
{
  "name": "hexo-site",
  "version": "0.0.0",
  "private": true,
  "hexo": {
    "version": "3.6.0"
  },
  "dependencies": {
    "hexo": "^3.6.0",
    "hexo-deployer-git": "^0.3.1",
    "hexo-generator-archive": "^0.1.4",
    "hexo-generator-category": "^0.1.3",
    "hexo-generator-index": "^0.2.0",
    "hexo-generator-searchdb": "^1.0.8",
    "hexo-generator-tag": "^0.2.0",
    "hexo-renderer-ejs": "^0.3.0",
    "hexo-renderer-marked": "^0.3.0",
    "hexo-renderer-stylus": "^0.3.1",
    "hexo-server": "^0.2.0"
  }
}
```
# 向github中添加ssh key
参照 [hexo搭建个人博客——搭建](https://shuangmianxiaoq.github.io/2018/03/17/hexo%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2%E2%80%94%E2%80%94%E6%90%AD%E5%BB%BA/) 中如何添加`ssh key`到`github`
# 代码下载
从github下载hexo项目核心代码到本地仓库
```
git clone https://github.com/shuangmianxiaoQ/myblog.git
```
# 安装依赖
```
npm i
```
# 测试并部署
```
hexo clean
hexo g
hexo s
hexo d
```

------