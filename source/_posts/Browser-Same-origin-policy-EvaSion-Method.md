---
title: Browser-Same-origin-policy-EvaSion-Method
date: 2019-05-18 13:47:21
tags:
---
# 浏览器同源政策以及规避方法
> 浏览器安全的基石是"同源政策"（same-origin policy）

## 一、简介
>同源政策为Netscape公司于1995年引入浏览器。
>目前，所有浏览器都实行这个政策

### 1）含义
> "同源"
>> A网页设置Cookie，B网页不能打开，除非“同源”
   
   * “同源”三同：
        1. 协议相同
        2. 域名相同
        3. 端口相同

> 目的
>> 保证Client信息安全，防止被恶意窃取数据。
>> 例如：
>> 用户C访问网站A，用户登陆后又去访问网站B(恶意网站)，若网站B可读取A网站Cookie？
>> 1. B网站通过Cookie获取到用户C的信息（若Cookie包含隐私，则会隐私泄露）
>> 2. 由于Cookie往往是来保存登陆信息，若用户没有退出登陆，则网站B可以冒充用户：为所欲为。浏览器规定：提交表单不受同源政策限制
>> 综上所述
>> 同源政策是必须的，“同源政策”越严格，用户安全性更高，网站安全性更高。（防止Cookie共享）

> 限制范围
> > 若非“同源”，则 共有三种行为限制

   * Cookie,LocalStorage 和 IndexDB 无法读取
   * DOM无法获得
   * AJAX请求无法发送

    虽然这些限制是必要的，但是有时很不方便，合理的用途也受到影响。下述将如何规避这些限制


## 二、Cookie
> Cookie是Server给Browser的一段信息，只有“同源”网页才能共享 但有时同属网页下，会出现一级域名相同二级域名不同的情况？
> 不同的网页通过设置相同的document.domain来共享Cookie
        
        document.domain = "example.com"

所以现在网页A通过脚本设置一个Cookie
    
        documenet.cookie = "test = lwh"
 
 网页B就可以读取到这个Cookie
        
        var allCookie = document.cookie

> 这种方法只适用于Cookie以及iframe窗口，LocalStorage以及IndexDB无法通过这种方法，规避“同源政策”，就需要使用PostMessage API

> 另外：Server在设置Cookie时，指定Cookie的所属域名为y一级域名，例如，.example.com

    Set-Cookie:key=value;domain=.example.com;path = /
    
    此后下属，二/三级域名不用做任何设置都可以读取这个Cookie
    
    
## 三、iframe
> 两个网页不同源，则无法获取到对方DOM
> >例子：
> >iframe 以及 window.open 打开的窗口都无法与父窗口通信

    强行访问则会报错  
    // Uncaught DOMException: Blocked a frame from accessing a cross-origin frame.
    未捕获，DOM异常：阻止了一个frame访问跨源frame
    
    无论子访问父or父访问子的DOM 都会报错
> 三种方法解决跨域访问的通信问题
    1. 片段识别符（fragment identifier）
    2. window.name
    3. 跨文档通信API(Cross-document messaging)

* 1. 片段识别符（fragment identifier）
    > URL # 号后面部分例如：
    > http://example.com/x.html#fragment的fragment就是偏度识别符，改变片段识别符，页面不会重新刷新
    > > 父窗口可以把信息写入子窗口的片段识别符
        
            var src = originURL + '#' + data;
            document.getElementById('myIFrame').src = src;
            
    >> 子窗口通过 监听 hashchange 事件得到通知

            
        window.onhashchange = checkMessage;

        function checkMessage() {
          var message = window.location.hash;
          // ...
        }
   >> 同时，子窗口也可以改变父窗口的片段标识

        parent.location.href= target + "#" + hash;
        
  * 2. window.name
    >Browser Window 有 window.name 属性
    >> window.name 特点：无论是否同源只要在同一个窗口中，前一个网页设置了这个属性，后一个网页可以读取它
    >> 父窗口首先打开一子窗口，载入一不同源网页，该网页将信息写入window.name属性
     
        window.name = data;
    >> 接着，子窗口跳回一个与主窗口同域的网址

        location = 'http://parent.url.com/xxx.html';
        
    >> 然后，主窗口就可以读取子窗口的window.name了

        
        var data = document.getElementById('myFrame').contentWindow.name;
    > 优点:window.name 容量很大，可以放置非常长的字符串，缺点是必须监听window.name属性变化影响网页性能
  
  * 3. postMessage
    > 上面两种办法属于破解，这种办法是HTML5为了解决这个问题，引入的一个新API:跨文档通信API(Cross-Document Message )


    > 这个API为window对象新增了一个window.postMessage方法，允许跨窗口通信，不论这两个窗口是否同源。举例来说，父窗口http://aaa.com向子窗口http://bbb.com发消息，调用postMessage方法就可以了。

        var popup = window.open('http://bbb.com', 'title');
        popup.postMessage('Hello World!', 'http://bbb.com');
    > postMessage方法的第一个参数是具体的信息内容，第二个参数是接收消息的窗口的源（origin），即"协议 + 域名 + 端口"。也可以设为*，表示不限制域名，向所有窗口发送。

    
    >子窗口向父窗口发送消息的写法类似。
        
        window.opener.postMessage('Nice to see you', 'http://aaa.com');
    > 父窗口和子窗口都可以通过message事件，监听对方的消息。

        window.addEventListener('message', function(e) {
          console.log(e.data);
          },false);
          
          
    > message事件的事件对象event，提供以下三个属性。
        
      * event.source：发送消息的窗口
      * event.origin: 消息发向的网址
      * event.data: 消息内容
    >  event.origin属性可以过滤不是发给本窗口的消息。


        window.addEventListener('message', receiveMessage);function receiveMessage(event) {
          if (event.origin !== 'http://aaa.com') return;
          if (event.data === 'Hello World') {
              event.source.postMessage('Hello', event.origin);
          } else {
            console.log(event.data);
          }}
  
  * 4. LocalStorage 
    > 通过window.postMessage，读写其他窗口的 LocalStorage 也成为了可能。下面是一个例子，主窗口写入iframe子窗口的localStorage。

        window.onmessage = function(e) {
          if (e.origin !== 'http://bbb.com') {
            return;
          }
          var payload = JSON.parse(e.data);
          localStorage.setItem(payload.key, JSON.stringify(payload.data));};
          
    >  上面代码中，子窗口将父窗口发来的消息，写入自己的LocalStorage。


