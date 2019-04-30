# 浅析JavaScript对象以及原型链路

## 1. 对象
#### 在JavaScript中大多事物都是对象，小到字符串、数组，大到自己建立在JavaScript之上的浏览器的API。当然，你也可以建立自己的对象，独一无二或忠于程序本身..；学习对象，这也是理解以及学习面向对象(Object-oriented)必不可少的

### 1.1. 对象基础
##### 对象是一个包含相关数据或方法的集合，通常由一些变量和方法组成，我们称它为对象中的属性和方法（对象.方法，对象.变量）↓↓↓↓↓↓↓↓↓↓如下创建一个简单对象↓↓↓↓↓↓↓↓↓↓
    
```
var person = {
  name : ['Bob', 'Smith'],
  age : 32,
  gender : 'male',
  interests : ['music', 'skiing'],
  bio : function() {
    alert(this.name[0] + ' ' + this.name[1] + ' is ' + this.age + ' years old. He likes ' + this.interests[0] + ' and ' + this.interests[1] + '.');
  },
  greeting: function() {
    alert('Hi! I\'m ' + this.name[0] + '.');
  }};
  
//再输入如下命令 ， 我们发现变量和方法的调用并没有什么不一样，其中需要注意的是，JavaScript对象中的key永远是一个字符串类型，无论是否加上了引号
person.name[0]
person.age
person.interests[1]
person.bio()
person.greeting()

```
#### 1.2. 点表示法
##### 在上面的简单例子中，你使用到了(dot notation)点表示法来访问对象里的变量以及方法(同为key)，这里 对象的名字 表现为一个命名空间(namespace)，它必须写在第一位----不然你是想调用谁的谁呢？（ 接着是一个点(.)，紧接着是你想要访问的项目，标识可以是简单属性的名字，或者是数组属性的一个元素又或者是方法的调用(根据你当前情况而定~)
```
person.age
person.interests[1]
person.bio()
```

> #####  1.2.1. 子命名空间
> ###### 当然 你甚至可以再对象中再定义一个对象，则你对象中的对象名为你对象中对象属性（方法）的命名空间
> 或许这很好理解...

#### 1.3. 括号表示法
##### 另外一种访问属性的方式是使用括号表示法(bracket notation)，替代这样的代码
    曾经
    person.age
    person.name.first
    
    现在
    person['age']
    person['name']['first']
##### 这看起来就像是再调用数组的元素---从根本上说这就是一回事儿，你使用了关联值的名字，而不是索引去选择元素------难怪有时候数组又称之为关联数组（associative array）了(,对象做到了字符串到值的映射，而数组则是做的数字(索引)到值的映射

#### 1.4. 设置对象成员
##### 目前我们从初始化一个对象到如何调用已经了如指掌----我们开始学习如何设置对象成员的值，通过声明你要设置的成员，向这样↓↓↓↓↓↓↓↓↓↓

    person.age = 45
    person['name']['last'] = 'Cratchit'
    
    这样，创建新的成员
    person['eyes'] = 'hazel'
    person.farewell = function() { alert("Bye everybody!") }
    
##### 括号表示法一个有用的地方是它不仅可以动态的去设置对象成员的值，还可以动态的去设置成员的名字。比如说，我们想让用户能够在他们的数据里存储自己定义的值类型，通过两个input框来输入成员的名字和值，通过以下代码获取用户输入的值：
    
    var myDataName = nameInput.value
    var myDataValue = nameValue.value
    
    我们可以这样把这个新的成员的名字和值加到person对象里：
    person[myDataName] = myDataValue
    
> 这是使用点表示法无法做到的，点表示法只能接受字面量的成员的名字，不接受变量作为名字。


#### 1.5. "this"的含义
>######  你也许在我们的方法里注意到了一些奇怪的地方，看这个例子：

    greeting: function() {
      alert('Hi! I\'m ' + this.name.first + '.');
      }
##### 你也许想知道"this"是什么，关键字"this"指向了当前代码运行时的对象( 原文：the current object the code is being written inside )——这里即指person对象，为什么不直接写person呢？当你学到下一篇Object-oriented JavaScript for beginners文章时，我们开始使用构造器(construnctor)时，"this"是非常有用的——它保证了当代码的上下文(context)改变时变量的值的正确性（比如：不同的person对象拥有不同的name这个属性，很明显greeting这个方法需要使用的是它们自己的name）。
##### 让我们以两个简单的person对象来说明：

    var person1 = {
      name : 'Chris',
      greeting: function() {
        alert('Hi! I\'m ' + this.name + '.');
      }}

    var person2 = {
      name : 'Brian',
      greeting: function() {
        alert('Hi! I\'m ' + this.name + '.');
      }}
      

>在这里，person1.greeting()会输出："Hi! I'm Chris."；person2.greeting()会输出："Hi! I'm Brain."，即使greeting这个方法的代码是一样的。就像我们之前说的，this 指向了代码所在的对象(其实代码运行时所在的对象)。在字面量的对象里this看起来不是很有用，但是当你动态创建一个对象（例如使用构造器）时它是非常有用的，之后你会更清楚它的用途。 

