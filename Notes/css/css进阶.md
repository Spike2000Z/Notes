# 文字图标
<br>
<br>
<br>

# 平面转换(位移、旋转、缩放)
`transform`
<br>
<br>
<br>

# 位移
`transform:translate`实现位移效果
```css
 transform: translate(100px,50px); /*向右100px,向下50px*/
 transform: translate(100%,50%);  /*盒子自身的百分比*/

```
![图片](D:\陈壁铭\Notes\Notes-images\平面转换.jpg)
<br>
配合`transition`实现平滑位移
<br>

```css
transform:translate()  /*一个值代表x轴方向的移动*/
transform:translateX() /*X */
transform:translateY() /*Y */
```

<br>
<br>
<br>	

# background-position
`background-position:right 0;` /*背景图最右边 */
<br>
<br>
<br>


# hover控制改变伪元素
`hover::before`
`hover::after`
不需要加空格
<br>
<br>
<br>



# 旋转
`transform:rotate`
<b>角度单位是`deg`</b>
默认按照中心旋转
<br>
`transform:origin: 原点水平位置 原点垂直位置`

参数值：
* 方位名词（top、left……）
* 像素单位
* 百分比（按照盒子自身尺寸）
<br>
<br>
<br>


# 多重转换
`transform:translate() rotate()`
一边旋转一边位移，类似轮胎滚动效果
`transform:rotate() translate()`
效果并不是你想象的那样,但终点是一样的。
`单独写开会因为重叠性重叠，展现后一个属性的效果`


# 缩放
`transform:scale(x轴缩放倍数，y轴缩放倍数)`
一般只写一个参数表示x轴和y轴等比例缩放。
<br>
<br>
<br>


# opacity(透明度)
`配合transition使用`
<br>
<br>
<br>


# 渐变背景
`background-image:linear-gradient(
    颜色1，
    颜色2
);`

<br>
<br>
<br>

# 透视
`perspective:800~1200（推荐）`给透视的盒子的父级加
眼睛离屏幕的距离。
`transform:translateZ`参数为正离得近，参数为负离得远。

<br>
<br>
<br>

# transform:rotate
`rotateZ`是围绕Z轴转动，同`rotate`效果相同。
`rotateX/Y`是围绕X/Y轴转动，具有空间转换效果
`rotate3D(x,y,z,角度度数)`自定义旋转轴的位置
x,y,z取值0-1之间的数字 
<br>
<br>
<br>

# 旋转的左手法则
`拇指指向转轴的正方向，当rotate值为正时，图片旋转方向为四指方向`
<br>
<br>
<br>

# transform-style:preserve-3d 立体呈现
添加后使子元素处于真正的3d空间，默认值为`flat`表示子元素处于2d平面内呈现。
<br>
<br>
<br>



# 立体导航思路
![](../Notes-images/立体导航.jpg)
<br>
<br>
<br>

# animation动画效果
`transition 实现的是两个状态之间的变化过程`
`animation 实现多个状态之间的变化，动画过程可控`

* 定义动画
  ```css
  @keyframes 动画名称{
      form{}
      to{}
  }
  ```
  或
  ```css
  @keyframes 动画名称{
      0%{}
      10%{}
      15%{}
      100%{}
  }
  ```
  实现多段动画
  <br>


* 使用动画
  `animation:动画名称 动画时长;`
  `annimation:动画名称 动画时长 速度曲线 延迟时间 重复次数 动画方向 执行完毕时状态`
  第一个时间表示动画是时长，第二个时间表示延迟时间，其余参数不分先后顺序。
  `infinite`无限次动画
  `alternate`动画方向 
  `执行完毕状态:backwards(默认,最初状态),forwards(最后状态)`
  `animation:动画1，动画2，……`实现多组动画
  `延迟时间`实现动画顺序不同
  <br>
  <br>
  <br>


# 使用annimation和精灵图实现动画效果
`steps的段数同精灵图段数相同`
<br>
<br>
<br>


# 走马灯 无缝动画
`显示页面的几张图要在复制放在最后面以便使用infinite时不会太突兀直接从最后跳到最前，实现无缝的动画效果，看不出开头的图片是哪一张.`
<br>
<br>
<br>


# 网页开发是基于逻辑分辨率开发
<br>
<br>
<br>

# 视口(viewpoint)
`使网页宽度和逻辑分辨率的宽度相同`
`移动端没有视口标签默认宽度980px`
`PC端默认有视口`
<br>
<br>
<br>

# 二倍图
指的是750px的图
为的使不让图片失真、模糊
<br>
<br>
<br>

# 百分比布局(流式布局)
`古老的布局方案`，只考虑宽度自适应，高度固定。
<br>
<br>
<br>

