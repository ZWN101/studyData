### 什么是Vuex

* 官方解释：Vuex是一个专门为Vue.js 应用程序开发的状态管理模式	
  * 它采用 集中式存储管理 应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。
  * Vuex 也集成到 Vue 的官方调试工具 devtools extension，提供了诸如零配置的 time-travel 调试、状态快照导入导出等高级调试功能。
* 他是把所有组件共享的状态（数据）全部存储在一个对象里面，然后把对象放在Vue实例中，供各个组件使用。Vuex带给我们的最大的便捷就是——响应式，当我们一个组件改变对象里数据的时候，其他组件里的数据也会同时发生改变
* Vuex就是为了提供这样一个在多个组件间共享状态的插件

### 管理什么状态

如：用户的登录状态、用户名、头像、昵称等等

### 单界面的状态管理

在单个组件中进行状态管理

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210114200650278.png" alt="image-20210114200650278" style="zoom:67%;" />

* State  

  组件中的状态，可以当做是data属性中的数据

* View

  视图，展示给我们的界面，当state发生变化时，界面会跟着发生变化

* Actions

  对state做的操作，当界面发生操作时，需要对state进行更新

### 多界面状态管理

* 当多个组件同时依赖一个状态时，这个状态发生变化，多个组件中的状态都会发生更新

* 官方图片

  <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210120133559464.png" alt="image-20210120133559464" style="zoom:67%;" />

  State：状态，存储的数据

  Mutations：进行同步操作，我们修改State里的状态，必须通过Mutations来进行修改

  Actions：进行异步操作，发送网络请求，异步操作完成之后，要通过Mutations来进行状态的修改

  devtools：Vue开发的一个浏览器插件，记录每一次改变的state的状态，只要是修改State的状态，必须通过Mutations来对State里的状态进行修改，只有通过Mutations进行修改，devtools才会记录。方便调试

### State单一状态树

组件共享的数据都放在一个store里来进行管理

### Vuex的核心

* **state **

  保存状态

  组件调用：$store.state.——

  Vuex定义：

  <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210125155657735.png" alt="image-20210125155657735" style="zoom:67%;" />

* **getters **

  类似于计算属性，要求提取state里经过变化的数据

  组件调用：$store.getters.fullName2

  Vuex定义：

  <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210125155603184.png" alt="image-20210125155603184" style="zoom:67%;" />

* **mutations**

  组件调用：<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210125155809474.png" alt="image-20210125155809474" style="zoom:67%;" />

  Vuex定义：<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210125155835990.png" alt="image-20210125155835990" style="zoom:67%;" />

* **actions**

  组件调用：<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210125160001522.png" alt="image-20210125160001522" style="zoom:67%;" />

  Vuex定义：<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210125160112508.png" alt="image-20210125160112508" style="zoom:67%;" />

* **modules**

  Vuex使用单一状态树，意味着很多的状态都会交给Vuex管理，如果状态过多的话store对象会显得很臃肿，所以提出将store分割成多个模块（modules），每个模块拥有自己的state、mutations、actions、getters

引用：<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210125160150061.png" alt="image-20210125160150061" style="zoom:67%;" />

