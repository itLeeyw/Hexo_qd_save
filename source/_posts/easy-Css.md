---
title: easy-Css
date: 2019-03-07 22:50:20
tags:
---
# **easy-Css**
#### Cascading Sytle Sheets
#### 层叠样式表


# *目录*
### 1.几种CSS的引入方式
### 2. a标签踩坑
### 3. float的魅力
### 4. CSS的常用单位
### end tips


> #### 做前端啊，要回使用各种测量工具,QQ截图，colorpix,FSCapture..
-------------
### 1.几种CSS的引入方式
1. 直接在标签内写（已经被淘汰）
`<body bgcolor="grey">第一种</body>`
2. 使用style属性
`<body style="background-color:grey">第二种</body>`
3.使用style标签 内联
```
    <style>
        body{
            background-color:grey;
            color:red;
        }
    </style>
```
4. link标签 外联
`<link rel="stylesheet" href='外联样式表路径，绝对相对路径都行'>`

5. CSS样式表引入其他CSS样式表
`@import url(路径)；`


### 2. a标签踩坑

##### + 取消下划线
` text-decoration = none;`

### 3. float的魅力
##### + float的BUG
```
    在爸爸爸爸类属性元素上面添加
    
.clearfix::after{
content: '';
display: block;
clear: both;
}

在儿子元素上面添加你需要的flat就ok了

{
    float:left;
}

```


### 4. CSS的常用单位
   #### 1. px 像素
   #### 2. em 相对长度单位
      1. > em的大小不是固定的
      2. > em是继承与父级元素size 
   > 任意浏览器的默认字体高都是16px=1em(未经过调整);
   > 12px = 0.75em 10px = 0.625em;
  


   #### 3. rem CSS新增的相对单位（相对根元素） 
   > + 对于只需要适配少部分手机设备，且分辨率对页面影响不大的，使用px即可 。   
   > + 对于需要适配各种移动设备，使用rem，例如只需要适配iPhone和iPad等分辨率差别比较挺大的设备。
   
   #### 4. % 宽泛的讲是对于父级元素的比例
   > 1. 对于普通定位元素就是我们理解的父元素
   > 2. 对于position: absolute;的元素是相对于已定位的父元素
   > 3. 对于position: fixed;的元素是相对于ViewPort（可视窗口)
   
   #### 5. vw
> css3新单位，viewpoint width的缩写，视窗宽度，1vw等于视窗宽度的1%。举个例子：浏览器宽度1200px, 1 vw = 1200px/100 = 12 px。

   #### 6. vh
   > css3新单位，viewpoint height的缩写，视窗高度，1vh等于视窗高度的1%。举个例子：浏览器高度900px, 1 vh = 900px/100 = 9 px

   #### 7. vm
   > css3新单位，相对于视口的宽度或高度中较小的那个。其中最小的那个被均分为100单位的vm举个例子：浏览器高度900px，宽度1200px，取最小的浏览器高度，1 vm = 900px/100 = 9 px。

### end-tips(很杂，随便看看)

    >  Q:  Html会把span之间所有的回车变成一个空格
            A:  放到同一行就完事啦~ 如果需要空格就加个margin嘛~
    
    > Q:   Body会默认有一个外边距
            A:  干掉他，margin:0;
    
    > Q:  padding是啥 咋用？
            A:  padding是元素内边距
            padding:上(top) 右(right) 下(bottom) 左(left);
            或者分开使用padding-top:20px;
    
    > Q:   活用透明元素，虽然你看不见我，但我确实存在噢
            A:   border-top: 3px solid transparent;(举例不唯一)

    > Q: 一个元素的高度是由什么决定的？
            A  : 是由内容决定
            tips:div 高度由其内部文档流元素的高度总和决定
           
           Q   : 文档流是什么？
                A: 文档内元素的流动方向
                tips:内联元素<span>从左往右流动，块级元素<div>从上往下流动
                
    > Q: 前端怎么调试
            A：border
    
    >Q : 不同于汉字，英文是无法自动换行的。那么我们如何在标签中实现同一个长单词的自动换行呢？
        A: word-break:break-all;(释：打断所有，把单词全部打断)
        
        
    >Q : font-size:100px;到底是什么?
           A: 文本内容基线最高和最低的宽度，为100px
    
    >Q : 为什么我的字体100px，但行高却不是这么多呢？
            A：浏览器会有一个建议行高，有的是1.4有的是1.21倍（跟字体有关，同样的字号，即便固定死了行高，也会有建议行高不同的情况）
            
    >Q: 如果不同的span在同一个div下div的行高会怎样。
            A：以最大span建议行高为基本
    
    >Q: 前端中span字体怎么对齐
            A: 默认基线对齐，四线谱~
    
    >Q：如何避免以上这些关于行高的蠢问题？
            A: line-height设大一点（比内联的任何元素行高都大），字体选择一样的
    
    >Q:咱宽高老是出问题 咋办？
        A:没事别设置height和width 100%和固定宽高，BUG的根源啊喂！QAQ
        
    >Q: 居中好难鸭  有啥子简单方法咩？
           A:  margin-left:auto;
            margin-right:auto;
            /*so easy*/
            
    >Q:  为啥我span设置了宽高但是没效果鸭？
           A:  span不能改变宽高啊笨蛋！！
           Q: 那可咋整啊？？？？？
                A: 你可以把他设置成可以调整宽高的样子嘛~
                    display:inner-block;
    
    >Q:我这样设置宽高并且垂直水平居中 感觉自己贼厉害!!
    
                    width: 70px;
                    height: 29px;
                    line-height: 29px;
                    text-align: center;
          A: 新手!  看我
          
                padding: 4px 16.5px;  流弊不流弊
                但是由于机器不同，所以我们还是需要明确一下
                line-height:XXpx;
                
    >Q: 如何尽量避免BUG???
        A: 尽量避免写宽高这两个奇怪的东西，我们由内向外来控制大小
        padding margin
     
     
    >Q: position里面fixed和absolute有什么区别鸭！？
            A:fixed 相对于网页窗口绝对定位
              absolute 相对于离自己最近的relative祖先绝对定位
    
    >Q:  为啥我float以后感jio我有些地方变窄了？
            A:  因为float会默认压缩鸭
            
    >Q: border-box和content-box有什么区别鸭？
            A:  border-box 是包含padding,margin border的和的面积
                content-box 真正的面积是不把padding margin border包含在内容中的大小
                

![border-box](https://i.loli.net/2019/03/11/5c85edd2eafdc.png "border-box")

![content-box](https://i.loli.net/2019/03/11/5c85edf40bfd5.png "content-box")
