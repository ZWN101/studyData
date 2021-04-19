###  1.什么是AJAX

AJAX=Asynchronous JavaScript and XML(异步的javascript和xml)

xml标记：自定义标记

### 2.AJAX的作用

在不重新加载页面的情况下，与服务器交换数据并更新部分网页的艺术

### 3.使用AJAX实现XMLHttpRequest对象

#### （1）创建XMLHttpRequset对象

   var xhr = new XMLHttpRequest();

#### （2）请求页面

* xhr.open(method,url,async)

  method  传输方式 get和post

  url  服务器的动态页面

  async  异步：true    同步：false

* xhr.send([String])   向服务器发送数据

  **注意：**post方式传输时用来传输数据

#### （3）判断什么时候可以响应数据

用xhr.onreadystatechange事件实现判断

xhr.readyState存有XMLHttPRequest的状态，

从0到4发生变化 

 0 请求未初始化   

1 服务器连接已建立   

2 请求已接收   

3 请求处理中   

4 请求已完成，且响应已就绪

xhr.status 状态码   200 成功   404 未找到页面   403 禁止访问页面   500 服务器页面问题

**get方式**

```js
var xhr=new XMLHttpRequest();
xhr.open("GET","login.php?username="+userName.value+"&&password="+passWord.value,true);
xhr.send();
xhr.onreadystatechange=function(){
		if(xhr.readyState==4&&xhr.status==200){
			box.innerHTML=xhr.responseText;
		}
   } 
}
```

**post方式**

```js
var xhr=new XMLHttpRequest();
xhr.open("post","login.php",true);
xhr.setRequestHeader("Content-type","x-www-...");
xhr.send("username="+username.value+"&&pwd="+password.value);
xhr.onreadystatechange=function(){
            if(xhr.readyState==4&&xhr.status==200){
                 box.innerHTML=xhr.responseText;
}
}
```





#### （4）相应页面

xhr.responseText

xhr.responseHTML

#### （5）传值

**get**

XXX.html?username=tom&&password=123

**post**

xhr.setRequestHeader("Content-type","application/x-www-form-urlencoded");  xhr.send("username="+username+"password="+password);

#### （6）B/S模型 Browser浏览器/Server服务器

 Server服务器 装有特定软件的计算机

web软件服务器  

MySQL软件服务器  

ftp软件服务器  



























