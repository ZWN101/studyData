### 改变URL不实现页面刷新的几种方法

location.hash('foo')    **页面URL：如:localhost:8080/#/foo**

history.pushState({},'','home')   压栈   **页面URL：如:localhost:8080/home**

history.back()  出栈，回退

history.forward()  向前

history.go(-1) 出栈一次  history.go(-2) 出栈两次

history.go(1) 出栈一次  history.go(2) 进栈两次

history.replaceState({},'','me')   替换







<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210108163603338.png" alt="image-20210108163603338" style="zoom:67%;" />

### 路由的两种模式

hash模式 和 history模式

#### 两种模式的区别

hash模式：#/home  改变url不会刷新页面  改变url本质调用location.hash()

hastory模式：/home 改变url不会刷新页面  改变url本质调用history.pushState()/history.replaceState()

### 什么是路由

：）访问的网页的路径不出现后缀名（如：.html/.jsp）等的称为路由

页面URL与组件之间的一种映射关系，改变URL，URL对应的组件就会显示到页面

### 安装路由

npm install vue-router --save (--save运行时依赖，运行在客户端的时候，仍需要路由)

### 将路由默认的hash模式转换成history模式

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210108202304201.png" alt="image-20210108202304201" style="zoom:67%;" />



### router-link的属性

```vue
 <router-link to="/home" tag="button" replace active-class="active">首页</router-link>
```

router-link默认渲染到页面上是a标签

* tag

  改变`<router-link>`渲染到页面的元素，tag="button"，渲染到页面上为button按钮

* replace

  使用history.pushState()点击左上角的回退按钮会实现回退

  将`<router-link>`实现跳转路由的方式由history.pushState()——>history.replaceState()

* active-class

  当`<router-link>`对应的路由匹配成功时, 会自动给当前元素设置一个`router-link-active`的class，可以通过`<router-link>`的active-class修改默认名称，也可以通过router实例的属性` linkActiveClass:'active'`进行修改

  <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210108205936220.png" alt="image-20210108205936220" style="zoom:67%;" />

### 通过代码实现路由跳转

 this.$router.push('/home')   this.$router.replace('/home')

### 动态路由

路由传递数据的一种方式

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109141155764.png" alt="image-20210109141155764" style="zoom:67%;" /><img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109141226071.png" alt="image-20210109141226071" style="zoom:67%;" />



<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109141325418.png" alt="image-20210109141325418" style="zoom:67%;" />

this.$router 获取的是路由对象

this.$route 获取的是当前处于活跃状态的某一个路由    this.$route.params.userId  获取当前活跃路由的参数

### 路由懒加载

#### 打包文件的解析

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109150417687.png" alt="image-20210109150417687" style="zoom:67%;" />

app——应用程序开发的所有代码（ 该文件是项目中我们手写的js代码，所有的业务逻辑代码都打包在了该文件里）

manifest——为我们打包的代码做底层支撑，比如我们项目中使用CommonJS、ES6等，浏览器是不能识别的，而该文件为我们的项目做底层支撑，将浏览器不识别的代码转换成可识别的代码

vendor——供应商、第三方，项目里引用的第三方的东西，如：axios、vue等

#### 路由懒加载

我们知道，当我们的项目比较大，对项目进行打包的时候，我们所有的业务逻辑层的代码都会放在app...文件里面，当用户输入URL访问静态资源服务器时，服务器会把所有的HTML＋CSS＋JS文件返回，JS文件过大不宜于页面的加载，可能会出现短暂的空白情况。为了避免这种情况出现，我们可以将不同的路由对应的组件打包成不同的js文件，然后当路由被访问的时候，才从服务器请求把该路由对应的js文件请求下来，然后浏览器加载该组件。

* 路由懒加载的主要作用是将路由对应的组件打包成一个个的js代码块
* 只有在这个路由被访问到的时候, 才加载对应的组件

#### 懒加载的方式

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109151922758.png" alt="image-20210109151922758" style="zoom:67%;" />

#### 懒加载的效果

* 没用懒加载

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109152622154.png" alt="image-20210109152622154" style="zoom: 67%;" />

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109152651296.png" alt="image-20210109152651296" style="zoom:67%;" />

