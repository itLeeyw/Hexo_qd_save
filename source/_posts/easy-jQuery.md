---
title: easy-jQuery
date: 2019-05-13 12:06:06
tags:
---
## easy - JQuery
> 1. jQuery 是一个JavaScript库
> 2. jQuery 能很大程度上简化JavaScript程序
> 3. jQuery 的学习非常简单

### Jquery 介绍
> jQuery的目的就是让你在你的网站更容易的使用JavaScript

> 需要学习到的前置知识：

* HTML
* CSS
* JavaScript

> jQuery到底是什么？
> > jQuery是一个轻量级的库，“write less, do more”,Javascript library

 > >  jQuery的任务是通过大量的常见Javascript代码来完成 ，封装成方法后，你可以通过一行代码来使用

>> jQuery还简化了很多来自Javascript的东西，比如AJAX的调用和DOM的操作
>> >> AJAX = (ansyc JavaScript and XML)

>>jQuery库包含了下列的一下特征
 
 * HTML/DOM 的操作方法
 * CSS 的操作方法
 * HTML事件方法
 * 效果和动画
 * AJAX
 * 工具

    
```
此外，jQuery的plugins 几乎能完成所有任务
```

> 为什么使用jQuery？
> > 有很多其他的Javascript框架，但jQuery似乎是最流行的，也是最可扩展的，许多大公司都在使用jQuery
> > 比如：

* Google
* Microsoft
* IBM
* Netflix

>> tips: jQuery在所有主要浏览器的运行完全相同

### jQuery 开始！

* 你在jQuery.com可以下载jQuery库
* 你也可以include，从CDN上找到jQuery,比如谷歌

> 有两个版本的jQuery可以下载

* 生产版：这是给你的live website，因为它是压缩后的mini版本
* 开发版：这是为了测试和开发的版本（为被压缩的可读code）

> 这两个版本都能在jQuery.com上下载到

>> jQuery是一个单独的JavaScript文件，所以我们要使用<script> Tag 来引用它(<script>标签应该在<head>中)

> tips: 也许你很惊讶我们在<script/>中没有type="text/javascript"？
>> 这是因为在HTML5中这不是必须的，在HTML5中和现代浏览器中，Javascript是一个默认的脚本语言

> jQuery CDN
> > 如果你不想在自己的电脑上下载jQuery，你可以在CDN上包含它
> > >> CDN = content delivery network
> > 在谷歌和微软的主机上引入jQuery
> > 在Google或者Microsort上使用jQuery时你需要使用下面：

    GOOGLE CDN：
    <head><script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.0/jquery.min.js"
    </script>
    </head>
    
    
    Microsoft CDN：
    <head><script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.0.min.js">
    </script>
    </head>
    
> tips： 一个引入Google or Microsoft的jQuery的一大优势
> > 很多用户从Google和Microsoft站点上下载了jQuery，它将直接从你访问站点时的缓存加载，这会很大程度的提高访问速度，并且，大多数CDN将确保一旦用户请求一个jQuery，jQuery将从服务器最上网络最近的服务器请求，这也会让你的访问速度提高


## jQuery语法

> jQuery Syntax
> > 对于在元素上执行某一动作或选择某一HTML元素来说，jQuery的语法是特定的(tailor-mode)

>> 基础语法：$(selector).active()

* $ 符号  定义/访问 jQuery
* (selector) 是”发现或者查询“HTML 元素
* active() 让元素执行某一动作

>> 例子：

    $(this).hide() //隐藏当前元素
    $('p').hide() // 隐藏所有p元素
    $(".test").hide() // 隐藏class name 为 test的元素
    $("#test").hide() // 隐藏id="test"的元素
    
>>> 你熟悉CSS选择器吗？
>>>> jQuery使用CSS选择器语法来选择元素，接下来你会学习到很多关于选择器的语法

> 你可能有注意到在jQuery例子中，所有jQuery method在一个document ready event 中


    $(document).ready(function(){ 
        // jQuery methods go here...
    });
 
 * 这是为了防止document加载结束之前运行jQuery code
 * 这是一种good 做法，在文档加载前准备好它
 * 这也允许你有其他的Javascript code

> 如果你不向上面那样做的话？

* 你要隐藏一个元素却还没有创建
* 你要改变一个图片大小却还没有加载好

> tips: 上面甚至有一个shorter版本

    $(function()){
        //jQuery method go here
    }
    
    第二种更简单，但第一种更容易理解
    

### jQuery 选择器
> jQuery选择器是jQuery library中最重要的部分

> jQuery选择器
> > jQuery selectors 允许你选择或者操作HTML元素
> > jQuery选择器是通过HTML元素的name,id,classes,attributes,属性的值和其他更多的value来"find"or"select
> > 它基于当前的CSS selectors和它的一些自定义选择器

>> 所有选择器的语法为:$()

