# 样式和类

## 基础语法

CSS样式是由一个个的键值对组成，每一个键值对描述了一个特定的样式，就像下面所示例的宽和高：

```css
width: 400; height: 50; ...
```

键值对的形式是`prop-name:prop-value`。键名是`prop-name`，键值是`prop-value`。通常，键名和键值的命名都是每个单词用`-`分开。键名和键值必须要用`:`分开，不同键值对之间用`;`隔开。

在Weex页面中，样式将会以以下两种方式出现：

* `<template>`标签内的`style`属性
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



