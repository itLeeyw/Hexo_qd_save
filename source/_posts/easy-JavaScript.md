---
title: easy-JavaScript
date: 2019-03-07 22:50:35
tags:
---


# easy-js
#easy-javascript

> ##### <script>code</script>

## 目录

### 1. 第一个导航页面案例
### 2. 监听事件
### 3. js的七大类型
### end. tips








### 1. 第一个导航页面案例
> ##### 需要用到的一些函数
    1. console.log() 打印 排错校验神器
    2. while 循环 没什么好讲的
    3. 字典与数组  没什么好讲的
    4. document 文档 JavaScript常用函数方法
    5. 通过给标签设置id在JavaScript中对标签进行操作
    6. onkeypress 从键盘在document中输入数据后，获取所有键入值
    7. location.href   当前页面链接 （可通过事件改写 进行跳转页面操作）
    8. window.open(href)  从新窗口中打开网页
    
### 2. 监听事件

> #####  监听鼠标
···

    //监听鼠标按下
    document.onmousedown = function(x){
        console.log(x)
    }
    
    //监听鼠标移动
    document.onmousemove = function(x){
        console.log(x)
    }
    
    //监听松开鼠标
    document.onmouseup = function(x){
        console.log(x)
    }
    
    //监听鼠标点击某个对象
    obj.onclick = function(x){
        console.log(x)
    }
    
···
> #####  监听键盘
···

    //监听键盘按下某个键
    document.onkeypress = function(x){
        console.log(x)
    }
    
···

> #####  监听错误
···

    //监听某个对象的错误信息
    obj.onerror = function(x){
        console.log(x)
    }

    
···

### 3. JS的七大类型
    1.number(数值类型)
    
    2.string(用单双引号括起来)
    
    3.undefined(常用于变量，可直接赋值于变量（推荐），或者对象)
        查看变量是否存在if(var in window）{...code...}
        
    4.null(常用于对象，也可以直接赋值于对象(推荐)|变量)
    
    5.object(数组，列表包含于此，非基本类型的类型)
    
        可以通过delete删除对象key in和forin 查询打印等操作
        
    6.boolean(真假)
    
    7.symbol
    
    tips:以及已经存在的函数方法  会有function 类型
    可以通过typeof var 来查看变量类型

### tips
```
Q:为什么我设置了监听mouse(touch)却在设备上无法使用
A:或许你该看看该设配是否支持mouse(touch) 下面命令
        document.body.ontouchstart !== undefined
        undefine:未定义，不支持
        null:未初始化，支持
        //通过特性检测来解决问题
        if(document.body.ontouchstart !== undefined){//特性检测
            //监听touch
         }else{
            //监听mouse
         }
Q：NULL和undefined的区别
A：一个变量没有被赋值则是undefined(更被js所接受)
    一个对象object暂时不给值，则给一个NULL（推荐，也可以给undefined）
    一个非对象值推荐给undefined(变量不赋给值默认Undefined，可写可不写)
      NULL表示空对象，undefined表示非空对象
```