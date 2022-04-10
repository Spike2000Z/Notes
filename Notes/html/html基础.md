# html标签 

## $\color{#FFEEDD}{input}$
 ```html
<input type="radio" name="1">1
<input type="radio" name="1">2
 ```
input标签`radio`类型如果指定`name`属性相同，则相当于按钮组的功能<br><br><br>





## $\color{#FFEEDD}{如何做到点击单选框文本也能选中单选框}$

<input type="radio"  name="sex" checked id="boy"> <label for="boy">男</label> <label><input type="radio" name="sex">女</label>

```html
<input type="radio"  name="sex" checked id="boy"> <label for="boy">男</label> <!-- 方法一 -->
<label><input type="radio" name="sex">女</label><!-- 方法二 -->
```
<br><br>


## $\color{#FFEEDD}{textarea}$
通过`css`禁用右下角拉大功能

​    


​        

       # HTML表单

## -requier

表单必填

## -autoFocus

页面刷新自动对焦

## -*novalidate*

提交表单时不对表单输入进行验证

## -使用正则表达式判断

patten

## -autocompletel自动记住输入的内容

参数为on/off

## -datalist下拉菜单

```html
 <input type="text" list="tips">
 <dataList id="tips">
     <option value="a"></option>
     <option value="a"></option>
     <option value="a"></option>
     <option value="a"></option>
     <option value="a"></option>
     <option value="a"></option>
    
 </dataList>
```

## -label

```html
<label for="man">男</label>
 <input type="radio" name="sex" id="man">
 <label for="woman">女</label>
 <input type="radio" name="sex" id="woman"> //点击单选框的标签，也是会选中d
```

