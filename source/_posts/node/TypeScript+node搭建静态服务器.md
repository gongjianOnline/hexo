---
title: TypeScript+node搭建静态服务器
categories: []
date: 2020-10-24 10:08:35
tags: node
keywords: 前端 
---
# TypeScript+node搭建静态服务器
1. 第一步初始化npm
2. 全局安装ts-node-dev
3. 在项目安装node的声明文件
4. 在文件中使用http模块构建服务
5. 获取post的请求的的请求提参数
6. 如何更改状态码
7. 响应到客户端的方式
8. 开始搭建静态服务器
9. 处理查询参数
10. 优化静态服务器
11. 添加静态缓存

## 第一步初始化npm
```javascript
   npm init -y
```
## 全局安装ts-node-dev
```javascript
    npm install ts-node-dev -g
```
运行文件 
```javascript
    ts-node-dev index.ts
```
## 在项目安装node的声明文件
```javascript
    npm install --dev @typs/node
```

## 在文件中使用http模块构建服务
```typescript
    import * as http from "http";
    const server = http.createServer();
    server.on("request",(request,response)=>{
        //可以用ts的强类型给req和res进行类型的赋值
        console.log("有人访问了")
        response.end("hello word")
    });
    server.listen(8888)
```
可以用控制台访问该端口;
```typescript
    curl http://localhost:8888
```
查看get方式的请求头
```typescript
    curl -v http://localhost:8888
```
用post方式请求
```typescript
    curl -v -d "xxx=xxx" http://localhost:8888
```

## 获取post的请求的的请求提参数
```typescript
    const array = [];
    //on事件监听的是上传中的数据,以片段的形式来接受
    request.on("data",(chunk)=>{
        arrray.push(chunk);
    })
    //end监听上传完成后的操作
    request.on('end',()=>{
        //利用Buffer模块将分段的数据连接,转成字符串
        const body = Buffer.concat(array).toString();
        console.log(body)
        response.end("上传完成")

    })
```
## 如何更改状态码
```typescript
    response.statusCode = 400;
```
## 响应到客户端的方式
```typescript   
    response.write("xxx")
    //或者
    response.end("xxx")    
```
两者区别:wirte响应到客户端是不会关闭服务,end响应到客户端后会关闭服务

## 开始搭建静态服务器
在搭建静态服务器前需要在根目录创建几个静态文件,文件名为public
```typescript
    import * as p from 'path'
    //p.resolve(from.to) //根据当前工作目录返回from到to的相对路径.
    const  publicDir = p.=resolve(__dirname,'public')
    server.on("request",(request: IncomingMessage,response: ServerResponse)=>{
      const {method,url,headers} = request
      switch(url){
        case "/index.html":
          fs.readFile(p.resolve(publicDir,'/index.html'),(error,data)=>{
            if(error) throw error;
            response.end(data) 
          })          
        break;
        case "/style.css":
          fs.readFile(p.resolve(publicDir,'/style.css'),(error,data)=>{
            if(error) throw error;
            response.end(data) 
          })          
        break;
        case "/main.js":
          fs.readFile(p.resolve(publicDir,'/main.js'),(error,data)=>{
            if(error) throw error;
            response.end(data) 
          })          
        break
      }   
    })
```
## 处理查询参数
需要引用URL模块   
```typescript
    server.on("request",(request: IncomingMessage,response:ServerResponse)=>{
      const {url:path} = request;
      const {pathname,serch} = url.pares(path)
      console.log(pathname); // 打印路径
      console.log(serch); //打印查询字符串
    })
```
## 优化静态服务器
```typescript
      import * as p from 'path'
      const  publicDir = p.resolve(__dirname,'public')
      server.on("request",(request: IncomingMessage,response: ServerResponse)=>{
      const {method,url:path,headers} = request;
      const {pathname,search} = url.parse(path);
      const filename = pathname.substr(1);
      fs.readFile(p.resolve(publicDir,filename),(error,data)=>{
        if(error){
          if(error.error === -4058){
            response.statusCode = 404;
            response.end()
          }else{
            response.statusCode = 500;
            response.end("服务器端错误")
          }
        }else{
          response.end(data.toString())
        }
      })          
         
    })
```
## 添加静态缓存
Cache-control静态缓存,可以在刷新后不再向服务器端请求css\js等静态文件.
````typescript
    response.setHeader('Cache-Control','public,max-age=3153600')
````






















