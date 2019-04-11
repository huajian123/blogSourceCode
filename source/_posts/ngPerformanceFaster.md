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

## 隐藏元素
``` bash
<!-- isSpecial is true -->
<div [class.hidden]="!isSpecial">Show with class</div>
<div [class.hidden]="isSpecial">Hide with class</div>

<!-- HeroDetail is in the DOM but hidden -->
<app-hero-detail [class.hidden]="isSpecial"></app-hero-detail>

<div [style.display]="isSpecial ? 'block' : 'none'">Show with style</div>
<div [style.display]="isSpecial ? 'none'  : 'block'">Hide with style</div>
```
如果通过以上代码来隐藏元素，子树中的组件及其状态仍然保留着。
即使对于不可见属性，Angular也会继续变更检测。子树可能占有相当可观的内存和运算资源。
应该使用ngIf来代替

## *ngFor
ngFor有时候性能较差，特别是在大型列表中。 对一个条目的一丁点改动、移除或添加，都会导致级联的 DOM 操作。

我们应该使用trackBy，往组件中添加一个方法，它会返回 NgFor应该追踪的值
``` bash
// ts中
trackByHeroes(index: number, hero: Hero): number { return hero.id; }

//html中
<div *ngFor="let hero of heroes; trackBy: trackByHeroes">
  ({{hero.id}}) {{hero.name}}
</div>
```
如果没有 trackBy，这些列在改变引用时都会触发完全的 DOM 元素替换。

有了 trackBy，则只有修改了 id 的列才会触发元素替换
