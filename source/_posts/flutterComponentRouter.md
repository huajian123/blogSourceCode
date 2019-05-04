---
title: 【Flutter】路由
date: 2019-05-03 20:26:29
categories: 
- Flutter
tags:
- Flutter
---
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(
    title: "导航",
    home: new FirstPage(),
  ));
}

class FirstPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    // TODO: implement build
    return Scaffold(
      appBar: AppBar(
        title: Text('导航'),
      ),
      body: Center(
        child: RaisedButton(
          child: Text('查看商品详情'),
          onPressed: () {
            Navigator.push(context,
                MaterialPageRoute(builder: (context) => new SecondPage()));
          },
        ),
      ),
    );
  }
}

class SecondPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('详情页面'),),
      body: Center(
        child: RaisedButton(onPressed: () {
          Navigator.pop(context);
        },
          child: Text('返回'),),
      ),
    );
    return null;
  }
}

```

### 路由传参
```dart
import 'package:flutter/material.dart';

class Product {
  final String title;
  final String description;

  Product(this.title, this.description);
}

void main() {
  runApp(MaterialApp(
    title: '导航数据参数和接收',
    home: ProductList(
        products: List.generate(20, (i) => Product('商品$i', '商品详情，编号 为$i'))),
  ));
}

class ProductList extends StatelessWidget {
  final List<Product> products;

  ProductList({Key key, @required this.products}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('商品列表'),
      ),
      body: ListView.builder(
        itemBuilder: (context, index) {
          return ListTile(
            title: Text(products[index].title),
            onTap: () {
              Navigator.push(
                  context,
                  MaterialPageRoute(
                      builder: (context) => ProductDetail(product: products[index])));
            },
          );
        },
        itemCount: products.length,
      ),
    );
  }
}

class ProductDetail extends StatelessWidget {
  final Product product;

  ProductDetail({Key key, @required this.product}) :super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('${product.title}'),),
      body: Center(child: Text('${product.description}'),),
    );
  }
}

```
### 路由传参数据返回
```dart
import 'package:flutter/material.dart';


void main() {
  runApp(MaterialApp(
      title: '导航数据参数和接收',
      home: FirstPage()
  ));
}

class FirstPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('测试路由传参带回'),),
      body: Center(
        child: RouteButton(),
      ),
    );
  }
}

class RouteButton extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return RaisedButton(
      onPressed: () {_navigateToNewPage(context);},
      child: Text('详情页面'),

    );
  }

  _navigateToNewPage(BuildContext context) async{
    final result = await Navigator.push(context, MaterialPageRoute(builder: (context) => NewPage()));

    Scaffold.of(context).showSnackBar(SnackBar(content: Text('$result')));
  }
}

class NewPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('新页面'),
      ),
      body: Center(
        child: Column(
          children: <Widget>[
            RaisedButton(
              child: Text('数据1'),
              onPressed: (){
                Navigator.pop(context,'数据1');
              },
            ),
            RaisedButton(
              child: Text('数据2'),
              onPressed: (){
                Navigator.pop(context,'数据2');
              },
            )
          ],
        ),
      ),
    );
  }
}

```
