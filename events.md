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

当用户点击图片的时候，定义在`<script>`标签内部的`handler`方法将会被触发。

## 事件传参

除了直接绑定函数名之外，还可以给该函数传递自定义参数。

示例如下：

```js
<template>
  <image onclick="handler('arg1', $event)" ...></image>//译者注：$event不可被省略，即便你不用
</template>

<script>
  module.exports = {
    methods: {
      handler: function (arg1, e) {
        // TODO
      }
    }
  }
</script>
```

## 事件对象

当一个事件被触发的时候，它接收的第一个参数便是事件对象。每一个事件对象都会包含以下属性：

* `type`：事件名称，如`click`
* `target`：触发事件的目标元素
* `timestamp`：事件触发的时间戳

接下来，让我们一起学习[显示逻辑控制](/display_logic_control.md)吧！

