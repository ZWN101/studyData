### el

### data

### methods——方法

### computed——计算属性

当我们的某一个数据必须经过一系列变化之后供页面展示，可以用计算属性

### filters——过滤器

### watch——监听数据

* handler 监听数据的变化

  ```js
  watch:{
      name:{
          handler(newValue,oldValue){
              
          }
      }
  }
  ```

  

* immediate

  默认值为false，在进入页面第一次绑定值时，不会立即执行监听，只有数据发生改变才会执行handler中的操作

* deep

  默认值为false，vue不能检测到对象属性的添加或删除，deep就是用来进行深度监听的





