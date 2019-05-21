---
title: CreateFreeCloudServer
date: 2019-05-21 23:31:46
tags:
---
# 在你的网页上创建一个免费的数据库(leancloud)
## 1.[注册账号](https://leancloud.cn/dashboard/login.html#/signup)
## 2. 创建应用

## 3. 进入[快速入门](https://leancloud.cn/docs/start.html)页面选择你的主要编译语言

## 4. 下载 or 引入 服务

    <script src="//cdn.jsdelivr.net/npm/leancloud-storage@3.13.2/dist/av-min.js"></script>
    
## 5. init

    
    var APP_ID = 'you APP_ID';
    var APP_KEY = 'you APP_KEY';

    AV.init({
      appId: APP_ID,
      appKey: APP_KEY
    });
    
## 6. 验证
    
    ping "kdqicvul.api.lncld.net"
    
    and
    
    /.js
    var TestObject = AV.Object.extend('TestObject');var testObject = new TestObject();
    testObject.save({
      words: 'Hello World!'}).then(function(object) {
      alert('LeanCloud Rocks!');})
      
      
## 7. 获取后端数据？查看API文档
