---
title: JS对象分类
categories: []
date: 2020-4-25 19:51:51
# cover: https://goss2.vcg.com/creative/vcg/800/version23/VCG41124554707.jpg
tags: JavaScript
keywords: 前端 
---

# JS对象分类
## 1. 构造函数
定义：能构造出对象的函数成为构造函数
- 注意点:
	- 所有的函数在创建后都会生成一个prototype属性,属性包含了constructor(构造函数)指向自己
	- `function f1() // console.gir(f1) //prototype.constructor 指向 f1 // f1.prototype.constructor === f1 --true`
	- 
- 如何创建

```javascript
 function X(name){
 	this.name = name
 }
 X.prototype.alertFun=function(){
	return `你好 ${this.name}`	
 }
 var x = new X("张无忌")
 //做了四件事
 1. 自动创建空对象
 2. 自动为空对象关联原型，原型的地址指定为X.prototype
 3. 自动将对象作为this关键字运行构造函数
 4. 自动运行 return this
 //构造函数X
 1.X函数本身负责给对象添加属性
 2.X.prototype对象负责保存对象的公有属性
```
- 代码规范
	-	new 后面的函数,使用名词
	-	普通函数,一般使用动词

## 2. 原型和公有属性的关系
- 规律 
- `let obj = new Object() //的原型是Object.prototype`
- `let arr = new Array() 的原型是Array.prototype`
- `let x - new X() 的原型是X.prototype`
- 公式
	- 对象.__proto__ === 其构造函数的.prototype
	- 你是谁构造的,你的原型就是谁的prototype属性对应的对象
	- 特殊
	- Object.prototype是哪个函数构造出来的 不知道
	- Object.prototype的原型是null
	- Object.prototype.__proto__是null

## 3.函数对象
- window 是谁构造的
	- Window
	- 可以通过comstructor属性看出构造函数
- window.Object是谁构造的
	- window.Function
	- 因为所有函数都是window.Funtion构造的
- window.Function是谁构造的
-	window.Function
-	因为所有函数都是window.functiuon构造的
-	浏览器构造了Function,饭后指定他的构造这是自己

## 4. class语法

```javascript
 class Square{
 	width = 0 //默认值为0
 	constructor(width){
		this.width = width
	}
	getArea(){
		return this.width
	}
	get area2(){
		return this.width
	}
	// get xxx为只读属性,调用时 .xxx即可不需要加()
 }
 let test = new Square(5)
 test.getArea() // 5
 test.area2 // 5
```
