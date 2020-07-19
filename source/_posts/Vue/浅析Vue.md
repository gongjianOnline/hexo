---
title: 浅析Vue
categories: []
date: 2020-7-6 20:41:35
tags: Vue
keywords: 前端 
---

# 浅谈Vue
## 摘要
1. Vue两个版本对应文件名
2. Vue两个版本的区别
3. 在不同版本中template和reader怎么用
4. 在codesandbox.io编写Vue代码

## 1.Vue两个版本对应文件名
https://cdn.bootcdn.net/ajax/libs/vue/2.6.11/vue.min.js //完整版CDN
https://cdn.bootcdn.net/ajax/libs/vue/2.6.11/vue.runtime.min.js //非完整版

## 2.Vue两个版本的区别
* 完整版
    * 特点 有compiler模块(体积相对较大)
    * 视图 写在HTML里或者写在template选项中

* 非完整版 
    * 特点没有complier模块(体积相对较小)
    * 视图 写在render函数里用h来创建标签

开发中使用非完整版,配合webpack的vue-loader和vue单应用文件
1. 保证用户体验,js文件体积会更小
2. 保证开发体验,开发者直接关注与vue文件里的逻辑即可,webpack会把vue文件里的HTML自动转为h函数

## 3.在不同版本中template和reader怎么用
* 完整版
```javascript
    new Vue({
        el:"#app"
        template: '<div>{{ hi }}</div>'
    })
```

* 编辑器
```javascript
    new Vue({
        render (h) {
            return h('div', this.hi)
        }
    })
```

## 4.在codesandbox.io编写Vue代码
在线编写Vue地址  https://codesandbox.io/s/vue
(方方老师说:不要登录)

个人建议还是通过命令行工具+编辑器自己构建和练习,这样更有连贯性