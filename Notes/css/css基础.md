# css引入方式
   >1.内嵌式: 写在style中 <br>
   >2.外联式：写在.css文件中 (项目开发)<br>
   >3.行内式: 写在标签的style属性中

<br>
<br>
<br>

# 选择器
1.标签选择器
``` css
<style>  p{ color:red;}
</style>
```

2.类选择器
``` css
<style> 
.类名1{color:red;} /*类名不能以数字和下划线开头*/
.类名2{font-size:10px;}
</style>

<body>
<p class="类名1"> asd</p>
<p class="类名1 类名2">asd</p>/* 调用的多个类名之间空格隔开*/
</body>
```


3.id选择器 
``` css
<style>
#id名{color:red;}
</style>

<body>
<p id="id名">asd</p>
</body>
```
用途主要为配和`js`找标签<br>
在一个页面上是唯一的，不可重复
<br><br>

4.通配符选择器

``` css
*{color:red}
```
所有标签
<br><br><br>


# Font-family

> font-family:微软雅黑，宋体，sans-serif;

如果电脑没有安装微软雅黑，就用宋体，若也没有宋体则按任意一种非称线字体显示
<br><br><br>

# 层叠性
``` css
p{
   color:red;
   color:blue
}
```
字体呈现蓝色，因为层叠性，后面覆盖前面的属性。
<br><br><br>

# font简写
>font:style weight size family

>font:style weight size/`line-height` family

复合属性 
前两个属性可以省略，视为默认
<br><br><br>

# text-align:center
  可用的元素：
  1.文本
  2.span、a标签
  3.input、img

# line-height的间距具体是哪里到哪里的间距
<br>

# 居中
>标签居中:`margin`

>内容居中:`text-align:center`
   
<br><br><br>

# 并集选择器の格式
```
标签a,
标签b,
……{css}
```
<br>
<br>
<br>


# 不同标签可以使用相同类名
<br>
<br>
<br>

# backgroud的复合写法
`url`、`color`、`repeat`、`position`顺序随意
如果`position`中使用关键字可以前后随意，若使用数字则以先水平后垂直的顺序。
<br>
<br>
<br>

# CSS的继承性
>`控制文字的属性都能继承，不是控制文字的属性都不能继承`

>例外：若有默认颜色的标签，如a标签，则无法继承颜色；
如有字体默认大小的标签，如h标签，则无法继承大小

<br>
<br>
<br>

#  层叠性
优先级一样才会有层叠关系

<br>
<br>
<br>

# 复合选择器的优先级
<br>
<br>
<br>

# border样式
除去`dashed`、`solid`、`dotted`，其它样式并不是所有浏览器都能够兼容。

<br>
<br>
<br>

# 盒子尺寸
>width+border-left的尺寸+border-right的尺寸× height+border-top+border-bottom

<br>
<br>
<br>

# margin和padding的参数

`四个参数`:
顺时针顺序：上、右、下、左

`三个参数`:上、左右、下


<br>
<br>
<br>

# div设置的是content的宽高 




<br>
<br>
<br>

# 外边距的合并现象
垂直布局的块级元素,上下的margin会合并，两者区间的margin取决于最大值


<br>
<br>
<br>


# 伪元素
```css
div::before{
   content:''  /*content必须存在,若无内容则单引号'*/
}
div::after{
   css
}
```
默认为`行级元素`


# placeholder样式
```css
input::placeholder{}
```

<br>
<br>
<br>


# 图片垂直居中
>vertical-align:middle


# 网页开发
* `标准流`
* `浮动`
* `定位`
<br>
<br>
<br>

# hover
`使用hover伪类控制其它元素时, a:hover b,b应为a的子元素`
`hover+xxx`控制兄弟元素
<br>
<br>
<br>


# background-position
`background-position:0 0`
图片向左则第一个参数为负数。
图片向上则第二个参数为负数。
<br>
<br>
<br>


# background-size
* 数字+px
* 百分比
* contain:将背景图片等比例缩放,可能有留白
* cover:将背景图片等比例缩放，直到盒子没有空白
  `如果图的比例和图片的比例相同，contain和cover展示的效果相同`

  <br>
  <br>
  <br>



  # background复合写法
  `background:color image repeat position/size(没有顺序之分)`
  <br>
  <br>
  <br>


  # box-shadow设置盒子阴影
* h-shadow 水平偏移量，必填
* v-shadow 垂直偏移量，必填
* blur 模糊度
* spread 阴影扩大
* color 阴影颜色
* inset 将阴影改为内部阴影(外阴影不用设置，outset会报错)
<br>
<br>
<br>


# transistion过渡
* 过渡的属性（all，width,height)
* 过渡的时长(s)
` 在要变样式的元素里加transistion，而是不在hover里加`
<br>
<br>
<br>


# html lang="en"
指网页默认英语。
中文参数为:`zh-CN`

<br>
<br>
<br>

# SEO简介
SEO(Search Engine Optimization):搜索引擎优化
作用：让网站在搜索引擎上排名靠前
提升SEO的方法：
1. 竞价排名
2. 网页为html后缀
3. 标签语义化（在合适的地方使用合适的标签）
<br>
<br>
<br>


# SEO三大标签
* title
* description  (meta name="desc")
* keywords   (meta name="keyword")

<br>
<br>
<br>


# 外链式样式表
`后写的生效，具有层叠关系`



<br>
<br>
<br>
