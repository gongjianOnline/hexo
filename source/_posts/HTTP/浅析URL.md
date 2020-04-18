---
title: 浅析URL
categories: []
date: 2020-4-16 20:47:19
tags: HTTP
keywords: 前端 
---
## 1. URL
url包含协议 域名 端口号 路径 查询参数 锚点

```javascript
https://www/baidu.com/s?wd=hellow&rsw_spt=1#5
协议          域名    路径    查询参数       锚点
```

## 2. DNS
- DNS：域名系统
- 过程：当你输入一个网址，你的chrome浏览器会向电信提供的DNS服务器询问这个网址对应的IP
电信会回答一个IP,然后chrome才会想对应IP的80/443端口发送请求,请求内容是查看这个网址的网页

```javascript
~ nslookup  www.baidu.com  8.8.8.8 -port=53
Server:     8.8.8.8 //dns server
Address:    8.8.8.8#53 //server+port

Non-authoritative answer:
www.baidu.com   canonical name = www.a.shifen.com. // 别名
Name:   www.a.shifen.com 
Address: 180.97.33.107  //地址
Name:   www.a.shifen.com
Address: 180.97.33.108
```
## 3. IP
IP 的作用是什么，ping 命令怎么用？

   -  IP：internet protocol
   -   没有IP就不能上网，IP主要约定两件事：一是如何定位一台设备；二是如何封装数据报文跟其他设备交流
 	
## 4. 域名
域名是什么，分别哪几类域名?

   - 域名就是对IP的别称
    一个域名可以对应不同的IP，这个叫做均衡负载，防止一台机器扛不住。一个IP可以对应不同的域名，这个叫做共享主机，没有钱的开发者一般共享主机域名分顶级域名，二级域名和三级域名.
