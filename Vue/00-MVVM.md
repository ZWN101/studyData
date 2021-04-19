### MVVM

* View层：
  视图层
  在我们前端开发中，通常就是DOM层。
  主要的作用是给用户展示各种信息。
  
* Model层：
  数据层
  数据可能是我们固定的死数据，更多的是来自我们服务器，从网络上请求下来的数据。
  在我们计数器的案例中，就是后面抽取出来的obj，当然，里面的数据可能没有这么简单。
  
* VueModel层：
  视图模型层
  视图模型层是View和Model沟通的桥梁。
  一方面它实现了Data Binding，也就是数据绑定，将Model的改变实时的反应到View中
  另一方面它实现了DOM Listener，也就是DOM监听，当DOM发生一些事件(点击、滚动、touch等)时，可以监听到，并在需要的情况下改变对应的Data。
  
  <img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210114211323870.png" alt="image-20210114211323870" style="zoom:67%;" />

View和Model之间没有联系，他们是通过ViewModel进行交互，当视图的数据发生变化时会同时修改数据源，而当数据源的数据发生变化时也会立即反应到视图中

### MVC



