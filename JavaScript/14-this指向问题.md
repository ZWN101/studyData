### 重点

**this指向在函数定义的时候是确定不了的，只有函数在执行的时候才能确定this到底指向谁，实际上this的最终指向是调用他的那个对象**

### 函数版的this

window是javaScript中的全局对象，我们创建的变量实际上是给window添加属性

```js
function a(){
    var user = "追梦子";
    console.log(this.user); //undefined
    console.log(this); //Window
}
a();//相当于window.a()调用  this指向window
```

```js
var o = {
    user:"追梦子",
    fn:function(){
        console.log(this.user);  //追梦子
    }
}
o.fn();//this指向对象o
```

```js
var o = {
    user:"追梦子",
    fn:function(){
        console.log(this.user); //追梦子
    }
}
window.o.fn();//this指向o
```

```js
var o = {
    a:10,
    b:{
        a:12,
        fn:function(){
            console.log(this.a); //12
        }
    }
}
o.b.fn();//this指向b
```

```js
var o = {
    a:10,
    b:{
        // a:12,
        fn:function(){
            console.log(this.a); //undefined
        }
    }
}
o.b.fn();//this指向b
```

1. 如果一个函数中有this，但是它没有被上一级的对象所调用，那么this指向的就是window，这里需要说明的是在js的严格版中this指向的不是window

2. 如果一个函数中有this，这个函数有被上一级的对象所调用，那么this指向的就是上一级的对象。

3. 如果一个函数中有this，**这个函数中包含多个对象，尽管这个函数是被最外层的对象所调用，this指向的也只是它上一级的对象**

```js
var o = {
    a:10,
    b:{
        a:12,
        fn:function(){
            console.log(this.a); //undefined
            console.log(this); //window
        }
    }
}
var j = o.b.fn;
j();//this指向window
```

**this指向的是最终调用他的对象**

### 构造函数版的this

```js
//Fn是一个函数对象
function Fn(){
    this.user="追梦者"
}
var a=new Fn();
//相当于复制了一份Fn对象，然后给了a变量，此时this是指向新创建出来的对象
var a={
    this.user="追梦者";
}
console.log(a.user);//追梦者
```

![image-20201114194450100](C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20201114194450100.png)	

### 当this遇到return

```js
function fn()  
{  
    this.user = '追梦子';  
    return {};  
}
var a = new fn();  
console.log(a.user); //undefined,a.user相当于给a添加了一个属性user，但该属性并未赋值，因此为undefined
```

```js
function fn()  
{  
    this.user = '追梦子';  
    return function(){};
}
var a = new fn();  
console.log(a.user); //undefined
```

```js
function fn()  
{  
    this.user = '追梦子';  
    return 1;
}
var a = new fn();  
console.log(a.user); //追梦子
console.log(a);//fn(){user:"追梦子"}
```

```js
function fn()  
{  
    this.user = '追梦子';  
    return undefined;
}
var a = new fn();  
console.log(a.user); //追梦子
```

**如果返回值是一个对象，那么this指向的就是那个返回的对象，如果返回值不是一个对象那么this还是指向函数的实例。**

```js
function fn()  
{  
    this.user = '追梦子';  
    return undefined;
}
var a = new fn();  
console.log(a); //fn {user: "追梦子"}
```

**如果返回值是一个对象，那么函数的实例就是返回的对象，如果返回值不是一个对象，那么函数的实例就是他本身**

```js
function fn()  
{  
    this.user = '追梦子';  
    return null;
}
var a = new fn();  
console.log(a.user); //追梦子
```

**还有一点就是虽然null也是对象，但是在这里this还是指向那个函数的实例，因为null比较特殊。**

