---
title: 【Angular】模板语法
date: 2019-04-11 14:16:07
categories: Angular
tags: Angular
---
## 安全导航操作符 ( ?. ) 和空属性路径
Angular 的安全导航操作符 (?.) 是一种流畅而便利的方式，用来保护出现在属性路径中 null 和 undefined 值。 下例中，当 currentHero 为空时，保护视图渲染器，让它免于失败。
``` bash
The current hero's name is {{currentHero?.name}}
```
还可以尝试通过 && 来把属性路径的各部分串起来，让它在遇到第一个空值的时候，就返回空。

``` bash
The null hero's name is {{nullHero && nullHero.name}}
```
但这样略显笨重
### 非空断言操作符（!）
默认开启严格空值检查的情况下，TypeScript为了确保有类型的变量是不允许null或undefined值，如果有未赋值的变量，或者试图把 null 或 undefined 赋值给不允许为空的变量，类型检查器就会抛出一个错误。
[TS中非空断言符](http://www.typescriptlang.org/docs/handbook/release-notes/typescript-2-0.html#non-null-assertion-operator)

Angular 模板中的非空断言操作符（!）也是同样的用途。
``` bash
<!--No hero, no text -->
<div *ngIf="hero">
  The hero's name is {{hero!.name}}
</div>
```
在 Angular 编译器把你的模板转换成 TypeScript 代码时，这个操作符会防止 TypeScript 报告 "hero.name 可能为 null 或 undefined"的错误。

与安全导航操作符不同的是，非空断言操作符不会防止出现 null 或 undefined。 它只是告诉 TypeScript 的类型检查器对特定的属性表达式，不做 "严格空值检测"。

### 类型转换函数$any
有时候，绑定表达式可能会报类型错误，并且它不能或很难指定类型。要消除这种报错，你可以使用 $any 转换函数来把表达式转换成 any 类型。
``` bash
<!-- Accessing an undeclared member -->
<div>
  The hero's marker is {{$any(hero).marker}}
</div>
```
在这个例子中，当 Angular 编译器把模板转换成 TypeScript 代码时，$any 表达式可以防止 TypeScript 编译器报错说 marker 不是 Hero 接口的成员。

$any 转换函数可以和 this 联合使用，以便访问组件中未声明过的成员。即可以跳过是否有某些成员属性的检查。
``` bash
<!-- Accessing an undeclared member -->
<div>
  Undeclared members is {{$any(this).member}}
</div>
```
$any 转换函数可以在绑定表达式中任何可以进行方法调用的地方使用。
