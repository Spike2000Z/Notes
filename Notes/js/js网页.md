# 元素偏移量offset系列
* offsetTop
* offsetLeft
以带`有定位`的父亲为准，如果没有父亲或者父亲没有定位则以`body`为准

* offsetWidth
* offsetHeight
包含`padding`、`border`
* offsetParent
返回有定位的父亲，如没定位则返回`body`
注意:parentNode返回的是最近一级的父亲，无关定位
<br>
<br>
<br>


# clint/scroll


# offset与style
![](..\Notes-images\offsetandStyle.png)
offset只能读

<br>
<br>
<br>

# 拖动模态框
主要方法：offsetLeft、offsetTop、pageX、pageY……
<br>
<br>
<br>


# 京东放大镜和可拖动表单
<br>
<br>
<br>


# client系列
* clientLeft  左边框大小
* clientTop
* clientWidth  返回自身包括padding、content的宽度
* clientHeight
和offset的区别:offset`包含边框`

<br>
<br>
<br>

# flexible.js解析
# 立即执行函数
* （function(){})() 第二个小括号可以当成调用函数，可加参数
```js

        (function(a){
            console.log(a);
        })(15)
```
* (function(){}())
无需调用,都是局部变量不会有冲突问题 
<br>
<br>
<br>


# 触发winodw.onload事件
* a标签的链接
* F5或者刷新按钮
* 前进/后退（火狐浏览器不适用,得使用window的pageshow事件)

<br>
<br>
<br>



# scroll系列
<br>
<br>

## scrollWidth/scrollHeight
包含border、padding
与client的区别在于:scroll系列展示元素内容实际大小
<br>
<br>

## scrollTop/scrollLeft
* scrollTop:内容向上滚动的距离
* scrollLeft
<br>
<br>

## 固定侧边栏
<br>
<br>

### 测出被滚动卷去的页面
* window.pageXOffset
* window.pageYOffset
注意:元素被卷去的头部使用`scrollTop`,页面则用`page`
侧边栏的`offsetTop`要写在scroll事件外边,不然一旦top为0，就无法判断了
<br>
<br>
<br>

#  三大系列对比
![](D:\cbm\Notes\Notes-images\三大系列.png)
获取元素位置:offset
获取元素大小：client
获取滚动距离:scroll

<br>
<br>
<br>


# mouseenter与mouseover事件的区别
mouseover鼠标经过`自身盒子`会触发，经过`子盒子`也会触发，mouseenter只会经过`自身盒子`触发
mouseenter搭配mouseleave使用
<br>
<br>
<br>


# 动画
原理：定时器`setInterval()`不断移动盒子位置
<br>
<br>

## 动画函数的封装
obj：目标对象
target:目标位置
<br>
<br>

## 给不同对象添加不同定时器
```js
function animate(obj,target){
    obj.timer=setInerval(function(){
        / 内容/
    },100)
}

```
定时器不重名

##  bug

如果设置一个按钮给如上定时器触发，连续点击按钮将导致开启多个定时器
解法：加上一行
clearInterval(obj.timer);

## 缓动动画效果
公式：（目标值-现在的位置）/10
匀速动画：盒子当前位置+固定值
缓动动画：盒子当前位置+ 变化的值
<br>
<br>

## 动画函数添加回调函数
<br>
<br>

## 🥵轮播图🥵
<br>

### 图片无缝滚动原理

<br>

把ul的第一个li复制一份放到ul的最后
当图片滚动到克隆的最后一张图片时，让ul快速的left为0 
<br>

### 手动调用点击事件

实现自动轮播!
<br>
<br>

## 节流阀
防止轮播图连续点击按钮变化过快，等上一个动画执行完毕后再执行下一个动画
核心:利用回调函数
<br>
<br>

## ⚪返回顶部
window.scroll(x,y)
不需要单位
可以使用定时器实现平滑滚动

## ⚪scoll滚动事件