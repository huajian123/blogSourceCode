---
title: ngSpecialClass
date: 2019-04-15 23:15:24
categories: 
- Angular
tags:
- Angular
---
## 特殊的类
### 指令中
用来获取对容器视图的访问权。
``` bash
import { Directive, ViewContainerRef } from '@angular/core';

@Directive({
  selector: '[ad-host]',
})
export class AdDirective {
  constructor(public viewContainerRef: ViewContainerRef) { }
}
```
