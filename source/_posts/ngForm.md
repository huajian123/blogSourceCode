---
title: 【Angular表单】
date: 2019-04-17 11:30:18
categories: 
- Angular
- Angular表单
- 小知识
tags:
- Angular
---

## 表单验证器执行时机
默认情况下，每当表单值变化之后，都会执行所有验证器。对于同步验证器，没有什么会显著影响应用性能的地方。不过，异步验证器通常会执行某种 HTTP 请求来对控件进行验证。如果在每次按键之后都发出 HTTP 请求会给后端 API 带来沉重的负担，应该尽量避免。

我们可以把 updateOn 属性从 change（默认值）改成 submit 或 blur 来推迟表单验证的更新时机。
对于模板驱动表单：
```
<input [(ngModel)]="name" [ngModelOptions]="{updateOn: 'blur'}">
```
对于响应式表单
```
new FormControl('', {updateOn: 'blur'});
```
