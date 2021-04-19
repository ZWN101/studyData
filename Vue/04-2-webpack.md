### 前端模块化

在ES6之前，我们要想进行模块化开发，就必须借助于其他的工具，让我们可以进行模块化开发。并且在通过模块化开发完成了项目后，还需要处理模块间的各种依赖，并且将其进行整合打包。

### 什么是webpack

- 前端模块化打包工具
- webpack其中一个核心——让我们可以进行模块化开发，并且会帮助我们处理模块间的依赖关系。不仅仅是JavaScript文件，CSS、图片、json文件等等在webpack中都可以被当做模块来使用。
- 打包的理解——将webpack中的各种资源模块进行打包合并成一个或者多个包（bundle），并且在打包的过程中，还可以对资源进行处理，比如压缩图片，将scss、less转成css，将ES6语法转成ES5语法，将TypeScript转成JavaScript等等操作，转换成浏览器识别的代码。

### webpack的安装

* 首先需要下载node.js，webpack依赖node环境

* 安装webpack，npm install webpack@3.6.0 -g，（全局安装，先指定版本号3.6.0，因为vue cli2依赖该版本)

  * 全局安装  在很多地方都可以使用webpack(在任何终端)

  * 局部安装   全局安装后需要对项目进行局部安装

    cd 对应目录   ——>   npm install webpack@3.6.0 --save-dev

    **`--save-dev`是开发时依赖，项目打包后不需要继续使用的。如：将px单位转化为vw的，在项目打包的时候会自动将所有的单位转化为vw，最终打包出来的项目的单位px都是vw**

    **`--save`是运行时依赖，运行在客户端的时候还需要依赖**
    
    package.json文件中，定义的scripts(脚本)，脚本里面使用webpack命令，则用的就是局部安装的webpack

### 起步

* 新建以下文件夹

  <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210107180207839.png" alt="image-20210107180207839" style="zoom:80%;" />

  dist——>打包后的代码存放位置

  src——>源码

  main.js——>程序的入口文件

  使用模块化方式开发，main.js利用CommonJS的模块化规范引用了mathUtils.js文件

* 对js文件进行打包

  1. 不建议在index.html中直接引用两个js文件，因为浏览器不识别CommonJS的模块化规范，并且在真实项目中一个个引用js文件不方便管理

  2. 使用webpack模块化打包工具，对多个js文件进行打包，将其放到一个js文件中，他会自动处理js文件之间的一个依赖关系

     输入命令行 webpack ./src/main.js ./dist/bundle.js

     









webpack为了能够正常运行，必须依赖node环境。node环境为了可以正常执行很多代码，其中必须包含各种依赖包，npm工具

（node packages manager，软件包管理工具）用来管理各种依赖包

npm run build  打包项目（dist）

pro构建项目

dev 开发项目

开发时依赖

运行时依赖

关掉Eslint(config--->index.js--->useEslint:false)