* 用懒加载

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109152821551.png" alt="image-20210109152821551" style="zoom:67%;" />

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109152832200.png" alt="image-20210109152832200" style="zoom:67%;" />

### 嵌套路由

一个组件中嵌套其他的组件，需要用到嵌套路由

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109162326675.png" alt="image-20210109162326675" style="zoom:67%;" /><img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109162347255.png" alt="image-20210109162347255" style="zoom:67%;" /><img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109162415524.png" alt="image-20210109162415524" style="zoom:67%;" />

### 路由传递参数

* params（传递一个参数）

  路由配置：<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109200042285.png" alt="image-20210109200042285" style="zoom:67%;" />

  router-link配置  <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109200156165.png" alt="image-20210109200156165" style="zoom:67%;" />

  获取参数  <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109200244304.png" alt="image-20210109200244304" style="zoom:67%;" />

* query（传递多个参数）

  router-link配置  <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109200317885.png" alt="image-20210109200317885" style="zoom:67%;" />

​       获取参数 <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109200337633.png" alt="image-20210109200337633" style="zoom:67%;" />

* 通过代码实现路由跳转并传递参数

  <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210109200702762.png" alt="image-20210109200702762" style="zoom:67%;" />

### $router和$route

**所有的组件（如：User.vue，Home.vue）都继承Vue类的原型（Vue.prototype）**

* $router  路由对象

* $route   当前处于活跃状态的路由

当我们导入vue-router时，须执行Vue.use(VueRouter)——>VueRouter.install（内部执行）

Object.defindePropety(obj,age,18)——>给obj这个对象添加属性age值为18

VueRouter源码执行Object.defindePropety()方法，给Vue.prototype添加$router和$route属性，所以我们可以在组件中获得$router和$route

### 导航守卫

* 什么是导航守卫

  监听路由之间的跳转（进入和离开）

* 为什么使用导航守卫？

  比如修改浏览器窗口的title
  路由的配置 

  <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210110164648011.png" alt="image-20210110164648011" style="zoom:67%;" />

  调用beforeEach()方法

  <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210110164700023.png" alt="image-20210110164700023" style="zoom:67%;" />

* 导航守卫的分类

  详情见Vue-Router官网 https://router.vuejs.org/zh/guide/advanced/navigation-guards.html

  - 全局导航守卫

  beforeEach 全局前置守卫，路由跳转前调用的函数

  afterEach 全局后置钩子，路由跳转完之后调用

  - 路由独享守卫

  - 组件内的守卫

### keep-alive

* keep-alive是Vue的一个内置组件，可以使被包含的组件保留原有的状态，或避免重新被渲染。router-view也是一个组件，如果被包含在keep-alive里面，所有匹配到路径的视图组件都会被缓存

  ```html
  <keep-alive>
      <router-view></router-view>
  </keep-alive>
  ```

  

* 当使用了keep-alive后，被路由匹配到的组件就会拥有activated（当前组件活跃）和deactivated（当前组件消失）两个函数<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210111114743719.png" alt="image-20210111114743719" style="zoom:67%;" />



* keep-alive的属性

  include - 字符串或正则表达，只有匹配的组件会被缓存

  exclude - 字符串或正则表达式，任何匹配的组件都不会被缓存

* 如：

  User，About为组件的name

  <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210111115723823.png" alt="image-20210111115723823" style="zoom:67%;" />

  <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210111115806164.png" alt="image-20210111115806164" style="zoom:67%;" />
  
  

未使用keepalive时——当前在Home组件中，点击其他组件会执行destroyed钩子函数，销毁该组件，当再次点击Home时，重新创建该组件（执行Vue的钩子函数）

使用keepalive时——点击其他组件不会执行destroyed钩子函数，不会销毁Home组件

### 路由跳转打开新的标签页

1. `<router-link>`

   ```html
   <router-link target="_blank" :to="{path:'/home',query:{id:'1'}}">新页面打开home页</router-link> query
   <router-link target="_blank" :to="{path:'/home/'+id">新页面打开home页</router-link> params
   ```

2. 编制式导航

   ```js
   seeShare(){
      let routeUrl = this.$router.resolve({
        path: "/share",
        query: {id:96}
      });
      window.open(routeUrl.href, '_blank');
   }
   ```

   