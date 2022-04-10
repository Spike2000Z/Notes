# Let

块级作用域但不会影响作用域链的效果

块级作用域的出现使得立即执行函数(IIFE)不再必要了

```js
// IIFE 写法
(function () {
  var tmp = ...;
  ...
}());

// 块级作用域写法
{
  let tmp = ...;
  ...
}

```



```js
{let a='a'
function fn(){
    console.log(a)
}}
fn()   //可以得到a
```

```js
{
let a='a'
} console.log(a) //得不到a
```

 ## -经典

```js
for(var i=0;i<items.length;i++){
    items[i].onclick.function(){
        items[i].style.background='pink'    //代码不会实现 此时的i值为item.length
    }
}
```

```js
for (let  i = 0; i < 10; i++) {
  let i='abc'
  console.log(i);
} //输出了10次abc,说明函数内部的变量i与循环变量i不在同一个作用域，let可以重新声明
```



# Const

* 定义的对象或者数组元素的修改不算对常量的修改，不会报错，因为常量指向的地址并未发生改变
* 对象冻结：const a =Object.freeze({})
* 指针的地址是不会改变的

# 对象简化写法

# 变量的解构赋值

只要某种数据结构具有 Iterator 接口，都可以采用数组形式的解构赋值

## -数组的结构赋值



```js
let [a, b, c] = [1, 2, 3];

let[a,...b]=[1,2,3,4,5,6];//a:1,b:[2,3,4,5,6]
```

## -对象的结构赋值

对象的属性没有次序，变量必须与属性同名，才能取到正确的值。

如果变量名与属性名不一致

```js
let obj = { first: 'hello', last: 'world' };
let { first: f, last: l } = obj;
```

## -函数参数的解构赋值





## -解构时可以指定默认值



结构赋值的原型：

```js
let { foo: foo, bar: bar } = { foo: 'aaa', bar: 'bbb' };
```

对象的解构赋值的内部机制，是先找到同名属性，然后再赋给对应的变量。真正被赋值的是后者，而不是前者。



## -结构赋值的用途

* 交换变量的值

  ```js
  let x = 1;
  let y = 2;
  
  [x, y] = [y, x];
  ```

* 从函数返回多个值

  ```js
  // 返回一个数组
  
  function example() {
    return [1, 2, 3];
  }
  let [a, b, c] = example();
  
  // 返回一个对象
  
  function example() {
    return {
      foo: 1,
      bar: 2
    };
  }
  let { foo, bar } = example();
  ```

* 

# 箭头函数

特性：

* this是静态的，指向外层作用域的this值
* 不能作为构造实例化对象
* 不能使用arguments变量
* 简写
* 不适合与this有关的回调，事件回调，对象的方法

# 函数参数默认值设置

给形参设置默认值

与解构赋值结合

```js
  function qq({name='cq',age,sex,color}){
        console.log(name);
        console.log(age);
        console.log(sex);
        console.log(color);
    }
    qq({
       
        sex:'boy',
        age:38,
        color:'blue'
    })

```

# rest

类似于argument

function fn(...args){

}

rest参数是一个数组，而arguments并不是一个真正的数组

`位置:函数声明的形参`



#  扩展运算符

function fn(...)

`位置：调用时的实参`

* 能把数组转为以逗号分割的参数序列，如果有引用类型的数据，则为浅拷贝
* 将伪数组转化为真正的数组

```js
  function Go(){
      console.log(arguments);
  }
  const boys=['老大','老二','老三'];
  Go(...boys);
```

返回结果:

![图片](D:\cbm\Notes\Notes-images\扩展运算符1.png)

```js
  function Go(){
      console.log(arguments);
  }
  const boys=['老大','老二','老三'];
  Go(boys);
```

返回结果:

![图片](D:\cbm\Notes\Notes-images\扩展运算符0.png)



# Symbol❓

第七种`原始数据类型`

作用：`从根本上防止属性名的冲突`

以 Symbol 值作为键名，不会被常规方法遍历得到

不能与其它数据运算

```js
let a =Symbol();
let b=Symbol('cbm');
let c=Symbol('cbm'); //b与C不等
let d =Symbol.for('acm');
let e =Symbol.for('acm'); //d与e相等 在全局中进行保存
```

USONB

