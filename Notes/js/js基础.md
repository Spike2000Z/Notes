# DOM
`文档对象模型`是W3C组织推荐的处理可扩展标记语言，也就是html或者xml的标准编程接口。
<br>
<br>
<br>


# document.getElementsByTagName
返回元素对象集合的伪数组
如果页面中只有一种元素，返回的还是伪数组
如没有元素，返回空的伪数组形式
<br>
<br>
<br>

# document.querySelector
返回指定选择器的第一个元素对象,选择器需要加符号
<br>
<br>
<br>


# 获取body元素和获取html元素
document.body // 获取body
document.documentElement //获取html 
<br>
<br>
<br>


# 事件执行过程
事件源-事件类型-事件处理程序
<br>
<br>
<br>

# innerText和innerHtml
区别：innrText不识别html标签，去除空格和换行    
<br>
<br>
<br>


# js修改css
* element.style(样式较少)
采用驼峰命名法，产生的是内行样式
* element.className
  该类名


<br>
<br>
<br>


# 焦点
* onfocus 获得焦点
* onblur  失去焦点
可用于表单

<br>
<br>
<br>


# 移除属性 removeAttribute 
<br>
<br>
<br>

# H5自定义属性
```html
<div data-index="2" data-list-name="cbm"></div>
```
```js
var div =document.querySelector('div');
div.dataset.index; //获取data-index属性
div.dataset.listName;  //使用驼峰命名法获取data-list-name属性
```
dataset是一个集合，里面存放了所有以`data`开头的自定义属性
IE11以上才支持
`getAttribute方法没有兼容性问题`
<br>
<br>
<br>


# 节点
元素结点：1
属性节点：2
文本节点：3
<br>
<br>
<br>


# 选取子节点
* childNodes选取的是所有结点
* children只选取元素节点
<br>
* firstchild 第一个子节点（所有元素）
* firstElementChild 第一个子元素结点（兼容性问题）
`实际开发使用children[0]获取第一个子元素结点,children[element.children.length-1]获取最后一个子元素结点`

<br>
<br>
<br>


# 兄弟结点
element.nextSibling:得到下一个兄弟结点(所有节点)
element.netxElementSibling 
previousElementSibling
<br>
<br>
<br>


# 动态创建元素结点
* document.CreateElement
# 添加结点
* node.appendChild(child)    类似于push
* node.insertBefore(要插入的元素，指定的元素)    指定元素前面
# 删除结点
node.removeChild(child)
# 克隆结点
node.cloneNode();
如果括号参数为空或者false,则是`浅拷贝`，只是复制结点本身，不克隆里面的子节点。

参数为true为深拷贝，克隆里面的子节点
<br>
<br>
<br>

# 阻止连接跳转
```html
<a href="javascript:;">
```
<br>

# 动态生成表格
<br>
<br>
<br>


# document.wirte()
当文档流加载完后再调用该方法会导致`页面重绘`
<br>
<br>
<br>


# 三种动态创建元素的区别
* document.wirte()
当文档流加载完后再调用该方法会导致`页面重绘`
* innerHtml
创建多个元素效率更高，不是采用拼接字符串，而是采取数组形式拼接。
* document.createElement()
  创建多个元素效率低一点点，但是结构清晰。
  <br>
  <br>
  <br>


# arr.join('')
将数组转化为字符串

<br>
<br>
<br>


# dom重点核心
创建、增删改查、属性操作、事件操作
<br>
<br>
<br>


# 注册事件（绑定事件）
* 传统注册方式
`<button onclick=''></button>`
`button.onclick=function(){}`
特点：具有`唯一性`
* 方法监听注册方式
  addEventListener()
  IE9之前使用attatchEvent()代替
  特点 :同一个元素同一个事件可以添加`多个监听器`
  <br>

  # 解绑事件
* 传统方式
  `button.onclick=null`
* 方法监听注册方式
  `button.removeEventListener()`
  不使用匿名函数
```css
    function fn(){
            alert('22');
            div[0].removeEventListener('click',fn);
        }
        div[0].addEventListener('click',fn);
```

   button.detachEvent()(了解)

   <br>
   <br>
   <br>


# dom事件流
* 捕获阶段
* 冒泡阶段
* 目标阶段
  

