---
title: WebSession和localStorage使用
categories: 
date: 2018-11-30 14:32:00
tags: 前端数据持久化
# cover: http://image20.it168.com/201805_0x0/3185/25a49c86a4459d96.jpg
keywords: web存储
---
## Session
>* session会话:浏览器从打开网页的一个页面开始,直至关闭浏览器的整个过程称为“浏览器与WEB服务器的一次会话”
----
### window.sessionStorage
>* 数组对象:会话级数据储存,可供此次会话的页面共同使用,浏览器关闭就消失,
----
```javascript
	sessionStorage[key]=val; 	//保存一个数据
	sessionStorage.setitem(key,val); 	//保存一个数据
	var val = sessionStorage['key']; 	//读取一个数据
	var val= sessionStorage.getitem('key'); 	//读取一个数据
	sessionStorage.removeltem('key'); 	//删除一个数据
	sessionStorage.length; 	 	//数据长度
	sessionStorage.key(i); 	//获取第i个key
```
-----
### window.localStorage 本地存储对象（跨会话及存储）
>* 在浏览器能管理外存（磁盘）中存储用户数据,可供此次会话和后续会话的页面共同使用;即使浏览器关闭了也不会消失--永久存在
----
```javascript
	localStorage[key]=val; 	//保存一个数据
	localStorage.setitem(key,val); 	//保存一个数据
	var val = localStorage['key']; 	//读取一个数据
	var val= localStorage.getitem('key'); 	//读取一个数据
	localStorage.removeltem('key'); 	//删除一个数据
	localStorage.length; 	 	//数据个数
	localStorage.key(i); 	//获取第i个key
```
>* **注意:**localStorage中若数据发生了修改,会触发事件window.onstorage事件,可以监听事件,实现监视localstorage数据改变目的,不能监视sessionStorage数据修改;