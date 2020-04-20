---
title: JS语法
categories: []
date: 2020-4-20 21:27:51
# cover: https://goss2.vcg.com/creative/vcg/800/version23/VCG41124554707.jpg
tags: JavaScript
keywords: 前端 
---
# JS的基本语法
## 1. 表达式和语句
- 表达式一般都有值,语句可能有也可能没有
- 语句一般会改变环境(声明和赋值)
**以上两点不是绝对的**

## 2.标识符的规则
- 第一个字符可以是 Unicode字母、$、_、中文
- 后面的字符,除了上面所有还可以是数字

## 3. if语句

```javascript
		if(表达式){语句1}else{语句2}
```
常用面试题

```javascript
	let a = 1;
	if(a===2)
		console.log("a")
		console.log("a等于2")
	// 上面代码 if会将下面的第一句代码包裹在花括号中,最后打印为'a等于2'
```

```javascript
	let a = 1;
	if(a===2)
		console.log("a"),console.log("a等于2")
	// 上面代码中,console.log以逗号相连,js会认为是一条执行语句,最后会打印'a'和'a等于2'
```

## 4. switch语句
语法

```javascript
	switch(要判断的内容){
		case '预测的值':
			执行语句
			break;
		default:
			执行语句
	}
```

## 5. while循环
语法

```javascript
	while(表达式){执行语句}
```
- 当表达式为真,执行语句,执行完在判断表达式的真假
- 当表达式为假,执行后面的语句

## 6. for循环

```javascript
	for(语句1;表达式2;语句3){执行语句}
```
- 先执行语句1
- 然后判断表达式2
- 如果为真,执行循环体,然后执行语句3
- 如果为假,直接退出循环

## 7. break和continue
- break 退出所有循环
- continue 退出当前一次循环 

## 8. label
语法
```javascript
	foo:{
		console.log(10);
		break foo;
		console.log("本行不会输")
	}
	//上面的东西就是label
```

## 9.压轴操作,逻辑运算符中'短路逻辑的运用'
 ### && 逻辑并
|&&|B真  | B假|
|--|--|--|
|  A真| B |B|
|  A假|  A|A|
如表格所示,以A为真B为假时为例,&&的取值会是B的值,而非false.

```javascript
	let a = 1
	let b = 2
	let c ;
	a && b && c //c
```

 ## || 逻辑或
|逻辑或|B真  | B假|
|--|--|--|
|  A真|  A|A |
|  A假|  B| B|
如上面表格所示,以A为真B为假时为例,逻辑或的取值会是A,而非true,*值得注意的是当A和B都为false时,逻辑或会取B*

```javascript
	let a = 1
	let b = 2
	let c ;
	a && b && c //a

	let a , b, c
	a && b && c //c
```
