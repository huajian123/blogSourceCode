---
title: 【Angular】管道
date: 2019-04-16 19:12:51
tags: 
- Angular 
categories: 
- Angular
---
---
## 日期
``` bash
{{ birthday | date:"yyyy-MM-dd HH:mm:ss" }}
```
## 链式管道
``` bash
{{  birthday | date:'fullDate' | uppercase}}
```
