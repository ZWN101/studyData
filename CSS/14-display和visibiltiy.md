### display:none和visibility:hidden的区别

#### 空间占据

display:none隐藏后的元素不占据任何空间，而visibility:hidden隐藏的元素空间依旧存在

#### 回流和渲染

设置display:none时页面会产生回流（重排）

设置visibility:hidden时页面会产生重绘

#### 株连性

display:none  一旦父元素设置了display:none，则父节点及其子孙节点的元素全部不可见，无论其子孙元素如何不屈挣扎都无济于事

#### 隐藏失效

visibility:hidden 父元素设置visibility:hidden，则其子孙元素也会被隐藏，如果子孙元素设置visibility:visible，则子孙元素会显示出来

