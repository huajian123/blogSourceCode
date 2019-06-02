---
title: 【Flutter】各种坑
date: 2019-06-02 23:04:33
categories: 
- Flutter
tags:
- Flutter
---

### Flutter 卡在 package get 的解决办法
新增两个环境变量

变量FLUTTER_STORAGE_BASE_URL	值https://storage.flutter-io.cn

变量PUB_HOSTED_URL	值https://pub.flutter-io.cn

###打开AndroidStudio的时候顶部的模拟器一直是loading状态，即使已经打开了模拟器。 
 ###  运行flutter doctor 提示
 ###Waiting for another flutter command to release the startup lock
+ 1、打开flutter的安装目录/bin/cache/ 
+ 2、删除lockfile文件 
+ 3、重启AndroidStudio

### Waiting for another flutter command to release the startup lock... 
进程中终止所有dart的进程

### Flutter项目在 Resolving dependencies 时卡住的解决办法
在文件目录的/android/build.gradle 文件中，将buildscript 的repositories 字段改成如下代码即可：

```$xslt
maven{ url 'https://maven.aliyun.com/repository/google'}

maven{ url 'https://maven.aliyun.com/repository/gradle-plugin'}

maven{ url 'https://maven.aliyun.com/repository/public'}

maven{ url 'https://maven.aliyun.com/repository/jcenter'}

google()

jcenter()


```

### flutter initializing gradle终极解决方案
[链接](https://www.cnblogs.com/yehuabin/p/10344713.html)
