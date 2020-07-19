---
title: Vue数据响应的理解
categories: []
date: 2020-7-8 20:42:35
tags: Vue
keywords: 前端 
---

# Vue数据响应式
1. Vue数据响应式
2. Vue数据响应式的BUG
3. 总结

## Vue数据响应式
vue的数据响应式是通过Object.defineProperty代理监听getter和setter来实现数据响应式的.
```javascript   
    Object.defineProperty(obj,'n',{
        value:5
    })
```

## Vue数据响应式的BUG
### 示例一: 关于对象
```javascript   
    new Vue({
        el:'#app'
        data(){
            return{
                obj:{
                    a
                }
            }
        },
        template:`
            <div>
                <div>{{obj.a}}</div>
                <div>{{obj.b}}</div>
                <button @click="test">测试</button>
            </div>
        `
        methods:{
            test(){
                this.obj.b = "1"
            }
        }
    })
```
以上代码点击button后不会显示obj.b的内容,原因是vue初始化是obj对象监听了n属性,所以操作能只能对n进行UI更新.

解决方法把Obj里b属性让vue进行监听
```javascript   
    Vue.set(this.obj,b,1) // 或者
    this.$set(this.obj.b,1)
    //代理之后下次可以正常使用
    this.obj.b = 2
```
### 关于数组
```javascript
    new Vue({
        el:'#app',
        data(){
            return{
                arr:[1,2,3]
            }
        },
        template:`
            <div>
                {{arr}}
                <button @click="test">add</button>
            </div>
        `,
        methods:{
            test(){
                this.arr[3] = 4
            }
        }
    })
```
以上代码中点击test向arr数组中后面追加一个4,在视图中打印是应然是[1,2,3],原因仍然是因为Vue代理监听的是arr中下标为0:1,1:2,2:3的值,没有后面的下标进行监听,所以无法更新到UI中.

解决这个方法:
Vue作者重新设计了数组的部分API,共七个push、shift、unshift、pop、sort、splice、reverse，在增删data中的数组使用API操作

```javascript
    this.arr.push(4)
```

## 总结 defineProperty
vue数据响应式思想主要是用到getter和setter方式,通过Es6提供的Object.definePropetry()方法来对数据进行监听,然后vue在初始时只会监听Data中的出现的对象,所以后面在其对象进行增加属性操作时Vue需要手动去将新属性添加到监听中才会更新UI视图.

    


