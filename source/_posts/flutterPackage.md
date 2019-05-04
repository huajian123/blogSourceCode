---
title: 【Flutter】打包
date: 2019-05-04 10:46:33
categories: 
- Flutter
tags:
- Flutter
---
### app图标
flutter_app\android\app\src\main\res\mipmap-mdpi

### 配置打包信息
flutter_app\android\app\src\main\AndroidManifest.xml

这个文件中
+ android:label对应打包的app名称
+ android:icon对应图标名称
+ 命令行运行keytool -genkey -v -keystore ~/key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias key
如果报错是因为没有设置指定的盘，则运行keytool -genkey -v -keystore e:/key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias key 用这条来生成，可以对比一下。
此时e盘有一个key.jks文件
+ 如果上面的命令找不到keytool这个工具，运行flutter doctor -v,找到命令行中Java binary at...,复制到bin目录例如E:\Program Files (x86)\AndroidStudio\jre\bin\java,则赋值到java前面的\\(包含),则重新修改命令为
E:\'Program Files (x86)'\AndroidStudio\jre\bin\keytool -genkey -v -keystore ~/key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias key
+ 在F:\projects\flutter_app\android\key.properties新建key.properties文件，赋值
```dart
storePassword=<password from previous step>
keyPassword=<password from previous step>
keyAlias=key
storeFile=<location of the key store file, e.g. /Users/<user name>/key.jks>

```
举个例子
```dart
storePassword=123123
keyPassword=123123
keyAlias=key
storeFile=E:/key.jks
```
+ 在F:\projects\flutter_app\android\app\build.gradle这个文件中

在android这个属性上添加代码
```dart
def keystorePropertiesFile = rootProject.file("key.properties")
def keystoreProperties = new Properties()
keystoreProperties.load(new FileInputStream(keystorePropertiesFile))

```
+ 替换
```dart

buildTypes {
    release {
        // TODO: Add your own signing config for the release build.
        // Signing with the debug keys for now, so `flutter run --release` works.
        signingConfig signingConfigs.debug
    }
}
为:

signingConfigs {
    release {
        keyAlias keystoreProperties['keyAlias']
        keyPassword keystoreProperties['keyPassword']
        storeFile file(keystoreProperties['storeFile'])
        storePassword keystoreProperties['storePassword']
    }
}
buildTypes {
    release {
        signingConfig signingConfigs.release
    }
}

```
+ 最后运行
flutter build apk即可得到包的路径，在F:\projects\flutter_app\build\app\outputs\apk\release下面
