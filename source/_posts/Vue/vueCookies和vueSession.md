---
title: Vue中使用vue-cookies和vue-session
categories: []
date: 2019-12-5 19:59
tags: Vue
keywords: 前端 
---
### 一、Vue中使用vue-session
* 安装
```
    npm install vue-session
```
* 在main.js中引入
```
    import VueSession from 'vue-session'
    Vue.use(VueSession)
```
* 使用
```
    this.$session.set("key",value); //存session
    this.$session.get("key") //获取session
```

### 二、Vue中使用vue-cookies
* 安装
```
    npm install vue-cookies --save
```
* 在main.js中引入
```
    import VueCookies from 'vue-cookies'
    Vue.use(VueCookies);
```
* 使用
```
    this.$cookies.set("key",value); //存cookies
    this.$cookies.get("key"); //获取cookies
```


