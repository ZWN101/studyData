### axios与ajax的区别

axios实现了对ajax技术的封装

### 如何引入axios

1. 通过在js里引入axios.js文件

2. ```
   切换到项目的目录，输入指令
   npm install --save axios vue-axios
   ```

   具体查看axios官网

### axios的基本用法

* 获取users表里的所有数据

  ```js
  axios.get("http://127.0.0.1/3000/users")
  //成功
  .then(function(response){
      //response.data为查询到的数据
  })
  //失败
  .catch(function(error){
      
  });
  ```

* 获取users表里id为2的数据

  ```js
  axios.get("http://127.0.0.1/3000/users?id="+2)
  .then(function(){
     //response.data为查询到的数据
  });
  ```

* 修改users表里的数据

  ```js
  put方法
  ```

* 添加数据

  ```
  post 
  ```

* 删除数据

  ```
  delete
  ```


### axios发送并发请求

```js
axios.all([axios({
    url:'url',
    method:'get',
    params:{//get请求?后的参数可以放在params里
        name:'朱婉宁',
        age:18
    }
}),axios({
    url:'url1',
    method:'post'
})]).then(results=>{
    //results是一个数组
    console.log(results[0])
    console.log(results[1])
})
//或者
.then(axios.spread((res1,res2)=>{
    console.log(res1);
    console.log(res2);
}))
```

### axios全局配置

```js
axios.defaults.baseURL='http://localhost:8080'
axios.defaults.timeout=5000 //请求超时时间
axios.defaults.headers.post['Content-type']='application/x-www-form-urlencoded' //post方式的请求头
```

### 创建对应的axios实例 

```js
//利用axios.create()创建axios实例
const instance1 = axios.create({
   baseURL: 'http://123.207.32.32:8000',
   timeout: 5000
 })
const instance2 = axios.create({
   baseURL: 'http://223.207.32.32:8088',
   timeout: 5000,
   headers:{
   }
 })
//使用axios
instance1({
    url:'/login',
    params:{
        name:'www'.
        age:19
    }
}).then(res=>{
    
}).catch(err=>{
    
})
```

利用axios发送网络请求，本身返回的是一个promise对象，因此可以调用.then()，.catch()

### axios设置拦截器

```js
//配置axios拦截
//请求拦截的作用
// 1.比如config中的一些信息不符合服务器的要求
// 2.比如每次发送网络请求时, 都希望在界面中显示一个请求的图标
// 3.某些网络请求(比如登录(token)), 必须携带一些特殊的信息
instance.interceptors.request.use(config => {
        console.log(config)
        return config;
 }, err => {
        console.log(err)
 })

//响应拦截
instance.interceptors.response.use(res => {
        return res.data;
}, err => { 
        console.log(err)
})
```

