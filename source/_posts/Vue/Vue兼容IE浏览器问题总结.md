---
title: Vue兼容IE浏览器问题总结
categories: []
date: 2019-12-6 10:32
tags: Vue
keywords: 前端 
---

#### axios的兼容问题
* 安装
```
    npm install es6-promise --save
```
* 在main.js中添加
```
    import promise from 'es6-promise';
    promise.polyfill();
```

#### 兼容IE9、IE10可能会遇到语法或者promise错误
* 安装
```
    npm install babrl-polyfill;
```
* 在main.js中添加
```
    import 'babel-polyfill';
```

#### 其他语法错误需要降低webpack版本
* 安装
```
    npm install webpack-dev-server@2.6.1
```