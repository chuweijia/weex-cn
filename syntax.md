# 语法

Weex的语法极大的借鉴了[Vue.js](http://vuejs.org/)，Vue.js是一个具有强大的组件系统和灵活的数据绑定的javascript框架。

一个简单的Weex页面仅需要包含一段`<template>`代码、一段`<style>`代码和一段`<script>`代码。这三个部分共同描绘了一个完整的Weex页面。

* [**&lt;template&gt;**](#template)：_必需_。运用HTML的语法创建多个标签来描绘Weex页面的整体结构。每个标签代表一类组件。
* [**&lt;style&gt;**](#style)：_可选_。基于CSS语法来描绘页面具体展示细节。
* [**&lt;script&gt;**](#script)：_可选_。基于JavaScript语法来渲染数据和行为。它定义了具体的数据内容以及数据的处理方式。

```java
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

我们将页面的整体结构都包含在`<template>`标签中，示例如下：

```java
<template>
  <container>
    <image style="width: 200; height: 200;" src="http://gtms02.alicdn.com/tps/i2/TB1QHKjMXXXXXadXVXX20ySQVXX-512-512.png"></image>
    <text>Alibaba Weex Team</text>
  </container>
</template>
```

在上面的这段代码中，`<container>`标签是整个组件的根标签，`<image>`标签负责展示一张图片，而`<text>`标签则展示了一段文字。

类似于HTML，Weex页面中的每一个组件都拥有自己的属性，一些组件还可能包含其他组件。

根节点：在一个`<template>`标签中，仅允许有一个没有任何显示意义的根节点。下面是我们目前支持的三种根节点：

* `<container>`：普通根节点
* `<scroller>`：滚动器根节点，适用于拥有滚动效果的页面
* `<list>`：循环列表根节点，适用于有多个可循环展示的列表页面

目前Weex仅支持以上三种根节点。

* 点击查看所有内置组件

## &lt;style&gt; {#style}

你可以理解为Weex的样式语法是CSS语法的一个子集，但某些地方却不完全相同。

我们可以直接在`<template>`内的标签上用`style`来直接添加样式；也可以创建`<style>`标签，运用自定义的类名去给标签添加样式。示例如下：

```js
<template>
  <container>
    <text style="font-size: 64;">Alibaba</text>
    <text class="large">Weex Team</text>
  </container>
</template>

<style>
  .large {font-size: 64;}
</style>
```

上面例子中的两个`<text>`标签的字体都被设置为64px大小。

* 点击查看Weex公共样式

### 注意：

Weex基本遵循[HTML属性](https://en.wikipedia.org/wiki/HTML_attribute)命名规则，所以在对属性命名的时候请**不要使用驼峰命名法**，如果遇到较长的名字，请**以“-”隔开**。

## &lt;script&gt; {#script}

Weex页面中的数据渲染和处理遵循JavaScript\(ES5\)的语法。示例如下：

```js
<template>
  <container>
    <text>The time is {{datetime}}</text>
    <text>{{title}}</text>
    <text>{{getTitle()}}</text>
  </container>
</template>

<script>
  module.exports = {
    data: {
      title: 'Alibaba',
      datetime: null
    },
    methods: {
      getTitle: function () {
        return 'Weex Team'
      }
    },
    created: function() {
      this.datetime = new Date().toLocaleString()
    }
  }
</script>
```

我们来分析一下上面的代码：`<script>`标签中的代码，定义了三个属性或方法，然后将其赋给了`module.exports`对象。页面中将会分行依次显示“当前的时间”、“Alibaba”和“Weex Team”。`<script>`标签中的`data`属性存储了用来绑定到`<template>`中的数据，当这些数据改变的时候，页面中的绑定值也会立即发生改变。当然，这些值也可以在各个方法里通过`this.x`来进行读写。

* 点击查看组件定义参考文档

接下来，让我们一起学习[数据绑定](/data_binding.md)吧！

