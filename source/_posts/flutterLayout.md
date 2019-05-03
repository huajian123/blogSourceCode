---
title: 【Flutter】布局
date: 2019-05-03 00:00:34
categories: 
- Flutter
tags:
- Flutter
---
### 水平布局
```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    // 传入上下文
    return MaterialApp(
      title: "小华试试Flutter",
      home: Scaffold(
          // Scffold组件表示搭建内容
          appBar: AppBar(
            title: Text("小华试水Flutter"),
          ),
          body: new Row(
            children: <Widget>[
              new RaisedButton(
                onPressed: () {},
                color: Colors.red,
                child: new Text('Button'),
              ),
              Expanded(child: new RaisedButton(//Expanded组件用来平均分配水平距离
                onPressed: () {},
                color: Colors.yellow,
                child: new Text('Button'),
              ),),
              new RaisedButton(
                onPressed: () {},
                color: Colors.green,
                child: new Text('Button'),
              ),
            ],
          )),
    );
  }
}

```
### 垂直布局
```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    // 传入上下文
    return MaterialApp(
      title: "小华试试Flutter",
      home: Scaffold(
          // Scffold组件表示搭建内容
          appBar: AppBar(
            title: Text("小华试水Flutter"),
          ),
          body: Center(//表示整体居中
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.center,//对齐属性，相对于Column居中，也是相对于所有文字的Column的居中
              mainAxisAlignment: MainAxisAlignment.center,//主轴设置对齐方式，这里是设置的Column，则主轴为垂直方向
              children: <Widget>[
                Text("I am huajian"),
                Expanded(child: Text("ceshi"),),//这里使用Expanded使用灵活的布局方式
                Text("dibu"),
              ],
            ),
          ) ),
    );
  }
}

```
### 层叠布局(头像)
```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    var stack = new Stack(
      alignment: const FractionalOffset(0.5, 0.8),//层叠属性，给的值是x值和y值，最小是0，最大是1
      children: <Widget>[
        new CircleAvatar( //相当于圆形头像
          backgroundImage: new NetworkImage(
              'http://pic37.nipic.com/20140113/8800276_184927469000_2.png'),
          radius: 100.0,
        ),
        new Container(
          decoration: new BoxDecoration(
              color: Colors.green
          ),
          padding: EdgeInsets.all(5.0),
          child: Text("小华测试"),
        ),
      ],
    );


    // 传入上下文
    return MaterialApp(
      title: "小华试试Flutter",
      home: Scaffold(
        // Scffold组件表示搭建内容
          appBar: AppBar(
            title: Text("小华试水Flutter"),
          ),
          body:Center(
            child: stack,
          )
      ),
    );
  }
}

```
### 类似于绝对定位组件(Positioned)
```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    var stack = new Stack(
      alignment: const FractionalOffset(0.5, 0.8), //层叠属性，给的值是x值和y值，最小是0，最大是1
      children: <Widget>[
        new CircleAvatar(
          //相当于圆形头像
          backgroundImage: new NetworkImage(
              'http://pic37.nipic.com/20140113/8800276_184927469000_2.png'),
          radius: 100.0,
        ),
        new Positioned(
          top: 10.0,
          left: 10.0,
          child: new Text('ceshi2'),
        ),
        new Positioned(
          top: 20.0,
          left: 10.0,
          child: new Text('ceshi3'),
        ),
        new Positioned(
          top: 10.0,
          left: 10.0,
          child: new Text('ceshi4'),
        ),
      ],
    );

    // 传入上下文
    return MaterialApp(
      title: "小华试试Flutter",
      home: Scaffold(
          // Scffold组件表示搭建内容
          appBar: AppBar(
            title: Text("小华试水Flutter"),
          ),
          body: Center(
            child: stack,
          )),
    );
  }
}


```
### 卡牌布局
```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    var card = new Card(//卡牌组件
      child: Column(//垂直布局组件
        children: <Widget>[
          ListTile(
            title: Text('江苏南京孝陵卫',style: TextStyle(fontWeight: FontWeight.w500),),
            subtitle: Text('花间：15151515151'),//副标题
            leading:new Icon(Icons.account_box,color: Colors.lightBlue,) ,
          ),
          new Divider(),//分割线
          ListTile(
            title: Text('江苏南京孝陵卫',style: TextStyle(fontWeight: FontWeight.w500),),
            subtitle: Text('花间：15151515151'),//副标题
            leading:new Icon(Icons.account_box,color: Colors.lightBlue,) ,
          ),
          new Divider(),//分割线
          ListTile(
            title: Text('江苏南京孝陵卫',style: TextStyle(fontWeight: FontWeight.w500),),
            subtitle: Text('花间：15151515151'),//副标题
            leading:new Icon(Icons.account_box,color: Colors.lightBlue,) ,
          ),
        ],
      ),
    );

    // 传入上下文
    return MaterialApp(
      title: "小华试试Flutter",
      home: Scaffold(
          // Scffold组件表示搭建内容
          appBar: AppBar(
            title: Text("小华试水Flutter"),
          ),
          body: Center(
            child: card,
          )),
    );
  }
}
```
