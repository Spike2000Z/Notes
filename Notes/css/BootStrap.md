 # BootStrap
 `前端UI框架`
 <br>
 <br>
 <br>


 # BootStrap栅格系统
 `把网页等分成12份`
 响应断点：
 * 超小屏幕(<768px)  col-xs-*
 * 小屏幕(768-992)   col-sm-*
 * 中等(992-1200)    col-md-*
 * 大屏幕            col-lg-*
  `*指的是一行占几等份`
  `如果div间要有间距，需要时内容间拉开，而不是margin，内容已经充满，再加margin会导致换行`
  <br>
  <br>
  <br>

# .container
.container(wrapper)
.container-fluid(通栏)
.row和.col
`container自带间距15px,row自带间距-15px`
<br>
<br>
<br>


# 引入JS插件
```js
<script src="./bootstrap-3.4.1-dist/js/jquery.js"></script>
    <script src="./bootstrap-3.4.1-dist/js/bootstrap.min.js"></script>
```
先引入jq再引入bs，因为bs中使用了jq。