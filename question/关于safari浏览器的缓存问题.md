```html
<meta http-equiv="Expires" CONTENT="-1">
<meta http-equiv="Cache-Control" CONTENT="no-cache">
<meta http-equiv="Pragma" CONTENT="no-cache">
```

```javascript
if (isSafari()) {
$(window).bind("pageshow", function (event) {
if (event.originalEvent.persisted && $('body').hasClass("no-cache")) {
document.body.style.display = "none";
window.location.reload();
}
});
}

function isSafari() {
if (navigator.userAgent.indexOf("Safari") > -1) {
return true;
}
return false;
}
```