## 创建一个 Vue 的实例

每个 Vue 应用都是通过 `Vue` 函数创建一个新的 **Vue 实例**开始的：

```javascript
var vm = new Vue({
  // 选项
})
```

当创建一个 Vue 实例时，你可以传入一个**选项对象**。这篇教程主要描述的就是如何使用这些选项来创建你想要的行为。作为参考，你也可以在 [API 文档](https://cn.vuejs.org/v2/api/#%E9%80%89%E9%A1%B9-%E6%95%B0%E6%8D%AE) 中浏览完整的选项列表。

## `el` 选项

> 参考文档：https://cn.vuejs.org/v2/api/#el

提供一个在页面上已存在的 DOM 元素作为 Vue 实例的挂载目标。可以是 CSS 选择器，也可以是一个 HTMLElement 实例。

- 不能作用到 `<html>` 或者 `<body>` 上
- 也可以通过 `实例.$mount()` 手动挂载

## `data` 选项

> 参考文档：https://cn.vuejs.org/v2/api/#data

- 响应式数据
- 可以通过 `vm.$data` 访问原始数据对象
- Vue 实例也代理了 data 对象上所有的属性，因此访问 `vm.a` 等价于访问 `vm.$data.a`
- 视图中绑定的数据必须显式的初始化到 data 中

## `methods` 选项

> 参考文档：https://cn.vuejs.org/v2/api/#methods

methods 将被混入到 Vue 实例中。可以直接通过 VM 实例访问这些方法，或者在指令表达式中使用。方法中的 `this` 自动绑定为 Vue 实例。

!> 注意，**不应该使用箭头函数来定义 method 函数** (例如 `plus: () => this.a++`)。理由是箭头函数绑定了父级作用域的上下文，所以 `this` 将不会按照期望指向 Vue 实例，`this.a` 将是 undefined。

示例：

```javascript
var vm = new Vue({
  data: { a: 1 },
  methods: {
    plus: function () {
      this.a++
    }
  }
})
vm.plus()
vm.a // 2
```



## 实例生命周期

![dsa](https://cn.vuejs.org/images/lifecycle.png)