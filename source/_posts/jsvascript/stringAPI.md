---
title: JavaScript--stringAPI
categories: []
cover: http://www.ittime.com.cn/uploadimage/images/20180801080150.jpg
date: 2018-11-27 11:57:51
tags: JavaScript
keywords: 前端 
---

## Unicode编码
### charCodeAt
> * charCodeAt() 返回指定字符的Unicode编号
```javascript
	var str = "A";
	str.charCodeAt() //65
```
------
### formCharCode 
>* formCharCode 将Unicode编码转回字符
```javascript
	var str = "65";
	str.formCharCode() //A
```
------

## 字符串截取
### subString 
>* subString(开始位置,结束位置)
```javascript
	var str = "hello";
	str.subString(1,3) //el
```
------

### substr
>* substr(开始位置,结束位置)  
```javascript
	var str = "hello";
	str.substr(1,3) //ell
```
------

## 转换大小写
### toLowercase
>* toLowercase() 转小写
```javascript
	var str = "HELLO";
	str.toLowercase() //hello
```
------

### toUppercase
>* toUppercase() 转大写
```javascript
	var str = "hello";
	str.toUppercase() //HELLO
```
------

## 查找
### charAt
>* charAt() 返回指定位置的字符
```javascript
	var str = "hello";
	str.charAt(0) //h
```
------

### indexOf
>* indexOf() 查找指定字符并返回下标，如果未找到则返回-1
```javascript
	var str = "hello";
	str.indexOf("h") //0
```
------

### split
>* split() 将字符串分割为数组,默认以逗号的形式
```javascript
	var str = "hello";
	str.split("") //[h,e,l,l,o]
```
------

## ecs5 新增
### StringValue
>* StringValue[index] 返回该字符串下标的内容
```javascript
	var str = "hello";
	str.StringValue[0] //h
```
------

### slice
>* slice[index] 字符串截取
```javascript
	var str = "hello";
	str.slice(1,3) //el
```
------

### trim
>* trim() 清空字符两端的空格
```javascript
	var str = "  hello  ";
	str.trim() //hello
```
------












