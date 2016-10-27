# 事件

Weex允许给`<template>`模版内的元素绑定事件属性。属性的名称是以on...开头加上事件的类型，属性的值为我们定义好的方法名称。以click事件来举个例子：onclick="handler"

```js
<template>
  <image onclick="handler" ...></image>
</template>

<script>
  module.exports = {
    methods: {
      handler: function (e) {
        // TODO
      }
    }
  }
</script>
```

