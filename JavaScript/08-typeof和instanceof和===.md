### typof(返回的是数据类型的字符串表达)

一般用来判断变量的类型**typeof(a)  typeof a**

但在判断对象类型的时候会出现一个问题，无论引用什么类型的对象，都会返回Object，所以需要用到instanceof来检测该对象是不是另一个对象的实例，instanceof也可以在继承关系中用来判断一个实例是否属于它的父类型。

* typeof  检查出来的某一变量的类型以字符串的形式存在

  ```js
  var a;
  console.log(a,typeof a,typeof a==='undefined',a===undefined);//undefined 'undefined' true true
  //a声明了但未赋值，则a的值为undefined；a的类型为undefined，'undefined'==='undefined',undefined===undefined
  ```

**typeof 可以用来判断  数值—字符串—布尔值—undefined—function（返回的是 function）**

**不能区别 null与Object，Object和Array**

### instanceof（返回true或false）

可以判断对象的具体类型       A instanceof B 判断左边的对象是不是右边这个类型的实例

如：

```js
//使用构造函数创建对象
function Foo(){}
//该对象的原型为Aoo类型
Foo.prototype = new Aoo();//javaScript原型继承

var foo  = new Foo();

console.log(foo instanceof Foo) //true

console.log(foo instanceof Aoo) //true
```

### ===（返回true或false）

判断null和undefined

**== 需要先转换类型再比较**

**=== 先判断类型，如果不是同一类型的就会直接false，表示恒等于，比较的两边要绝对相等**

```js
console.log(null == undefined);//true
console.log(null === undefined);//false
```



