---
title: nodejs-install
categories:
  - nodejs
tags:
  - nodejs
  - nodejs安装
abbrlink: 60861
date: 2020-04-18 16:10:04
---

## 简介
简单的说 Node.js 就是运行在服务端的 JavaScript;Node.js 是一个基于Chrome JavaScript 运行时建立的一个平台;Node.js是一个事件驱动I/O服务端JavaScript环境，基于Google的V8引擎，V8引擎执行Javascript的速度非常快，性能非常好。

如果不懂得像PHP、Python或Ruby等动态编程语言，而且会JavaScript,然后你想创建自己的服务，那么Node.js是一个非常好的选择。
<!-- more -->

## 下载
nodejs中文网址:[http://nodejs.cn/](http://nodejs.cn/)
nodejs英文网址:[https://nodejs.org/en/](https://nodejs.org/en/)

{% tabs nodejsdownload %}
    <!-- tab window -->
    window 32位系统下载:[https://npm.taobao.org/mirrors/node/v12.16.2/node-v12.16.2-x86.msi](https://npm.taobao.org/mirrors/node/v12.16.2/node-v12.16.2-x86.msi)
    window 64位系统下载:[https://npm.taobao.org/mirrors/node/v12.16.2/node-v12.16.2-x64.msi](https://npm.taobao.org/mirrors/node/v12.16.2/node-v12.16.2-x64.msi)
    <!-- endtab -->

    <!-- tab mac -->
    mac 64位系统下载:[https://npm.taobao.org/mirrors/node/v12.16.2/node-v12.16.2.pkg](https://npm.taobao.org/mirrors/node/v12.16.2/node-v12.16.2.pkg)
    <!-- endtab -->

    <!-- tab liunx -->
    liunx 64位系统下载:[https://npm.taobao.org/mirrors/node/v12.16.2/node-v12.16.2-linux-x64.tar.xz](https://npm.taobao.org/mirrors/node/v12.16.2/node-v12.16.2-linux-x64.tar.xz)
    <!-- endtab -->
{% endtabs %}

## 验证
安装成功之后在终端命令行输入`node -v`,成功之后会显示版本号,否则安装失败,再重新安装

## 初始化项目
```
npx es10-cli create projectName
```
es10-cli创建项目的脚手架,create创建项目的命令,projectName项目名称

## 启动项目
```
cd projectName
npm start
```