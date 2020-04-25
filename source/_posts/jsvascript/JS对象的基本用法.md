---
title: JS对象的基本用法
categories: []
date: 2020-4-22 21:13:51
# cover: https://goss2.vcg.com/creative/vcg/800/version23/VCG41124554707.jpg
tags: JavaScript
keywords: 前端 
---
# JS对象的基本用法
## 1. 声明Object的语法
-  1.构造函数声明
- `var obj = new Object()`
-  2.字面量方式声明
- `var obj= {}`
## 2.对象操作
### 2.1 删除对象

```javascript
var obj = {name:'张无忌'}
//删除value
obj.name = undefined; 
console.log(obj.name) //undefined
//删除key和value
delete obj.name
'name' in obj //false
```
上面代码可以看出,给对象赋值undefined只能清空value,而delete可以清空对象的属性和值,**属性名 in obj 可以查看对象是否有该对象 返回bool**

### 2.2 读对象
两种方式
```javascript
var obj= {name:'test'}
obj.name //test
obj.['name'] //test
```
- 其他操作
- `object.entrues(obj) //返回key value的数组`
- `Object.keys(obj) //返回key的数组`
- `console.dir(obj) // 查看自有属性和公有属性`
- `obj.hasOwnproperty('toString') //判断是自有属性还是公有属性 返回bull`
### 2.3 修改和增加
JS对象中的key名如果重复,会自动覆盖之前的赋值,从而达到修改的目的,如果对象中没有key会自动创建key.例如

```javascript
var obj = {name:'张无忌'}
obj.name = '张三丰'
obj.age = "100"
console.log(obj.name,obj.age) // '张三丰','100' 之前的张无忌会被覆盖
```
- 批量赋值
- `Object.assign(obj,{name:''张无忌,age:'20'})  //obj={name:'张无忌',age:'20'}`

### 3.原型
- 每个对象都有原型
- obj.__proto__存着原型的地址
- 对象的原型也是对象,所有对象的原型也有原型
- obj={} 的原型为所有对象的原型,这个原型包含了所有对象的公有属性,**即对象的根**,根的原型是null

#### 3.1 修改公有属性

```javascript
var obj= {}
obj.prototype.tostring = "张无忌"
```
此时所有对象上原型的tostring属性都会变成'张无忌'

### 3.2 修改原型

```javascript
var obj1 = {name:'张三丰'}
var obj2 = Object.create(obj)
obj2.name = '张无忌'
```
此时对象obj2上的原型已经更改成obj1

