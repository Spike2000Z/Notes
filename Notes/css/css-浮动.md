# 浮动默认顶对齐

<br>
<br>
<br>






# 清除浮动
子级元素有浮动属性的同时父级元素不设置高度，后面的标准流盒子会受到影响,当div容器需要根据子级内容改变高度时需要清除浮动。 清除浮动有以下方法：
* 定行高
* 额外标签
  >在要清除浮动的父元素的最后在加一个属性为`clear:both`的块级元素

* 单伪元素
  >与额外标签类似
* 双伪元素
```css
.clearfix::before,.clearfix::after{
            content: '';
            display: table;/* 外边距塌陷：父子标签都是块级，子级加Margin会影响父级的位置 */
        }.clearfix::after{
            clear: both;  /* 解决浮动 */
        }


<body>
<div class="div clearfix></body>
```
* overflow 
<br>
<br>
<br>
  

# 外边距塌陷
<br>
<br>
<br>




# calerfix清除浮动和解决外边距塌陷问题



<br>
<br>
<br>






