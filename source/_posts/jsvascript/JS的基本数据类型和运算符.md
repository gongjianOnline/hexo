---
title: JS的基本数据类型和运算符
categories: []
date: 2020-4-21 22:28:51
# cover: https://goss2.vcg.com/creative/vcg/800/version23/VCG41124554707.jpg
tags: JavaScript
keywords: 前端 
---
# JS中的数据类型和运算符
## 1. JS的数据类型
一共七中,简称 **四基两空一对象**
- 数字 number
- 字符串 string
- 布尔 bool
- 符号 symbol
- 空 undefined
- 空 null
- 对象 object (数组\函数\日期\正则)

### 1.1 number
- 特殊值
	- 正0 负0 都等于0
	- 无穷大(正无穷,负无穷)
		- Infinity \ +Infinity \ -infinity
	- 无法表示的数字
		-NaN(Not a Number)
### 1.2 string
- 转义
	- 'IT \'s ok''
	-  \ '表示'
	- \ "表示"
	- \n 换行
	- \r tab键
	- \\ 表示\
- base4转码
- `window.btoa  //转为Base64`
- `window.atob  //解析Base64`
### 1.3 flasy值
- falsy相当于false但又不是false的值
- `分别是  undefined null 0 NaN '' `
- 