#### 1.6  你一直在使用对象
##### 通过上述这些例子已经了解到了对象的基本情况，接下来会发现再学习JavaScript的过程中对象将贯穿你的一生
    使用字符串prototype的方法
    myString.split('sep')//sep是分隔符
    
    使用document. API的时候
    var myDiv = document.createElement('div');
    var myVideo = document.querySelector('video');
    

你正在使用Document实例上可用的方法。每个页面在加载完毕后，会有一个Document的实例被创建，叫做document，它代表了整个页面的结构，内容和一些功能，比如页面的URL。同样的，这意味document有一些可用的方法和属性。这同样适用许多其他内建的对象或API，你使用过有—— Array，Math， 等。请注意内建的对象或API不会总是自动地创建对象的实例，举例来说，这个 Notifications API——允许浏览器发起系统通知，需要你为每一个你想发起的通知都使用构造器进行实例化。尝试在JavaScript终端里输入以下代码


    var myNotification = new Notification('Hello!');
    
    
### > 关于面向对象的操作就不再多做赘述
##### > 构造函数，多态，重写， 这里需要注意的是JavaScript中可以通过一个已有的对象来创建一个新的对象Create（）函数
    var person2 = Object.create(person1);
### > 2. Proto 原型链

> #### 通过原型这种机制，JavaScript 中的对象从其他对象继承功能特性；这种继承机制与经典的面向对象编程语言的继承机制不同。本文将探讨这些差别，解释原型链如何工作，并了解如何通过 prototype 属性向已有的构造器添加方法
 
#### 2.1. 基于原型的语言?
#### JavaScript 常被描述为一种基于原型的语言 (prototype-based language)——每个对象拥有一个原型对象，对象以其原型为模板、从原型继承方法和属性。
#### 原型对象也可能拥有原型，并从中继承方法和属性，一层一层、以此类推。这种关系常被称为原型链 (prototype chain)，它解释了为何一个对象会拥有定义在其他对象中的属性和方法。
#### 准确地说，这些属性和方法定义在Object的构造器函数(constructor functions)之上的prototype属性上，而非对象实例本身。在传统的 OOP 中，首先定义“类”，此后创建对象实例时，类中定义的所有属性和方法都被复制到实例中。在 JavaScript 中并不如此复制——而是在对象实例和它的构造器之间建立一个链接（它是__proto__属性，是从构造函数的prototype属性派生的），之后通过上溯原型链，在构造器中找到这些属性和方法。
>注意: 理解对象的原型（可以通过Object.getPrototypeOf(obj)或者已被弃用的__proto__属性获得）与构造函数的prototype属性之间的区别是很重要的。
>前者是每个实例上都有的属性，后者是构造函数的属性。也就是说，Object.getPrototypeOf(new Foobar())和Foobar.prototype指向着同一个对象。

> ####  具体实验
> var obj = new func();
> obj.__proto__ === func().prototype
> var o = new func().prototype;
> o.__proto__ === func().prototype.__proto__

> 注意：必须重申，原型链中的方法和属性没有被复制到其他对象——它们被访问需要通过前面所说的“原型链”的方式。

> 注意：没有官方的方法用于直接访问一个对象的原型对象——原型链中的“连接”被定义在一个内部属性中，在 JavaScript 语言标准中用 [[prototype]] 表示（参见 ECMAScript）。然而，大多数现代浏览器还是提供了一个名为 __proto__ （前后各有2个下划线）的属性，其包含了对象的原型。你可以尝试输入 person1.__proto__ 和 person1.__proto__.__proto__，看看代码中的原型链是什么样的！

> prototype 属性大概是 JavaScript 中最容易混淆的名称之一。你可能会认为，this 关键字指向当前对象的原型对象，其实不是（还记得么？原型对象是一个内部对象，应当使用 __proto__ 访问）。prototype 属性包含（指向）一个对象，你在这个对象中定义需要被继承的成员。

##### 之前我们做过实验
我们曾经讲过如何用 Object.create() 方法创建新的对象实例。

    var person2 = Object.create(person1);   

    person2.__proto__ == person1
    true

#### constructor 属性

##### 每个实例对象都从原型中继承了一个constructor属性，该属性指向了用于构造此实例对象的构造函数。


> 一个小技巧是，你可以在 constructor 属性的末尾添加一对圆括号（括号中包含所需的参数），从而用这个构造器创建另一个对象实例。毕竟构造器是一个函数，故可以通过圆括号调用；只需在前面添加 new 关键字，便能将此函数作为构造器使用。 ----------------这显然没有什么屁用
 
    var person3 = new person1.constructor('Karen', 'Stephenson', 26, 'female', ['playing drums', 'mountain climbing']);
    

###### 正常工作。通常你不会去用这种方法创建新的实例；但如果你刚好因为某些原因没有原始构造器的引用，那么这种方法就很有用了。此外，constructor 属性还有其他用途。比如，想要获得某个对象实例的构造器的名字，
##### 可以这么用
    instanceName.constructor.name 
    具体 
    person1.constructor.name