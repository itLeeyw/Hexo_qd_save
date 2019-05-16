---
title: js-call-apply-bind
date: 2019-05-16 11:25:54
tags:
---
## Javascript call() apply() bind()的用法
> ECMScript规范给所有函数都定义了call和apply两个方法，他们的应用广泛，作用一样，只是参数列表传参形式不同

* call()  
    > 指定一个this,并给出一个或多个参数来调用一个函数(function)
    > 与apply（）方法类似，但call()接受的是一个参数列表，而apply()接受的是一个包含多个参数的数组
        
        //apply的用法
        var obj = {
            name : 'linxin'
        }

        function func(firstName, lastName){
            console.log(firstName + ' ' + this.name + ' ' + lastName);
        }

        func.apply(obj, ['A', 'B']);    // A linxin B
        * obj作为函数上下文的对象函数func中 this指向这个对象，在默认情况下this指向的为全局对象
        //call的用法    
        var obj = {
            name: 'linxin'
        }

        function func(firstName, lastName) {
            console.log(firstName + ' ' + this.name + ' ' + lastName);
        }

        func.call(obj, 'C', 'D');       // C linxin D
        
### apply和call的用法？
   1. 改变this的指向


            var obj = {
                name: 'linxin'
            }

            function func() {
                console.log(this.name);
            }

            func.call(obj); 

            等同于
             function func() {
                console.log(obj.name);
            }
       > 我们知道了call第一个参数为函数上下文的对象，这里将obj传递给了func，此时函数里的this便指向了obj
      
   2. 借用别的对象的方法

            var Person1  = function () {
                this.name = 'linxin';
            }
            var Person2 = function () {
                this.getname = function () {
                    console.log(this.name);
                }
                Person1.call(this);
            }
            var person = new Person2();
            person.getname();       // linxin
            
      > 在实例化的person使用getname() 获取到了Person1的name.
      > 
      > 我们注意到Person2中将当前上下文的this传递到了Person1中，所以此时Person1的this指向的是Person2的this，于是Person1中，this.name = ‘linxin’ 等同于 Person2中 name = 'linxin'，所以等同于Person2能继承Person1中的所有属性以及方法，等于Person2继承了Person1

 3. 调用函数(call()和apply()都会让函数立即执行，所以可做为调用函数的方法)

        function func() {
            console.log('linxin');
        }
        func.call();            // linxin
        
        
        
### call()与bind()的区别？
> bind()为ECMScript5中扩展的新方法，所以一些老版本的浏览器(IE低版本)无法兼容，它和call类似，接收的参数与call()相同，第一个为函数上下文，第二个是参数列表，可以接受多个参数

#### 他们之间有两个区别
1. bind发返回值是函数

        var obj = {
            name: 'linxin'
        }

        function func() {
            console.log(this.name);
        }

        var func1 = func.bind(obj);
        func1();                        // linxin
   > bind方法不会立刻执行，其中，它会返回一个改变过上下文this的函数，而原函数不会改变，原函数的this依然指向window


2. 参数的使用

        function func(a, b, c) {
            console.log(a, b, c);
        }
        var func1 = func.bind(null,'linxin');

        func('A', 'B', 'C');            // A B C
        func1('A', 'B', 'C');           // linxin A B
        func1('B', 'C');                // linxin B C
        func.call(null, 'linxin');      // linxin undefined undefined
> 其中返回过后的函数会以bind参数为基础，后面调用这个bind返回的函数会将参数往后排

### 若低版本的ie无法兼容bind则可以自己写一个


    if (!Function.prototype.bind) {//若没有bind函数
            Function.prototype.bind = function () {//在在function的原型中添加一个bind方法
                var self = this,                        // 保存原函数
                    context = [].shift.call(arguments), // 保存需要绑定的this上下文
                    args = [].slice.call(arguments);    // 剩余的参数转为数组
                return function () {                    // 返回一个新函数
                    self.apply(context,[].concat.call(args, [].slice.call(arguments)));
                }
            }
        }