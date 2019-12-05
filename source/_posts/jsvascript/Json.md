---
title: JSON对象的常用场景
categories: []
date: 2018-11-27 13:57:51
# cover: https://goss2.vcg.com/creative/vcg/800/version23/VCG41124554707.jpg
tags: JavaScript
keywords: 前端 
---

在前后端交互过程中，前端会将所用的请求参数转换成JSON字符串的格式，传给后端，后端响应过来的数据为json对象时才能使用,下面两种方法是在工作中遇到的两种json格式互换的解决方案。
## 将值转换为json字符串
>* JSON.string(obj) 
> * 注意：该方法对数组无效
```javascript
	var obj = {
		a:1,
		b:2
	};
	JSON.string(obj) // '{'a':'1','b':'2'}'
```

## 将json字符串转换为json对象
>* JSON.parse() 
```javascript
	var str = JSON.parse('{"name":"张三"}');
	str.name //张三
```
