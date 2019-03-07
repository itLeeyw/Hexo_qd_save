---
title: easy-github
date: 2019-03-07 13:39:25
tags:
---

### _本篇博客主要为 Git与GitHub的交互操作_

# 目录
## 一、准备工作
### 1. 安装Git Bash
### 2. 配置Git Bash
### 3. 一定运行的命令
### 4. 配置GitHub
#### 4. 1 进入Keys配置页
#### 4. 2 生成🔒
### 5. 使用Git生成一个本地Key
## 二、使用Git
    + 三种方式
### 1. 初始化并创建仓库
### 2. bulabula~
### 3. 总结性发言
## 三、上传到 GitHub
### 1. 创建新的仓库（二中已完成）
### 2. 图操
### 3. 执行相关命令
### 3. 5 如果二次Edit file
### 4. 例子
### 5. Clone仓库到本地
## 4. 其他命令


# 一、准备工作
### 1. 安装Git Bash
### [下载链接](https://pan.baidu.com/s/1op0QmiOBZD-sYduV2B9yNw)提取码：uxb0 
### 2.下面就随便[配置](http://www.baidu.com)一下界面字体什么
-----
### 3. 在命令行运行下面这五句话
'''flow
git config --global user.name xxxxxx(把xxxxxx替换成你的英文名字随便什么都行)                                      
git config --global user.email xxxxxx(把xxxxxx替换成你的邮箱跟github一致或者不一致也行)                                  
git config --global push.default simple                                             # 本来我写的是 matching，不过想了想可能 simple 更好
git config --global core.quotepath false                                           #防止文件名变成数字
git config --global core.editor "vim"                                                   # 使用vim编辑提交信息

'''

### 4. 配置GitHub
#### 1. 进入https://github.com/settings/keys (肯定得配置一个🔒和🔑嘛~
#### 2. 咋在git上面***生成***一个🔒
```
ssh-keygen -t rsa -b 4096 -C "你的邮箱" (回车三次)
cat ~/.ssh/id_rsa.pub   （复制key到key）
Add SSH key 配置完成~
```
### 5. Git运行
`ssh -T git@github.com` (输入yes~)
#### 出现Permission denied (publickey).就是失败，Hi FrankFang! You've successfully authenticated, but GitHub does not provide shell access. 就说明你成功了！

## ok、SSH key添加好了

```一台电脑只需要一个SSH key
它用来访问你的仓库，all
如果你新买了一台电脑，就再用以上方法Add SSH key
如果你删除了key，就重新生成一个key，替换之前的key```


--------------

# 二、使用git
    + 三种方式
       1. 只在本地使用
       2. 将本地文件上传到gayhub
       3. 将gayhub上的仓库下载或者clon
       4. gayhub?思想逐渐变gay

## 1. 初始化
    1. 1 创建一个项目目录:mkdir git-demo-1
    1. 2 进入目录 cd git-demo-1
    1. 3 git init ，初始化，这句命令会在git-demo-1中创建一个.git目录
    1. 4 ls -la 你就会看到.git目录，他就是一个仓库
    1. 5 在git-demo-1目录中添加任意文件
        '''
        1. touch index.html
        2. mkdir css
        3. touch css/style.css
        '''
    1. 6 运行git status -sb 可以看到文件前面有 ***??*** 号
       + ***这个问号的意思是，git不知道你要怎么对待这些变动***
    1. 7 使用git add 将“变动”添加到【暂存区】
       + 你可以一个个的add
        ' 1. git add index.html '
        ' 2. git add css/style.css'
       + 你也可以一次性add
        ' 1. git add . '
    1. 8 再次运行 git status -sb 可以看到 ***??*** 变成了 ***A***
        + A的意思是添加，告诉git这些文件我都要添加至仓库
    1. 9 使用git commit -m "信息（任意）" 将 ***add*** 内容【正式提交】到本地仓库 并添加注释信息，方便以后查询
        + 一个个commit
           1. git commit index.html -m "添加index.html"
           2. git commit css/style.css -m "添加css/style.css"
        + 一次性commit
           1. git commit . -m "添加多个文件"

    1. 10 再再次运行git status -sb ，发现没有文件变动，因为文件的变动已经记录至长裤
    1. 11 使用 ***git log*** 查看历史变动
    1. 10 若再次变动文件，保存变动后执行
        'git add 变动文件'
        'git commit -m "更新变动文件"'
    1.11 ***git status -sb 查看文件变动信息***

