# 显示逻辑控制

Weex目前共支持两种显示逻辑控制属性：`if`和`repeat`，它们使我们对Weex页面的构建更加灵活。

**注意：不能对根节点**`<template>`**进行显示逻辑控制，也就是说**`if`**和**`repeat`**不可直接应用在**`<template>`**标签上。**

## `if`

`if`属性可以通过设置`true`或`false`值来控制节点的显示，如果值为`true`，则该节点将被创建并渲染，否则该组件将被移除（页面源码中将无法看到此节点）。

```js
<template>
  <container>
    <text onclick="toggle">Toggle</text>
    <image src="..." if="{{shown}}"></image>
  </container>
</template>

<script>
  module.exports = {
    data: {
      shown: true
    },
    methods: {
      toggle: function () {
        this.shown = !this.shown
      }
    }
  }
</script>
```

## `repeat`

