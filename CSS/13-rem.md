rem相对于跟元素html来设置字体大小的

浏览器默认字体大小为16px，最小字体大小为12px

```css
html{
    font-size:62.5%; //10÷16*100%=62.5%
}
body{
    font-size:1rem;//10px
}
div{
    font-size:2.4rem;//24px
}
```

随着窗口大小调整字体大小

```js
function setHtmlFontSize(initWidth) {
    adjust();
    $(window).resize(function() { //监听窗口变化
        adjust(); //调用调整字体函数
    })

    function adjust() {
        var windowWidth = $(window).width(); //获取窗口宽度
        var fontSize = windowWidth > initWidth ? 10 : (10 * windowWidth) / initWidth; //如果大于初始值，新的到的字体的大小
        $('html').css('font-size', fontSize + 'px'); //赋值给font-size属性
    }
}

 setHtmlFontSize(1920);
```

echart字体大小的设置

```js
function fontSize(res) {
    let clientWidth = window.innerWidth || document.documentElement.clientWidth || document.body.clientWidth;
    if (!clientWidth) return;
    let fontSize = clientWidth > 1920 ? 10 : (10 * clientWidth) / 1920;
    return res * fontSize;
}
```











