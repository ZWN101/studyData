**server 服务器**    **service 服务**

### json-server的基本使用

#### 1.为什么要使用json-server

 作为一个前端开发工程师，在后端还没有ready的时候，不可避免的要使用mock（虚假的、模拟的）的数据。很多时候，我们并不想使用简单的静态数据，而是希望自己起一个本地的mock-server来完全模拟请求以及请求回来的过程。json-server是一个很好的可以替 
 我们完成这一工作的工具。

json-server是一个简易的后台服务器，使用它模拟API接口服务器，模拟后端接口

#### 2.安装json-server

   **首先要安装nodeJS**

* 打开终端，输入指令 npm install -g json-server

  ![img](file:///C:\Users\ZHUWAN~1\AppData\Local\Temp\ksohtml10976\wps1.jpg)

* 创建一个文件夹存放json文件，在终端切换到创建文件夹的目录（该文件夹可以认为是项目），json文件自命名

  ![image-20201104110236103](C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20201104110236103.png)

* 初始化package.json文件，输入指令 **npm init --yes** ，就会在当前文件下下载对应的模块和插件，创建完成后就会生成一个package.json文件

* 安装我们需要用到的模块json-server，输入指令 npm install json-server -save   -save就是将模块存储到package.json文件中，之后就会下载模块

* 设置快捷键启动json-server 

  <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20201104111604992.png" alt="image-20201104111604992" style="zoom: 80%;" />

* 输入指令 npm run json:server运行json-server