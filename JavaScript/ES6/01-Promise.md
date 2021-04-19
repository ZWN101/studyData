### Promise的含义

**协助实现异步中的同步问题**

promise是异步编程的一种解决方案，比**传统的解决方案——如回调函数和事件（这是异步操作常见的语法）**——更加合理和强大

promise对象代表了将来将要发生的事件，用来传递异步操作的消息

https://www.jianshu.com/p/1b63a13c2701

<img src="C:\Users\zhuwanning\AppData\Roaming\Typora\typora-user-images\image-20201115162456128.png" alt="image-20201115162456128" style="zoom:67%;" />

具体参照阮一峰老师的ES6入门，以下为链接

https://es6.ruanyifeng.com/#docs/promise

### Promise对象的状态

* pending 未完成
* fulfilled 成功
* rejected 失败

状态的改变只有两种可能：

**pending——>fulfilled**              **pending——>rejected**

只要这两种情况发生，状态就不会再发生改变。	

### Promise的缺点

`Promise`也有一些缺点。首先，无法取消`Promise`，一旦新建它就会立即执行，无法中途取消。其次，如果不设置回调函数，`Promise`内部抛出的错误，不会反应到外部。第三，当处于`pending`状态时，无法得知目前进展到哪一个阶段（刚刚开始还是即将完成）。

### 基本用法

Promise对象是一个构造函数，用来生成promise实例

```js
const promise=new Promise(function(resolve,reject){
		//some code
		if(/*异步操作成功*/){
			resolve(value);
		}else{
			reject(error);
		}
	});
promise.then(function(value){
	//success
   },function(error){
	//failure
   });
```

Promise构造函数接收一个函数作为参数，该函数的参数分别是resolve和reject。他们是两个函数，有JavaScript引擎提供，不需要自己部署

resolve函数的作用：将promise对象的状态从pending变成fulfilled（未完成——>成功）

reject函数的作用：将promise对象的状态从pending变成rejected（未完成——>失败）

Promise实例生成以后，可以用then方法分别指定fulfilled和rejected状态的回调函数

`then`方法接收两个参数。第一个回调函数是Promise对象的状态变为fulfilled时调用，第二个回调函数是Promise对象的状态变为rejected时调用，第二个参数是可选的。这两个函数都接收Promise对象传出的值作为参数

**Promise新建后会立即执行**

```js
let promise=new Promise(function(resolve,reject){
	console.log('Promise');
	resolve();
});
promise.then(function(){
  console.log('resolved');
})
console.log('Hi!');

//Promise
//Hi!
//resolved

//Promise新建后会立即执行，所以首先输出的是Promise，然后then方法指定回调函数，将回调函数插入到任务队列中去等待执行，需要将主线程上的任务执行完毕后，才会执行任务队列里的任务
```

### promise.all()

当我们有多个网络请求需要同时发送的时候，使用promise.all()

使用promise.all()他会等所有的网络请求完成之后，调用then方法，results数组里封装了网络请求封装的结果

当所有的请求都成功时，这个promise就成功了，调用then方法

```js
Promise.all([new Promise((resolve,reject)=>{
    setTimeout(()=>{
        resolve('name');
    },10)
},new Promise((resolve,reject)=>{
    setTimeout(()=>{
        resolve('age');
    },20)
})]).then(results=>{
    console.log(results[0])//name
    console.log(results[1])//age
})
```

如果有一个失败了，这个promise就失败，调用catch方法

```js
const p1 = new Promise((resolve, reject) => {
        resolve('第一个任务');
})
const p2 = new Promise((resolve,reject) =>{
    setTimeout(() => {
        reject('第二个任务')
    }, 1000);
})
const p3 = new Promise((resolve, reject) => {
    setTimeout(() => {
        reject('第三个任务');    
    }, 500);
  })

Promise.all([p1,p2,p3]).then(
    result=>console.log(result)
  ).catch(
    e=>console.log(e)        
  )//第三个任务
```

### Promise.race()

`promise.race(iterable)`方法返回一个promise，一旦迭代器中的某个promise解决resolve或拒绝reject，返回的promise就会解决或拒绝

**比比谁更快** 

```js
const p1=new Promise((resolve,reject)=>{
    setTimeOut(()=>{
        reolve('p1')
    },100)
})
const p2=new Promise((resolve,reject)=>{
    setTimeOut(()=>{
        reject('p2')
    },300)
})
const p3=new Promise((resolve,reject)=>{
    setTimeOut(()=>{
        reolve('p3')
    },50)
})
Promise.race([p1,p2,p3])
.then(result=>{
    console.log(result+'result') //p3result
}).catch(error=>{
    console.log(error+'error')
})
```

