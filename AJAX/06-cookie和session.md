## cookie

### 什么是cookie

cookie是最原始也最简单的客户端存储方式。web应用程序是使用http协议传输数据的，http协议是无状态的协议，一旦数据交换完毕，客户端与服务器端的连接就会关闭，再次交换需要建立新的连接，这就意味着服务器无法从连接上跟踪会话。

**cookie主要用来身份认证，而不用来存储其他信息，防止http报文过大** 

参考：https://www.cnblogs.com/linguoguo/p/5106618.html

![image-20210214171405650](C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210214171405650.png)

### cookie是如何工作的

当网页要发http请求时，浏览器会检查是否有相应的cookie，有则自动添加在request header中的cookie字段中，这些是浏览器自动帮我们做的，而且每次http请求，浏览器都会自动帮我们做。

在localStroage出现之前，cookie被滥用当做了存储工具，什么数据都放在cookie中，即使这些数据不需要随请求传送到服务端。cookie标准做了限制：每个域名下cookie的大小最大是4KB，每个域名下cookie数量最多为20个

### cookie的优点和缺点

* 优点
  1.  通过良好的编程，控制保存在cookie中的session对象的大小
  2. 通过加密和安全传输技术（SSL），减少cookie被破解的可能性
  3. 只要在cookie中不存在敏感数据，即使被盗也不会有重大损失
  4. 控制cookie的生命周期，使之不会永远有效，偷盗者可能拿到一个过期的cookie
* 缺点
  1. cookie的数量和长度的限制，每个domain下最多只能有20个cookie，每个cookie的长度不能超过4KB，否则会被截掉
  2. 安全性问题，如果cookie被人拦截了，那人就可以取得所有的session信息，即使加密也于事无补，因为拦截者并不需要知道cookie的意义，他只需要原样转发cookie就可以达到目的
  3. 有些状态不可能保存在客户端。例如，为了防止重复提交表单，我们需要在服务端保存一个计数器，如果我们把这个计数器保存在客户端，那么它起不到任何作用

### cookie的格式

* 创建cookie

  <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210215102952660.png" alt="image-20210215102952660" style="zoom: 80%;" />

* 获取cookie

  ![image-20210215103119497](C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210215103119497.png)

### cookie的属性

属性包括：expires、domain、path、secure、HttpOnly，在设置这些属性时，属性之间由一个分号和一个空格隔开

#### expires

expires用来设置cookie什么时间内有效。expires是cookie的失效日期，expires必须是GMT格式的时间，可通过`new Date().toGMTString()`或者`new Date().toUTCString()`来获得

默认值为：session，在浏览器关闭后就失效

![image-20210215111408552](C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210215111408552.png)

#### domain和path

domain：域名    path：路径     两者一起限制cookie能被哪些URL访问

![image-20210215111959246](C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210215111959246.png)

![image-20210215112022546](C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210215112022546.png)

#### secure

secure选项决定设置的cookie在确保安全的请求中才会发送，当请求时https或者其他安全协议时，包含secure选项的cookie才能被发送到服务器。默认情况下，secure选项为空。

**如果在网页中通过js设置secure类型的cookie，必须保证网页是https协议的，在http协议的网页中是无法设置secure类型的cookie的**

#### httpOnly

该选项用来设置cookie能否被js访问。默认情况下，HttpOnly选项为空，所以默认情况下，客户端可以通过js代码访问这个cookie，当cookie携带httpOnly选项时，客户端无法通过代码`document.cookie`去访问。

在客户端无法通过js代码去设置httpOnly类型的cookie，该类型的cookie只能通过服务端设置

![image-20210215114304838](C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210215114304838.png)

### 服务端设置cookie

请求资源文件（HTML/JS/CSS），还是发送ajax请求，服务端会返回response，response header中的set-cookie专门用来设置cookie，不能将cookie放在一个set-cookie中

![image-20210215120528726](C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210215120528726.png)

参考：https://blog.csdn.net/playboyanta123/article/details/79464684

## Session

#### 什么是session

session存储在服务端，主要与cookie配合使用完成身份认证和状态保持的功能

截取：https://www.cnblogs.com/linguoguo/p/5106618.html

![image-20210215134124203](C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210215134124203.png)

## cookie和session的配合

截取：https://segmentfault.com/a/1190000012256432

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210215122320339.png" alt="image-20210215122320339" style="zoom:80%;" />

