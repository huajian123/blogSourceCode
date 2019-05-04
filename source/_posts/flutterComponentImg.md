---
title: 【Flutter】Img组件
date: 2019-05-02 11:56:21
categories: 
- Flutter
tags:
- Flutter
---
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
        body: Center(
          child: Container(
            child: new Image.network(
              'http://pic37.nipic.com/20140113/8800276_184927469000_2.png',
              fit: BoxFit.fitWidth,//BoxFit.contain,保持原图比例，fill容器填满,fitWidth横向要充满容器,cover可能拉伸可能不变形，图片充满容器,scaleDown保持原图片大小
              repeat: ImageRepeat.repeat,// 图片重复
            //  color: Colors.blueAccent,
             // colorBlendMode: BlendMode.darken,// 图片和颜色混合
            ), //asset目录中放的图片，file手机上，本地的图片，network网络图片
            width: 300.0,
            height: 200.0,
            color: Colors.blue,
          ),
        ),
      ),
    );
  }
}
```
### 引用项目中的图片
这样添加会在打包时添加到包体里面，增大安装包体积
+ 在项目根目录建立文件夹images,里面存放header.jpg
+ pubspec.yaml文件中 assets里面添加
```dart
  assets:
    - images/head.jpg
```
+ 添加代码
```dart
import 'package:flutter/material.dart';

void main()=>runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Container(
      child: Image.asset('images/head.jpg'),
    );
  }
}
```
