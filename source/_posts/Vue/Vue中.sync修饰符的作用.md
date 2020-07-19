---
title: Vue中.sync修饰符的作用
categories: []
date: 2020-7-9 20:00:35
tags: Vue
keywords: 前端 
---

# Vue中修饰符的作用
1. 什么是修饰符
2. 修饰符的用法
3. .sync修饰符的作用
4. 总结

## 1. 什么是修饰符

Vue在部分指令中添加了修饰符,用来执行一些方法
* v-on支持的有.{keycode | keyAlias}\ .stop \ .prevent \ .capture \ .self \ .once \ .passive \ .native
* 快捷键相关: .ctrl .alt .shift .metact
* 鼠标相关: .lefty .right .middle
* v-bind支持的有: .prop .camel .sync
* v-model支持的有：.lazy .number .trim

## 2. 修饰符的用法
```javascrpt
    @click.stop="fnName"  // 表示阻止冒泡
    @click.prevent = "fnName" //表示阻止默认行为
    @click.stop.prevent = "fnName" //表示阻止冒泡和默认行为
```


## 3. .sync修饰符的作用
Vue内置了EvntBus事件总线传值方法，.sync是EvntBus的语法糖
如下实例
父组件parent.vue

```javascript
    <template>
        <div>
            父组件的值{{number}}
            <Child :num="number" v-on:update:num="number=$event"/>
        </div>
    </template>
    <script>
        import Child from "./child.vue"
        export default{
            components:{
                Child
            }
            data(){
                return{
                    number:1000
                }
            }
        }
    </script>
```

 子组件为 child.vue
 
 ```javascript
    <template>
        <div>
            <p>{{num}}</p>
            <button @click="test">修改减100 </button>
        </div>
    </template>
    <script>
        export default{
            props:['num'],
            methods:{
                test(){
                    this.$emit("update:num",this.num-100)
                }
            }
        }
    </script>
 ```
以上代码Vue事件总线算传参方式,但父组件的v-on可以用.sync进行简化,简化代码如下

```javascript
    <template>
        <div>
            父组件的值{{number}}
            <Child :num.sync="number"/>
        </div>
    </template>
    <script>
        import Child from "./child.vue"
        export default{
            components:{
                Child
            }
            data(){
                return{
                    number:1000
                }
            }
        }
    </script>
```

## 4. 总结
修饰符是Vue作者在部分Vue指令上对常用的方法比如(冒泡,默认事件)等进行了封装,而.sync是对Vue.eventBus的再一次优化(语法糖),使开发者调用更加简洁





