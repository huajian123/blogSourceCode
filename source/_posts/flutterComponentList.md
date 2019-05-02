---
title: 【Flutter】List组件
date: 2019-05-02 16:54:39
categories: 
- Flutter
tags:
- Flutter
---

### 基本使用
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
          body: new ListView(
            children: <Widget>[
              new ListTile(
                leading: new Icon(Icons.filter_vintage),
                title: new Text('filter_vintage'),
              ),
              new ListTile(
                leading: new Icon(Icons.ac_unit),
                title: new Text('ac_unit'),
              ),
              new ListTile(
                leading: new Icon(Icons.accessibility_new),
                title: new Text('accessibility_new'),
              ),
              new Image.network(
                  'http://pic37.nipic.com/20140113/8800276_184927469000_2.png'),
              new Image.network(
                  'http://pic37.nipic.com/20140113/8800276_184927469000_2.png')
            ],
          )),
    );
  }
}
```


### 横向列表以及组件拆分
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
            width: 200.0,
            height: 200.0,
            child: MyList(),
          ),
        ),
      ),
    );
  }
}

class MyList extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return new ListView( scrollDirection: Axis.horizontal, //横向,竖向是vertical
      children: <Widget>[
        new Container(
          width: 180.0,
          color: Colors.blue,
        ),
        new Container(
          width: 180.0,
          color: Colors.pink,
        ),
        new Container(
          width: 180.0,
          color: Colors.cyanAccent,
        ),
        new Container(
          width: 180.0,
          color: Colors.blue,
        )
      ],
    );
  }
}
```

### 动态加载列表
```
import 'package:flutter/material.dart';

void main() =>
    //传递参数
    runApp(MyApp(
        items: new List<String>.generate(
            1000, (i)=>"item $i") //声明数组 List(),List<String>(),[1,2.3]
        ));

class MyApp extends StatelessWidget {
  final List<String> items;

  MyApp({Key key, @required this.items}) : super(key: key);

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
        body: new ListView.builder(
          itemCount: items.length,
          itemBuilder: (context, index) {
            return new ListTile(title: new Text('${items[index]}'));
          },//itemCount要生成多少条
        ),
      ),
    );
  }
}

```
### 网格列表写法一
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
        body:GridView.count(//网格列表
          padding: const EdgeInsets.all(20.0),
          crossAxisSpacing: 10.0,// 网格的距离
          crossAxisCount: 5,//一行显示多少咧
          children: <Widget>[
            const Text('huajianceshi'),
            const Text('huajianceshi'),
            const Text('huajianceshi'),
            const Text('huajianceshi'),
            const Text('huajianceshi'),
          ],

        )
      ),
    );
  }
}

```
### 网格列表写法二
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
        body:GridView(
          gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
            crossAxisCount: 4,//一行放几个
            mainAxisSpacing: 8.0,//纵轴之间的间距
            crossAxisSpacing:2.0,//横轴之间的间距
            childAspectRatio: 1.2,//宽度和高度的比例
          ),
          children: <Widget>[new Image.network("http://pic37.nipic.com/20140113/8800276_184927469000_2.png",fit: BoxFit.cover,),
        new Image.network("http://pic37.nipic.com/20140113/8800276_184927469000_2.png",fit: BoxFit.cover,),
        new Image.network("http://pic37.nipic.com/20140113/8800276_184927469000_2.png",fit: BoxFit.cover,),
        new Image.network("http://pic37.nipic.com/20140113/8800276_184927469000_2.png",fit: BoxFit.cover,),
        new Image.network("http://pic37.nipic.com/20140113/8800276_184927469000_2.png",fit: BoxFit.cover,),
      ],
        )
      ),
    );
  }
}


```

