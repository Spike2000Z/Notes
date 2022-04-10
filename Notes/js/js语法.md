# 浏览器
* 渲染引擎 解析html和css，俗称内核
* js引擎  也称js解释器 逐行解释
<br>
<br>
<br>



# 组成
* ECMASCRPIT
* DOM
* BOM
<br>
<br>
<br>

# 书写位置
* 行内式
* 内嵌式
* 导入 
```css
<script src=""></script>
```
<br>
<br>
<br>

# var命名
 $、_、英文字母开头

<br>
<br>
<br>

# var
var num1=010;
var num2=0xa;
`八进制`的数字开头为0.上图num1的值为8。
`十六进制`数字开头为0x,num2为10

<br>
<br>
<br>

# 转义
 \n 表示换行
 <br>
 <br>
 <br>

 # true为1,flase为0，可参与运算
 <br>
 <br>
 <br>


 # String(num)、num.toString()

 <br>
 <br>
 <br>

 # 转数字
*  parseInt(String)
```js
parseInt("120px")
```
结果为数字类型的120
小数则会取整
* Number(string)
* 隐式转换
console.log('12' - 0);
字符间的相减也会算出数字形式
<br>
<br>
<br>

# boolean()
''、0、Nan、null、undefined为false
其余全为true
<br>
<br>
<br>


# 先置自增和后置自增
```js
var age=10;
console.log(++age + 10); // 结果为21
console.log(age++ + 10); // 结果为20 
//但age结果还是一样的
```
<br>
<br>
<br>


# 双等号判断会转型
把字符串和数字相比较，字符串会转型。
<br>
<br>
<br>


# 短路运算
123 && 456 返回456
0 && 3232 && 123*9999  返回0
<br>
<br>
<br>

# 逻辑中断
123 || 456 返回123
0 || 456 || 789 返回 456
<br>
<br>
<br>


# argument
只有函数才有argument对象，内置不需要声明
argument:传递过来的实参
<br>
<br>
<br>


# 声明函数 
* function fn(){ 命名函数
  }  
  fn();
* var fn= function(){  匿名函数
  }
  fn();

  <br>
  <br>
  <br>

  # 全局变量
  * 在script中声明
  * 在函数内部没有声明直接赋值的变量也是全局变量
  <br>
  <br>
  <br>

  # 预解析
  js引擎会把var和function提升到当前作用域的最前面
  * 变量提升
  把变量声明提升到当前作用域最前面 不提升赋值操作，匿名函数也是如此
  * 函数提升
  案例：
```js
  f1();
  console.log(c);
  console.log(b);
  console.log(a);  
  function f1(){
    var a=b=c=9;
     console.log(a); 
       console.log(b);
         console.log(c);
  }
```
<br>
<br>
<br>

# 创建对象
  var obj={
    name:'cbm',
    age: 18,
    sayHi:function(){ };
  }

<br>
<br>
<br>


# for-in 遍历对象




