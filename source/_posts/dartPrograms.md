---
title: 【Dart】语法
date: 2019-05-02 10:22:28
categories: 
- Flutter
- Dart
tags:
- Flutter
- Dart
---
### 函数
```
void main() => runApp()

```
### b??=23
表示b为空的话，将23赋值给b

### ?
```dart
// a如果为空，则不取他的属性b
a?.b
```
### is
判断类型
```dart
Person p=new Person()
if(p is Person){
  
}
```
### as
断言
```dart
var p1;
p1="";
p1=new Person();
(p1 as Person).say();

```

### ..级联操作符
```dart
Person p=new Person("name",13);
p1.name='aaa';
p1.age=55;
p1.say();

//可以写成
p1..name='aa'
  ..age=30
  ..say();
```

### ??运算符
```dart
var a;
var b=a??10;
// 如果a为空，则赋10
```
### 字符串isEmpty方法
```dart
var str="xxx";
if(str.isEmpty){}
```

### list,map,set
```dart
// 属性
List list=['a','b'];
print(list.length);
print(list.isEmpty);
print(list.isNotEmpty);
print(list.reversed.toList());

//方法
list.add('c');
list.addAll(['d','e']);// 拼接数组
list.indexOf('a');
list.remove('e');//直接删除就行
list.removeAt(1);

//修改
// list=['d','e','f']
list.fillRange(1,2,'ddd');
// print(list) list=['d','ddd','f']

list.insert(1,'aaa');
list.insertAll(1,['aaa','bbb'])

list.join(',');


// map
Map person={
  "name":"aaa",
  "age":'1234'
};
print(person.keys.toList());
print(person.values.toList());
print(person.isEmpty);
print(person.isNotEmpty);

person.forEach((key,value){
  
})

person.addAll({
  "work":['bbb',"ccc"],
  "height":'123'
})

person.remove('height');

//判断value里面是否有123
person.containsValue('123');

// 循环
for(var item in list){
  
}

list.forEach((value){
  
});

// 类似于filter的方法
list.where((value){
  return value>5;
})

// 类似于some
list.any((value){
  return value>5;
})

//类似于every
list.every((value){
  return value>5;
})

```
### 函数
```dart
// 可选参数,
String aaa(String username,[int age]){
  
}

// 默认参数
String aaa(String username,[int age=123]){
  
}

// 命名参数
String aaa(String username,{int age,String sex='男'}){
  
}
aaa('huajian',age:20,sex:'nv');

// 匿名方法
var print=(int n){
  
}

// 自执行方法
((int n){
  print(n);
})(12)

// 递归
var sum=1;
fn(n){
  sum*=n;
  if(n==1{
    return;
  })
  fn(n-1);
}
fn(5);

// 闭包
fn(){
  var a =1;
  return (){
    print(a);
    return a;
  }
}
var b=fn();
b();


```
### 类
```dart
class Person{
  String _names;// 私有属性，只有这个类在别的文件才能私有
  String name;
  int age;
  int score;
  
  //简写，直接将声明的字段赋值给这个类中
  Person(this.name,this.age,this.score);
  
  // 在构造函数运行之前初始化变量
  Person():age=2,score=3;
  
  get scores{
    return this.score;  
  }
  
  set setAge(value){
    this.age=value;
  }
  
  String getName(){
    return this._names;
  }
  
  
  // 命名构造函数
  Person.now(){
    
  }
}

var person=new Person('a',12);
var person1=new Person.now();
print(person1.scores);
person1.setAge=7;

```

### 静态类
```dart
// 静态方法不能访问非静态成员，非静态方法可以访问静态成员
Class Person{
  static String name='张三';
  static void show(){
    print(name);
  }
}
Person.name
Person.show()

```
### 继承

```dart
 Class Person{
  String name;
  num age;
  Person(this.name,this.age);
  void say(){
    
  }
 }
 
 Class Teacher extends Person{
  String sex;
  Teacher( String name,num age,String sex):supper(name,age){
    this.sex=sex;
  }
  
  //子类调用父类的方法
  // super.say()
  
  @override //重写父类方法
  say(){
    
  }
 }

```
### 抽象类

