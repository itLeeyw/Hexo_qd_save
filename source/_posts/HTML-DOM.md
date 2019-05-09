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


## JavaScript HTML DOM EventListener
 >  添加一个监听方法
 >  The addEventListener() method

   
    //当用户点击按钮的时候触发时间监听   document.getElementById("myBth").addEventListener("click",displayDate)

> 1.addEventListener()将时间处理程序添加到指定的元素上
>
> 2.且它不会覆盖已有的事件处理程序
> 
> 3.你可以给除了HTML 元素的其他元素如windows object等某一元素添加多个处理事件（也可以是同一触发条件触发的多个事件处理程序）
> 
> 4.它同样可以更容易的处理和控制事件的冒泡行为
> 
> 5.使用它的时候可以为你带来更好的可读性，且JavaScript于HTML标记分离开处理，允许你添加事件监听，即便你不控制HTML的标记
> 
> 6.你可以使用它更简单的移除掉事件监听 通过removeEventListener()

Syntax:   

    element.addEventListener(event, function, useCapture);
first parameter : 事件类型，"click" or "mousedown"..
secand parameter : 处理函数
third parameter : 是否指定冒泡捕获，用Boolean value 确定，可选参数
> onclick != click
> click 是对象的方法，  onclick是事件，
> 我们在点击按钮时会先执行onclick 然后执行click，因为onclick是点击事件，首先触发事件，然后触发事件的点击方法，
> 得出，我们即便不添加点击方法(click) 也会触发点击事件~~~

> 给一个元素添加一个事件处理程序

> 让一个元素在触发点击方法的时候弹出“hello world”的alert
    
    element.addEventListener("click", function(){ alert("Hello World!"); });

> 当然 ，你也可以引用外部函数

    element.addEventListener("click", myFunction);
    function myFunction() {
    alert ("Hello World!");
    }
    
> 给同一个元素添加多个事件处理程序

    element.addEventListener("click", myFunction);
    element.addEventListener("click", mySecondFunction);
> 此时会按照程序顺序依次执行事件处理程序

> 将不同类型的处理函数添加到同一元素中

    element.addEventListener("mouseover", myFunction);
    element.addEventListener("click", mySecondFunction);
    element.addEventListener("mouseout", myThirdFunction);

