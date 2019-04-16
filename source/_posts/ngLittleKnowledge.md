---
title: 【Angular小知识】事件
date: 2019-04-15 09:19:04
tags: 
- Angular 
- Angular小知识
categories: 
- Angular
- Angular小知识
---
## 使用get和set截听输入属性的变化
typescript中存取器写法
``` bash
class Person {
    constructor() {
    }
    private _name: string;

    public get name() {
        return this._name;
    }

    public set name(name: string) {
        this._name = name;
    }
}
let person = new Person();
// person._name = "apple";  // 无法访问到_name变量
person.name = "apple";
console.log(person.name);  // 输出 apple

```
Angular中写法
``` bash
@Component({
  selector: 'app-name-child',
  template: '<h3>"{{name}}"</h3>'
})
export class NameChildComponent {
  private _name = '';
 
  @Input()
  set name(name: string) {
    this._name = (name && name.trim()) || '<no name set>';
  }
 
  get name(): string { return this._name; }
}
```
在这里会将输入属性的name,trim调空格，并且把空值替换成默认字符串。

