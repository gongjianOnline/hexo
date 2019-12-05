---
title: Vue多个反向代理,解决本地接口跨域问题
categories: []
date: 2019-12-5 16:10
tags: Vue
keywords: 前端 
---

#### 场景描述
前端项目对接多个不同路径的接口地址,需要多个代理解决本地跨域问题
#### 解决方案

``` 
    //在config/index.js中
    dev:{ 
        ......
        proxyTable: {
            '/api1': {
                target: '需要代理的接口地址',
                changeOrigin: true,
                secure: false,
                pathRewrite: {
                    '^/api1': ''
                }
            },
    
            '/api2': {
                target: '需要代理的接口地址',
                changeOrigin: true,
                secure: false,
                pathRewrite: {
                    '^/api2': ''
                }
            },
        }
    }  

```

***

```
    //axios调用api1的接口
    this.$axios({
        methods:'get',
        url:'/api1/url',
        params:{}
    }).then((response)=>{
        
    })
    
    //调用api2的代理接口
    this.$axios({
        methods:'get',
        url:"/api2/url",
        params:{}
    }).then((response)=>{
        
    }) 

```

#### 说明
以第一个代理为例,如果pathRewrite{'^/':" "},api接口会被代理成"url/api1/xxx/xxx".
如果pathRewrite{'^/api1':" "},会重写路径代理成"url/xxx/xxx"
