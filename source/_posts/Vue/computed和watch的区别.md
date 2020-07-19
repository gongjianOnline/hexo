---
title: computed和watch的区别
categories: []
date: 2020-7-8 20:42:35
tags: Vue
keywords: 前端 
---

# computed && watch
1. computed是什么?
2. watch是什么?
3. 总结

## 1. computed
computed是vue提供的计算属性,
* 支持缓存机制,在监听数据没有改变时不会重新计算
* computed不支持异步,当computed内有异步方法时是无效的,不能监听到数据的变化.
* computed提供了get和set两个方法,当数据返回时调用get方法,数据改变是调用set的方法
```javascript   
    new Vue({
        el:"#app",
        template:`
            <div>
                <span>{{name}}</span>
                <button @click="add">add</button>
            </div>
        `,
        data(){
            return{
                firstname:"张",
                lastname:'无极',
                nameTest:''
            }
        },
        computed:{
            name:{
                get(){
                    return this.firstname + this.lastname
                },
                set(value){
                    this.nameTest = value
                }
            }
        },
        methods:{
            add(){
                this.name = "宋"
            }
        }
    })
```
以上代码说明,computed中的name属性get方法返回了一个姓+名字的计算值,set方法修改姓氏,通过add按钮触发;当修改的值是相同时computed将不会重新计算.

## 2. watch属性
watch是Vue提供的监听属性,用于监听数据的变化
* watch监听属性返回了两个参数 oldval(更新前的值)和newval(更新后的值)
* watch支持异步方法
* watch不会被缓存,无论监听的数据值是否重复都会被监听到
* ==注意:在watch中禁止使用箭头函数,因为使用箭头watch的this会指向window或者node的global==
* watch: deep:true,深度监听object的属性.
* watch: immediate:true ,在第一次的是时候就调用这个watch
```javascript   
    new Vue({
        el:"#app",
        template:`
            <div>
                {{n}}
                <button @click="reset">n=1</button>
                <button @click="add">add</button>
                <div>
                    {{recordArr}}
                </div>
            </div>
        `,
        data(){
            return{
                n:0,
                recordArr:[]
            }
        },
        methods:{
            reset(){
                this.n = 0
            },
            add(){
                this.n ++                
            }
        },
        watch:{
            n:function(oldval,newval){
                this.recordArr.push({oldval,newval})
            }
        }
    })
```
以上事例,watch监听了n的属性,当触发reste方法后无论n的值是否和当前的值重复,都会被watch监听.

## 3.总结
computed是vue提供的计算属性,便于多个数据的整合和计算
watch是vue提供的监听属性,主要是用于监听一个属性的变化记录,(并且监听过程中消耗的资源相对较大)
