# 类

* 类里的函数不需要使用`function`
* 类的本质还是一个function
* super调用父类中的构造函数
* super在构造方法中需要在子类的this之前
* ES6中类没有变量提升
* constructor 里this指向实例对象，方法里的this指向这个方法的调用者

```js
 class Star{
        constructor(uname,uku){
            this.uname=uname;
            this.uku=uku;
            this.btn=document.querySelector('button');
            this.btn.onclick=this.sing
        }
        sing(){
            console.log(this.uname);   //这里会输出 undifined,因为this指的是this.btn
        }
```

## -添加元素



insertAdiacentHTML(position,text);

position:beforebegin/afterbegin,beforeend/afterend



# 构造函数和原型

## -构造函数

​	ES6前实现面向对象的方法

### --实例成员

通过构造函数内部的this添加的

### --静态成员

 只能通过构造函数访问，不能通过对象来访问



### --protype

原型对象

作用：`共享方法`,节约内存资源



### -- __proto__

对象身上的proto指向原型对象，与构造函数protype等价

```js
 function Star(uname,uage){
             this.uname=uname;
             this.uage=uage;
         }

         Star.prototype.sing=function(){
            console.log('我会唱歌');
         }
         var cbm=new Star('cbm',15);
         var ccm=new Star('cbm',15);
         console.log(cbm);
         console.log(cbm.sing==ccm.sing); //返回true
         cbm.sing(); // 输出'我会唱歌'
```

先查看cbm对象上是否有sing的方法，有就执行，如果没有，因为有proto的存在，就会去构造函数的原型对象身上查找

proto存在的意义在于为对象查找机制提供一个方向，但它是一个非标准属性



> 其次是 __proto__ ，绝大部分浏览器都支持这个非标准的方法访问原型，然而它并不存在于 Person.prototype 中，实际上，它是来自于 Object.prototype ，与其说是一个属性，不如说是一个 getter/setter，当使用 obj.__proto__ 时，可以理解成返回了 Object.getPrototypeOf(obj)。

### --constructor 属性

重新赋值构造函数的prototype属性的时候需要constructor指向构造函数名

```js
Star.prototype={
             sing:function(){
            console.log('我会唱歌')},
            run:function(){
                console.log('我会跑步');
            },
            constructor:Star ///*********
            
                 }
```

### --构造函数、实例、原型对象三者之间的关系

![图片](D:\cbm\Notes\Notes-images\构造函数与原型对象.png)





## -原型链

只要是对象，就有__proto__属性指向原型对象

![原型链](D:\cbm\Notes\Notes-images\原型链.png)

```js
function Person() {

}
var person = new Person();
console.log(person.constructor === Person); // true
```

person中没有constructor属性，这时会往person的原型Person.prototype中读取，原型中就有该属性

### --原型链中的this指向

指向实例对象

### --组合继承

es6之前的继承方式 ，构造函数+原型对象模拟实现继承，构造函数继承父类的对象属性，原型对象继承父类方法

* call()  修改函数运行时的this指向 
* 继承属性(call方法)

```js
 function Father(uname,uage){
            this.uname=uname;
            this.uage=uage;

        }

        function Son(uname,uage){
            Father.call(this,uname,uage);
        }
        var son =new Son('cbm',12);   
        console.log(son);    //通过call()让子类获取父类的属性
```

* 继承方法(修改prototype)

  ![图片](D:\cbm\Notes\Notes-images\继承父元素的方法.png)

# ES5新增方法

## -数组

### --forEach()

foreach(function(value,index,数组本身){})

### --map()

### --filter()