### 总结
    1. git init，初始化本地仓库 .git
    2. git status -sb，显示当前所有文件的状态
    3. git add 文件路径，用来将变动加到暂存区
    4. git commit -m "信息"，用来正式提交变动，提交至 .git 仓库
    5. 如果有新的变动，我们只需要依次执行 git add xxx 和 git commit -m 'xxx' 两个命令即可。别看本教程废话那么多，其实就这一句有用！先 add 再 commit，行了，你学会 git 了。
    6. git log 查看变更历史

----
# 三、上传到GitHub
    1. 创建一个新的仓库
    2. 下为图操
    ![点击SSH](https://video.jirengu.com/FqewHjBnXJH9_TAeV_JaC3gGVFsT "ssh")
    ![简单介绍](https://video.jirengu.com/Fta476rO6oPJIgxbIec8vINTZV3E)
    ## ***看图，点击 SSH 按钮，点击 SSH 按钮，点击 SSH 按钮，我想你现在肯定不会忘了点击 SSH 按钮了吧~~~~如果不点击这个按钮，你就会使用默认的 HTTPS 地址。但是千万不要使用 HTTPS 地址，因为 HTTPS 地址使用起来特别麻烦，每次都要输入密码，而 SSH 不用输入用户名密码。为什么 SSH 不用密码呢，因为你已经上传了 SSH public key。还记得吗？***
    3. 我们已经有了本地仓库 于是
        1. 找到图中的「…or push an existing repository from the command line」这一行，你会看到 git remote add origin https://github.com/xxxxxxxxxx/git-demo-1.git， 如果你发现这个地址是 https 开头的，那你就做错了，还记得吗，我们要使用 SSH 地址，GitHub 的 SSH 地址是以 git@github.com 开头的。
        2. 再次「点击 SSH按钮」，点击之后，整个世界就会变得美好起来
        3. 得到新的命令 git remote add origin git@github.com:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx/git-demo-1.git，复制并运行它
        4. 复制第二行 git push -u origin master，运行它
        5. 刷新当前页面，你的仓库就上传到 GitHub 了！
## 如何上传更新
'''
git add 文件路径
git commit -m "信息"
git pull （如果其他人提前更新仓库，你得先下载（更新）仓库）
git push
'''
###例子
'''
cd git-demo-1
touch index2.html
git add index2.html
git commit -m "新建 index2.html"
git pull
git push
'''

## 如何下载Github已有的仓库到本地
![图解](https://video.jirengu.com/FkftOFnWOoe3W6SKetIjskFZun1p "图解")
1. 关键命令 git clone
![下载](https://video.jirengu.com/Fh5OogA65vQk3_r78zxMNhb7pWYW 'download')

### 开始***clone***

1. 确保弹出层里的地址是 SSH 地址，也就是 git@github.com 开头的地址，如果不是，就点击 Use SSH 按钮。然后复制这个地址。
2. 打开 Git Bash，找一个安全的目录，比如 ~/Desktop 桌面目录就很安全：cd ~/Desktop。运行。
3. 运行 git clone 你刚才得到的以git@github.com开头的地址，运行完了你就会发现，桌面上多出一个 git-demo-2 目录。
4. 进入这个多出来的目录
5. 运行 ls -la 你会看到，远程目录的所有文件都在这里出现了，另外你还看到了 .git 本地仓库。这是你就可以添加文件，git add，然后 git commit 了。

## 4.其他命令
+ git remote add origin git@github.com:xxxxxxx.git 将本地仓库与远程仓库关联
+ git remote set-url origin git@github.com:xxxxx.git 上一步手抖了，可以用这个命令来挽回
+ git branch 新建分支
+ git merge 合并分支
+ git stash 通灵术
+ git stash pop 反转通灵术
+ git revert 后悔了
+ git reset 另一种后悔了
+ git diff 查看详细变化