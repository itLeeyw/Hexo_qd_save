---
title: HTML-DOM
date: 2019-05-06 22:02:54
tags:
---
# 认识DOM
## DOM 基础
> When a web page is loaded, the browser creates a Document Object Model of the page.The HTML DOM model is constructed as a tree of Objects:
> 译: 当加载一个网页的时，浏览器会创建一个由文档、对象、模式组成的页面，这个HTML DOM 构造了一个对象树

> What You Will Learn?
> Change to HTML elements and Style(CSS) and lesten to DOM event and add or  delete HTML element
> DOM is a W3C standard,that is define for  accessing documents

> What is the HTML DOM?
> The HTML DOM is a standard object model and programming interface  for HTML . it define:
> HTML element as Object
> all properties in HTML element 
> thet events for all HTML element 
> the methods to access all HTML element
## HTML DOM 的方法
> HTML DOM 方法是一个可以执行的动作(在HTML element中)
> HTML DOM 属性是一个value(在HTML element中) 所以可以设置或者改变它

>  about DOM Programming Interface .
>  HTML DOM 用Javascript或者其他的编程语言进行访问
>  在DOM中，所有的html元素都是Object
>  编程接口是每个对象的属性和methods
>  property是一个value你可以get or set 这个value
>  method 是一个动词，你可以对HTMl元素进行添加和删除
例子：
    <!DOCTYPE html>
    <html>
    <body>
    <h2>My First Page</h2>

    <p id="demo"></p>

    <script>
    document.getElementById("demo").innerHTML = "Hello World!";
    </script>

    </body>
    </html>
    <!DOCTYPE html>
    <html>
    <body>

    <h2>My First Page</h2>

    <p id="demo"></p>

    <script>
    document.getElementById("demo").innerHTML = "Hello World!";
    </script>

    </body>
    </html>
> 在上面例子中，**getElementById** 是一个方法，但是在HTML中，它是一个属性

> The** getElementById** Method 是最常见的访问HTMl中页面元素的方式。
> 上面的例子中getElementById 方法使用 id="demo"寻找到元素

> **innerHTML**属性是最简单获取元素中内容的方法
> **innerHTML** property 可以很有效的获取或者改变页面元素内容
>> innerHTML可以改变任何HTML element的内容，包括<body> 和 <html>

## The HTML DOM Document
> HTML DOM Document Object 是你Web page中所有其他对象的所有者(爸爸)

> About HTML DOM Document
> 1. document Object 就是你的web page
> 2. 如果你想访问你web page的任何元素，你都是从document Object开始的
> 3.下面的一些例子将会告诉你操作和访问HTML的办法

>  寻找 HTML Elements ?
    
    Method
    document.getElementById(id) //通过元素id寻找元素
    
    document.getElementsByTagName(name)//通过标签名字寻找元素s
    
    document.getElementsByClassName(name)//通过class的名字寻找元素s

> 改变页面元素？ 

    Property

    element.innerHTML =  new html content //更改元素内容
    
    element.attribute = new value//更改元素属性值    
    
    element.style.property = new style //更改元素的style(CSS)
    
    Method
    element.setAttribute(attribute, value)//改变元素的属性值

> 添加和删除元素？
 
    Method    
    document.createElement(element)//创建一个HTML元素

    document.removeChild(element)//移除一个HTML元素儿子

    document.appendChild(element)//添加一个元素儿子

    document.replaceChild(new, old)//替换一个元素儿子

    document.write(text)//Write into the HTML output stream
 
> 添加一个事件处理函数？
    
    Method 
    document.getElementById(id).onclick = function(){code} //添加一个事件处理程序，code中为onclick 事件

