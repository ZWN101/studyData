### 什么是webpack

- 前端模块化打包工具
- webpack其中一个核心——让我们可以进行模块化开发，并且会帮助我们处理模块间的依赖关系。不仅仅是JavaScript文件，CSS、图片、json文件等等在webpack中都可以被当做模块来使用。
- 打包的理解——将webpack中的各种资源模块进行打包合并成一个或者多个包（bundle），并且在打包的过程中，还可以对资源进行处理，比如压缩图片，将scss、less转成css，将ES6语法转成ES5语法，将TypeScript转成JavaScript等等操作，转换成浏览器识别的代码。

### webpack的五个核心

#### Entry

入口指示，webpack以哪个文件为入口起点开始打包，分析构建内部依赖图

#### Output 

输出指示，webpack打包后的资源bundles输出到哪里去，以及如何命名

#### Loader（翻译操作）

Loader让webpack能够去处理那些非JavaScript文件（webpack自身只理解JavaScript、和JSON），将css、less等翻译成webpack识别的资源，这样webpack就能打包这些资源了

#### Plugins

插件用于执行范围更广的任务，插件的范围包括，从打包优化和压缩（比如：样式文件的压缩），一直到重新定义环境中的变量等

#### Mode （模式）

模式指示，webpack使用相应模式的配置

* development

  能让代码本地调试运行的环境

* production

  能让代码优化上线运行的环境

### webpack安装

全局安装：npm install webpack webpack-cli -g(webpack_cli 使我们能够通过指令去使用webpack内部的功能)

局部安装：npm install webpack -D(--save-dev) 开发时依赖

课程中版本webpack@4.41.6    webpack-cli@3.3.1





