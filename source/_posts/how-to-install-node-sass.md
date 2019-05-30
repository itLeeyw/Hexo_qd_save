---
title: how-to-install-node-sass
date: 2019-05-30 17:50:54
tags:
---
## plan 1:

 在*macOS*或者*Window*已经配置了**git**在**git bash窗口**的条件下**直接执行**命令：

	//使用淘宝镜像
    SASS_BINARY_SITE=https://npm.taobao.org/mirrors/node-sass/ npm install node-sass 
***若你的window没有git环境***
则依次执行：

    set SASS_BINARY_SITE=https://npm.taobao.org/mirrors/node-sass/
    npm install node-sass

## plan 2：
在你的project下创建一个 **.npmrc** 文件
在文件中**添加** `sass_binary_site=https://npm.taobao.org/mirrors/node-sass/`
再执行    `npm -g install node-sass`

以上安装成功后使用`node-sass -v` 测试安装是否成功