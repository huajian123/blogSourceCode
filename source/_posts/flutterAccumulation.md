---
title: 【Flutter】小积累
date: 2019-06-02 23:28:44
categories: 
- Flutter
tags:
- Flutter
---
### 隐藏手机状态栏
```dart
    import 'package:flutter/services.dart';
    隐藏
    SystemChrome.setEnabledSystemUIOverlays([]);
    显示
    SystemChrome.setEnabledSystemUIOverlays(SystemUiOverlay.values)；
```

