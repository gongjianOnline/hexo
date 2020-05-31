---
title: DOM事件委托
categories: []
date: 2020-5-30 20:49:51
# cover: https://goss2.vcg.com/creative/vcg/800/version23/VCG41124554707.jpg
tags: JavaScript
keywords: 前端 
---

## DOM事件委托
1. 场景一
2. 场景二
3. 优点


### 1.场景一
需求: 给100个按钮添加点击事件
方案: 监听这100个按钮的祖先,等冒泡的时候判断target是不是这100个按钮中的一个
案例:直接上代码

```html
    <div id="btnDiv">   
        <button data-id="1">button 1</button>
        <button data-id="2">button 2</button>
        <button data-id="3">button 3</button>
        <button data-id="4">button 4</button>
        <button data-id="5">button 5</button>
        <button data-id="6">button 6</button>
        <button data-id="7">button 7</button>
        <button data-id="8">button 8</button>
        <button data-id="9">button 9</button>
        <button data-id="10">button 10</button>
    </div>
```
```javascript
    btnDiv.addEventListener('click',(e)=>{
        let t = e.target;
        if(t.tagName.toLowerCase() === "button"){
            console.log(t.dataset.id)
        }
    })

```


### 2.场景二
需求: 监听目前不存在的元素的点击事件
方案: 监听祖先,等点击的时候看看是不是想要的元素
案例:直接上代码
```html
    <div id="div1">   </div>
```

```javascript   
    setTimeout(()=>{
        const button = document.createElement('button');
        button.textContent = "chilk 1"
        div1.appendChild(button)
    },1000)

    function on(eventType,element,selector,fn){
        let elem = element;
        if(!(element instanceof Element)){
            elem = document.querySelector(element)
        }
        elem.addEventListener(eventType,(e)=>{
            const t = e.target
            if(t.matches(selector)){
                fn()
            }
        })
    }

    on("click","#div1",'button',()=>{
        console.log('点击了')
    })
```

### 3.优点
1. 省监听数(内存)
2. 可以监听动态元素