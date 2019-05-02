---
title: 【Flutter】Text组件
date: 2019-05-02 11:17:35
categories: 
- Flutter
tags:
- Flutter
---
### Text组件
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
          child: Text(
            "HELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLDHELLO WORLD",
            textAlign: TextAlign.left,// 文本位置
            maxLines: 2,
            overflow: TextOverflow.ellipsis,// fade值可以让文字下面有点隐藏的效果，ellipsis值是可以有省略号
            style: TextStyle(
              fontSize: 25.0,//必须设置浮点数
              color: Color.fromARGB(255, 255, 125, 125),
              decoration: TextDecoration.underline,//下划线
              decorationStyle: TextDecorationStyle.solid//实线
            ),
          ),
        ),
      ),
    );
  }
}

```

