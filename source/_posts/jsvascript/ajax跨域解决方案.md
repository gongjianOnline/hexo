---
title: ajax跨域解决方案
categories: []
date: 2020-6-14 16:24:51
# cover: https://goss2.vcg.com/creative/vcg/800/version23/VCG41124554707.jpg
tags: JavaScript
keywords: 前端 
---

# ajax跨域解决方案
1. 同源
2. 同源策略
3. 如何解决跨域(一)[CORS]
4. 如何解决跨域(二)[JSONP] 
   1. 什么是JSONP
   2. JSONP的优缺点
   3. JSONP的用法
5. 跨域问答

## 1. 同源
 什么是同源?
    协议&域名&端口号都一致才算同源
 源:
    window.origin 或 location.origin 可以查看当前源
    源： 协议+域名+端口号

## 2. 同源策略
 什么是同源策略？
    浏览器规定 如果JS运行在源A里，那么就只能获取源A的数据；不能获取源B的数据，及不允许跨域。

## 如何解决跨域(一)[CORS]
 CORS : 跨资源共享
 Access-Control-Allow-Origin:协议+域名

## 如何解决跨域(二)[JSONP]
 什么是JSONP?
    当前浏览器不支持CORS方式，必须使用另一种方式跨域。于是就请求一个js文件去执行一个回调，回调里面有请求的数据，回调的名字可以随机动态生成，已callback命名的参数传给后台。

 JSONP的优缺点
    优点:
        1.兼容IE
        2.可以跨域
    缺点:
        1.只能接受成功和失败,读不到其他信息
        2.只能用get请求
 
 JSONP的用法
    ```javascript
        <script src="url"> </script>
    ```
[跨域案例 https://github.com/gongjianOnline/crossDomain](https://github.com/gongjianOnline/crossDomain "跨域案例")

## 问答
 - 为什么可以跨域使用CSS、js和图片等
   - 同源策略限制的是数据访问,我们引用CSS、js和图片的时候，其实并不知道其内容，我们只是在引用。