> 通过tagName选择元素
> > jQuery通过元素的名字来选择元素，你能选择页面上所有的<p>元素：

    $("p")

> 通过id选择元素
> >jQuery通过#id 选择到属性为id的HTML 元素，获取到指定元素
> > id在页面中应该是unique的，所以在选择时查找到的元素只会的单独一个，它是独一无二的特殊元素
>> 在通过指定id查找一个元素的时候，写一个哈希字符集

    
    $(document).ready(function(){ 
        $("button").click(function(){
            $("#test").hide();  
        });
    });

> 通过.class 选择器来选择元素
> > jQuery .class 选择器来查询指定元素
> > 通过指定class来找到元素，写一段字符集？？？例如：

    $(".test")
    
    $(document).ready(function(){  
        $("button").click(function(){ 
            $(".test").hide();  
        });
    });
    
    
[更多选择器的查询方法](https://www.w3schools.com/jquery/jquery_selectors.asp)

### jQuery Event Methods
> jQuery在HTML页面专门设计了了响应事件

> 什么是事件？
> > 不同的user在网页上的行为我们称之为事件，做出相对的respond回应这种行为
> > 一个事件代表某物在某时发生的精确操作 例子
> > > moving a mouse over an 元素
> > > 选择一个radio button
> > > clicking on an element
> > 在事件上我们常常使用"fires/fired"这个词语，“按键响应时间fired,当你按下一个键”
> > 下面是一些常用的DOM events:
> > mouse events : click dblclick mouseenter mouseleave. 
> > keyboard events: keypress , keydown , keyup
> > form Events: submit , change, focus, blur.
> > document/ windows events: load resize , scroll, unload.

> jQuery 语法 For Event Methods
> > 在jQuery中，很多的DOM事件等同于，jQuery方法
> > 给所有的段落<p/>标签分配一个click事件。列子：

    $("p").click();

>> 你如果想通过一个函数事件定义，当发生这个事件时，应该要发生什么，例子

    
    $("p").click(function(){  
             // action goes here!!
    } );
    
> 常用的jQuery事件方法

* (document).ready()
> 这个函数允许你在document完全加载好后执行

* click()
> 这个方法在一个HTML元素上绑定了一个事件处理函数
> 函数在HTML元素被点击时候执行
> 下面这个例子是说，当点击这个p元素的时候，隐藏它


    $("p").click(function(){
        $(this).hide();
    });

* dblclick()
> 这个方法在一个HTML元素上绑定了一个事件处理函数
> 在双击HTML 元素的时候会执行这个方法


    $("p").dblclick(function(){ 
        $(this).hide();
    });
    
* mouseenter()
> 这个方法在一个HTML元素上绑定了一个事件处理函数
> 当鼠标指向这个HTML元素时会触发这个事件函数

    
    $("#p1").mouseenter(function(){
            alert("You entered p1!");
    });

* mouseleave()
> 这个方法在一个HTML元素上绑定了一个事件处理函数
> 当鼠标离开指向的这个元素时会触发这个事件函数


    $("#p1").mouseleave(function(){ 
        alert("Bye! You now leave p1!");
        });
        
* mousedown()
> 这个方法在一个HTML元素上绑定了一个事件处理函数
> 当鼠标按下(左键，右键或者滚轮键)的时候，会触发这个事件函数


    $("#p1").mousedown(function(){ 
        alert("Mouse down over p1!");
        });

* mouseup()
> 这个方法在一个HTML元素上绑定了一个事件处理函数
> 鼠标点击后离开会触发的事件


    $("#p1").mouseup(function(){  
        alert("Mouse up over p1!");
        });
        

* hover()
> 这个方法在一个HTML元素上绑定了一个事件处理函数
> 鼠标移动到HTML元素会触发的事件，第一个函数为enter元素的时候，第二个为leave元素的时候


    $("#p1").hover(function(){
         alert("You entered p1!");
        },function(){ 
          alert("Bye! You now leave p1!");
        });

* focus()
> 这个方法在一个HTML表单字段上绑定了一个事件处理函数
> 当聚焦于某一个表单字段的时候会触发这个函数


    $("input").focus(function(){  
        $(this).css("background-color", "#cccccc");
    });
    
* blur()
> 这个方法在一个HTML表单字段上绑定了一个事件处理函数
> 当丢失聚焦后会触发这个函数


    $("input").blur(function(){
         $(this).css("background-color", "#ffffff");
    });

* The on() 方法
> on() 方法对于选择到的元素来说，绑定了一个或者多个事件处理函数
> 例如

    
    $("p").on("click", function(){ 
        $(this).hide();
        });

或者
    
    $("p").on({ 
      mouseenter: function(){
         $(this).css("background-color", "lightgray"); 
      },   
      mouseleave: function(){ 
          $(this).css("background-color", "lightblue");  
      },   click: function(){ 
             $(this).css("background-color", "yellow");  
        } 
    });