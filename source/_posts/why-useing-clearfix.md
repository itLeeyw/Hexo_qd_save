---
title: 解决CSS的定位方案！(clearfix)
date: 2019-05-29 20:44:55
tags: clearfix,清除浮动，闭合浮动,BFS,CSS,HTML
---

# 前置知识
## 一般我们使用那些定位？
#### 1. staic(普通定位流/默认)
   * block || inline 从上到下 || 从左到右排列布局

#### 2. float(浮动定位)
   * value：(none/left/right)
   *  会脱离文档流，但仍然属于父元素

#### 3. position
   * value：(relative/absolute/fixed/sticky)
   > relative
   > > 相对原位置偏移某些距离，但仍然占据原位置的空间
   > > 不脱离文档流(或许?,因为偏移了以后仍然占据原空间)

   > absolute
   > > 寻找父元素的relative，一直向上找青蛙，直到(html/body)
   > > 脱离文档流

   > fixed
   > > 将element固定在窗口的某个相对位置，不随着滚动条的位置变化而变化
   > > 脱离文档流
   
   ##  注意！
   #### 0. 浮动定位解决的问题多个块级元素在同一行显示
   #### 1. block element允许修改尺寸，inline 不允许修改尺寸
   #### 2. 若“一行”内显示不下所有float内容last element则会换行
   #### 3. block or inline or inline-block 再浮动后都会变成block
   
  ---

  # 正片! 如何清除浮动 or 闭合浮动？
  
 #### Q: 为什么浮动这么好却要 ~~清除~~（闭合）浮动?
 #### A: 
 ---
 #### 1. clear ： 译为清除，以下取值详解
 #### 2. 闭合浮动：使浮动元素“闭合”减少浮动带来的影响
---
#### plan 1：给父元素添加空子元素（after），设置clear:both,简单点说就是添加额外的标签
 * clear:none 默认，不做任何操作
 * clear:left 清除前面元素带来的所有左浮动影响
 * clear:float 和楼上类似效果
 * clear:both 清除前面元素所有浮动带来的影响
 
**优势**：代码量少，易学，好懂
**劣势**：推荐


    .clearfix::after{
        content: ''; //添加空元素
        display: block;//设置成块级元素
        clear: both;//清除前面浮动带来的所有效果
    }


#### plan 2: 添加<br/ clear="both">标签，通过其本身HTML特性
   * 在浮动元素的父元素下添加一个last child 标签为<br/ clear="both">
   * OK!
   * 

**优势**： 代码量更少
**劣势**：同有违结构和表现的分离，不推荐

#### plan 3:添加 overflow:hidden;
   * 在浮动元素的父元素下添加CSS样式 overflow:hidden

**优势**：代码量更更少了
**劣势**：内容增多会造成不会自动换行导致内容被隐藏，无法显示要溢出的内容
注意：(这个bug写者并没有实验出来)，但既然已经有人排过雷便少使用此方法罢。

#### plan 3:添加 overflow:auto;
   * 在浮动元素的父元素下添加CSS样式 overflow:auto

**优势**：代码量更更更少了...
**劣势**：冒失雷挺多的，不要使用




#### plan 5:添加 display:table;
  * 在浮动元素的父元素下添加CSS样式 display:table;

**优势**：代码量... 懂的
**劣势**：盒模型属性改变，造成的影响可能比带来的好处要大，不推荐


### 小结：
* 推荐Plan 1
* “闭合”浮动无非是两种方法:
    > 1. 通过在浮动元素末尾添加一个元素 然后clear:both
    > 2. 通过overflow or display:table 闭合浮动

* 如何理解其中原理 便看我另一篇文章《（Block formatting contexts）BFS是啥子？》


    参考资料：
   * [《那些年我们一起清除过的浮动》]( http://www.iyunlu.com/view/css-xhtml/55.html)
   * [《清除浮动的多种方式》](https://cloud.tencent.com/developer/article/1438265)
   * [Css clear Property](https://www.w3schools.com/cssref/pr_class_clear.asp)
   * [Css float Property](https://developer.mozilla.org/zh-CN/docs/CSS/float)