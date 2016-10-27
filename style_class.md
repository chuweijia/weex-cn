# 样式和类

## 基础语法

CSS样式是由一个个的键值对组成，每一个键值对描述了一个特定的样式，就像下面所示例的宽和高：

```css
width: 400; height: 50; ...
```

键值对的形式是`prop-name:prop-value`。键名是`prop-name`，键值是`prop-value`。通常，键名和键值的命名都是每个单词用`-`分开。键名和键值必须要用`:`分开，不同键值对之间用`;`隔开。

在Weex页面中，样式将会以以下两种方式出现：

* `<template>`标签中的`style`属性
* `<style>`标签内的样式表

### `style`属性

把样式直接写在style属性中，示例如下：

```css
<template>
  <container style="width: 400; height: 50;">
    ...
  </container>
</template>
```

以上代码将`<container>`标签的宽高分别设置成了`400px`和`50px`

### `<style>`标签

看下面的例子：

```css
<style>
  .wrapper {width: 600;}
  .title {width: 400; height: 50;}
  .highlight {color: #ff0000;}
</style>
```

样式表包含多条样式规则，每一条规则都有一个唯一的类以及用`{...}`包裹起来的若干样式构成。像下面这样：

```css
.title {width: 400; height: 50;}
```

就是一条样式规则。

### `class`属性

`<template>`标签中的`class`属性将会匹配`<style>`标签内的样式，`class`属性里面的类名需要用**空格**分开。看下面的例子：

```css
<template>
  <container class="wrapper">
    <text class="title">...</text>
    <text class="title highlight">...</text>
  </container>
</template>
<style>
  .wrapper {width: 600;}
  .title {width: 400; height: 50;}
  .highlight {color: #ff0000;}
</style>
```

最外层的`<container>`标签宽是`600px`，里面的两个`<text>`标签的宽和高都分别是`400px`和`50px`，第二个`<text>`标签的文本颜色被设置成红色。

### 提示：

* 为了简化页面的设计和实现，我们默认所有的屏幕宽度都是`750px`，不同尺寸的屏幕将按照这一比例进行缩放。
* 标准CSS支持很多种选择器，但Weex目前仅支持单个类的选择器。
* 标准CSS支持很多长度单位，但Weex目前仅支持像素`px`，`px`可以省略不写，只写数值。更多详情请查看通用基本样式。
* 子元素的样式不会继承父元素的样式，这一点与标准CSS不同，比如`color`和`font-size`。
* 标准CSS包含了非常多的样式，但Weex目前仅支持了一部分，像盒模型，`flexbox`，`position`等布局，以及`font-size`、`color`等。

## 结合数据绑定

页面数据也可以绑定在`style`和`class`属性中。示例如下：

```js
<template>
  <container>
    <text style="font-size: {{fontSize}};">Alibaba</text>
    <text class="large {{textClass}}">Weex Team</text>
  </container>
</template>
<style>
  .large {font-size: 32;}
  .highlight {color: #ff0000;}
</style>
<script>
  module.exports = {
    data: {
      fontSize: 32,
      textClass: 'highlight'
    }
  }
</script>
```

接下来，让我们一起学习[事件](/events.md)吧！

