---
title: 浅析MVC
categories: []
date: 2020-6-30 21:11:51
# cover: https://goss2.vcg.com/creative/vcg/800/version23/VCG41124554707.jpg
tags: mvc
keywords: 前端 
---

# 浅析MVC
1. MVC三个对象分别做什么
2. EventBus有哪些API,是做什么用的
3. 表驱动编程是什么
4. 如何理解模块化

## 1.MVC三个对象分别做什么
- M (Model)——数据模型,负责操作所有的数据
- V (view)——视图,负责所有的UI界面
- C (controller)——控制器,负责其他

## 2.EventBus有哪些API,是做什么用的
EventBus.on(eventName,fn); //监听函数
EventBus.trigger(eventName,data); //触发函数
EventBus.off(eventName,fn) //取消监听

EventBus又称为事件总线,可以用来组件(对象)之间的通信.


## 3.表驱动编程是什么
表驱动法是一种编程模式(scheme)——从表里面查找信息而不使用逻辑语句(if和case)。事实上，凡是能通过逻辑语句来选择的事物，都可以通过查表来选择。对简单的情况而言，使用逻辑语句更为容易和直白。但随着逻辑链的越来越发杂，查表法也就愈发显得更具吸引力。
## 4. 如何理解模块化
模块化开发可以提高代码的复用率,降低块与块之间的耦合性,各个模块可以相互独立互不影响,每个模块有一个肚子的作用域,本剧需求调用,从而提高网页开发效率,降低维护成本,快速发现问题,在修改BUG模块中不会出现牵一发动全身的现象.


