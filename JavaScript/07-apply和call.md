### 定义

* apply：调用一个对象的一个方法，用另一个对象替换当前对象。例如：B.方法.apply(A,arguements)；即：A对象调用B对象的方法

* call：调用一个对象的一个方法，用另一个对象替换当前对象。例如：B.方法.call(A,arguments,arguements)；即：A对象调用B对象的方法

  **可以让一个函数成为任意对象的方法进行调用**

### 相同点

* 方法的含义是一样的，方法的功能是一样的
* 第一个参数的作用是一样的

### 不同点

两者传入的参数列表形式不一样

* apply只能传入两个参数，所以第二个参数往往是作为数组形式传入
* call可以传入多个参数

### 存在意义

实现多重继承

### 栗子

```js
var name="小张";
age=17;
var obj={
    name:"小刘",
    objAge:this.age,
    myFun:function(){
        console.log(this.name+"年龄"+this.age);
    }
}
console.log(obj.objAge);
obj.myFun();

//输出 17 小刘的年龄undefined
//1.输出obj对象的objAge属性的值，objAge在属性声明并赋值的时候就已将this.age的值赋值给objAge，所以输出17
//2.调用obj的myFun方法，此时方法中的this指向obj，obj的name为小刘，obj.age相当于给obj添加一个属性为age，但未赋值，所以输出为undefined
```

```js
var fav="唐僧";
function shows(){
    console.log(this.fav);
}
//输出 唐僧
//调用shows方法，此时this指向的是window，所以输出为唐僧
```

```js
var name="小张";
age=17;
var obj={
    name:"小刘",
    objAge:this.age,
    myFun:function(){
        console.log(this.name+"年龄"+this.age);
    }
}
var db={
    name:"德玛",
    age:99
}
obj.myFun();  //小刘年龄undefined  此时this指向obj
obj.myFun.apply(db);//德玛年龄99 --->此时this指向db
obj.myFun.call();//小张年龄17 --->此时this指向window
obj.myFun.call(db);//德玛年龄99 --->此时this指向db
```

```js
var name="小张";
age=17;
var obj={
    name:"小刘",
    objAge:this.age,
    myFun:function(fm,t){
        console.log(this.name+"年龄"+this.age",来自"+fm+"去往"+t);
    }
}
var db={
    name:"德玛",
    age:99
} 
obj.myFun.apply(db,["江西","深圳"]);//德玛的年龄99,来自江西去往深圳  ------>this指向db
obj.myFun.call(db,"江西","深圳");//德玛的年龄99,来自江西去往深圳 ---->this指向db
```

```js
function test(){
    console.log('hhh');
}
test.call(obj);
//临时让test方法成为obj方法进行调用
```

### bind

 主要是将函数绑定到某个对象上，可以改变某个函数内部的this指向

例子：

```js
var a={
    b:function(){
        var func=function(){
            console.log(this.c) //this指向window
        }
        func();
    },
    c:'hello'
}
a.b();//undefined 

var a={
    b:function(){
        var that=this;
        var func=function(){
            console.log(that.c) //this指向a
        }
        func();
    },
    c:'hello'
}
a.b();//hello

var a={
    b:function(){
        var func=function(){
            console.log(this.c) 
        }.bind(this)
        func();
    },
    c:'hello'
}
a.b();//hello

var a={
    b:function(){
        var func=function(){
            console.log(this.c) 
        }
        func.bind(this)();
    },
    c:'hello'
}
a.b();//hello
```

```js
function fun(y,z){
    return this.x+y+z;
}
var m=func.bind({x:1},2) //{x:1}会作为函数内的this对象，剩余的作为函数的参数
console.log(m(3))
```

