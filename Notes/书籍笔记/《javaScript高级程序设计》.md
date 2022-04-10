# 3.3 变量

## -let

使用let和const在全局作用域中的声明不会成为window对象的属性(var声明的变量则会)

# 3.4 数据类型

## -模板字面量标签函数

标签函数：标签使您可以用函数解析模板字符串

```js
functioin simpleTag(strings,a,b,c……){
    //strings:字符串数组，以${}分隔开得到的数组
    //a:模板字符串中第一个${}
    //b:第二个
    //c:第三个 以此类推
}
```

## -symbol

* symbol.for()中第一次出现的字符串会生成新符号添加到注册表中
* symbol.keyfor()能查询全局注册表中的符号，也就是symbol.for注册的符号，而symbol生成的符号会返回undefined

## -Object.defineProperty

`Object.defineProperty`方法直接在一个对象上定义一个新属性，或者修改一个已经存在的属性， 并返回这个对象

- value: 设置属性的值
- writable: 值是否可以重写。true | false
- enumerable: 目标属性是否可以被枚举。true | false
- configurable: 目标属性是否可以被删除或是否可以再次修改特性 true | false
- set: 目标属性设置值的方法
- get：目标属性获取值的方法  　

#  3.5 操作符

## -一些特殊的计算结果

* -infinity加它本身=它本身
* -0 + +0 =+0
* -0 + -0 =-0
* +0 - -0 =-0
* NaN == NaN 结果为false

# 3.6 语句

## -标签语句

配和break和continue使用

# 4.2 执行上下文与作用域

## -const声明时必须初始化，不然就会报错

## -引用值是对象，储存在堆内存上

## - type of 和 instance of



# 4.3 垃圾回收

* 标记清理
* 引用计数清理

# 5.2 RegExp

* 正则表达式的模式

# 5.3 原始值包装类型

引用类型与原始值包装类型的主要区别在于对象的生命周期。引用类型实例会在`离开作用域`时被销毁，而自动创建的原始值包装对象则只存在于访问它的那行代码执行期间

引用类型：Boolean、String、Number

```js
   let a ='sdsdi';
     a.color='red';
     console.log(a.color);  //undefined
//这里第二行代码尝试给字符串a添加一个color属性，第二行运行时会临时创建一个Strinng对象，而当第三行代码执行时这个对象已经被销毁了
```



# 5.4 单例内置对象

## -Global

没有直接访问Global对象的方式，浏览器将window对象实现为Global对象的代理。

## -Math

Math对象上提供的计算要比直接在JS上计算快得多，但受各种浏览器、操作系统等各种因素影响



# 6.1 Object

```js
let person{   //对象字面量表示法，此方法不会实际调用Object构造函数(数组同理)
    name:'cbm',
    age：14
}


log(person.name);
log(person['name']);
```

   

# 6.2 Array

## -Array.from()



```js
Array.form()  //参数为任何可迭代结构，或者有一个length属性和可索引元素的结构,转化为数组
Array.form('12345') //['1','2','3','4','5'];

const a1 =[1,2,3,4];
Array.from(a1,x=>x**2)  //[1,4,9,16]
```

## -Array.of()

```js
Array.of(1,2,3,4)  //[1,2,3,4]
```

## -使用length属性更方便地往数组添加元素

```js
const color =['red','blue','green'];
color[color.length]='pink';
color[color.length]='yellow';
```

## -迭代器方法

* keys(),values(),entries() 返回的都是迭代器
* 使用Array.from()方法将上述方法返回值转化为数组实例

## -填充数组

```js
const zeroes=[0,0,0,0,0,0];
zeroes.fill(5)  //全为5
zeroes.fill(5,3) //索引大于3的元素为5
zeroes.fill(5,3,5) //索引大于3小于5的元素为5
```

## -push/pop/shift/unshift

## -revverse/sort

## -splice

## -归并方法 

本质是加法

* redece()  1——n
* redeceRight()  n——1

# 6.4 Map

选择Object还是Map



# 6.5 WeakMap(弱映射)

* 只能用对象作为键
* 不可迭代

# 6.7 WeakSet

# 7.2 迭代器模式

* 迭代器是一种一次性使用的对象
* 如果对象原型链上的父类实现了Iterable接口，那这个对象也就实现了这个接口
* 不同迭代器实例之间没有联系

```js
let arr=['foo','bar'];
let iter1=arr[Symbol.iterator]();
let iter2=arr[Symbol.iterator]();
console.log(iter1.next());
console.log(iter2.next());
console.log(iter1.next());
console.log(iter2.next());
```





# 7.3 生成器

