```javascript
// 解决安卓手机，软键盘抬起输入框不在可是区域内（软键盘抬起被遮挡）

if(/Android/.test(navigtor.appVersion)) {
    window.addEventListener("resize",function(){
        if(document.activeElement.tagName=="INPUT" || document.activeElement.tagName=="TEXTAREA"){
            window.setTimeout(function() {
                document.activeElement.scrollIntoViewIfNeeded(true);
            },100);
        }
    })
}


//  解决苹果手机12版本，软键盘收回页面底部空白
if(/iphone/gi.test(navigator.userAgent)) {
    document.body.addEventListener('focusout', function () {
        window.scrollTo(0, 500);
    })
}
```
