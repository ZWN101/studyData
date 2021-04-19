### 什么时候使用箭头函数

当我们准备把一个函数作为参数传到另一个函数里的时候

### 箭头函数中的this是如何查找的

向外层作用域中一层一层的查找this，直到有了this的定义

```js
const obj={
    fun(){
        setTimeout(function(){
            console.log(this);//window
        })
        setTimeout(()=>{
            console.log(this);//obj
        })
    }
}

obj.fun()
```

* 箭头函数不会改变this的指向
* 回调函数是由call函数调用的，`func.call(window)`，所以第一个定时器中this指向window，第二个定时器中没有this的定义，则会往上一层作用域中寻找this，此时this指向obj