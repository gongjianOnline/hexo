---
title: JS函数
categories: []
date: 2020-5-1 10:38:51
# cover: https://goss2.vcg.com/creative/vcg/800/version23/VCG41124554707.jpg
tags: JavaScript
keywords: 前端 
---

# JS函数
## 1.  定义函数
- 具名函数
	- `function fn(形式参数1,形式参数2){语句 return 返回值}`
- 匿名函数
	- `let a = function(x,y){return x+y}`
- 箭头函数
	- `let fn = (x,y)=>{return x+y}`
- 构造函数声明
	- `let f =new Function('x','y','return x+y')`

## 2.JS函数的执行时机
- 示例1 

```javascript
	let a = l
	function fn(){
		console.log(a)
	}
	fn() //1
	a=2
```
- 示例2

```javascript
	let a = 1;
	function fn(){
		console.log(a)
	}
	a=2;
	fn() //2
```
如示例一和示例二,如果在fn调用前改变a的值,fn执行前a已经改变,所以fn打印2,如果在fn之后改变a的值,此时的fn已经执行完毕,所以打印更新前的值



- 示例3
```javascript
	let a = 1
	function fn(){
		setTimemout(()=>{
			console.log(a)
		},0)
	}
	fn(); //2
	a=2
```
如上代码,fn里面声明了定时函数,当fn()执行时触发定时器,因为定时器是稍后执行的函数,会在放在队列执行的后面执行,所以当执行定时器打印的时候a的值已经是2.

- 示例4

```javascript
	let i = 0;
	for(i=0;i<6;i++){
		setTimeout(()=>{
			console.log(i)
		},0)
	}
	// 6个6
```
如上面代码,i作为全局变量,每次for循环后都会+1,因为定时器会在执行的队列后面执行,当定时器执行的时候,全局的i,已经被for循环了5次,因为第五次执行完后进行了i++,当i等于6时不满足条件,跳出循环,此时的i等于6,循环了6遍定时器所以一次会打印6个6
 - 如何枚举出i的值
 	- 方式1
 		使用for let循环

```javascript
	for(let i=0;i<6;i++){
		setTimeout(()=>{
			console.log(i)
		},0)
	} // 1 2 3 4 5
```
如上面代码,for循环会在每次循环时,创建一个i,定时器会打印当前作用域下的i
	- 方式2
		使用闭包
```javascript
	for(var i=0;i<6;i++){
	    function fn(count){console.log(count)}
	    fn(i)
	} // 0,1,2,3,4,5
```
如上面的代码,利用闭包的特点,使用闭包可以上函数中的值始终保存在内存中,fn调用后不会被自动清除.

## 3.闭包的定义
 - 什么是闭包?
  - 如果一个函数用到了外部的变量,那么这个函数加这个变量就是闭包.