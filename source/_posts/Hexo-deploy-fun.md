---
title: easy_Hexo
date: 2019-03-07 13:01:51
tags:
---
### _Hexo在github上的部署方法_

# 目录
### 1. GitHub配置
### 2. Hexo配置
### 3. 初始配置成功后再次创建博客
### 4. 注意
### 5. 主题设置



## 1. Github配置
### 创建一个名字为：_你的github用户名.github.io_ 的仓库
### 若不会创建github 详见我如何创建github博客



## 2. Hexo配置
```
1. mkdir repo _(repo可以是任意名字)_
2. cd 到repo
3. npm install -g hexo-cli _安装 Hexo_
4. hexo init myBlog _初始化一个博客myBlog为你的项目名称，（可以为任意名称）_
5. cd myBlog
6. npm i
7. hexo new 大吉大利，今天开博  _new出你的博客，这个时候你会看到一个md文件_
8. start source/_post/开博大吉.md *edit你的博客，语法详见我第四篇博客*
9. start _config.yml，编辑网站配置
*    把第 6 行的 title 改成你想要的名字
+    把第 9 行的 author 改成你的大名
-    把最后一行的 type 改成 type: git
*    在最后一行后面新增一行，左边与 type 平齐，加上一行 repo: 仓库地址 （请将仓库地址改为「你的用户名.github.io」对应的仓库地址，
+    仓库地址以 git@github.com: 开头你知道吧？不知道？不知道的话现在你知道了）
-    第 4 步的 repo: 后面有个空格，不要眼瞎。
10. npm install hexo-deployer-git --save _安装 git 部署插件_
11. hexo deploy _部署_
```
### 12. 进入「你的用户名.github.io」对应的 repo，打开 GitHub Pages 功能，如果已经打开了，你应该会看到一个预览链接
### 13. 访问这个连接，访问成功！
-----------
## 3.初始配置成功后再次创建博客

```

### 1. hexo new 第二篇博客
### 2. start 第二篇博客路径(相对绝对都ok)
### 3. hexo generate  _生成_
### 4. hexo deploy    _部署_
```

----------------
## 4. 注意
# 注意！你保存的只是你的博客，并没有保存【生成博客的代码】，你需要再创建一个blog-generator(名称任意)的仓库，用来保存myBlog里面的【生成博客的程序代码】
# 如何创建一个新仓库详见我[如何玩转github仓库]博客


## 5.主题设置
```
https://github.com/hexojs/hexo/wiki/Themes 上面有主题合集
随便找一个主题，进入主题的 GitHub 首页，比如我找的是 https://github.com/iissnan/hexo-theme-next
复制它的 SSH 地址或 HTTPS 地址，假设地址为 git@github.com:iissnan/hexo-theme-next.git
cd themes
git clone git@github.com:iissnan/hexo-theme-next.git
cd ..
将 _config.yml 的第 75 行改为 theme: hexo-theme-next，保存
hexo generate
hexo deploy
等一分钟，然后刷新你的博客页面，你会看到一个新的外观。如果不喜欢这个主题，就回到第 1 步，重选一个主题。

```