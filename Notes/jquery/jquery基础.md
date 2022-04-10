# 入口函数

* 等着DOM加载完毕再执行js代码

  $(document).ready(function(){

  执行代码

  });

* $(function(){

  ​      执行代码

  ​    });  //与上一个代码等价

  

  同

  

  jQuery(function(){

  执行代码

  })；





# **$**



与JQuery可替换



# **Jquery对象与DOM对象**

jq与原生获取的对象使用的方法不同



## -转换

### --DOM转JQ



```javascript
var video=documnt.querySelector('video');
$(video) //不加引号
```

### --JQ转DOM

* $('div')[index]
* $('div').get(index)



# JQ常用API

## -选择器

通用

## -隐式迭代

$(element).css('color','red');   //所有名为element的元素都会改变样式

## -筛选选择器

first\last\eq\odd\enven……

## -筛选方法

* .nextAll()   当前后的所有同辈元素
* .prevAll()
* .find()  后代选择器
* .parents('') 祖宗选择器

##  -排他思想

使用隐式迭代和兄弟选择器

```js
$('button').click(function(){
                $(this).css('background','#bfa');
                $(this).siblings().css('background','none');
            })
```

## -链式编程

```js
$('button').click(function(){
                $(this).css('background','#bfa').siblings().css('background','none');
            })
```



# JQ样式操作

## -设置类样式

* addClass('classname');  追加类名    *同原生classlist相同？*
* removeClass
* toggleClass('classname')  切换类

# JQ效果

![图片](D:\陈壁铭\Notes\Notes-images\JQ效果.png)

## -show

show([speed,[easing],[fn]])

* speed:动画时长
* easing:linear
* fn:回调函数

## -hide

参数同`show`

## -toggle

实现`show`和`toggle`的切换

## -hover

hover(经过函数,离开函数);

hover(经过/离开函数)

## -停止动画队列的排队行为

stop().动画效果

## -animate

animate({})



# JQ属性操作

## -获取属性

* 固有属性

$("a").prop("href")

* 自定属性

$('a').attr("index")

## -获取内容

*  获取文本

$("div").html() 

$('div').html('123') 修改

**text同理**

* 获取表单

$('input').val()

## -tofixed

tofixed(n):保留n位小数  



# 元素操作

## -遍历

* $('div').each(function(index,domEle){

//index为每个元素的下标

//domEle为每一个元素,为DOM对象

})

* $.each($('div'),function(index,domEle){   //遍历数据数组

  

  })

## -增删改查

* 创建

$("<li></li>")  

* 添加

**内部添加：**

append()  类似于原生的`appendchild`

prepend() 放到最前面

**外部添加：**

ater() 

before()

* 删除

$('ul).remove() 自杀

$('ul).empty() 删除匹配中的元素中的子节点





