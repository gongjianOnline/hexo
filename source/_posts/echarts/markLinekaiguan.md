---
title: echarts中legend控制markLine的开关
categories: []
date: 2019-12-19 9:57
tags: Echarts
keywords: 前端 
---

#### 场景描述
当一组数据出现多条markLine的线段时,整体感观太乱,因为echarts没有提供专门的属性去调整,所以利用多组Data数据去模拟legned的开关效果.

#### 示例
```
option = {
    xAxis: {
        type: 'category',
        data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
    },
    tooltip:{},
    legend:{
      data:["本月销量","季度销量","年度销量"]  
    },
    yAxis: {
        type: 'value'
    },
    series: [
        {   
            name:'本月销量',
            data: [120, 200, 150, 80, 70, 110, 130],
            type: 'bar'
        },
        { //这两组数据用来模拟markLine线段开关,data可以为空
            name:'季度销量',
            type:'line',
            markLine:{
                data:[
                    {
                        name:'季度销量',
                        yAxis:"150"
                    }
                ]
            }
        },
        {
            name:'年度销量',
            type:'line',
            markLine:{
                data:[
                    {
                        name:'年度销量',
                        yAxis:"100"
                    }
                ]
            }
        }
        
    ]
};

```
* 效果
![效果](https://img-blog.csdnimg.cn/20191217114109568.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zOTUxMzgyMQ==,size_16,color_FFFFFF,t_70 "最终效果");
