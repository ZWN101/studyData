templae（解析成）——>ads（抽象语法树）——>（编译）render（函数）——>虚拟DOM——>真实DOM

组件中的template，利用这个第三方，把他转换成render函数

![image-20210110212157034](C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20210110212157034.png)



 https://www.jianshu.com/p/410b6099be69

### beforeCreate（创建前）

初始化事件还未开始

### created（创建后）

组件创建完成后调用，data已经初始化，计算属性、event、watch事件回调

### beforeMount（载入前）

在挂载前被调用，render函数首次被调用生成虚拟DOM

### mounted（载入后）

挂载完成，DOM树已经渲染到页面，可进行DOM操作

### beforeUpdate（更新前）

当数据发生改变的时候调用，完了之后重新渲染虚拟DOM，然后把虚拟DOM和我们现在的真实DOM进行对比，把真实DOM修改下

### updated（更新后）

beforeUpdate完成时候的操作完成，调用

### beforeDestroy（销毁前）

实例销毁前调用，此时还可以访问实例的数据

### destroyed（销毁后）

组件销毁后调用