JS代码中只能执行捕获或者执行中的一个阶段
onclick和attachEvent只能得到冒泡阶段 
addEventListener第三个参数为true时位于捕获阶段，false或省略为冒泡阶段，默认为冒泡阶段。
`onblur、onfoucs、onmouseover、onmouseleave没有冒泡阶段`
<br>
<br>
<br>

# 事件对象
event
window.event(IE)
形参，无需传递实参
event.target ：触发事件的元素（点击哪个元素，就返回哪个元素）
this:绑定事件的元素

<br>
<br>
<br>

# 阻止默认行为
让链接不跳转，让提交按钮不生效……
e.preventDefault();
<br>
<br>
<br>

# 阻止冒泡阶段
e.stopPropagation();
<br>
<br>
<br>


# 事件委托
`不是每个子节点单独设置事件监听器，而是事件监听器设置在其父节点上然后利用冒泡原理影响设置每个子节点`
<br>
<br>
<br>

# 常用的鼠标事件
* contextmenu+e.preventDeafault()：禁止弹出右键菜单
* selectstart+阻止默认行为 ：禁止鼠标选中
* mousemove:鼠标移动1px便触发
<br>
<br>
<br>


# 鼠标事件对象
* e.clientX/e.clientY(可视区的距离)
* e.pageX/e.pageY(相对于页面文档) 
<br>
<br>
<br>


# 常用的键盘事件
* onkeyup   松开
* onkeydown  按下
* onkeypress  按下(不识别功能键，如方向键、ctrl、shift)
执行顺序 `down>press>up`
keydown和keypress：在文本框里边，事件触发的时候文字还没有落入文本框中
<br>
<br>
<br>

# 键盘事件对象
* e.keyCode：返回触发按键的ASCLL码
`keyup和keydown不区分大小写，所以输入大小写ascll码一样`
<br>
<br>
<br>


# DOM与BOM
![图片](D:\cbm\Notes\Notes-images\DOM与BOM.png)
<br>
<br>
<br>


# window.onload
只能写一次，多个的话以最后一个为准
`如果使用addEventListener则没有限制`:
```js
window.addEventListner('load',function(){}
)
```
等页面全部加载完毕才执行
<br>
<br>
<br>

# DOMContentLoaded
当DOM加载完成就触发，不包括样式表、图片等
```js
document.addEventListener('DOMContentLoaded',function(){})
```
<br>
<br>
<br>


# resize实现响应式布局 
* window.innerWidth
* window.innerHeight
<br>
<br>
<br>


# 定时器
* setTimeout()
setTimeout(function(){},ms);
setTimeoyut(函数名,ms);
setTimeout('函数名()',ms);
`ms为毫秒，省略则为0`
* setInterval(回调函数，ms);
`反复调用一个函数，每隔一段时间就调用一次函数`

<br>
<br>


# 回调函数
* 计时器
* 事件绑定
<br>
<br>
<br>


# 停止定时器
clearTimeout(定时器ID)
clearInterval(ID)
<br>
<br>
<br>


# this
* 指向调用者
* 全局作用域或者普通函数中的this指向全局对象window(定时器)
* 构造函数
```js
function Fun(){
  console.log(this);
}
var fun=new Fun(); //this 指向的是fun的实例对象
```
<br>
<br>
<br>

# 同步和异步
* 同步任务 （主线程执行栈）
* 异步任务（任务队列/消息队列）
回调函数、定时器
<br>
<br>
<br>

# JS执行机制
主线程不断重复获得任务、执行任务、再获取任务、再执行，这种机制被称为`事件循环`
![](D:\cbm\Notes\Notes-images\js执行机制.png)
<br>
<br>
<br>


# 获取localtion.search的值
```html
  <form action="5.html"> //默认get方式提交
   用户名： <input type="text" name="uname">
   <input type="submit" value="登录"></form>
```
`substr(起始位置,截取几个字符);` 截取问号
`split("=")` 分割等号
<br>
<br>
<br>


# location常见方法
* location.assign('url') ：重定向 同href
* location.replace(): 替换当前页面，不记录历史，无法退回
* location.reload(): 刷新，参数为true，ctrl+F5强制刷新
<br>
<br>
<br>


# navigator 对象
navigator.userAgent
<br>
<br>
<br>

# histroy对象
* history.forward() 相当于浏览的前进按钮
* history.back()
* histroy.go(数字)  数字代表前进几步，负数为后退