### 四、AJAX
>  同源政策规定，AJAX只能请求同源网址，否则报错

> 除了架设服务器代理(Browser request 同源Server，再由后者request 外部服务)，有三种办法规避这个限制

   * JSONP
   * WebSocket
   * CORS

> 1. JSONP  
    >> JSONP是Server于Client跨源通信的常用方法
    >> 特点：简单适用，老式Browser全部支持，服务器改动较小
    >> 它的基本思想是，网页通过添加一个<script>元素，向服务器请求JSON数据，这种做法不受同源政策限制；服务器收到请求后，将数据放在一个指定名字的回调函数里传回来。
   >> 首先，网页动态插入<script>元素，由它向跨源网址发出请求。

        
    function addScriptTag(src) {
      var script = document.createElement('script');
      script.setAttribute("type","text/javascript");
      script.src = src;
      document.body.appendChild(script);}

    window.onload = function () {
      addScriptTag('http://example.com/ip?callback=foo');}

    function foo(data) {
      console.log('Your public IP address is: ' + data.ip);
  >上面代码通过动态添加<script>元素，向服务器example.com发出请求。注意，该请求的查询字符串有一个callback参数，用来指定回调函数的名字，这对于JSONP是必需的。
  
  > 服务器收到这个请求以后，会将数据放在回调函数的参数位置返回。
 

    foo({
      "ip": "8.8.8.8"
      });
      
  
 > 由于<script>元素请求的脚本，直接作为代码运行。这时，只要浏览器定义了foo函数，该函数就会立即调用。作为参数的JSON数据被视为JavaScript对象，而不是字符串，因此避免了使用JSON.parse的步骤。

* 2. WebSocket
    > WebSocket是一种通信协议，使用ws://（非加密）和wss://（加密）作为协议前缀。该协议不实行同源政策，只要服务器支持，就可以通过它进行跨源通信。
   例子，浏览器发出的WebSocket请求头信息：
   
        GET /chat HTTP/1.1
        Host: server.example.com
        Upgrade: websocket
        Connection: Upgrade
        Sec-WebSocket-Key: x3JJHMbDL1EzLkh9GBhXDw==
        Sec-WebSocket-Protocol: chat, superchat
        Sec-WebSocket-Version: 13
        Origin: http://example.com
   > 上面代码中，有一个字段是Origin，表示该请求的请求源（origin），即发自哪个域名。


   > 正是因为有了Origin这个字段，所以WebSocket才没有实行同源政策。因为服务器可以根据这个字段，判断是否许可本次通信。如果该域名在白名单内，服务器就会做出如下回应。

        HTTP/1.1 101 Switching Protocols
        Upgrade: websocket
        Connection: Upgrade
        Sec-WebSocket-Accept:     HSmrc0sMlYUkAGmm5OPpG2HaGWk=
        Sec-WebSocket-Protocol: chat
        
        
        
* 3. CORS(Cross-Origin Resource Sharing):跨域资源分享
    > W3C标准，是跨域AJAX请求的根本解决方案，相比JSONP只能发送GET 请求，CORS允许任何类型的请求。

### 参考文献
[阮一峰：浏览器同源政策及其规避方法](http://www.ruanyifeng.com/blog/2016/04/same-origin-policy.html)