* 可以定义函数的地方就可以定义生成器（箭头函数不能用来定义生成器）
* yield关键字只能在生成器函数内部使用
* 第一次调用next()的值不会被使用,因为第一次调用是为了开始执行生成器函数
* yield *

```js
//等价写法
function * generatorFnA(){
      for(const x of [1,2,3]){
          yield x;
      }
   }
   for(const x of generatorFnA()){
       console.log(x);
   }//1 2 3

   function * generatorFnB(){
       yield * [1,2,3];
   }
   for(const x of generatorFnB()){
       console.log(x);
   }//1 2 3
```

* 利用yield* 实现递归
* return停止生成器，只要通过它进入关闭状态，就无法恢复了，再次调用next会显示`done:true`状态
* throw提供错误能暂停生成器，如果生成器函数内部能处理这个错误，则恢复执行，若不能，则无法执行

# 8.1 理解对象

## -数据属性

* Configurable  是否可以通过`delete`关键字进行删除
* Enumerable  是否通过for-in 循环返回
* Writable 是否可以修改
* Value  默认值为:undefined
* Object-assign(被合并的对象，要合并的对象源)  `拷贝的是可枚举属性值`

不能在对象间转移get函数和set函数

最后的同名属性将覆盖前面的同名属性

* 对象解构

```js
  let person={
      GOGOname:'cbm',
      GOGOage:22
  };
  
  let{GOGOage,GOGOname}=person; //如果变量名直接使用属性名，此为简写
  console.log(GOGOage);
```

* 通过解构来复制对象属性

```js
  let person={
      GOGOname:'cbm',
      GOGOage:22
  };
  let HumanPerson={};
  ({
      GOGOname:HumanPerson.name,
      GOGOage:HumanPerson.age
  }=person);

  console.log(HumanPerson);//此时修改复制的对象属性，被复制的对象属性也会被修改
```

* 参数上下文匹配

```js
 let person={
      GOGOname:'cbm',
      GOGOage:22
  };
 function Go(one,{GOGOname,GOGOage}){
     console.log(GOGOname);
     console.log(GOGOage);
 }

 Go(1,person);
```



# 8.2 创建对象

## -构造函数与普通函数

构造函数与普通函数唯一的区别就是调用方式不同。任何函数只要使用new操作符调用就是构造函数，而不使用new操作符的函数就是普通函数。

## -理解原型

* 实例与构造函数原型之间有直接的联系，但实例与构造函数之间没有
* Obejct的原型的原型是null
* 重写整个原型之前创建的实例在重写之后会报错，因为指向不同的原型（实例指向最初的原型），修改原型则不会
* 可以在原生对象的原型上自定方法

# 8.3 继承

* 盗用构造函数

使用call或apply方法继承属性



# 8.4 类


constructor

* 与普通构造函数的区别是，调用类构造函数的时候必须使用new操作符不然就会报错
* 把类当作特殊函数
* 类本身具有与普通构造函数一样的行为，本身在使用new调用时就会被当成是构造函数
* 类中定义的constructor方法不会被当成是构造函数

* 类可以像函数一样在任何地方定义
* 类可以立即实例化:

```js
new class Go{  //立即实例化
    constructor(x){
        console.log(x);
    }
}('sndisd');


(function ssss(xi){  //立即执行函数
    console.log(xi);
}('xi'));
```



* 类中的各种方法

```js
class Person{
             constructor(){
              this.getName =()=>{
                  console.log('构造函数中的方法');
              }
             }

             getName(){
                 console.log("定义在类原型对象上的方法");
             }
             static getName(){
                 console.log("定义在类本身的方法");
             }
         }

         let p =new Person();
         p.getName();  //构造函数中的方法
         Person.prototype.getName();  //定义在类原型对象上的方法
         Person.getName();  //定义在类本身的方法
```

* 类的继承依然使用的是原型链
* 静态方法的继承

```js
 class Person{
             constructor(){
              this.getName =()=>{
                  console.log('构造函数中的方法');
              }
             }

             getName(){
                 console.log("定义在类原型对象上的方法");
             }
             static getName(){
                 console.log("爹地的静态方法");
             }
         }

        class Man extends Person{ //super关键字可以继承的类上的静态方法
            static getName(){
                super.getName();
            }
        }
        Man.getName();
```

* super关键字只能在派生类构造函数和静态方法中使用

# 9.1 代理基础

* Proxy.prototype是undefined
* '==='可以用来区别代理与目标
* 捕获器：捕获在代理对象上的操作

* 可撤销代理revocable()

撤销代理对象与目标对象的关联，操作不可逆

* 反射api:适用于细粒度的对象控制与操作



# 10.1 箭头函数

