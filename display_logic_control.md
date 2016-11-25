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

repeat仅用来对数组数据进行渲染，数组中的每一项都是一条结构化数据。也就是说， 可以直接将数组数据绑定在重复显示的组件或节点上。

```
<template>
  <container>
    <container repeat="{{list}}" class="{{gender}}">
      <image src="{{avatar}}"></image>
      <text>{{nickname}}</text>
    </container>
  </container>
</template>

<style>
  .male {...}
  .female {...}
</style>

<script>
  module.exports = {
    data: {
      list: [
        {gender: 'male', nickname: 'Li Lei', avatar: '...'},
        {gender: 'female', nickname: 'Han Meimei', avatar: '...'},
        ...
      ]
    }
  }
</script>
```

此外，不在数组中的数据也可以绑定在重复组件或节点上：

```
<template>
  <container>
    <container repeat="{{list}}" class="{{gender}}">
       <image src="{{avatar}}"></image>
       <text>{{nickname}} - {{group}}</text>
    </container>
  </container>
</template>

<style>
  .male {...}
  .female {...}
</style>

<script>
  module.exports = {
    data: {
      group: '...',
      list: [
        {gender: 'male', nickname: 'Li Lei', avatar: '...'},
        {gender: 'female', nickname: 'Han Meimei', avatar: '...'},
        ...
      ]
    }
  }
</script>
```

## `repeat`属性扩展

**使用**`$index`**来获取数组的当前索引值**

```js
<div repeat="{{list}}">
  <text>No. {{$index + 1}}</text>
<div>
```

**获取数组对应的键和值**

```js
<div repeat="{{v in list}}">
  <text>No. {{$index + 1}}, {{v.nickname}}</text>
</div>
```

```js
<div repeat="{{(k, v) in list}}">
  <text>No. {{k + 1}}, {{v.nickname}}</text><!--译者注：数组的key都是从0开始，若想得到通常意义的序号，应加1-->
</div>
```

**使用**`track-by`**绑定特定属性，以避免重复渲染**

通常，当数组中的数据发生变化，对应的`repeat`列表将整体被重新渲染。我们可以用`track-by`来指定数组中的某个键，当该键所对应的值没有发生变化的时候，该条数据不会被重新渲染。

**注意：不能用数据绑定符**`{{}}`**来设置**`track-by`**的属性值**

```js
<template>
  <container>
    <container repeat="{{list}}" track-by="nickname" class="{{gender}}"><!--译者注：此处直接写nickname即可-->
      <image src="{{avatar}}"></image>
      <text>{{nickname}} - {{group}}</text>
    </container>
  </container>
</template>
```

接下来，当`{{list}}`中的数据发生变化，如果检测到该条数据中`nickname`所对应的值没有发生变化，则该条数据所绑定的节点不会重新渲染。

## 简写方式

对于`if`和`repeat`属性，`{{}}`可以被省略。

```js
<template>
  <container>
    <text if="shown">Hello</text>
    <text if="{{shown}}">Hello</text>
  </container>
</template>

<script>
  module.exports = {
    data: function () {return {shown: true}}
  }
</script>
```

在上面的例子中，`if="shown"`和`if="{{shown}}"`的效果相同，两条Hello文本都将会被显示出来。

接下来，让我们一起学习[渲染逻辑控制](/render_logic_control.md)吧！

