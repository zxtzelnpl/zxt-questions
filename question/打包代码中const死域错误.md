Cannot declare a const variable twice: 'e'. /entz/static/js/h5.3eed7b481d38764.js

# 可能原因
vuex-persist 编译后出现如下代码
```javascript
function(e) {
 const e = // ...用const 
}
```

# 暂时解决防范
1. 暂时不使用vuex-persist
