# XML简介

XML可扩展标记语言

XML被设计用来传输和存储数据

XML和HTML类似，不同的是HTML都是预订标签，而XML中没有预定义标签，全都是自定义标签，用来表示一些数据。

> 比如说，我有一个学生数据：
>
>  name=“孙悟空”;age=18;gender=“男”;
>
> 用XML表示：
>
> ​	<student>
>
> ​		<name> 孙悟空</name>
>
> ​		<age>18</age>
>
> ​		<gender>男</gender>
>
> ​	</student>

dwadw

# AJAX的特点

## Ajax的优点

（1）可以在无需刷新页面与服务器端进行通信

（2）允许你根据用户事件来更新部分页面



## Ajax的缺点

（1）没有浏览历史，不能回退

（2）存在跨域问题

（3）SEO不友好

> SEO搜索引擎



# HTTP协议

HTTP超文本传输协议

规范了请求和响应：

> 请求报文：
>
> 请求行：
>
> ​			POST	/****************	HTTP/1.1
>
> 请求头：
>
> ​			HOST: 
>
> ​			Cookie:
>
> ​			Content-type:
>
> ​			User-Agent: 
>
> 空行
>
> 请求体：
>
> ​			username=admin&password=admin
>
> 

> 响应报文：
>
> 响应行：
>
> ​			HTTP/1.1	200	OK
>
> 响应头：
>
> ​			
>
> 空行
>
> 响应体：
>
> 



# AJAX请求的基本操作

```js
// 获取button元素
const btn = document.getElementsByTagName("button")[0];

const result = document.getElementById("result");

// 绑定事件
btn.onclick = function() {
    // 1、创建对象
    const xhr = new XMLHttpRequest();
    // 2、初始化 设置请求方法和URL
    xhr.open('GET', 'http://127.0.0.1:8000/server');
    // 3、发送请求
    xhr.send();
    // 4、事件绑定 处理服务端返回的结果
    // readystate 是xhr对象中的属性，表示状态0 1 2 3 4
    xhr.onreadystatechange = function() {
        // 判断 服务端是否返回了所有的结果
        if(xhr.readystate === 4) {
            // 判断响应状态码 200 404 403 401 500
            if(xhr.status >= 200 && xhr.status < 300) {
                // 处理结果
                
                // 设置result的文本
                result.innerHTML = xhr.response;
            }
            else{
                
            }
        }
    }
}

```



# AJAX设置请求参数

```js
xhr.open('GET', 'http://127.0.0.1:8000/server?a=100&b=200&c=300');
```





# AJAX发送POST请求

```js
// 获取元素对象
const result = document.getElementById("result");
// 绑定事件
result.addEventListener("mouseover", function(){
	// 1、创建对象
    const xhr = new XHLHttpRequest();
    // 2、初始化 设置类型与URL
    xhr.open('POST', 'http://127.0.0.1:8000/server');
    // 3、发送请求
    xhr.send();
    // 4、事件绑定
    xhr.onreadystatechange = function(){
        // 进行状态判断
        if(xhr.readyState === 4){
            if(xhr.status >= 200 && xhr.status < 300){
                // 处理服务器返回的数据
                result.innerHTML = xhr.response;
            }
        }
    }
})
```



```js
// 引用express
const express = require('express');

// 创建应用对象
const app = express();

// 创建路由规则
app.get('/server', (request, response)=>{
    // 设置响应头 设置允许跨域
    response.setHeader('Access-Control-Allow-Origin','*');
    // 设置响应体
    response.send('HELLO AJAX');
});
app.post('/server', (request, response)=>{
    // 设置响应头 设置允许跨域
    response.setHeader('Access-Control-Allow-Origin','*');
    // 设置响应体
    response.send('HELLO AJAX POST');
});
```



# AJAX设置POST请求的参数

```js
// 获取元素对象
const result = document.getElementById("result");
// 绑定事件
result.addEventListener("mouseover", function(){
	// 1、创建对象
    const xhr = new XHLHttpRequest();
    // 2、初始化 设置类型与URL
    xhr.open('POST', 'http://127.0.0.1:8000/server');
    // 3、发送请求
    xhr.send('a=100&b=200&c=300');
    // 4、事件绑定
    xhr.onreadystatechange = function(){
        // 进行状态判断
        if(xhr.readyState === 4){
            if(xhr.status >= 200 && xhr.status < 300){
                // 处理服务器返回的数据
                result.innerHTML = xhr.response;
            }
        }
    }
});
```



# AJAX设置请求头信息

```js
// 获取元素对象
const result = document.getElementById("result");
// 绑定事件
result.addEventListener("mouseover", function(){
	// 1、创建对象
    const xhr = new XHLHttpRequest();
    
    // 2、初始化 设置类型与URL
    xhr.open('POST', 'http://127.0.0.1:8000/server');
    // 设置请求头
    // 设置请求体类型
    xhr.setRequestHeader('Content-Type','application/x-www-form-urlencoded');
    
    // 3、发送请求
    xhr.send('a=100&b=200&c=300');
    
    // 4、事件绑定
    xhr.onreadystatechange = function(){
        // 进行状态判断
        if(xhr.readyState === 4){
            if(xhr.status >= 200 && xhr.status < 300){
                // 处理服务器返回的数据
                result.innerHTML = xhr.response;
            }
        }
    }
});
```



```js
// all可以接受任何请求
app.all('/server', (request, response)=>{
    // 设置响应头 设置允许跨域
    response.setHeader('Access-Control-Allow-Origin','*');
    // 设置响应头
    response.setHeader('Access-Control-Allow-Header','*');
    // 设置响应体
    response.send('HELLO AJAX POST');
});
```



# AJAX服务端响应JSON数据

```js
// 获取对象
const result = document.getElementById('result');


// 绑定键盘按下事件
window.onkeydown = function(){
    // 发送请求
    const xhr = new XMLHttpRequest();
    
    // 设置响应体数据的类型 JSON格式自动转换
    xhr.responseType = 'json';
    
    // 初始化
    xhr.open('GET', 'http://127.0.0.1:8000/json-server');
    
    // 发送
    xhr.send();
    
    // 事件绑定
    xhr.onreadystatechange = function(){
        if(xhr.readyState === 4){
            if(xhr.status >= 200 && xhr.status < 300){
                // 处理数据 手动转化
                // let data = JSON.parse(xhr.response);
                // result.innerHTML = data.name;
                
                // 处理数据 自动转化
                result.innerHTML = xhr.response.name;
            }
        }
    }
}
```



服务端

```js
// all可以接受任何请求
app.all('/json-server', (request, response)=>{
    // 设置响应头 设置允许跨域
    response.setHeader('Access-Control-Allow-Origin','*');
    
    // 设置响应头
    response.setHeader('Access-Control-Allow-Header','*');
    
    // 响应一个数据
    const data = {
        name:'atguigu'
    };
    
    // 对对象进行字符串转换
    let str = JSON.stringify(data);
    
    // 设置响应体
    response.send(str);
});
```





# AJAX缓存问题

```js
xhr.open('GET', 'http://127.0.0.1:8000/json-server'+Date.now());
```





# AJAX请求超时设置与网络异常处理

在 XHR 请求中设置 `onerror`事件处理器是一个非常实用的做法，它主要用于捕获和处理那些**未能成功到达服务器或从服务器接收响应的网络层错误**。

```js
// 获取对象
const result = document.getElementById('result');


// 绑定键盘按下事件
window.onkeydown = function(){
    // 发送请求
    const xhr = new XMLHttpRequest();
    
    // 超时设置 2s之内没有结果这个请求就取消
    xhr.timeout = 2000;
    
    // 超时的回调
    xhr.ontimeout = function(){
        alert("网络异常，请稍后重试!");
    }
    
    // 网络异常
    xhr.onerror = function(){
        alert("你的网络似乎出现了问题");
    }
    
    // 初始化
    xhr.open('GET', 'http://127.0.0.1:8000/delay');
    
    // 发送
    xhr.send();
    
    // 事件绑定
    xhr.onreadystatechange = function(){
        if(xhr.readyState === 4){
            if(xhr.status >= 200 && xhr.status < 300){
                // 处理数据
                result.innerHTML = xhr.response.name;
            }
        }
    }
}
```



```js
// all可以接受任何请求
app.all('/delay', (request, response)=>{
    // 设置响应头 设置允许跨域
    response.setHeader('Access-Control-Allow-Origin','*');

    // 设置超时 3s之后发送数据
    setTimeout(()=>{
        // 设置响应体
        response.send('延时响应');
    }, 3000)
});
```





# AJAX取消请求

```js
<button> 点击发送 </button>
<button> 点击取消 </button>

// 获取元素对象
const btns = document.querySelectorAll('button');

let x = null;

btns[0].onclick = function(){
    const x = new XMLHttpRequest();
    x.open('GET', 'http://127.0.0.1:8000/delay');
    x.send();
}

btns[1].onclick = function(){
    x.abort();
}
```



```js
// all可以接受任何请求
app.all('/delay', (request, response)=>{
    // 设置响应头 设置允许跨域
    response.setHeader('Access-Control-Allow-Origin','*');

    // 设置超时 3s之后发送数据
    setTimeout(()=>{
        // 设置响应体
        response.send('延时响应');
    }, 3000);
});
```



# AJAX请求重复发送

- 标识变量
- 

```js
<button> 点击发送 </button>

// 获取元素对象
const btns = document.querySelectorAll('button');
let x = null;
// 标识变量 是否正在发送AJAX请求
let isSending = false;

btns[0].onclick = function(){
    // 如果正在发送 则取消该发送的请求 创建一个新的请求
    if(isSending) x.abort();
    const x = new XMLHttpRequest();
    // 修改标识变量的值
    isSending = true;
    x.open('GET', 'http://127.0.0.1:8000/delay');
    x.send();
    xhr.onreadystatechange = function(){
        if(xhr.readyState === 4){
            // 修改标识变量
            isSending = false;
            if(xhr.status >= 200 && xhr.status < 300){
                // 处理数据
                result.innerHTML = xhr.response.name;
            }
        }
    }

}
```





# jQuery发送AJAX请求

```js
$('button').eq(0).click(function(){
    $.get('http://127.0.0.1:8000/jquery-server', {a:100, b:200}, function(data){
        console.log(data);
    });
})

$('button').eq(1).click(function(){
    $.post('http://127.0.0.1:8000/jquery-server', {a:100, b:200}, function(data){
        console.log(data);
    }, 'json');
})
```



```js
app.all('/jquery-server', (request, response)=>{
    // 设置响应头 设置允许跨域
    response.setHeader('Access-Control-Allow-Origin','*');
    // 设置响应体
    // response.send('Hello jQuery AJAX');
    const data = {name: '尚硅谷'};
    // 转换为JSON格式的字符串 {"name":"尚硅谷"}
    response.send(JSON.stringify(data));
});
```



# JSON

```js
const jsonObject = {name: "Alice", age: 25};

// 使用JSON.stringify() 将其序列化为JSON字符串
const jsonString = JSON.stringify(jsonObject);
console.log(jsonString); // {"name":"Alice","age":25}
```





# jQuery通用方法发送AJAX

```js
$('button').eq(2).click(function(){
    $.ajax({
        // url
        url: 'http://127.0.0.1:8000/jquery-server',
        // 参数
        data: {a:100, b:200},
        // 请求类型
        type：'GET',
        // 响应体结果类型
        dataType: 'json',
        // 成功的回调
        success: function(data){
        	console.log(data);
    	}
    	// 超时的时间
    	timeout: 2000,
    	// 失败的回调
    	error: function(){
            console.log('出错了');
        }
    });
})
```



# Axios发送AJAX请求

```js
const btns = document.querSelectorAll('button');

// 配置baseURL
axios.defaults.baseURL = 'http://127.0.0.1:8000';

btns[0].onclick = function(){
    // GET请求
    axios.get('/axios-server', {
        // url参数c
        params: {
            id:100,
            vip:7
        }
        // 请求头信息
        headers: {
        	name:'atguigu',
        	age:20
    	}
    }).then(value => {
        console.log(value);
    })
}

btns[0].onclick = function(){
    // GET请求
    axios.post('/axios-server',        
        // 请求体
        data: {
               username:'admin',
               password: 'admin'
               },
    	{
        // url参数
        params: {
            id:100,
            vip:7
        }
        // 请求头参数
        headers: {
        	name:'atguigu',
        	age:20
    	}
    }).then(value => {
        console.log(value);
    })
}
```



# Axios函数发送AJAX请求

```js
btn[2].onclick = function(){
    axios({
        // 请求方法
        method: 'post',
        // URL
        url: 'axios-server',
        // url参数
        params: {
            vip:10,
            level:30
        },
        // 头信息
        headers: {
            a:100,
            b:200
        },
        // 请求体参数
        data: {
            username: 'admin',
            password: 'admin'
        }
    }).then(response => {
        console.log(response);
    })
}
```





# 使用fetch函数发送AJAX请求

```js
btn[2].onclick = function(){
    fetch('http://127.0.0.1:8000/fetch-server?vip=10', {
        // 请求方法
        method: 'post',
        // URL
        url: 'axios-server',
        // 头信息
        headers: {
            name:'atguigu'
        },
        // 请求体参数
        body: 'username=admin&password=admin'
    }).then(response => {
        console.log(response);
    })
}
```



# AJAX同源策略

同源策略：协议、域名、端口号必须相同，违背同源策略就是跨域







# AJAX-jsonp实现原理

JSONP





































