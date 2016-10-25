# 语法

Weex的语法极大的借鉴了[Vue.js](http://vuejs.org/)，Vue.js是一个具有强大的组件系统和灵活的数据绑定的javascript框架。

一个简单的Weex页面仅需要包含一段`<template>`代码、一段`<style>`代码和一段`<script>`代码。这三个部分共同描绘了一个完整的Weex页面。

* [**&lt;template&gt;**](#template)：_必需_。运用HTML的语法创建多个标签来描绘Weex页面的整体结构。每个标签代表一类组件。
* **&lt;style&gt;**：_可选_。基于CSS语法来描绘页面具体展示细节。
* **&lt;script&gt;**：_可选_。基于JavaScript语法来渲染数据和行为。它定义了具体的数据内容以及数据的处理方式。

```js
<template>
  <!-- (required) the structure of page -->
</template>

<style>
  /* (optional) stylesheet */
</style>

<script>
  /* (optional) the definition of data, methods and life-circle */
</script>
```

## &lt;template&gt; {#template}