永远不会重复的字符串

# 迭代器

* for-of

和for-in的区别:

for(var k of Object) 保存键值(value)

for(var k in Object) 保存键名(key)

工作原理:Symbol中的迭代器的next方法的调用



* 自定义迭代器遍历对象

```js
var clazz = {
            name: '一般',
            stus: ['a', 'b', 'c', 'd'],
            [Symbol.iterator]() {
                let index = 0;
                return {
                    next: () => {
                        if (index <= this.stus.length) {
                            const result = { value: this.stus[index], done: false }
                            index++;
                            return result;
                        } else {
                            return { value: undefined, done: true }
                        }
                    }
                }
            }
        }



        for (var v of clazz) {
            console.log(v);
        }
```

# 生成器

function * fn(){

}



```js
function * fn(arg){
    console.log(arg);
    yield 111;
    yield 222;
    yield 333;
}
let iterator=fn('asd');
console.log(iterator.next()); //next()可以传入实参
console.log(iterator.next());
console.log(iterator.next());
console.log(iterator.next());
```

![图片](D:\cbm\Notes\Notes-images\生成器.png)



## -回调地狱

回调函数层层嵌套

解法：

```js
function a(){
    setTimeout(() => {
       console.log('第一'); 
       LetsGo.next('第2次调用！');
    }, 1000);
    
}

function b(){
    setTimeout(() => {
         console.log('第二');
         LetsGo.next('第3次调用！');
    }, 2000);
}

function c(){
    setTimeout(() => {
        console.log('第三');
        LetsGo.next('第4次调用！');
    }, 3000);
}


function * Go(){
   let as= yield a(); //第二次调用Next()
    console.log(as);
    let bs=yield b();
    console.log(bs);
   let cs= yield c();
}

var LetsGo =Go();
LetsGo.next();

```

## -yield

yield并不能直接生产值，而是产生一个等待输出的函数

某个函数包含了yield，意味着这个函数已经是一个生成器

# Promise

解决异步编程

在Promise新建的实例对象使用then方法对异步的结果做处理

```js
const a =new Promise(function(resolve,reject){
setTimeout(() => {
    let ac='done！'
    
    resolve(ac);
}, 1000);
   })
   a.then(function(value){ //调用resolve之后会使用该方法
     console.log(value);
   },
   function(reason){ //调用了reject之后会使用该方法
    console.log(reason);
   })
```

## -Promise读取文件

 ```js
 const fs=require('fs');
 
 
 //调用方法读取文件
 // fs.readFile('./Notes/css/查漏补缺.md',(err,data)=>{
 //     if(err) throw err;
 //     console.log(data.toString());
 // });
 
 // 使用promise封装   
 //promise封装的是异步操作，而读取文件就是异步操作
 const p=new Promise(function(resolve,reject){
     fs.readFile('./Notes/css/查漏补缺.mda',(err,data)=>{
         if(err) reject(err);
         resolve(data);
     })
 }).then(
      function(value){
          console.log(value.toSting());
      },
      function(reason){
          console.log('读取失败！');
      }
 );
 ```



## -Promise封装AJAX请求

```js

 const P=new Promise(function(resolve,reject){
  const xhr=new XMLHttpRequest();
  xhr.open("GET","https://api.apiopen.top/getJoke");
  xhr.send();
  
  xhr.onreadystatechange = function(){
      if (xhr.readyState === 4){
          if(xhr.status>=200 &&xhr.status<300){
              resolve(xhr.response);
          }
          else{
              reject("失败aaaa！")
          }
          
      }
  }  }).then(function(vallue){
      console.log(vallue);
  },
  function(reason){
    console.log(reason);
  }) 
```

## -Promise.prototype.then方法

then方法的返回结果是Promise对象，对象状态由回调函数的执行结果决定

* 返回值非promise类型的属性，返回结果为成功，值相同
* 若是promise对象，返回结果受到与该对象的返回结果相同，value相同

链式调用：then().then().then()……   解决回调地狱



## -promise多个文件内容读取

```js
const p=new Promise(function(resolve,reject){
    fs.readFile('./test1.md',(err,data)=>{
        resolve(data.toString());
    })
})
.then(value=>{
     return new Promise((resolve,reject)=>{
        fs.readFile('./test2.md',(err,data)=>{
            resolve([value,data.toString()]);
        });
     })
})
.then(value=>{
    console.log(value);
})
```

