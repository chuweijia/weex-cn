# 数据绑定

在Weex中，我们运用mustache语法将已经在&lt;script&gt;标签中定义的数据绑定到&lt;template&gt;模板上。一旦数据和模版绑定成功，数据的任何改变，将直接会在模版中实时体现出来。

## 双向数据绑定

```js
<template>
  <container>
    <text style="font-size: {{size}}">{{title}}</text>
  </container>
</template>

<script>
  module.exports = {
    data: {
      size: 48,
      title: 'Alibaba Weex Team'
    }
  }
</script>
```