> 在window object上添加事件处理程序
> > 你可以在任何HTML DOM 上使用addEventListener()添加事件监听处理，(如：xmlHttpRequest Object

> 用户改变窗口大小时的事件监听

    window.addEventListener("resize", function(){  
    document.getElementById("demo").innerHTML = sometext;
    });

> 传递参数
> 在用户触发事件时可做传递参数的函数使用

    element.addEventListener("click", function(){ myFunction(p1, p2); });

> 事件的冒泡和捕获？
> >HTML DOM 中有两种方式传递事件，1. 冒泡 2.捕获
> >事件的传播是一种定义元素发生时事件时顺序的的方法？？
> >例如：<div>中<p>的click被点击，先触发那个的click？

>所以我们可以通过第三个参数来控制，当为false时则采用冒泡，

>若为ture时 则采用捕获

    document.getElementById("myP").addEventListener("click", myFunction, true);
    document.getElementById("myDiv").addEventListener("click", myFunction, true);

> 可以通过removeEventListener()来移除已有的处理程序

## DOM Nodes
> 根据W3C标准，一切东西在HTML document中都是一个Node(节点)

* 文档是文档节点
* 所有的元素是元素节点
* 在HTML 元素中的文本是文本节点
* 所有的属性是属性节点（弃用）
* 所有的注释都是注释节点

> JavaScript能访问所有存在于节点数中的节点
>  可以对节点进行增删改的操作 


> 节点之间的关系

> 显而易见，结点之间有着层级关系
> 
> 他们之间通过，parent,child,sibling来组成的关系网

* 在节点树种，最顶上的节点就是root，称为根节点
* 除根节点之外，所有的节点都有一个爸爸节点parent
* 一个节点可以有很多的子节点
* siblings 有相同的parent

> 节点与节点之间的跳转，导航
> > JavaScript可以使用以下一些属性在节点直接跳转

* parentNode//爸爸节点
* childNodes[nodenumber] //儿子们节点
* firstChild //第一个儿子节点
* lastChild//最后一个儿子节点
* nextSibling //下一个兄弟节点
* perviousSibling//上一个兄弟节点
* 小操作：获取到你爸爸节点的儿子们节点，排除自己就能获取到所有的兄弟节点辣

> 子节点和节点值
> DOM 经常会让你想获取的期望节点种含有文本
> 元素节点中的文本节点可以通过innerHTML访问
> innerHTML方法和访问元素节点的第一个子节点的nodeValue的值一样
> 或者直接使用childNodes[0].nodeValue 的结果一样

> nodeName Property总是会返回一个大写的tag name
> nodeValue 返回一个指定节点的值

 * 如果是一个元素节点则返回null
 * 如果是一个文本节点则返回文本
 * 如果是一个属性节点，则返回属性的值

> nodeType Property 返回节点的类型

* ELEMENT_NODE   === 1
* ATTRIBUTE_NODE  === 2
* TEXT_NODE === 3
* COMMENT_NODE === 8 
*  DOCUMENT_NODE === 9
*  DOCUMENT_TYPE_NODE === 10

## JavaScript HTML DOM Element(Nodes)
> 添加或者删除元素节点

> 创建一个新的元素节点首先需要创建一个元素，然后将这个元素添加到已有的元素当中去
    
    document.createElement(TagName)
    document.createTextNode(TextContent)
    appendChild(Node)
    element.appendChild(NodeElement)
    
> 创建一个新的元素---->insertBefore()
> > appendChild()方法在上面的列子中，添加了一个新的元素在parent的last Children
> > 如果你不想那样，则可以使用insertBefore()方法
> > parent.insertBefore(newNode,child)//将newNode节点添加到child之前

> 删除一个已有的元素
> 删除一个已有的元素，你首先得知道它的父亲元素

    var parent = document.getElementById("div1");
    var child = document.getElementById("p1");
    parent.removeChild(child);
    
>//IE所有的版本都不兼容node.remove()方法 


>替换某个元素
>>如果你要在HTML DOM中替换某个元素，就使用replaceChild() 方法
>> first find parent element then find 你要替换的元素，然后通过你已经创建好的新元素使用replaceChild(para,child)来替换

    
    var para = document.createElement("p");
    var node = document.createTextNode("This is new.");
    para.appendChild(node);
    var parent = document.getElementById("div1");
    var child = document.getElementById("p1");
    parent.replaceChild(para, child);


## JavaScript HTML　DOM　Colection

> 对于HTMLCollection 对象
> > 对于getElementByTagName()方法，他会return一个HTMLCollection对象
> > 一个HTMLCollection 对象是一个在HTML Element中的一个类似数组的列表（collection）


Example:
    
      var x = document.getElementByTagName(Tag)
> 我们可以使用index number来访问collection的元素
> 例如 访问第二个tag元素我们可以这样写：

    y = x[1]//index number 从 0 开始
    
> HTML 中HTMLCollection 的长度
>> 对于length属性是在colection中的元素数量

       var myCollection = document.getElementsByTagName("p");
    document.getElementById("demo").innerHTML = myCollection.length;
    
    1. 创建一个p的collection
    2. 获取到collection的长度
    
> 长度的作用 可以让你loop完所有的元素  好用的一匹
        
    var myCollection = document.getElementsByTagName("p");
    var i;
    for (i = 0; i < myCollection.length; i++) {  
    myCollection[i].style.backgroundColor = "red";
    }
    
  > An HTMLCollection is NOT an array!
  > HTML collection 不是不是不是一个数组啊啊啊！！
  > 它看起来像，但它不是
  > 你可以遍历列表和get单个元素，这让他看起来像一个数组
  > 然鹅，你不能在HTMLCollection上使用Array的方法
  > push pop valueOf join .... 这些都不行
  
  ## JavaScript HTML DOM Node Lists
  > 关于HTML DOM Nodelist 对象

* NodeList 对象是一个List(collection)它从document中提取出来
* NodeList 对象几乎等同于HTMLCollection 对象
* 一些浏览器会返回NodeList对象来代替HTMLCollection对象对于getElementByClassName()方法
* 所有浏览器使用childNodes方法都会返回NodeList对象
* 大部分的浏览器使用querySelectorAll()方法会返回一个NodeList对象


> HTML DOM Node List Length
> MyNodelist.length

> HTMLCollection 和 NodeList 有什么不同

1. HTMLCollection是collection的HTML元素
2. NodeList是collection的Document节点
3. NodeList和HTML collection有很多相同的东西(功能)
4. HTMLCollection和NodeList都是类似数组的集合
5. 两者都有length，用于记录列表中的item数目
6. 两个都提供了index(0,1,2,3,4..)访问
7. 可以通过items name id 来访问HTMLCollection
8. NodeList只能通过索引访问
9. 只有NodeList含有属性节点和文本节点