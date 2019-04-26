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
   ### 5. CSS布局问题
   ### end tips


> #### 做前端啊，要回使用各种测量工具,QQ截图，colorpix,FSCapture..
-------------
### 1. 几种CSS的引入方式
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



### 5. CSS布局问题（超大量图文警告）
> #### css的水平对齐&垂直对齐问题一直是让人摸不着头脑的知识，这一章节将让你深入了解css的对齐方法

   #### 1. 将会用到的关键字
```
    1. margin 外边距
    2. padding 内边距
    3. auto  自动
    4. top   上
    5. right 右
    6. bottom   下
    7. left  左
    8. float 浮动
    9. table 表单
    10. position 定位
    11. relative  相对定位
    12. absolute 绝对定位
    12.5. fixed 固定定位
    13. box-sizing 盒子样式
    14. border-box 边框盒子 /具体可以在本篇博客收到具体解释
    15. conten-box 内容盒子 /具体同上
    16. display 陈列关键字
    17. flex 伸缩模型
    ... 
```
   ##### 2.两栏布局理解以及具体实现方法
   > 两个盒子平行布局
   ##### 原样式
   
   ![原样](https://i.loli.net/2019/03/14/5c89e19b3ef58.png)
   
   ##### float 实现
   ![float](https://i.loli.net/2019/03/14/5c89e24ac81a4.png)
   + #### 这里要注意，float实现会导致元素错位和坍塌（如何解决）
   
   ![坍塌问题](https://i.loli.net/2019/03/14/5c89e795d2331.png)
   
>   ##### 2.绝对定位

![绝对定位](https://i.loli.net/2019/03/14/5c89e88d220ea.png)   
   + #### 相对定位和绝对定位是什么？
   ```
    通常情况下 position 的默认值是static,就是没有定位。
    如果设置了position 其他属性那么就会脱离文档流
    则可以通过left top right bottom等操作进行对元素块的控制
    # 一般来说只有设置了position 才可以使用 top left等操作，z-index也无法生效
   ```
> ##### 相对定位 raletive
+ > ###### 相对定位并不脱离文档流
    一般两个配合使用，但是也可以单独使用，需要注意的是，raletive在进行元素偏移以后仍然占据没有偏移之前的空间，（偏移不是边距，相当于∪）

![相对定位.PNG](https://i.loli.net/2019/03/14/5c8a303ebed7f.png)

> ##### 绝对定位 absolute
+   > 绝对定位脱离文档流
    
```
    在布置文档流中文件时，绝对定位元素不会占据空间。
    绝对定位元素相对于最近的非static祖先元素做绝对定位，当这样的祖先元素不存在的时候，则相对ICB(initel container block 初始包含块)

```

![捕获.PNG](https://i.loli.net/2019/03/14/5c8a33ade5f1a.png)

#### 2. 三栏布局
> 一般为两边固定，中间自适应
+ > 1. 使用margin手动自适应 -_-||
![margin.PNG](https://i.loli.net/2019/03/14/5c8a373c80bfa.png)
+ > 2. 使用左右栏浮动的方法再进行margin

![左右栏浮动.PNG](https://i.loli.net/2019/03/14/5c8a396e67cee.png)

+ > 3. 使用[flex](https://developer.mozilla.org/zh-CN/docs/Web/CSS/flex)布局实现（弹性盒子） 

![flex.PNG](https://i.loli.net/2019/03/14/5c8a397580481.png)

+ > 4. 使用table布局(将容器变为单元格子table-cell)
        > + 高度由文档流决定
![捕获.PNG](https://i.loli.net/2019/03/14/5c8a3a68e5c4b.png)

+ > 5. 使用gird布局（设置行高和列，与table有异曲同工之处）

![gird布局.PNG](https://i.loli.net/2019/03/14/5c8a3b4b28254.png)


+ > 6. 圣杯布局
    >> + 圣杯布局和双飞翼布局 实现的都是三栏布局，两边的盒子宽度固定，中间盒子自适应
    
+ > 7. 双飞翼布局 (用的少，直接用flex就ok了 以后去面试的时候可以背一下~)


# 参考文献:
[详解七种CSS布局方法](https://blog.csdn.net/ganyingxie123456/article/details/77054124)
[position mdn](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position)
[float mdn](https://developer.mozilla.org/zh-CN/docs/CSS/float)
[flex mdn](https://developer.mozilla.org/zh-CN/docs/Web/CSS/flex)
[table mdn](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/table)

-------------------






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
    >Q: 为啥我的内联元素在下设置了padding 和 margin 依然没有得到我想要的效果？
            A: 因为内联元素不是block 只能设置padding的左右间距不能改变上下，必须要设display:inline-block才能撑起来
               内联元素无法通过margin 0px auto；来达到居中效果，必须使用到他的父标签,在父标签上设置text-align:center才能实现居中
    
    >Q：我想对所有的动画效果有一个延时进行 怎么办?
            A: transition: all Xs;

    >Q: 如何将文字光标改成指针光标？
           A:  cursor: pointer;

    >Q: 我对内联元素使用了display:inline-block;以后bottom会多出一小截距离咋办？
           A: 这是bug 我们可以使用vertical-align:top；来解决这个bug(有时候也不会出现这种bug)
    >Q: 为什么我的body 无法占满屏幕 有间距
           A: 因为这是body自带的8像素margin
![border-box](https://i.loli.net/2019/03/11/5c85edd2eafdc.png "border-box")

![content-box](https://i.loli.net/2019/03/11/5c85edf40bfd5.png "content-box")