不能使用arguments、super，也不能用作构造函数，而且没有prototype属性

# 10. 函数

```js
function sum(a,b){
           return a+b;
         }

         let jiji=sum; //jiji和sum此时指向同一个函数
```

* 函数的name属性
* ECMAScript函数的参数只是为了方便才写出来的而不是必须
* ECMAScript函数不能重载,后定义的函数将覆盖前面的函数
* 默认参数作用域与暂时性死区

```js
 function sum(a=b,b){  //报错 参数是按顺序初始化的
           return a+b;
         }
```

* 参数扩展与收集(...args)
* 函数声明与函数表达式

js引擎在任何代码执行前会先读取函数声明，而函数表达式必须等到执行到它那一行

```js
 console.log(sum(12));
         function sum(a,b=a){
           return a+b;
         } //可行

console.log(sum(12));
       var sum=  function (a,b=a){
           return a+b;
         }//出错
       //除了函数什么时候真正有定义这个区别外，这两种语法是等价的
```

## -函数内部

### --arguments

类数组对象

callee属性，指向arguments对象所在函数的指针

aruguments.callee() 对递归函数解耦(严格模式不可行，严格模式需要使用命名函数表达式)



### --this

箭头函数的this指向定义它的上下文



## -函数的属性和方法

* call()和apply()的第一个参数都是this,但是call剩下的参数要一个一个传递，而apply可以传递数组或者arguments对象（如果不用给被调用的函数传参，则方法都一样）

## -函数表达式

代码块中声明函数会报错，函数表达式则不会出问题



## -尾调用优化

要求必须在严格模式下才有效，因为非严格模式下有能引用外部函数栈帧的方法，如f.arguments和f.caller



## -闭包

* 全局环境不会被回收
* 每个函数被调用时自动创建两个特殊变量,this和arguments，内部函数永远无法访问到外部函数的这两个变
* 广义上讲，js中所有的函数都是闭包
* 闭包能延伸作用域的，同时也会造成查找变量所需时间变长的问题

## -内存泄漏

使用null防止内存泄漏				

## -立即调用函数

es5中模拟块级作用域

常用在遍历dom元素上模拟块级作用域防止数据泄露

## -私有变量

特权方法:能够访问函数私有变量(私有函数)的公有方法



## -单例对象

只有一个实例的对象



# 11. promise与异步函数

# 11.2 Promise



## -Promise的状态

* 待定(pending)
* 解决(fulfilled)
* 拒绝(rejected)

## -then

* 返回一个新的promise实例
* 若调用then()时不传处理程序，则原样向后传
* 无论是resolve还是reject返回结果相似



## -非重入特性

```js

  let p =Promise.resolve();

  p.then(()=>console.log('promise!'));
 
  console.log('consoloe!');

// consoloe!
// promise!
// then()中处理程序在当前线程上的同步代码执行完成前不会执行
```

## -连锁与合成

* 连锁

then()、catch()、finally()都会返回一个新的promise对象，而这个promise对象又有自己的实例方法，连缀调用，在实例方法里面调用异步任务，就是串行化异步任务。

* 合成

Promise.all([promise1,promise2,promise3……])

接收一个可迭代对象，返回一个新promise对象，该对象创建的新Promise会在这一组promise解决后再解决

如果有迭代数组里面有一个promise是拒绝的，则all方法返回的对象就是拒绝的，reason等同于拒绝的`第一个`promise对象

* Promise.race()

参数同all方法，返回一个可迭代数组中最先解决或者拒绝的promise

迭代顺序决定了落定顺序，与定时器无关

## -取消promise和查看进度

ES6并不支持，但是可以实现

# 11.3 异步

async/await

* 能让同步方式写的代码异步执行
* 异步函数始终返回promise对象

```js
 async function foo(){
   console.log(1);
   return 3
 }
 foo().then(console.log)
 console.log(2);
//1
//2
//3 
//输出1普通函数的正常行为，return为异步对象，要等到同步函数执行之后才执行
```

* 使用then解包

```js
async function foo(){
    return 'foo';
}
foo.then(console.log); //foo
```



## -await

暂停和恢复执行异步函数

* 解包

```js
async function oo(){
  console.log(await Promise.resolve(1));
}
oo(); //1



async function oo(){
  console.log( Promise.resolve(1));
}/* Promise {<fulfilled>: 1} */
```

* 使用await打印1-9

```js
async function foo(){
  console.log(2);
  console.log(await Promise.resolve(6));
  console.log(7);
}
async function bar(){
  console.log(4);
  console.log(await 8);
  console.log(9);
}
console.log(1);
foo();
console.log(3);
bar();
console.log(5);
```

* awiat和async实现串行异步代码