```dart
/*
Dart中抽象类: Dart抽象类主要用于定义标准，子类可以继承抽象类，也可以实现抽象类接口。


  1、抽象类通过abstract 关键字来定义

  2、Dart中的抽象方法不能用abstract声明，Dart中没有方法体的方法我们称为抽象方法。

  3、如果子类继承抽象类必须得实现里面的抽象方法

  4、如果把抽象类当做接口实现的话必须得实现抽象类里面定义的所有属性和方法。

  5、抽象类不能被实例化，只有继承它的子类可以

extends抽象类 和 implements的区别：

  1、如果要复用抽象类里面的方法，并且要用抽象方法约束自类的话我们就用extends继承抽象类

  2、如果只是把抽象类当做标准的话我们就用implements实现抽象类



案例：定义一个Animal 类要求它的子类必须包含eat方法

*/

abstract class Animal{
  eat();   //抽象方法
  run();  //抽象方法  
  printInfo(){
    print('我是一个抽象类里面的普通方法');
  }
}

class Dog extends Animal{
  @override
  eat() {
     print('小狗在吃骨头');
  }

  @override
  run() {
    // TODO: implement run
    print('小狗在跑');
  }  
}
class Cat extends Animal{
  @override
  eat() {
    // TODO: implement eat
    print('小猫在吃老鼠');
  }

  @override
  run() {
    // TODO: implement run
    print('小猫在跑');
  }

}

main(){

  Dog d=new Dog();
  d.eat();
  d.printInfo();

   Cat c=new Cat();
  c.eat();

  c.printInfo();


  // Animal a=new Animal();   //抽象类没法直接被实例化

}
```
### 多态
子类实例赋值给父类的引用
```dart
/*
Datr中的多态：
    允许将子类类型的指针赋值给父类类型的指针, 同一个函数调用会有不同的执行效果 。

    子类的实例赋值给父类的引用。
    
    多态就是父类定义一个方法不去实现，让继承他的子类去实现，每个子类有不同的表现。

*/


abstract class Animal{
  eat();   //抽象方法 
}

class Dog extends Animal{
  @override
  eat() {
     print('小狗在吃骨头');
  }
  run(){
    print('run');
  }
}
class Cat extends Animal{
  @override
  eat() {   
    print('小猫在吃老鼠');
  }
  run(){
    print('run');
  }
}

main(){

  // Dog d=new Dog();
  // d.eat();
  // d.run();


  // Cat c=new Cat();
  // c.eat();


  Animal d=new Dog();

  d.eat();

  Animal c=new Cat();

  c.eat();
}

```
### 接口
```dart
/*
和Java一样，dart也有接口，但是和Java还是有区别的。

  首先，dart的接口没有interface关键字定义接口，而是普通类或抽象类都可以作为接口被实现。

  同样使用implements关键字进行实现。

  但是dart的接口有点奇怪，如果实现的类是普通类，会将普通类和抽象中的属性的方法全部需要覆写一遍。
  
  而因为抽象类可以定义抽象方法，普通类不可以，所以一般如果要实现像Java接口那样的方式，一般会使用抽象类。

  建议使用抽象类定义接口。

*/

/*
定义一个DB库 支持 mysql  mssql  mongodb

mysql  mssql  mongodb三个类里面都有同样的方法

*/


abstract class Db{   //当做接口   接口：就是约定 、规范
    String uri;      //数据库的链接地址
    add(String data);
    save();
    delete();
}

class Mysql implements Db{
  
  @override
  String uri;

  Mysql(this.uri);

  @override
  add(data) {
    // TODO: implement add
    print('这是mysql的add方法'+data);
  }

  @override
  delete() {
    // TODO: implement delete
    return null;
  }

  @override
  save() {
    // TODO: implement save
    return null;
  }

  remove(){
      
  }

  
}

class MsSql implements Db{
  @override
  String uri;
  @override
  add(String data) {
    print('这是mssql的add方法'+data);
  }

  @override
  delete() {
    // TODO: implement delete
    return null;
  }

  @override
  save() {
    // TODO: implement save
    return null;
  }


}

main() {

  Mysql mysql=new Mysql('xxxxxx');

  mysql.add('1243214');
  
}

```
### 一个类实现多个接口
```dart
/*
Dart中一个类实现多个接口：
*/

abstract class A{
  String name;
  printA();
}

abstract class B{
  printB();
}

class C implements A,B{  
  @override
  String name;  
  @override
  printA() {
    print('printA');
  }
  @override
  printB() {
    // TODO: implement printB
    return null;
  }
}


void main(){
  C c=new C();
  c.printA();
}

```

