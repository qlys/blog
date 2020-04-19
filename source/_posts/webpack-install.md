---
title: webpack-install
abbrlink: 24855
date: 2020-04-18 17:42:39
categories: 
    - webpack
tags:
    - webpack-install
---

## 简介
webpack在使用之前需要本地电脑确保安装了nodejs和npm,webpack支持ES Module模块引入方式、CommonJS模块引入规范、CMD、ADM
<!-- more -->

## 安装
```shell
mkdir progect
cd progect
npm init
//之后项目的配置就不多赘述了,一路回车就行了

# 安装webpack、webpack-cli
npm i webpack webpack-cli -D

# 检查webpack、webpack-cli是否安装成功
# npx *** -v 命令检查本地项目中是否安装成功
npx webpack -v
npx webpack-cli -v
# 安装成功之后会显示版号
```

## 配置
```js
// 在新建项目中建立webpack的配置文件:webpack.config.js,配置如下:

// webpack模块引入
const path = require('path');

// webpack基本配置
const config = {
    mode: 'development', //开发者模式
    entry: './index.js', //入口文件设置
    output: { //出口文件设置
        path: path.resolve(__dirname, 'dist'), //配置导出文件路径
        filename: 'main.js' //配置导出文件名称
    }
};

// 曝露webpack配置config对象
module.exports = config;
```
