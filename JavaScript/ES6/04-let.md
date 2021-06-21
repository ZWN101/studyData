var声明全局变量会注册到window对象上，但let和const不会

### 全局作用域

直接写在script中的js代码是全局作用域

在页面打开时创建，页面关闭时销毁

全局作用域中的变量为全局变量，在页面任意部分都可以访问到

在全局作用域中

  	创建的变量都会作为window的属性保存

​	   创建的函数都会作为window的方法

### 局部作用域

每个函数在定义时有自己的作用域成为局部作用域

局部作用域中的变量成为局部变量，在函数内部可以访问到，函数执行完毕后局部变量销毁

### 变量和函数声明提前

使用function声明的函数和var同级，都会声明提前

```js
console.log(a);//undefined
func();//12
var a=10;
console.log(a);//10
function func(){
    console.log("12");
}
```

```js
var关键字的声明规则有一条，如果是undefined，就不会覆盖 
function fun(a){
    var a;
    console.log(a);
}
fun(1000);//1000

function fun1(a){
    var a=999;
    console.log(a);
}
fun1(222);//999

function fun2(a){
    a=888;
    b=123;
    console.log(888)
}
fun2(666);//666
console.log(b);//123
```



### let的特性

#### 变量不能重复声明

```js
let a=10;
let a=11;
console.log(a);//报错

var b=10;
var b=12;
console.log(b);//输出12
```

#### 有自己的块级作用域

if else while for等

```js
{
	let name='猪八戒';
}
console.log(name);//报错
```

#### 不存在变量提升

```js
console.log(height);//报错Cannot access 'height' before initialization
let height=170;
```

#### 不影响作用域链

```js
{
	let address='河南'
	function fun1(){
		console.log(address);//河南
	}
	fun1();
}
```

### const

1. 一定要赋初始值，否则会报错

2. 一般常量用大写

3. 常量的值不能修改

4. 块级作用域

   



