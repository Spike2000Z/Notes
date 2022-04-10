# BFC
<br>
<br>
<br>




# 水平垂直居中
* 固定宽高的块级盒子
1.绝对定位+margin
```css
 position: absolute;
            width: 200px;
            height: 200px;
            background-color: #bfa;
            top: 50%;
            left: 50%;
            margin-left: -100px;
            margin-top: -100px;
```

```css
  position: absolute;
            width: 200px;
            height: 200px;
            background-color: #bfa;
            top: calc(50% - 100px);
            left: calc(50% - 100px); /*同上*/
```
2. 绝对定位+margin:auto
```css
 position: absolute;
            width: 200px;
            height: 200px;
            background-color: #bfa;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            margin: auto;
```
* 不固定宽高的块级盒子
1.绝对定位+transform
```css
position: absolute;
            background-color: #bfa;
            left: 50%;
            top: 50%;
            transform: translateX(-50%);
            transform: translateY(-50%);
```
2.通过父级设置弹性布局

<br>
<br>
<br>

# 两栏布局
1.BFC原理(float+overflow)
2.浮动+maargin(一个浮动，另一个不浮动加margin)
3.flex布局



# 三栏布局
* 圣杯布局
```css 
 .layout{
          overflow: hidden;
          background-color: #bfa;
          width: 400px;
          height: 400px;
          padding: 0 200px;
      } .left,.middle,.right{
          float: left;
          height: 100%;
          color: white;
      }
      .left,.right{
          position: relative;
          background-color: brown;
          width: 200px;
      }.middle{

          width: 100%;
          background-color: darkblue;
      }.left{
          left: -200px;
          margin-left: -100%;

      }.right{
      margin-right:-100%;
      }
```
```html
<body>
    <header>a</header>
    <div class="layout">
        <div class="middle">Lorem ipsum dolor sit amet consectetur adipisicing elit. Inventore exercitationem quaerat pariatur amet! Repellendus explicabo amet consequuntur? Ipsum cumque adipisci fugiat, dolor maiores sit, veritatis iusto animi modi aliquam eveniet.</div>
  <div class="left">左边</div>
  <div class="right">右边</div>
    </div>
   <footer>b</footer>
   </body>
```
注意：margin百分比是父元素的百分比而不是自己的百分比，
如果宽度足够,left和right应该依次在middle的右边，因为它们都是左浮动的元素，但是因为宽度不够被挤到了第二行。
![图片](D:\cbm\Notes\Notes-images\圣杯布局1.jpg)
上图是left使用margin-left:-100%后到达父级元素的最左边，再使用相对定位的left:-{自己盒子的尺寸}就能到达预留的padding地区。

`关于margin-right取负的盒子，如果数值等于他自己本身，可以理解为这个盒子没有宽度。`<br>
`margin-right取负值，本身不会向右走，如果右边有盒子，右边的盒子会向左走`<br>
`right元素还有一种写法:margin-left:-200px,right:-200px，理解为向左位移200px进入left,middle一行，同时进入	middle内，再进行相对定位向右移动200px`





* 双飞翼布局
```css
.layout{
            height: 400px;
            width: 800px;
            margin-left: 200px;
        }.main,.left,.right{
            height: 100%;
            color: aliceblue;
            float: left;
        }
        .left,.right{
            background-color: orange;
            width: 100px;

        }.main{
           background-color: darkblue;
            width: 100%;
        }.main-contain{
            margin: 0 100px;
            height: 100%;
        }.left{
            margin-left: -100%;
        }.right{
            margin-left: -100px;

        }
```
```html
<body>
    <div class="layout">
        <div class="main"><div class="main-contain">232323</div>
        </div>
        <div class="left">322323</div>
        <div class="right">23323</div>
    </div>
   
</body>
```
注意:相比于圣杯布局，双飞翼布局不需要使用相对定位移出main中，因为主区域是main-contain，.left和.right定位main中,main-contain的margin里边。<br>
而圣杯布局则是定位在了主区域外面，layout的padding里面。






# margin
`margin：百分比的计算基于生成框的包含块(父元素)的width（margin-top/bottom也是如此）。`
相对于height计算会引起无限循环
正常流中的大多数元素都会足够高以包含其后代元素（包括外边距），如果一个元素的上下外边距是父元素的height的百分数，就可能导致一个无限循环，父元素的height会增加，以适应后代元素上下外边距的增加，而相应的，上下外边距因为父元素height的增加也会增加，如此循环。
<br>
注意:margin,padding基于宽度，但height的百分比还是基于父元素高度
<br>
<br>
<br>

# link、:visited、:hover、:active的执行顺序是怎么样的？
L-V-H-A，l(link)ov(visited)e h(hover)a(active)te，即用喜欢和讨厌两个词来概括。
