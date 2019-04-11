---
title: 【Angular】变更检测策略
date: 2019-04-11 19:32:14
tags: Angular
categories: Angular
---
## 变更检测
当导致绑定的值发生改变的事件都是异步发生的，那么这些异步发生的事件就会通知Angular,那么他就会检测到变化。
有如下几种情况：
+ 用户输入操作，如点击，提交等
+ 请求服务端数据（XHR）
+ 定时事件，setTimeout,setInterval

### 小栗子
``` bash
<input #box (keyup)="0">
<p>{{box.value}}</p>
```
在这个简单的模板中，使用(keyup)，做了异步事件，Angular才更新了绑定。虽然绑定到了0身上，但是满足了Angular变更检测的要求。



[相关文章](https://juejin.im/post/5b0a6d686fb9a07acb3d54aa)