filter(function(value,index,数组本身){ 筛选条件}）

返回一个新的数组   return  

一般只用到value

### --some()

返回布尔值,查询数组中有没有选中的元素 return

查找到第一个满足的元素就停止查找了

一般只用到value

`return true 终止循环`

## -字符串方法

### --trim()

去除两侧空格

## -对象方法

### --Object.keys(obj)

效果类似于for-in，获取对象所有的`属性名`

### --Object.defineProperty()

Object.defineProperty(obj,prop,descriptor)

![图片](D:\cbm\Notes\Notes-images\define.png)





# 函数进阶

## -函数定义方式

```js
 var a=new Function('a','b','console.log(a + b)');
    a(1,2);
```

`所有函数都是Fnction的实例`

![图片](D:\cbm\Notes\Notes-images\Function.png)

##  -作用域

词法作用域(lexical scoping)

> 因为 JavaScript 采用的是词法作用域，**函数的作用域在函数定义的时候就决定了。**
>
> 而与词法作用域相对的是动态作用域，函数的作用域是在函数调用的时候才决定的。

```js
var value = 1;

function foo() {
    console.log(value);
}

function bar() {
    var value = 2;
    foo();
}
bar();  //结果为1
```

>假设JavaScript采用静态作用域，让我们分析下执行过程：
>
>执行 foo 函数，先从 foo 函数内部查找是否有局部变量 value，如果没有，**就根据书写的位置**，查找上面一层的代码，也就是 value 等于 1，所以结果会打印 1。
>
>假设JavaScript采用动态作用域，让我们分析下执行过程：
>
>执行 foo 函数，依然是从 foo 函数内部查找是否有局部变量 value。如果没有，就从调用函数的作用域，也就是 bar 函数内部查找 value 变量，所以结果会打印 2。
>
>前面我们已经说了，JavaScript采用的是静态作用域，所以这个例子的结果是 1。

## -变量对象

> 在函数上下文中，我们用**活动对象**(activation object, AO)来表示**变量对象**。
>
> 活动对象和变量对象其实是一个东西，只是变量对象是规范上的或者说是引擎实现上的，不可在 JavaScript 环境中访问，只有到当进入一个执行上下文中，这个执行上下文的变量对象才会被激活，所以才叫 activation object 呐，而只有被激活的变量对象，也就是活动对象上的各种属性才能被访问。

执行上下文的代码分为两个阶段：

1.进入执行上下文

 2.代码执行

> ```js
> function foo(a) {
>   var b = 2;
>   function c() {}
>   var d = function() {};
> 
>   b = 3;
> 
> }
> 
> foo(1);
> ```
>
> 
>
> 在**进入执行上下文后**，这时候的 AO 是：
>
> ```js
> AO = {
>     arguments: {
>         0: 1,
>         length: 1
>     },
>     a: 1,
>     b: undefined,
>     c: reference to function c(){},
>     d: undefined
> }
> ```
>
> **代码执行**:
>
> ```js
> AO = {
>     arguments: {
>         0: 1,
>         length: 1
>     },
>     a: 1,
>     b: 3,
>     c: reference to function c(){},
>     d: reference to FunctionExpression "d"
> }
> ```

VO与AO：

>未进入执行阶段之前，变量对象(VO)中的属性都不能访问！但是进入执行阶段之后，变量对象(VO)转变为了活动对象(AO)，里面的属性都能被访问了，然后开始进行执行阶段的操作。
>
>它们其实都是同一个对象，只是处于执行上下文的不同生命周期。

## -this指向问题

### --call方法

调用函数同时改变函数内部的this指向

经常用于继承

### --apply方法

同call,但是参数必须是数组形式

使用apply求数组的最大值：

```js
var max=Math.max.apply(Math,arr); arr为数组
```

### --bind

bind不会调用，但会改变this指向

```js
for(var i=0;i<btns.length;i++){
        btns[i].onclick=function(){
            this.disabled=true;
            setTimeout(function(){
                btns[i].disabled=false;
            },2000)
        }
    }//此代码会报错，因为定时器执行动作时，for循环已经走完了，此时i的值为btns的长度，已然越界。
```



## -严格模式

## -高阶函数

对其他函数进行操作的函数，接受函数作为参数或将函数作为返回值输出



## -闭包

指有权访问另一个函数作用域中变量的函数

主要作用：延申了变量的作用范围

### --例子:点击li打印当前索引

```js
var ul =document.querySelector('ul');
    var lis=ul.querySelectorAll('li');
   for(var i=0;i<lis.length;i++){
      (function(i){
          lis[i].onclick=function(){
              console.log(i);
          }
      })(i);
       }
```

`立即执行函数人称小闭包，因为里面的函数都可以使用立即执行函数的i`

### --例子：延迟后打印所有li中的内容

```js
for(var i=0;i<lis.length;i++){
     (function(i){
          setTimeout(function(){
              console.log(lis[i].innerHTML);
          },3000)
     })(i);
       } //同时生成了四个k
```



## -递归

## -深拷贝和浅拷贝

### --浅拷贝

```js
var obj={
           name:'cbm',
           age:15,
           msg:{  //浅拷贝只是复制了该值(更深层次)的地址，此时o中与obj中的msg指向同一个地方(在同一个空间)，修改会互相影响
               color:'red'
           }
       }
var o={};
       for( var k in obj){
           o[k]=obj[k];
       }
```

ES6中的浅拷贝方法：Object.assign(要拷贝的对象，拷贝的原型);

### --深拷贝

```js
function deep(oldObject,newObject){
    for( var k in oldObject){
           var item=oldObject[k];
        //先判断array是因为 array也属于Object,如果把object放前面，不会执行此语句。
           if(item instanceof Array){  
               newObject[k]=[];
               deep(item,newObject[k]);
           }else if(item instanceof Object){
               newObject[k]={};
               deep(item,newObject[k]);
           }else{
               newObject[k]=item;
           }
       }
}
```

## -正则表达式

在js中作为对象存在

### --test()

### --特殊字符(元字符)

### --预定义类

### --正则替换

replace(正则表达式,替换成的文本)

```js
span.innerHTML=textarea.value.replace(/激情|♂/gi,'**'); //敏感词替换效果
```



