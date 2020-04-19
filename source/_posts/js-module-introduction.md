---
title: js模块引入方式
categories:
  - JavaScript
tags:
  - module-introduction
  - ES Module模块引入方式
  - CommonJS模块引入
  - AMD
  - CMD
abbrlink: 58252
date: 2020-04-18 18:27:04
---

## ES Module模块引入方式
ES Module模块引入在浏览器端模块需要提前打包处理编译(浏览器不支持ES Module模块引入),但是,也是最流行的模块引入方式.

<!-- more -->

```
|-module
  |---a.js
  |---b.js
|-main.js
```

```js
// 方式一
/******* a.js文件 *******/ 
// 分别曝露的方式
export function a1(){
  console.log('a.js');
};
export let a2 = [1,2,3,4];

/******* b.js文件 *******/ 
// 统一曝露的方式
function b1(){
  console.log('b.js function b1');
}
function b1(){
  console.log('b.js function b2');
}
export {b1,b2}; //导出函数b

/******* main.js文件 *******/ 
import {a1,a2} from './module/a.js';
import {b1,b2} from './module/b.js';
a1();
a2();
b1();
b2();



//方式二
/******* a.js文件 *******/ 
// 默认曝露的方式
// 多个数据(类似分别曝露)
export default{
  strings:'数字曝露',
  function a1(){console.log('a.js');},
  function a2(){console.log(strings);},
};

/******* main.js文件 *******/ 
import a from './a.js';
a.a1();
a.a2();
```

## CommonJS模块引入
CommonJS在服务器端的加载是同步的, 在浏览器端模块需要提前打包处理编译(浏览器不支持CommonJS规范),浏览器加载时可能微慢

```
目录
|-module
  |---a.js
  |---b.js
|-main.js
```

```js
// 方式一
/******* a.js *******/
function a(){
  //函数内容
}
module.exports = a;//导出模块a

/******* b.js *******/
function b(){
  //函数内容
}
module.exports = a;//导出模块a

/******* main.js *******/
//require以同步的方式获取模块
var a = require('./a.js');
var b = require('./a.js');
//函数执行
a();
b();



// 方式二(推荐)
/******* a.js *******/ 
//导出模块a
// 为a模块添加c属性
exports.c = function (){
  //函数内容
}

// 为a模块添加d属性
exports.d = function (){
  //函数内容
}

/******* b.js *******/ 
//导出模块b
// 为a模块添加e属性
exports.e = function (){
  //函数内容
}

// 为a模块添加f属性
exports.f = function (){
  //函数内容
}

/******* main.js *******/
var a = require('./a.js');
var b = require('./a.js');
//函数执行
a.c();
a.d();
b.e();
b.f();
```


## AMD
专门用于浏览器端,模块的加载方式是异步.

```
目录
|-js
  |-libs
    |---require.js
    |---jquery.js
    |---angular.js
  |-module
    |---amodule.js
    |---bmodule.js
  |-main.js
```
```js
/******* amodule.js *******/ 
// 没有依赖的模块
define(function(){
  let txt = 'amodule.js';
  function afunction(){
    return txt;
  };

  // 曝露amodule模块对象,通常曝露的是个对象,这样可以包含多个
  return {afunction};
});

/******* bmodule.js *******/ 
// 有依赖的模块,依赖于a.js模块
// 依赖的模块必须与function行参一一对应
define(['amodule'],function(amodule){
  let txts = 'bmodule.js';
  function bfunction(){
    consloe.log(txts,a.afunction());
  };
  return {bfunction};
});

/******* main.js *******/ 
// 依赖的模块必须与function行参一一对应
(function(){

  // requirejs配置
  requirejs.config({
    baseURL:'js/';//基本路径
    // 路径
    // 引入路径不需要添加文件后缀
    path:{
      amodule:'./module/amodule',
      bmodule:'./module/bmodule'
    }
  });

  // 有依赖的模块,依赖于b.js模块
  require(['bmodule'],function(bmodule){
    // 运行b模块的bmodule函数
    b.bfunction();
  });

})();


// index.html js文档引入
// js标签是先引入require.js文件,后引入自己编写的main.js文件
<script data-main="js/main.js" src="js/libs/require.js"></script>
```
AMD模块加载是异步的,jQuery支持AMD,但是jQuery引用时这步`define(['module','jQuery'],function(module,$){})`必须改成小写的`jquery`才行,就是这样`define(['module','jquery'],function(module,$){})`才不会报错;还有`angular,js`需要单独配置,正确配置如下:
```js
// requirejs配置
  requirejs.config({
    baseURL:'js/';//基本路径
    // 路径
    // 引入路径不需要添加文件后缀
    path:{
      amodule:'./module/amodule',
      bmodule:'./module/bmodule',
      jquery:'./libs/jquery',
      angular:'./libs/angular',
    },

    // shim就是一个单独配置
    shim:{
      angular:{
        export:'angular' //曝露libs/angular对象
      }
    }
  });
```


## CMD
不推荐学习,CMD不流行只做了解就行,CMD模块引入是阿里巴巴内部使用的