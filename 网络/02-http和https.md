* http协议

  是客户端和服务器请求和应答的标准

  http是超文本传输协议，这个协议它是用一种明文的方式发送我们的内容，没有任何的加密。比如：访问一个网站，我们需要在网站输入密码，登录账号之类的操作，那我们的账号和密码就会发送到网站的服务器上面，但要是有人中途截取了我们的信息，那我们的一些重要的信息可能就暴露了。

* https协议

  **所以为了解决http在传输过程中不加密的问题，之后又增加了一个SSL协议，这个协议简单说就是一个提供数据安全和完整性的协议，也就是负责网络连接的加密**,比如我们访问了一个https的网站，那我们的电脑会先和服务器建立一个安全的连接通道，然后服务器会先发送一份网站的证书信息到我们电脑，就相当于告诉我们电脑，你访问的服务器没有问题，确认了信息之后，我们的服务器就会生成 一个加锁的箱子，这把锁有两把不同的钥匙，一把是给我们电脑的，一把是给服务器自己的，服务器把没有上锁的箱子和钥匙发给我们电脑，我们把信息放在箱子里面后，用钥匙锁上，然后发给服务器，服务器再用自己的钥匙打开箱子，来保证信息的安全。在这个过程中，即使箱子被别人拦截了，因为没有服务器的钥匙，以目前的技术来讲，还是很难打开箱子的。所以现在的一些大网站，如购物网站等基本都是https的。
  
* 两者的区别

  http传输的数据都是未加密的，就是明文的，而https协议是由http和ssl协议构建的可进行加密传输和身份认证的网络协议，比http的安全性更可靠

