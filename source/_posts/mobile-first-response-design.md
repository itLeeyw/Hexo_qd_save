---
title: mobile-first-response-design
date: 2019-05-14 20:57:36
tags:
---
# 移动端设计如何做适配？
## 1.mete viewport
> 历史遗留问题宽度在没设计之前为980px,所以我们需要给手机上的页面重新定义一下。

    
    <meta name="viewport" content="width=device-width, height=device-height, user-scalable=no, initial-scale=1.0, maximum-scale=1.0 minimum-scale=1.0">


## 2. media查询(响应式处理)
> 不同的媒体设备，或者不同的页面size或样式时对应不同的页面样式 两种方式使用。

    1. style中直接定义
    <style>
    @media(max-width:800px){background: red;}
    </style>
    2.link时定义
    <link type="text/css" href="./style.css"  media="(max-width: 500px)" />
    
    
## 3.动态rem方案
> 一般通过scss px 转换成 css 的rem 更加方便

>Q： 为什么不使用百分比
>>A: 因为百分比无法硬链接宽高 pass

> Q: em?
> > A: no em是适用于当前元素的font-size若没有才继承爸爸的font-size，

>Q:rem?
>>A:  yes rem 是适用于html的font-size，继承html

>Q:一个rem是多少？
>> 一个字的长度 or 一个 M 的长度..

> Q:HTML font-size?
> > A: 它的默认font-size = 16px,chrome可以定义最小网页显示字的大小。


    //js
    var pageWidth = window.innerWidth
    document.write('<style>html{font-size: ' + pageWidth + 'px}</style>')
    
    //scss
    
    @function px( $px ){
      @return $px/$designWidth*10 + rem;
    }

    $designWidth : 640; // 640 是设计稿的宽度。

    .child{
      width: px(320);
      height: px(160);
      font-size: 1.2em;
    }