---
title: CSS基础概述
categories: []
date: 2020-4-11 17:55:19
tags: CSS
keywords: 前端 
---

# CSS基本概述
## 基本语法
语法一

```css
选择器{
	属性名:属性值
	/*注释*/
}
```
语法二

```css
@charset "UTF-8"; /*字符编码为UTF-8*/
@import url(2.css); /*引入外部的css文件*/
@media(min-width:100px)and(max-width:200px){ /*媒体查询*/
	选择器:{
		属性名:属性值
	}
}
```
## CSS文档流
- 流动的方向
	- inline 元素从左到右,到达最左边才会换行
	- block 元素从上到下,每一个都另起一行
	- inline-block 也是从左到右 ***(区别:到达最左边会整体换行)***
- 宽度
	- inline 宽度为内部的元素决定,不能指定width
	- block 默认宽度auto,可以指定width
	- inlink-block 可以指定width
- 高度
	- intine 高度有line-height简介决定,和height无关
	- block 取决于文档流的高度决定,可以指定width
	- inline-block 同block

## overflow溢出
- auto 灵活设置
- scroll 永远显示
- hidden 隐藏溢出
- visible 显示溢出
- overflow 可以分为overflow-x和 overflow-y

## 如何脱离文档流
1. float
2. position:adsolute/fixed

## CSS 盒模型
css盒模型包括分为两种content-box和border-box;
1. content-box 内容是内容盒模型,content就是盒子的边界;

```
	content-box width = 内容的高度
```

2.  border-box 边框盒- 盒子包括 content+padding+border

```
	border-box width = 内容高度+padding+border
```
**推荐使用 border-box**

```css
	选择器:{
		box-sizing:border-box
	}
```

## margin 合并
css默认会margin合并
1. 父子合并

```css
.parent{
	margin-top:20px;
}
.child{
	margin-top:20px;
}
```
同上面css中,当父级和子集元素都设置margin-top,父子的margin-top的间距会合并 ;**不会相加渲染 .**

2. 兄弟渲染

```css
.childA{
	margin-bottonm:20px;
}
.childB{
	margin-top:20px
}
```
同上面的css中两个div子元素,元素A的外边距和元素B的外边距会合并,AB的间距是20px.
 
 - 如何阻止合并
 	-  父子合并用 padding/border/overflow:hidden/display:flaex;
 	- 兄弟合并可以用 inline-block消除	
 
 ## CSS 学习常用到的小知识和技巧
 1. 目前主流全部支持的css版本是2.1
 2. css兼容性可以使用[caniuse](https://canuise.com)
 3. 推荐使用border调试法
 4. css颜色吸色工具推荐[snipaste](https://www.snipaste.com/)
 
