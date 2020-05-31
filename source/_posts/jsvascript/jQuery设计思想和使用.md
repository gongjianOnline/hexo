---
title: jQuery设计思想
categories: []
date: 2020-5-30 19:47:51
# cover: https://goss2.vcg.com/creative/vcg/800/version23/VCG41124554707.jpg
tags: JavaScript
keywords: 前端 
---

## jQuery设计思想
1. jQuery 如何获取元素
2. jQuery 的链式操作是怎样的
3. jQuery 如何创建元素
4. jQuery 如何移动元素
5. 如何修改元素的属性


### 1. jQuery 如何获取元素

``` javascript
	/**通过选择器选择*/
    $(document) //选择整个文档对象
 
 	$("#myId") // 利用ID选择器查找,id为myid的元素
 
 	$('div.myclass') //选择class为myclass的div元素
 
 	$('input[name=first]') //选择input的name为first的元素
	
    /*特殊选择器*/
    $('a:first') //选择网页中第一个a元素
    
    $('tr:odd') //选择表格的奇数行  
    
    $('#muform :input') // 选择的id为muform中的input元素
    
    $('div:visible') // 选择可见的div元素
    
    $('div:get(2)') //选择所有的div元素,除了前三个
    
    $('div.animated') //选择当前处于动画状态的div元素
    
    /*过滤选择器*/

	$('div').has('p'); //选择包含P元素的Div元素
    
    $('div').not('.myClass') //选择class不等于myClass的元素
    $('div').first() //选择第一个div元素
    
    $('div').eq(5) //选择第6个div元素
    
    /*选择附近元素*/
    $('div').netx('p') //选择div元素后面的第一个p元素
    
    $('div').parent() // 选择div的父元素
    
    $('div').closest('form') //选择离div最近的那个form元素
    
    $('div').children() //选择div的所有子元素
    
    $('div').siblings() //选择div的同级元素
    
```
### 2. jQuery 的链式操作是怎样的
链式操作是选中网页元素以后,可以对他进行一系列的操作,并且所有操作可以连接在一起,以链条的形式写出来,
原理:在于每一步的Jquery操作,返回的都是一个Jquery对象,所以不同操作可以连接在一起

``` javascript
	$('div').find('h3').eq(2).html('Hello');
```

### 3.jQuery 如何创建元素

```javascript
    $('<p>Hello</p>');
　　$('<li class="new">new list item</li>');
　　$('ul').append('<li>list item</li>');
```

### 4.jQuery 如何移动元素
``` javascript
    $('div').insertAfter($('p')); //把div元素移动p元素的后面
    $('p').after($('div')) //把p元素添加到div元素的前面
    .insertBefore()和.before()：在现存元素的外部，从前面插入元素
    .appendTo()和.append()：在现存元素的内部，从后面插入元素
    .prependTo()和.prepend()：在现存元素的内部，从前面插入元素
```

### 5.jQuery 如何修改元素的属性

``` javascript
    $(selector).attr(属性名,属性值)
```

