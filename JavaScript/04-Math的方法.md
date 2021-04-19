* 四舍五入

  ```js
  var num=2.84;
  console.log(Math.round(num));
  //输出3
  ```

* 绝对值

  ```js
  var num=-2.84;
  console.log(Math.abs(num));
  //输出2.84
  ```

* 向下取整

  ```js
  var num=2.84;
  console.log(Math.floor(num));
  //输出2
  ```

* 向上取整

  ```js
  var num=2.84;
  console.log(Math.ceil(num));
  //输出3
  ```

* 求最大值最小值

  ```js
  console.log(Math.max(12,20,33,1,77)); //输出77
  console.log(Math.min(12,20,33,1,77)); //输出1
  ```

* 随机数

```js
Math.random();//在0~1之间取值
Math.floor(Math.random()*10);//在0~9之间取值（整数）
Math.floor(Math.random()*10+1);//在1~10之间取值
Math.floor(Math.random()*11);//在0~10之间取值
Math.floor(Math.random()*100);//在0~99之间取值
Math.floor(Math.random()*100+1);//在1~100之间取值
Math.floor(Math.random()*101);//在0~100之间取值
Math.floor(Math.random()*62);//在0~61之间取值
```