# 12.BOM

* window变量的属性查询

```js
var newValue=oldValue; //报错，因为oldValue没有声明
var newValue=window.OldValue; //不报错因为是属性查询
```

* setInterval()

参数中的时间间隔一到，浏览器就会把任务添加到执行队列。



## -location对象

* 即使window的属性也是document的属性

# 14.DOM

* Node接口时所有DOM节点类型都必须实现的
* 所有结点类型都继承Node类型
* 文档中的所有结点都和其他结点有关系

```js
let arrayofNodes=Array.from(someNode.childNodes); //将Nodelist对象转化为数组
```

* normalize() 删除指定节点中的空文本节点或合并相邻同胞文本节点
* document是window对象的属性 nodetype=9

document.documentElement = document.childNodes[0]=document.firstChild()   统统指向<html>

* HTML可以包含子节点，但是不能多于一个
* url、domain(域名)、referrer
* 自定义属性名应该加`data-`前缀以方便验证
* NdeList

```js
  let div=document.getElementsByTagName('div');
      for(let i=0;i<div.length;i++){
        let div =document.createElement('div');
        document.body.appendChild(div);
      } //无穷循环
//第一行取得了包含文档中所有<div>元素的HTMLCollection，因为这个集合是'实时的',任何时候向页面添加一个新元素，集合都会多一项
```

* MutationObserver接口

该接口是处于性能考虑而设计的，核心是异步回调与记录队列模型



# 15.DOM扩展

* querySelectorAll()

返回的NodeList是一个静态的‘快照’而非‘实时查询‘，避免了性能问题

* classList属性修改类名
* outerHTML不仅包含inner部分而且包含对象本身的标签
* 内存与性能问题

如果被移除的子树元素删除前与js或其它程序有关联，那它们之间的绑定关系会滞留在内存中

减少使用InnerHTML





# 17.事件

## -事件处理程序

```html
<input type='text' onclick='console.log(event.type)'>  <!-- event/this都可代表目标元素 -->
```

## -跨浏览器事件处理程序

先判断传入元素上是否存在DOM2方式，也就是addEven,若没有，如果 存在IE方式（attach），则IE，如果都没有，则是使用DOM0方式，执行事件处理



## -mouse两对事件

mouseenter/mouseleave:`事件不冒泡，也不会在光标经过后代元素时触发`

mouseover/mouseout:`光标移动过到另一元素时触发，内内，内外都可以触发`

> mouseover触发优先级高于mouseenter，mouseout触发优先级高于mouseleave

mouseover移入移出子元素会触发，mouseenter不会触发



## -事件委托

事件委托利用事件冒泡，可以只使用一个时间处理程序来管理一种类型的事件

# 18.动画和Canvas图形

## 18.2 基本的画布功能

* fillStyle 填充颜色

* strokeStyle 边框颜色

  每种style都有对应的Rect

```js
  <canvas id="drawing" height="200" width="300">画画？</canvas>
    <script>
        let canvas=document.getElementById('drawing');
        if(canvas.getContext){
        let context=canvas.getContext("2d");
        context.fillStyle="#ff0000"
        context.fillRect(10,10,50,50);


        context.strokeStyle="rgba(0,0,255,0.5)";
        context.strokeRect(30,30,50,50);
        }
    </script>
```

* clearRect()

擦除，四个参数，分别代表坐标和擦除面积大小

## 18.3.3 绘制路径

```js
 context.beginPath(); //开始绘制

context.stroke(); //描绘路径
// context.fill()也可描绘
```

## 18.4 WebGL

画布的3D上下文

WebGL是OpenGL的Web版本

# 19.表单脚本

```js
document.forms   //可以获取页面上所有的表单元素
```

## 19.1.3 表单字段

所有表单元素都是表单elements属性中包含的一个值

```js
 let form=document.querySelector('form');
        let field1 =form.elements[0];
        let field2 =form.elements['name'];//返回表单中名为'name'的字段
```



# 20.JS API

跳了……

# 21.错误处理

跳

# 22.处理XML

XML和json

跳

# 23.JSON

* JSON字符串和JS字符串主要区别:JSON字符串必须要双引号
  * JSON直接被解析为JS对象，XML被解析为DOM文档

* JSON中没有变量

* 数组与对象的组合使用

* JSON对象的方法:

  * stringify()

    JSON.stringfy(JS对象) 将该对象转化为JSON字符串(不包含空格或缩进,undefined被跳过）

  * parse() 

    JSON.parse(JSON对象) 将该JSON字符串转为JS对象
    辗转两次之后的对象与原来的对象是两个完全不同的对象，但是它们有相同的属性和值

* 

  

  

  

  

