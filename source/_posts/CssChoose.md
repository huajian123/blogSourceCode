---
title: 【CSS】选择符
date: 2019-04-20 21:38:23
tags: CSS
categories: CSS
---
### 子选择符
子选择符只选择一个元素的直接后代，也就是子选择符。
```
#nav>li
```
### 相邻选择符
```
h2+p
```
选择位于某个元素后面，并与该元素拥有共同父元素的元素。
### 一般同辈组合子
```
 h2 ~ p {
      color: red;
    }
```
选择h2后面所有的同辈的p元素
### 属性选择器
```
 p[name]{
      color: red;
    }
    
 p[name="aaa"]{
      color: red;
    }
```
选择所有有name属性的元素，也通过可以指定属性的值来选择
其他一些变通：
+ 匹配以某些字符串开头
```
 a[href^="http:"]
```
+ 匹配以某些字符串结尾
```
 img[src$=".jpg"]
```
+ 匹配包含某些字符的属性值
```
 a[href*="/about/"]
```
+ 匹配以空格分割的字符串中的属性值（比如rel属性的值）
```
 a[rel~=next]
```
+ 选择开头是指定值或指定值后连着一个短下划线
```
 a[lang|=en]
```
### 伪元素
+ :first=letter
文本第一个字符
+ :firlst-line
文本第一行
+ :before :after内容开头或末尾处假象的元素，适合用来插入小图标及版面装饰符号。
```
 p:before{
    content:'“';
    font-size:15em;
 }
```
### 注意
应该避免用伪元素插入对交互有实质影响的内容。

### 伪类
基于文档结构以外的情形来位页面添加样式，这时候就可以使用伪类。
```$xslt
   /*未问过的链接*/
    a:link{color:blue}
    /*访问过的链接*/
    a:visited{color:blue}
    /*链接在鼠标悬停及获取键盘焦点时*/
    a:hover,a:focus{color:blue}
    /*活动状态时*/
    a:active{color:blue}
```
### :target伪类
匹配的元素有一个ID属性，并且该属性的值出现在当前页面URL末尾的井号（#）后边。
如打开http://example.com/blog/1/#comment-3找到页面的标记为<article class="component" id="comment-3">...的评论
那么就可以匹配一下规则来高亮显示
```$xslt
   .comment:target{
    background-color:red
   }
```
### :not()选择符伪类
```$xslt
   .comment:target:not(.comment-downvoted){
    background-color:red
   }
```

### 结构化伪类
+  tr:nth-child(odd) 奇数odd,偶数even
+   tr:nth-child(3)
+   tr:nth-child(3n+4)
+   tr:nth-child(-n+3) 只会选择前三个元素
+   :nth-last-child伪类，表示从最后一个元素倒数
+   :first-child===:nth-child(1)
+   :last-child:nth-child(1) 选择最后一个子元素 
+   div：nth-of-type（n） 第n个类型是div的子元素
+   :only-child选择的是父元素中只有一个子元素，而且只有唯一的一个子元素。也就是说，匹配的元素的父元素中仅有一个子元素，而且是一个唯一的子元素。
```$xslt
  <div class="post">
    <p>我是一个段落</p>
    <p>我是一个段落</p>
  </div>
  <div class="post">
    <p>我是一个段落</p>
  </div>
  
  .post p {
    background: green;
    color: #fff;
    padding: 10px;
  }
  .post p:only-child {
    background: orange;
  }
```

### 表单伪类
```
<input type="text" name="aaa" required>
```
+ input:required{outline:2px solid red;}有requried的属性添加边框
+ input:optional{}为没有requried...
+ input[type='email']:invalid{} 
+ :read-only有readonly, :read-write没有readonly等
 
