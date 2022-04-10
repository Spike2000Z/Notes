# 触屏事件
## ⚪touch
* touchstart 点
* touchmove  划
* touchend   松

## ⚪TouchEvent
* touches 所有触摸屏幕的手指的列表
* targetTouches  触摸当前DOM元素的手指的列表
如果侦听的是一个DOM元素，上面两个值相同
* changedTouches  手指状态发生改变的列表，无到有或有到无

手指离开屏幕后，就没有了touches和targetTouches了，但是changedTouches还会有

## ⚪ 拖动元素
注意：手指移动会触发滚动屏幕事件，所以要阻止默认行为：e.preventDefault();

## ⚪🥵轮播图🥵
### *结构
3-1-2-3-1
前面要放一张图防止拖动时露馅
`注意：li与Ul的百分比宽度设置`

### *监听过渡完成的事件
transitionend
### *从最后一张第一张的时候去除过渡效果，防止回滚动画被看见
### *classList
* add
* remove
* toggle(有这类名去掉，没有这类名加上)
注意：类名前不用加.

## ⚪移动端常见特效
### *click 300ms延迟问题
原因是双击屏幕会缩放（double tap to zoom）页面
解决方案：
* 禁用缩放功能
```html
<meta name="viewpoint" content="user-scalable=no">
```
* 利用touch事件封装解决
1.手指触屏，记录触摸时间
2.离开屏幕，用离开的时间减去触摸时间
3.如果时间小于150ms,并且没有滑动过屏幕，定义为点击

<br>

* fastclick插件
  
  
### *swiper插件

