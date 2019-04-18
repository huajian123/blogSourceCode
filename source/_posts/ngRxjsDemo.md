---
title: 【Rxjs】小例子收集
date: 2019-04-17 14:06:31
categories: 
- Angular
- Rxjs
tags:
- Angular
- Rxjs
---
### 时间每秒显示
```
  time = new Observable(observer => {
    setInterval(() => {
      observer.next(new Date().toString());
    }, 1000);
  });
  // 模板中
  {{ time | async }}
  ```
