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
