---
title: 前端框架基础总结——angular
date: 2018-03-13 23:05:54
tags:
---

------

# 概述
## 官网
中文：[Angular中文网](https://angular.cn/)
英文：[Angular官网](https://angular.io/)
## What
`angular`是`Google`推出的一个`JS`框架。
## When
主要实现`SPA`，用在数据操作比较频繁的场景；实现大而全的平台，能实现移动端和桌面端的开发。
## How
如何开发搭建环境？（基于`CLI`）
1. 官方推荐：`Angular CLI`是一个命令行界面工具，它可以创建项目、添加文件以及执行一大堆开发任务，比如测试、打包和发布。
``` javascript
// ①安装node.js
// ②通过npm安装 angular cli
npm install -g @angular/cli
// ③通过安装的cli去创建一个项目
ng new my-app
// ④启动开发服务器
cd my-app
ng serve --open
```
2. 借助`angular`提供的`quickstart`项目（[Angular QuickStart](https://github.com/angular/quickstart)）
``` javascript
// ①下载`quickstart`项目
// ②解压缩，安装该项目依赖的所有的资源文件
npm install
// ③启动开发服务器：
npm start
```
# 基础知识
## 组件的创建和使用
### 创建
```
在app目录下创建`***.component.ts`的文件
在该文件中，通过 @Component 装饰当前的类为一个组件类，然后通过export导出该类
```
### 使用
```
①到模块中声明
import {***Component} from '***';
在 @ngModule 装饰器中的 declaration 数组中，添加 ***Component

②使用组件
像使用html标签一样去使用（ @Component 装饰器中 selector 的名字）
```
## angular常见指令
###  循环指令
``` javascript
// 遍历集合（数组、对象）中的每一个元素，并根据元素个数来创建多个标签
<any *ngFor="let tmp of list"></any>
<any *ngFor="let tmp of list; let idx = index"></any>
```
###  选择指令
``` javascript
// 根据表达式执行结果的真假，来决定是否要将该元素挂载到DOM树上
<any *ngIf="expression"></any>
```
### 多重选择指令
``` javascript
// 根据多重判断来选择将哪个元素挂载到DOM树上
<div [ngSwitch]="answer">
	<p *ngSwitchCase="a">A</p>
	<p *ngSwitchCase="b">B</p>
	<p *ngSwitchDefault>其他</p>
</div>
```
### 事件绑定（圆括号）
``` javascript
<any (eventName)="处理事件函数"></any>
```
### 属性绑定（中括号）
``` javascript
<any [attr]="变量"></any>
// 借助 ngStyle 来实现样式的动态修改
<any [ngStyle]="color: colorExp"></any>
// 借助 ngClass 来实现样式类的动态绑定
<any [ngClass]="{customColor: true}"></any>
```
**扩展**：如何给一个组件指定`css`文件？
``` javascript
@Component({
	templateUrl: '',
	styleUrls: ['test.css', './test2.css']
})
```
### 插值表达式
``` javascript
// 叫法：双花括号、插值表达式、mustache、interpolation
// 作用：将表达式执行的结果输出到当前元素的innerHTML 中
<any>{{}}</any>
```
### 双向数据绑定
``` javascript
// ngModel 指令，属于 FormsModule （表单模块）
// ①在 app.module.ts 中引入 FormsModule 模块
import { FormsModule } from 'angular/froms';
// ②在 app.module.ts 中，通过 imports 数组来指定当前模块需要依赖的其他模块
@NgModule({
	import: [ FormsModule ]
})
// ③使用双向数据绑定指令
<input type="text" ([ngModule])="变量" (ngModelChange)="监听事件($event)" />
```
**注意**：通过绑定`ngModelChange`事件来监听用户的操作结果。
## angular路由模块
**作用**：建立起`url`和组件之间的关系
### 实现SPA的基本步骤
``` javascript
	// ①在 app 目录下创建 app.router.ts 的自定义模块
	// 指定依赖于 Routes、RouterModule 模块
	import { Routes, RouterModule } from '@angular/router';
	
	import { NameComponent } from './name.component';
	
	const routes: Routes = [
	  { path: 'path', component: NameComponent },
	];
	
	@NgModule({
	  imports: [RouterModule.forChild(routes)],
	  exports: [RouterModule],
	})
	export class NameRoutingModule { }
```
### 路由跳转
### 传参
### 路由嵌套
