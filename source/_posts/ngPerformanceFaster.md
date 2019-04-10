---
title: 【Angular】性能优化
date: 2019-04-07 16:21:02
categories: Angular
tags: Angular
---
## 注册服务
在根一级提供服务，Angular会创建一个单一，共享的实例，并且
在 @Injectable 元数据中注册提供商的方式还让 Angular 能够通过移除那些从未被用过的服务来优化大小。
``` bash
@Injectable({
  providedIn: 'root',
})
```
## 模版表达式应该快速结束
Angular在每个变更检测周期结束后执行
模版表达式。变更检测周期会被多种异步活动触发，如Promise解析，Http返回结果，
定时器时间，按键或鼠标移动等。
所以模版表达式应该快速结束。
