### 1.差值表达式
{{}}
### 2.v-on
* 用于事件绑定
  鼠标事件（click、mouseover、mouseout）
  键盘事件（keydown、keyup、keypress）
  表单事件（submit、reset、change）
  窗体事件（onload、open）
  焦点事件（focus、blur）
* 语法糖
  @click（鼠标单击事件）
* 修饰符
  **.prevent**
  阻止事件默认行为，如：阻止表单提交
  **.once**
  事件只触发一次
  **.middle**
  按下鼠标滚轴调用
  **.ctrl**
   @click.ctrl
  需按住ctrl点击按钮才会调用btnClick方法
  **enter**
  @keyup.enter
  按下键盘的enter键才会触发  
### 3.v-bind
* 语法糖
  :
* 用于绑定属性
  **1.绑定class属性**
    （1）对象语法
         :class={类名:boolean类型的变量名}
         :class={active:isActive,show:isShow}
         isActive isShow都为boolean类型的变量      
    （2）数组语法
         :class=[变量,变量]
         :class=[active,show]
         data:{
         active:"类名"
         show:"类名"
         }
 **2.绑定style属性**
     （1）对象语法
         :style={样式名:变量名}
         :style={fontSize:fs}
         data:{
         fs:"30px"
         }
     （2）数组语法
         :style=[变量,变量]
         :style=[baseStyle,baseStyle1]
         data:{
         baseStyle:{
         backgroundColor:red
         }
         baseStyle1:{
         fontSize:30px
         }
### 4.v-model
* 双向绑定，一般用于可以与用户交互的元素，如：input、textarea等

* 原理：input标签的input事件，监听input的输入框
          v-bind绑定属性事件绑定value
  `<input type="text" :value="message" @input="message=$event.target.value"/> `
  
* 修饰符
      
  **.lazy**
  
  失去焦点
```html
<input type='text' v-model='inputValue'>

vue中：
data(){
   inputValue:'你好'
}
```



### 5.v-text

```html
<h2 v-text="message">哈哈哈哈</h2>
```

页面中显示message变量绑定的值
但是v-text只能绑定文本，不够灵活

### 6.v-html

解析HTML代码

```html
<h2 v-html="url"></h2>
```

url:"<a href='http://www.baidu.com'>百度一下</a>"


### 7.v-for
* 遍历数组
  v-for="(value,index) in items" 
  value：值
  index：下标
* 遍历对象
  v-for="(value,key,index)' in items"
  value：值
  key：属性名
  index：下标
### 8.v-if
v-if v-else-if v-else
通常条件过多时不用这个标签来进行判断
**当v-if的条件为false时，它对应的标签元素会从dom树中直接删除，适用于一次切换**
### 9.v-show
**v-show 当条件为false时，会给该元素添加一个行内样式：display:none适用于多次切换**













