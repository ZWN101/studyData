https://www.jianshu.com/p/e31a921c6888

https://blog.csdn.net/qq_33505829/article/details/103419143

### 加载网页时浏览器做了哪些工作

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210308195147830.png" alt="image-20210308195147830" style="zoom:80%;" />

1. 浏览器接收到服务器发送来的HTML文件，开始解析
2. 根据HTML文件构建DOM树（**DOM树的构建过程是一个深度遍历：当前节点的所有子节点都构建好才会构建当前节点的下一个兄弟节点**）和CSSDOM树。在构建DOM树期间，如果遇到JS，就会阻塞DOM树和CSSDOM树的构建，优先加载JS文件，加载完毕后，再继续构建DOM树及CSSDOM树
3. 根据DOM树和CSSDOM树构造Rendering Tree **Rendering Tree渲染树并不等同于DOM树，因为一些像Header或display:none的东西就没必要放在渲染树中了**
4. 有了Render Tree，浏览器已经知道网页中有哪些节点、各个节点的CSS定义以及他们的从属关系。下一步操作就是layout，就是计算出每个节点在屏幕中的位置
5. 绘制，遍历render树

**为了更好的用户体验，渲染引擎会尽可能早的将内容呈现到屏幕上，并不会等到所有的HTML都解析完了之后再去构建和布局render树。他是解析一部分内容就显示一部分内容，同时，可能还在通过网络下载其余内容**

### 页面的重绘和重排

页面渲染完了之后，若JS操作了DOM节点，根据JS对DOM操作动作的大小，浏览器对页面进行重绘或者重排

* 重绘

  屏幕的一部分要重绘。渲染树节点发生改变，但不影响该节点在页面中的空间位置及大小。如：某个div标签节点的背景颜色、字体颜色发生改变，但是该div标签节点的宽、高、内外边距不发生变化，此时触发的是浏览器重绘

* 重排（也称回流）

  当渲染树节点发生变化，影响了节点的几何属性（如宽、高、内边距、外边距、float、position、display:none等），导致节点的位置发生变化，此时触发浏览器的就是重排，需要重新生成渲染树，重新布局

### 为什么在加载js文件的时候要阻塞DOM树的构建

因为js会对DOM节点进行操作，浏览器无法预测未来的DOM节点的具体内容，为了防止无效操作，节省资源，只能阻塞DOM树的构建

### 为什么说js、css放置的位置影响前端性能呢

当js文件放在header中的时候，浏览器构建DOM树的过程遇到js文件加载就会阻塞，一旦js文件的数量和内容过大，就可能会出现页面一片空白、几秒钟之后才出现的情况。不利于用户的体验

关于js和css放置的位置：

1. js有可能会修改DOM。浏览器无法预测未来的DOM节点的具体内容，为了防止无效操作，所以js最好放在最后
2. js的执行有可能依赖css样式。浏览器必须保证在js代码执行前的所有的css都已经下载和解析完成

