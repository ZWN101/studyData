`npm install -d`就是`npm install --save-dev`

`npm install -s`就是`npm install --save`

### npm install --save-dev

安装**开发时**依赖

会将安装的插件写入到`devDependencies`中

devDependencies里的插件只用于开发环境，不用于生产环境

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210516165031454.png" alt="image-20210516165031454" style="zoom:67%;" />

### npm install --save

安装**运行时**依赖

会将安装的插件写入到`dependencies`中

dependencies是需要发布到生产环境的

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210516165054214.png" alt="image-20210516165054214" style="zoom:67%;" />



如一个项目要依赖于jQuery，没有这个包依赖运行就会报错，这个时候把依赖写入`dependencies`中；但又如一些构建工具glup、webpack这些只是在开发中使用的包，上线后就不需要了，这个时候写入到`devDependencies`中



### npm install 

使用`npm install`会将插件安装到`dependencies`中