### 类混入
```dart
/*
mixins的中文意思是混入，就是在类中混入其他功能。

在Dart中可以使用mixins实现类似多继承的功能


因为mixins使用的条件，随着Dart版本一直在变，这里讲的是Dart2.x中使用mixins的条件：

  1、作为mixins的类只能继承自Object，不能继承其他类
  2、作为mixins的类不能有构造函数
  3、一个类可以mixins多个mixins类
  4、mixins绝不是继承，也不是接口，而是一种全新的特性
*/

class Person{
  String name;
  num age;
  Person(this.name,this.age);
  printInfo(){
    print('${this.name}----${this.age}');
  }
  void run(){
    print("Person Run");
  }
}

class A {
  String info="this is A";
  void printA(){
    print("A");
  }
  void run(){
    print("A Run");
  }
}

class B {  
  void printB(){
    print("B");
  }
  void run(){
    print("B Run");
  }
}

class C extends Person with B,A{
  C(String name, num age) : super(name, age);
  
}

void main(){  
  var c=new C('张三',20);  
  c.printInfo();
  // c.printB();
  // print(c.info);

   c.run();
}

```
### 泛型方法
```dart
/*

通俗理解：泛型就是解决 类 接口 方法的复用性、以及对不特定数据类型的支持(类型校验)

*/


//只能返回string类型的数据

  // String getData(String value){
  //     return value;
  // }
  

//同时支持返回 string类型 和int类型  （代码冗余）


  // String getData1(String value){
  //     return value;
  // }

  // int getData2(int value){
  //     return value;
  // }

//同时返回 string类型 和number类型       不指定类型可以解决这个问题


  // getData(value){
  //     return value;
  // }

//不指定类型放弃了类型检查。我们现在想实现的是传入什么 返回什么。比如:传入number 类型必须返回number类型  传入 string类型必须返回string类型
 
  // T getData<T>(T value){
  //     return value;
  // }

  getData<T>(T value){
      return value;
  }

void main(){

    // print(getData(21));

    // print(getData('xxx'));

    // getData<String>('你好');

    print(getData<int>(12));

}

```
### 泛型类
```dart
//集合List 泛型类的用法



//案例：把下面类转换成泛型类，要求List里面可以增加int类型的数据，也可以增加String类型的数据。但是每次调用增加的类型要统一


//  class PrintClass{
//       List list=new List<int>();
//       void add(int value){
//           this.list.add(value);
//       }
//       void printInfo(){          
//           for(var i=0;i<this.list.length;i++){
//             print(this.list[i]);
//           }
//       }
//  }

//  PrintClass p=new PrintClass();
//     p.add(1);
//     p.add(12);
//     p.add(5);
//     p.printInfo();




 class PrintClass<T>{
      List list=new List<T>();
      void add(T value){
          this.list.add(value);
      }
      void printInfo(){          
          for(var i=0;i<this.list.length;i++){
            print(this.list[i]);
          }
      }
 }



main() {  
    // PrintClass p=new PrintClass();
    // p.add(11);
    // p.add('xxx');
    // p.add(5);
    // p.printInfo();



  // PrintClass p=new PrintClass<String>();

  // p.add('你好');

  //  p.add('哈哈');

  // p.printInfo();




  PrintClass p=new PrintClass<int>();

  p.add(12);

   p.add(23);

  p.printInfo();


 
  // List list=new List();
  // list.add(12);
  // list.add("你好");
  // print(list);



  // List list=new List<String>();

  // // list.add(12);  //错误的写法

  // list.add('你好');
  // list.add('你好1');

  // print(list);





  // List list=new List<int>();

  // // list.add("你好");  //错误写法
  // list.add(12); 

  // print(list);
}

```
### 泛型接口
```dart
/*
Dart中的泛型接口:

    实现数据缓存的功能：有文件缓存、和内存缓存。内存缓存和文件缓存按照接口约束实现。

    1、定义一个泛型接口 约束实现它的子类必须有getByKey(key) 和 setByKey(key,value)

    2、要求setByKey的时候的value的类型和实例化子类的时候指定的类型一致


*/


  // abstract class ObjectCache {
  //   getByKey(String key);
  //   void setByKey(String key, Object value);
  // }

  // abstract class StringCache {
  //   getByKey(String key);
  //   void setByKey(String key, String value);
  // }


  // abstract class Cache<T> {
  //   getByKey(String key);
  //   void setByKey(String key, T value);
  // }


abstract class Cache<T>{
  getByKey(String key);
  void setByKey(String key, T value);
}

class FlieCache<T> implements Cache<T>{
  @override
  getByKey(String key) {    
    return null;
  }

  @override
  void setByKey(String key, T value) {
   print("我是文件缓存 把key=${key}  value=${value}的数据写入到了文件中");
  }
}

class MemoryCache<T> implements Cache<T>{
  @override
  getByKey(String key) {   
    return null;
  }

  @override
  void setByKey(String key, T value) {
       print("我是内存缓存 把key=${key}  value=${value} -写入到了内存中");
  }
}
void main(){


    // MemoryCache m=new MemoryCache<String>();

    //  m.setByKey('index', '首页数据');


     MemoryCache m=new MemoryCache<Map>();

     m.setByKey('index', {"name":"张三","age":20});
}
```
### 库名冲突
```dart
/*
1、冲突解决
当引入两个库中有相同名称标识符的时候，如果是java通常我们通过写上完整的包名路径来指定使用的具体标识符，甚至不用import都可以，但是Dart里面是必须import的。当冲突的时候，可以使用as关键字来指定库的前缀。如下例子所示：

    import 'package:lib1/lib1.dart';
    import 'package:lib2/lib2.dart' as lib2;


    Element element1 = new Element();           // Uses Element from lib1.
    lib2.Element element2 = new lib2.Element(); // Uses Element from lib2.

*/

import 'lib/Person1.dart';
import 'lib/Person2.dart' as lib;

main(List<String> args) {
  Person p1=new Person('张三', 20);
  p1.printInfo();


  lib.Person p2=new lib.Person('李四', 20);

  p2.printInfo();

}
```
### 库管理
```dart
/*
pub包管理系统:


1、从下面网址找到要用的库
        https://pub.dev/packages
        https://pub.flutter-io.cn/packages
        https://pub.dartlang.org/flutter/

2、创建一个pubspec.yaml文件，内容如下

    name: xxx
    description: A new flutter module project.
    dependencies:  
        http: ^0.12.0+2
        date_format: ^1.0.6

3、配置dependencies

4、运行pub get 获取远程库

5、看文档引入库使用
*/
import 'dart:convert' as convert;
import 'package:http/http.dart' as http;
import 'package:date_format/date_format.dart';

main() async {
  // var url = "http://www.phonegap100.com/appapi.php?a=getPortalList&catid=20&page=1";

  //   // Await the http get response, then decode the json-formatted responce.
  //   var response = await http.get(url);
  //   if (response.statusCode == 200) {
  //     var jsonResponse = convert.jsonDecode(response.body);
     
  //     print(jsonResponse);
  //   } else {
  //     print("Request failed with status: ${response.statusCode}.");
  //   }


  
    print(formatDate(DateTime(1989, 2, 21), [yyyy, '*', mm, '*', dd]));

}
```
### 库的部分导入
```dart
/*
部分导入
  如果只需要导入库的一部分，有两种模式：

     模式一：只导入需要的部分，使用show关键字，如下例子所示：

      import 'package:lib1/lib1.dart' show foo;

     模式二：隐藏不需要的部分，使用hide关键字，如下例子所示：

      import 'package:lib2/lib2.dart' hide foo;      

*/

// import 'lib/myMath.dart' show getAge;

 import 'lib/myMath.dart' hide getName;

void main(){
//  getName();
  getAge();
}

```
### 库的懒加载
```dart
/*
延迟加载

    也称为懒加载，可以在需要的时候再进行加载。
    懒加载的最大好处是可以减少APP的启动时间。

    懒加载使用deferred as关键字来指定，如下例子所示：

    import 'package:deferred/hello.dart' deferred as hello;

    当需要使用的时候，需要使用loadLibrary()方法来加载：

    greet() async {
      await hello.loadLibrary();
      hello.printGreeting();
    }


*/


```
