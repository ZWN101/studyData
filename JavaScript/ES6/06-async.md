### async await

async await 语法结合可以让异步代码像同步一样

**async**函数的返回值是promise对象

```js
async function fun(){
    return 'success' //结果是成功的promise对象
    throw new Error('error') //失败的promise对象
    return new Promise((resolve,reject)=>{
        resolve('success')
    })  //结果是promise对象
}
```

### await

await要放在async函数里，await函数右侧必须是promise对象，await的返回结果是promise对象成功的值

promise对象执行失败要通过try catch进行捕获

```js
async function fun(){
    try {
        let result = await promise函数
    }catch(e){
        console.log(e)
    }
}
```