> Finding HTML 对象 ?
> 第一版的HTML DOM 只定义了11个HTML 对象，对象集合和性质。这是在HTML5中仍然有效的，后来有了第三版的HTML DOM 添加了很多的对象，集合以及性质
![a9cfd0a63e16b169ff2f19d00d005c88.png](en-resource://database/1306:1)

## JavaScript HTML DOM 元素
> 这将教你如何查找访问到一个page中的element

> 查找HTML 页面元素
>  通常你会想使用JavaScript操作HTML的元素
>  To do so， 你首先得找到element，有几种办法可以实现：

    寻找页面元素 By （Id ，Tag name, Class name, Css selectors , HTML Object Collections） 
    
> 通过Id 寻找页面元素
> > 这是寻找页面元素最简单的办法。例如：


    var myElement = document.getElementById("intro");


> 如果寻找到了元素，则会返回一个元素作为对象，如果没有找到，则会返回null

> 通过标签名字找元素
    
     var x = document.getElementsByTagName("p");
     
> 通过类名找元素

       var x = document.getElementsByClassName("intro");

> 通过Css选择器找元素
> > 如果你想找到所有指定的HTML元素的CSS选择器(id,class names, types, attributes, value of attributes, etc ),则可以使用querySelectorAll()方法

    var x = document.querySelectorAll("p.intro");
> querySelectorAll()不支持IE8以及之前版本，ie果然是辣鸡

> 通过对象集 来找元素
> 例子：通过发现表单id为frm1的元素，再遍历元素中的值获取后innerHTML添加内容
    
    var x = document.forms["frm1"];
    var text = "";
    var i;
    for (i = 0; i < x.length; i++) {
        text += x.elements[i].value + "<br>";
    }
    document.getElementById("demo").innerHTML = text;


> 下面的HTML Object和对象集 也可以访问进入使用

    document.anchors
    document.body
    document.documentElement
    document.embeds
    document.forms
    document.head
    document.images
    document.links
    document.scripts
    document.title



## JavaScript HTML DOM - Changing HTML 
> HTML DOM 允许JavaScript 改变page element 内容

> 改变HTML的输出流
> Javascript 能创建 dynamic(动态) 的html内容，通过document.write()直接作为HTML 的输出流
> 例子：输出时间



    <!DOCTYPE html>
    <html>
    <body>
    <script>
    document.write(Date());
    </script>
    </body>
    </html>

> 注意在加载文档之后不要使用document.write()，这会覆盖之前的文档内容

> 改变HTML内容
> 使用inner HTML来修改HTML Element 的content 是 easiest way
>  syntax(语法):
       
    document.getElementById(id).innerHTML = new HTML

> 改变属性的值
> 改变HTML属性值的语法:
    
    document.getElementById(id).attribute = new value


    <!DOCTYPE html><html><body>     <img id="myImage" src="smiley.gif">
    <script>                  document.getElementById("myImage").src = "landscape.jpg";       </script>
    </body></html>

## JavaScript HTML DOM - Changing CSS
> HTML DOM 允许JavaScript改变HTML elements的Style

> 改变HTML 的Style
> 我们要改变HTML元素风格的使用的语法:

    document.getElementById(id).style.property = new style
> 通过下面的例子来改变元素p的Style

    <html><body>
    <p id="p2">Hello World!</p>
    <script>
    document.getElementById("p2").style.color = "blue";
    </script>
    <p>The paragraph above was changed by a script.</p>
    </body></html>


> 利用事件
> > HTML DOM 允许你在事件发生时执行代码
> > 事件是HTML元素在浏览器上"things happen"(事件发生)时生成的

* 元素的点击
* 页面的加载
* 字段的改变

> 你会了解很多的事件
> 下面这个例子改变了HTML Element Style 对于id="id1"的标签，(在点击这个按钮时


    <!DOCTYPE html><html><body>
    <h1 id="id1">My Heading 1</h1>
    <button type="button" 
    onclick="document.getElementById('id1').style.color = 'red'">Click Me!
    </button>
    </body></html>
 >上面这个例子讲事件封装在button中
 
## JavaScript HTML DOM Animation
> 了解如何使用Javascript创建HTML动画

> 一个基础的web页面中，所有的动画应当都基于一个容器
> 分别创建容器样式的风格，以及动画样式的Style
> 动画通过计时器控制，若计时器间隔够小则会让动画看起来十分连续


    var id = setInterval(frame, 5);
    function frame() {  
    if (/* test for finished */) {  
*     clearInterval(id);  

    } else { 
    /* code to change the element style */    
    }
    }
> 动画执行顺序

* 获取动画标签对象
* 设置一个源点(计时)
* 设置间隔(frame,5)参数1是动作，参数2是间隔
* 设置一个动作函数，并设置出点(否则会死循环),若完成动作则使用clearInterval(id)退出，id为setInterval(1,2)的对象
* 此时一个简单动画完成
* 安利一个tween.js的外部库

## JavaScript HTML DOM Events
> HTML DOM 允许JavaScript对于事件做出反应

> 对事件做出反应？
> 当用户点击HTML Elements 时候JavaScript能通过code执行做出相应的反应

>HTML  事件的例子

*  点击鼠标
*  页面加载
*  图片加载
*  鼠标移动到某个元素
*  表单提交
*  敲击键盘

> 我们可以通过封装事件在标签中，或者script的函数中来实现监听效果

> 可以通过分配事件属性给HTML元素
> 分配一个onclick事件给一个按钮元素
    
    <button onclick="displayDate()">Try it</button>

> 指定使用HTML DOM 事件
> HTML DOM 允许你使用JavaScript事件分配给HTML元素
> 例如，我们指定一个onclick事件给按钮元素

    <script>
    document.getElementById("myBtn").onclick = displayDate;</script>
> 上述例子为，将分配一个onclick事件给id为MyBth的标签对象在点击时执行名为displayDate的函数

> 加载页面和离开页面事件 onload and onunload events
> 这两个事件在进入和离开page时发生
> onload 可以用来检测访问者浏览器的版本的类型，然后加载对应的版本信息渲染在web page
> 这两个函数也可以用来处理cookies
> 例子：
    <body onload="checkCookies()">

> onchange 事件
> onchange 事件常常使用在输入字段的验证

    <input type="text" id="fname" onchange="upperCase()">

> 上述例子中，通过在script中使用toUpperCase() 将小写转换成大写

> onmouseover and onmouseout 会在鼠标在标签对象上或离开标签对象上时发生

> onmousedown and onmouseup and onclick 事件是所有的mouse-click，第一个会在鼠标点击的时候发生，第二个会在鼠标释放的时候发生，第三个会在鼠标点击完成后发生
