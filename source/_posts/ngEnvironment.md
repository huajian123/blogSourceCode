---
title: 【Angular】环境搭建
date: 2019-04-07 16:21:02
categories: Angular
tags: Angular
---
## 安装NVM
如果已经安装好了Node，建议先卸载

在下载页面中选择nvm-setup.zip进行下载
[点击进入下载页面](https://github.com/coreybutler/nvm-windows/releases)

下载完成后之后新建一个nodejs文件夹，用来映射当前使用的node

![nvm安装](ngEnvironment/nvm-setup.png)

安装完成以后使用nvm -v 来查看安装的版本
如果能看到版本号，表示安装成功

键入命令
``` bash
$  nvm list available
```
查看可安装的node版本，通过nvm install node版本号来安装node

## 安装Node
举个例子
``` bash
$  nvm install 10.15.0
```
## 安装angular-cli
*这里安装的是最新版本的angular-cli，如果想指定版本就要在后面加上@版本号*
``` bash
$  npm install -g @angular/cli
```
验证版本
``` bash
$  ng version
```
## 安装typescript
``` bash
$  npm install -g typescript
```
验证版本
``` bash
$  tsc -v
```
## 创建项目
命令行进入指定的目录,这里是自动安装依赖，如果想跳过安装依赖的过程，请加上参数
--skip-install
``` bash
$  ng new (项目名) 
```
## 启动项目
``` bash
$  ng serve 
```
