# HTTP

## 请求报文

* 行
* 头
* 空行
* 体 get时为空/post时可不为空

## 响应报文

* 行
* 头
* 空行
* 体

# express



```js
const express =require('express');

const app=express();


app.get('/sever',(request,response)=>{
    //设置响应头，设置允许跨域
    response.setHeader('Access-Control-Allow-Origin','*');
response.send('Hello express');
});

app.listen(8000,()=>{
    console.log("服务已经启动")
})
```

?

```js
  const button=document.querySelector('button');
        button.onclick=function(){
           //1.创建对象
            const xhr=new XMLHttpRequest();
            //2.初始化，设置请求方法和url
            xhr.open('GET','http://127.0.0.1:8000/sever');
            //3 .发送
            xhr.send();
            //4.事件绑定 处理服务端返回的结果
            //readystate xhr对象中的属性，状态0 1 2 3 4
            //0:未初始化；1：open()调用完毕 2:send()方法调用完毕 3:服务端返回部分结果 4：服务端返回全部结果
            xhr.onreadystatechange=function(){
                //判断（服务端返回了所有结果）
                if(xhr.readyState === 4){
                 //判断响应状态码
                 //2开头的都表示成功
                 if(xhr.status >=200 && xhr.status <300){
                     //处理结果 行、头、空行、体
                     console.log(xhr.status);
                     console.log(xhr.statusText); //响应状态字符串
                     console.log(xhr.getAllResponseHeaders);//服务端返回所有响应头
                     console.log(xhr.response);//响应体
                     
                 }else{

                 }
                }
            }
        }
```

# 对对象进行字符串转换

* 服务端

let str =JSON.stringify(data);    将JS值转为JSON字符串

response.send(str);

* 接收端

1.let data=JSON.parse(xhr.response)  //手动转化，将响应体中的JSON字符串转化为JS对象

2.xhr.responseType='json'; //设置响应体数据的类型

# 解决IE缓存问题

```js
xhr.open('get','http://127.0.0.1:8000/ie?t='+Date.now());
```



# 请求超时与网络异常

* xhr.timeout={time}   //超过该事件自动取消respone

* xhr.ontimeout=function(){ }

  xhr.onerror=function(){ //断网   

  }

# 取消请求

abort方法

# 请求重复发送问题

   设置一个判断值，在发送请求前判断是否上个请求的结果是否返回，如果还没返回，取消上一个请求，创建一个新的请求。

发送请求后，该值为true, 当ajax的readyState的值为4时，为flase，表示已无正在发送的请求。

# axios

## -axios发送get请求

```html
 <script crossorigin="anonymous" src="https://cdn.bootcdn.net/ajax/libs/axios/0.26.1/axios.min.js"></script>
```

```js
 axios.defaults.baseURL='http://127.0.0.1:8000';
        button[0].onclick=function(){
             axios.get('/axios-sever',{
                 //url 参数
                 params:{
                     id:100,
                     vip:7
                 },

                 headers:{
                     namexcxcx:'cbm',
                     age:29
                 }
             });

        }
```

## -axios通用方式发送请求

```js

button[2].onclick=function(){
            axios({
                method:'POST',
                url:'/axios-sever',
                //url参数
                params:{
                    vip:1000,
                    level:300
                },
                //头信息
                headers:{
                    headeraaaaaa:100,
                    headerbbbbbb:23133
                },
                //请求体参数
                data:{
                    username:'chengming',
                    pasword:'space'
                }
                
            }).then(response=>{
                console.log(response.status);
                console.log(response.statusText);
            })
        }
```

# fetch

```js
button.onclick=function(){
            fetch('http://127.0.0.1:8000/fetch-sever?vip=10',
            {
                method:'POST',
                headers:{
                    name:'chenbiming'
                },
                body: 'username=admmin'
            }).then(response =>{
                return response.json()
            }).then(response =>{
                console.log(response);
            })
        }
```





# 同源策略

同源: 协议、域名、端口号 必须完全相同。

违背同源策略就是跨域。



# 如何解决跨域

## -jsonp

只支持get,非官方

```js
<script src="http://127.0.0.1:8000/jsonp-sever"></script>
```

```js
 app.all('/jsonp-sever', (request, response) => {
        //设置响应头，设置允许跨域
        const data={
            name:'陈壁铭jsonp'
        }
        response.send('console.log("sdsd")'); //返回一段js代码
    });
```

```js
  const script=document.createElement('script');
    script.src='http://127.0.0.1:8000/jsonp-sever';
    document.body.appendChild(script);
```

## -CORS

支持get/post,官方

```js
 response.setHeader('Access-Control-Allow-Origin', '*');
```

