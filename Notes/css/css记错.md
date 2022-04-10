# li与ul的浮动

如果ul 设置`float:right`,且li也设置`float:right`，导航栏中常见，会使li元素反转(即本来的从左到右变成从右到左)，这时候要在li的样式里将`float`改为left，方可解决。
<br>
<br>
<br>

# 各种居中
* `margin:0 auto` 一般用来div水平居中，版心居中
* `text-align:center`
  1.文本
  2.span、a标签
  3.input、img
* `line-height`设置参数等于父级元素的高度实现水平居中，一般用于span,li等元素
* `vertical-align:middle` 水平居中，不适用于块级元素。
 行内块对齐行内块
 行内块对齐文字
<br>
<br>
<br>

# 盒子如何水平垂直都居中？
不能具体到像素

解：百分比定位后用transform
<br>
<br>
<br>

# transiton:all
`padding,margin`之类会受到all的影响，如果参数为all,页面刷新时会导致加了padding,margin的元素也执行过渡。
<br>
<br>
<br>


# li改浮动后掉下来可能是ul没有设置宽度
<br>
<br>
<br>


# background:center 背景图片居中
<br>
<br>
<br>


# 如果要让 body的高度覆盖整个屏幕，html中也需要添加height:100%
<br>
<br>
<br>

# 绝对定位和固定定位(fixed)都使元素转化为行内块

<br>
<br>
<br>

# 元素隐藏
* visibility:hidden(占位隐藏效果，不常用)
* display:none(不占位隐藏)

<br>
<br>
<br>


# 文字太多如何省略
```css
 text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
  ```

`如果是在flex布局,则该元素的父级还要添加flex权重并且指定具体宽高或宽高为零`

<br>
<br>
<br>

# link网站图标和iconfont
```html
<link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
    <link rel="stylesheet" href="./lib/iconfont/iconfont.css">
 ```

 <br>
 <br>
 <br>

 # 移动端适配
 根据设计稿给的尺寸进行对rem的换算。
 <br>
 <br>
 <br>


 # 利用CSS的层叠性提高代码效率
 <br>
 <br>
 <br>


 # 行内块元素换行写会有一点边距，无关padding和margin
 <br>
 <br>
 <br>



 # 如果要让有iconfont类名的i元素与span对齐，在i元素上使用vertical-align：middle
 而不是在它们的父级添加。
 <br>
 <br>
 <br>


 # flex布局换行效果
 flex-wrap:wrap
 <br>
 <br>
 <br>

 # 头部导航栏被底部覆盖问题
 * 背景色
 * z-index设置
  <br>
  <br>
  <br>


  # 轮播图小圈圈不一定要用List-style，设置为行块盒设置背景色也可行