# flex布局(弹性布局)
`浏览器提倡的布局模型`
`避免浮动脱标的问题`
`不兼容低版本浏览器`
<br>
<br>
<br>


# flex的使用
`父元素(亲爹)添加display:flex,子元素自动挤压或拉伸`
`父级(弹性容器),子级(弹性盒子)`
`默认：X轴(主轴),Y轴(侧轴、交叉轴)`

<br>
<br>
<br>

# 主轴对齐方式(justify-content)
参数:
* flex-start:起点开始排列
* flex-end:终点开始排列
* center:主轴居中
* space-around：视觉效果子级之间的距离是两头子级和父级距离的两倍。
* space-between:
* space-evenly:子级与子级、子级与父级之间的间距相等
<br>
<br>
<br>

# 侧轴对齐方式(align-items)
`添加到弹性容器(父级)`
参数:
* flex-start
* flex-end
* center
* stretch:子级没有高度时，有拉伸效果。该参数为align-items的默认效果。甚至不用设置。
<br>
<br>
<br>


# 侧轴对齐方式(align-self)
`添加到弹性盒子(子级)`
参数同`align-items`

<br>
<br>
<br>


# 弹性盒子的宽高
`如果不给宽，弹性盒子的宽同内容相关`
`如果不给高且修改了默认设置stretch, 则高度同内容相关`
<br>
<br>
<br>

# 伸缩比
* 属性：flex
* 取值分类：整数
  `占用父盒子剩余尺寸`
  <br>
  <br>
  <br>


  # 主轴方向(flex-direction)
  `column`主轴垂直,侧轴自动切换水平
  <br>
  <br>
  <br>


  # 弹性布局子级尺寸会自动伸缩
  <br>
  <br>
  <br>

  # 弹性盒子换行显示
  `flex-wrap:wrap`实现换行 
  默认值为`nowrap`
  `align-content`调整行间的显示方式，取值与`justify-content`基本相同
<br>
<br>
<br>

# 移动适配
`网页元素随着设备分辨率相应调整`
* rem
* vw/vh
<br>
<br>
<br>

# rem
`相对单位`
1rem=1HTML字号大小
`HTML字号=根标签字号`
`HTML标签是网页的根标签`
<br>
<br>

# rem移动适配-媒体查询
`媒体查询能检测视口的宽度，然后编写差异化的CSS样式`
一般把HTML标签字号设置为视口宽度的1/10。

```css
@media(width:375px){
  html{
    font-size:37.5px
  }
}

```
<br>
<br>
<br>


# flexible
`通过js实现通用移动适配`
<br>
<br>
<br>

# less语法
`目标:使用Less运算写法完成px到rem的转换`
使css代码变简单,使css具备一定逻辑能力
`浏览器不会识别less文件`
<br>
<br>
<br>



# less计算
* 加减乘正常
* 除法
```less
width:(100/12rem);
width:100./12rem;
```
<br>
<br>
<br>

# less变量
```less
@color:pink;
.box1{
  color:@color;
}

.box2{
  background-color:@color;
}
```
 `方便修改`
 <br>
 <br>
 <br>


 # less导入
 `在Less导入其它Less文件中的css样式，自动生成的css文件中自动生成导入的样式`
 @import+空格+'相对路径';
 less文件可以省略后缀

 <br>
 <br>
 <br>

 # less导出css文件
 * easyless插件导出方法
 * 控制当前文件导出路径(还可以改变css的名字)
    less第一行:
    `// out: 路径 (css命名) `

<br>
<br>
<br>

# less禁止导出
less第一行：
`// out:false`
<br>
<br>
<br>

# CSS实现箭头
`将border属性的颜色设置为transparent`
<br>
<br>
<br>

# vw/vh
`相对视口尺寸计算结果`
* vw:viewpoint width
* vh:viewpoint height
先算出vw/vh，再根据设计稿计算出具体数值。
计算出通用的vw\vh，以达到移动适配的效果。
<br>
<br>
<br>

# 响应式网页
`核心：媒体查询(@media)`
常用写法：max-width、min-width
<b>具有层叠性</b>
min-width:从小到大
max-width:从大到小
保证后写的样式层叠前面的样式

```css

 @media screen and(min-width:500px) and(max-width:900px) {
            
        }
```




# 媒体查询完整写法

`@media 关键词 媒体类型 and (媒体特性){CSS代码}`
关键词:and、only、not
<br>
<br>
<br>

# 媒体查询Link引入
```html
<link rel="stylesheet" href="./css/1.css" media="(max-width:500px)">
    <link rel="stylesheet" href="./css/2.css" media="(min-width:700px)">
```
 不同宽度对应不同样式表
 <br>
 <br>
 <br>

