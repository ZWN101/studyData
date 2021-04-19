参考：https://blog.csdn.net/sinat_36422236/article/details/88763187

### 什么是BFC

BFC（Block Formatting Context）块级格式化上下文

BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之也如此

### 如何创建BFC

1. float的值不是none

2. position的值不是static或者relative
3. display的值不是inline-block、table-cell、flex、table-caption或者inline-flex
4. overflow的值不是visible

### BFC的作用

* 利用BFC避免margin重叠
* 自适应两栏布局
* 清除浮动