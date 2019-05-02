---
title: 【Flutter】Container组件
date: 2019-05-02 11:37:07
categories: 
- Flutter
tags:
- Flutter
---
```
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
        body: Center(
        child: Container(
          child: new Text("华舰来搞一搞",style: TextStyle(fontSize: 40.0),),
          alignment:Alignment.topLeft ,//container里面子内容的对齐方式,
          width: 500.0,
          height: 400.0,
          // color: Colors.pink,
          padding: const EdgeInsets.all(40.0),// 边距，如果设置具体某个边距const EdgeInsets.fromLTRB(40.0,30.0,34.0,34.0)
          margin: const EdgeInsets.all(10.0),
          decoration:new BoxDecoration(//线性渐变
            gradient: const LinearGradient(colors: [Colors.pink,Colors.amberAccent]),
            border: Border.all(width: 2.0,color: Colors.red)//边框
          ) ,
        ),
        ),
      ),
    );
  }
}


```
