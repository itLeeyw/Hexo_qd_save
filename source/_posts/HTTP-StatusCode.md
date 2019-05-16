---
title: HTTP-StatusCode
date: 2019-05-16 20:58:28
tags:
---

## HTTP　状态码
>　Ｓｔａｔｕｓ－ｃｏｄｅ为服务器的返回值，是用３个数字来表示，第一个数字是作为状态码的分类，后两位数字只做类别再次细分不做大类分别

1. 1XX:信息(Informational)
    > 请求已经收到，请求过程正在继续
    
    * 100 Continue
        > Client 应当继续等待请求，这个是Server端的临时状态，用于通知服务端
    
    * 101 Switching Protocols
        > 请求者已要求服务器切换协议，服务器已确认并准备切换。
    


2. 2XX:成功(Success)
    > 请求成功，被服务器理解并允许访问

    * 200 OK
        > 服务器已成功处理了请求，表示服务器提供了被请求的网页。
    
    * 201 Create
        > 请求成功并且创建了新的资源

    * 202 Accepted
        > Server已接受请求，但尚未处理，也可能请求的是Server有意拒绝的服务，导致请求失败。
    
    * 204 No Content
        > 请求到了 但服务器没有返回内容
    
3. 3XX:重定向(Readirecion)
    > 必须进一步的采取行动操作才能完成请求
   
    * 304 Not Modified
     > 表示请求后但资源暂未被修改
     
4. 4XX:客户端错误(Client Error)
    > 请求失败，语法错误或某些操作无法完成
    
    * 400 Bad Request
        > 请求过程中，语法格式错误(域验证错误，缺少数据等
        
    * 401 Unauthorized 
      >  没有被授权访问，需要用户身份验证，与403 Forbidden类似，但特别适用于可能进行身份验证但已失败或尚未提供的情况。响应必须包含WWW-Authenticate头字段，其中包含适用于所请求资源的讯息
        
    *  403 Forbidden
    
        > 服务器理解请求(请求合法)，但拒绝。与401不同的是这与授权验证无关，若不希望将此页面信息交给用户，则可以使用404status code
        
        
    *  404 Not Found
        > 服务器没有找到Requests-URI匹配的任何内容，不确定是永久性或是暂时性，服务器可以通过一些配置告知客户端旧资源是不可见且无重定向地址，则我们可以使用410(Gone)状态码
        > 
        > 服务器若不希望确切说明请求被拒绝原因时或没有其他相应适用的时候常用此状态码 
   
   * 409 Conflict
        > 服务器在完成请求时发生冲突。 服务器必须在响应中包含有关冲突的信息。
    
    
5. 5XX:服务器错误(Server Error)
    > 服务器并未能完成一个明显(合法)的请求
   
  *  500 Internal Server Error
      >   服务器内部错误）  服务器遇到错误，无法完成请求。
    
### 参考文献
[参考1](https://www.restapitutorial.com/httpstatuscodes.html)
[维基百科](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)