## -catch 方法

```js

/* p.then(value=>{},
    reason=>{
        console.log(reason);
    }); */

//效果等同于上面的代码，语法糖一颗
p.catch(reason=>{
    console.log(reason);
})
```

# 集合

## -Set

* 对数组去重
* 长度单位：size

## -Map

* 特点:key和value值中可以放对象、方法、数组……
* map.set(key,value) 
* 长度单位:size

可以使用结构赋值遍历Map结构

```js
const map = new Map();
map.set('first', 'hello');
map.set('second', 'world');

for (let [key, value] of map) {
  console.log(key + " is " + value);
}
// first is hello
// second is world
```



# 数值扩展

* Number.EPSILON  //表示最小精度

# 对象方法扩展

*  Object.is

判断两个值是否完全相等

```js
Object.is(NaN,NaN);  //返回结果为true
console.log(NaN===NaN); //返回结果为false
```



* Object.assign

合并

Object.assign(被覆盖的数组，要覆盖的数组) 

第二个参数覆盖第一个参数

* Object.setPrototypeOf/get

设置原型

# 模块化

将一个大的程序文件拆分成许多小的文件，再将小文件组合起来

作用：

* 防止命名冲突
* 代码复用
* 高维护 性

ES6之前的模块化规范:

* CommonJS 
* AMD
* CMD

## -语法

* export

*-分别暴露*

```js
export let school='cn';
export function fn(){
    
}
```

*-统一暴露*

```js
 let school='cn';
 function fn(){


}
export{school,fn};
```

*-默认暴露*

```js
export default{
   school:'ni',
   fn:function(){
       
   }

}
```

* import

*-通用方式*

```js
<script type="moudle">
    import * as m1 from '{js文件路径}';
</script>
```

*-解构赋值形式*

```js
 import{school,fngogo} from './m1.js';
```

```js
import{default as m1} from './m1.js';  //导入默认暴露模块
        console.log(m1);              
```

*-简便形式*

```js
import m1 from './m1.js'; //只适用于导入默认暴露模块
        console.log(m1); 
```

## -模块引入

app.js引入其他模块，前端script引入app.js

```js
<script src='app.js' type='module'>
```

## -babel对ES6模块化代码转换

1.使用babe进行代码转换

2.打包





# ES8新特性

## -async

返回值为promise对象

promise的结果由async函数执行的返回值决定,如果返回的结果不是一个promise对象，就会返回一个成功的promise，

如果返回了一个promise对象，这个对象如果是成功的，则返回值也是成功的

## -await

await必须写在async函数中

# 对象方法扩展

* Object.keys
* Object.values
* Object.entries(将对象转化为二维数组)

# ES9正则扩展-命名捕获分组

```js
 let a ='<a href="https://www.baidu.com/">百度</a>';
    const reg=/<a href="(?<url>.*)">(?<name>.*)<\/a>/;
    const result=reg.exec(a);
    console.log(result);
    console.log(result.groups);
```

# ES10扩展对象方法

Object.fromEntries(数组或map)

如果是二维数组，数组中第一个参数为Key，第二个 参数为value

## -字符串扩展

* trimstart 消左
* trimend  消尾

## -数组扩展

* arr.flat(深度)

将高维数组转化为低维数组，参数为深度，若想将三维数组转为一维数组，参数应该为2

* flatMap

# ES11的私有属性

```js
    class Person{
     name;
     #age; //私有属性
     #weight; //私有属性
     constructor(name,age,weight){
         this.name=name;
         this.#age=age;
         this.#weight=weight;
     }
        intro(){//类内部的方法可以得到私有属性
            console.log(this.#age);
            console.log(this.#weight);
        }
    }
    const girl=new Person('cbm',15,122);
    console.log(girl);
    console.log(girl.#age);//类的外部得不到结果
```

# ES11-Promise.allSettled方法

返回结果始终是成功的(无论promise是成功还是失败，都会返回)

对比：promise.all()中如果有一个promise对象是失败的，则返回的结果就是失败的



#  ES11动态引入



# Bigint类型

大整形

运用:大数值运算

只能同类型互相加减
