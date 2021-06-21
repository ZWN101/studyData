### 使用npm初始化项目

例子：E/data/web项目/shopping

一个项目，不可能只是使用一个第三方包，而包越多，管理起来就越麻烦，而 npm init 给我们提供了项目初始化的功能，也解决了多个包的管理问题：

**新建一个项目，进入这个项目中，输入命令 npm init**

```
"name": "usenpm", // 项目名
"version": "1.0.0", // 版本号
"description": "这是我们第一次使用npm", // 描述信息
"main": "index.js", // 入口文件
"scripts": { // npm 设置的一些指令
  "test": "echo \"Error: no test specified\" && exit 1"
},
"keywords": [ // 关键字
  "第一次"
],
"author": "itheima6期", // 作者
"license": "ISC" // 当前项目的协议
```

### 解决 npm 被墙问题

npm 存储包文件的服务器在国外，有时候会被墙，速度很慢，所以我们需要解决这个问题。http://npm.taobao.org/ 淘宝的开发团队把 npm 在国内做了一个备份。

1. 安装淘宝的 cnpm：**命令：npm install --global cnpm**

在任意目录执行都可以， --global 表示安装到全局，而非当前目录， --global 不能省略，否则不管用

接下来你安装包的时候把之前的 `npm` 替换成 `cnpm`。

* 例子：

\# 这里还是走国外的 npm 服务器，速度比较慢

npm install jquery

\# 使用 cnpm 就会通过淘宝的服务器来下载 jquery

cnpm install jquery

2. 如果不想安装 `cnpm` ，就得使用淘宝的服务器来下载：

命令：npm install jquery --registry=https://registry.npm.taobao.org 

但是每一次手动这样加参数很麻烦，所我们可以把这个选项加入配置文件中：

进入项目——>输入指令 npm config list， 查看 npm 配置信息  org——全球   cn——中国

![img](file:///C:\Users\ZHUWAN~1\AppData\Local\Temp\ksohtml14712\wps1.jpg) 

​    配置到淘宝服务器

命令：npm config set registry https://registry.npm.taobao.org

![img](file:///C:\Users\ZHUWAN~1\AppData\Local\Temp\ksohtml14712\wps2.jpg)

 

只要经过了上面命令的配置，则以后所有的 `npm install` 都会默认通过淘宝的服务器来下载。

### node模块化开发

1. 核心模块 node自带 如 fs url mysql等

2. 第三方模块，引入第三方模块之前需要npm install  

   npm install art-template moment jquery bootstrap axios element-ui mysql express formidable

3. 自定义模块 

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20201123203858068.png" alt="image-20201123203858068" style="zoom:67%;" />

^代表 可升级的

### 小组共同开发项目

例：小组人员共同开发项目，只需要把package.json等自己写的页面给别人，在终端输入 npm install，就会把所有会用到的东西安装下来

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20201123204221831.png" alt="image-20201123204221831" style="zoom:67%;" />

### package.json 与 package-lock.json 文件

如果后期开发过程中，需要项目迁移，我们只需要将package.json文件迁移即可，在新项目下执行

`npm install ` ，所有第三方包会自动安装；

package.json的作用就是用来记录当前项目及包的使用情况；`不能在package.json中添加注释`

package-lock.json 保存第三方包的版本和下载路径等详细信息；

当我们使用npm管理包时，package.json 及package-lock.json 的内容都会自动更新

### NODE链接MySQL

1. MySQL是8以上版本，请在mysql的bin目录下输入cmd

2. mysql -u root -p

登陆mysql 并输入密码

![img](file:///C:\Users\ZHUWAN~1\AppData\Local\Temp\ksohtml14712\wps3.jpg) 

3. 继续输入alter USER 'root'@'localhost' IDENTIFIED BY 'root' 其中 root为mysql密码

4. 继续输入 alter USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root';

如下如，mysql修改成功

![img](file:///C:\Users\ZHUWAN~1\AppData\Local\Temp\ksohtml14712\wps4.jpg) 

5. 在node中安装npm install mysql 后

```js
var mysql= require('mysql');
//1.数据库连接配置项
var connection = mysql.createConnection({
 host:'localhost',
 user:'root',
 password:'11653505453',
 database:'tjise'
});
//2.数据库连接
connection.connect();
//3.数据库操作命令及其执行项
connection.query('select * from teacher where id=1', function (error, results, fields) {
 console.log(error);
 console.log(".................................");
 console.log(results);//查询到的数据
 console.log(".................................");
 console.log(fields);
});
//4.数据库连接关闭
connection.end();
```

### 运行js文件

在终端将该项目打开，输入：node http.js

