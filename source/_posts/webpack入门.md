---
title: webpack入门
date: 2018-07-11 21:15:54
tags:
---

------
# webpack简介
## 什么是webpack
webpack是一个**模块打包**的工具，可以根据你的项目结构，找到JavaScript模块和一些不能直接在浏览器运行的语言（如Less，Scss，TypeScript等），并将其转换和打包成浏览器所能识别的格式。
## 为什么使用webpack
- **模块化**
- 类似TypeScript，JSX的这些语言转换为浏览器可以识别的语言
- Scss，Less等css预处理器
- 打包压缩代码，图片等资源

## webpack的特性
Gulp/Grunt是一种能够优化前端开发的工具，而webpack是一种模块化的解决方案，大部分场景下可替代Gulp/Grunt。
webpack的处理速度也更快更直接，能打包更多的文件类型。
# webpack的使用
## 安装
```
// 初始化项目，并创建package.json
npm init -y
// 安装webpack
npm install --save-dev webpack
```

------