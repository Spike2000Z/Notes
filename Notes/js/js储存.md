# 1.SessionStorage
* 存储在用户的浏览器中
* 页面刷新也不丢失数据，浏览器关闭时死亡
* 只能储存字符串，将对象JSON.stringify()
## 1.1具体方法
* sessionStorage.setItem(keyname,value)
* sessionStorage.getItem(keyname)
*  sessionStorage.removeItem(keyname);
*   sessionStorage.clear();


# 2.localStrorage
* 生命周期永久生效，除非删除，关闭页面也是存在的
* 多窗口共享（同一浏览器）
## 2.1具体方法
同SessionStorage
