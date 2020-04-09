# cannot read property ‘range’ of null Occurred
### 可能原因：
1. import引入不确定可能是null
```javascript
{
    // ...
    component: (() => import(`@/views/${item.component}`))
    // ...
}
```

2. babel-eslint版本过高
3. @babel/types版本冲突

### 解决方案：
1. 修改动态路由加载方式
```javascript
{
    // ...
    component: (resolve => require([`@/views/${item.component}.vue`], resolve))
    // ...
}
```
2. 将babel-eslint版本降级，降低到8.2.1
3. eslint中先注释
```javascript
{
    // ...
    parser: 'babel-eslint'
    // ...
}
```
