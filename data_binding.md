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

上面的代码将`size`和`title`数据绑定在了模版对应的位置上。

我们也可以用`.`语法来绑定级联结构数据。让我们来看看下面的代码：

```js
<template>
  <container>
    <text style="font-size: {{title.size}}">{{title.value}}</text>
  </container>
</template>

<script>
  module.exports = {
    data: {
      title: {
        size: 48,
        value: 'Alibaba Weex Team'
      }
    }
  }
</script>
```

## 模版表达式

除了直接数据绑定之外，Weex还支持简单的javascript表达式，示例如下：

```js
<template>
  <container style="flex-direction: row;">
    <text>{{firstName + ' ' + lastName}}</text>
  </container>
</template>

<script>
  module.exports = {
    data: {
      firstName: 'John',
      lastName: 'Smith'
    }
  }
</script>
```

该表达式将会在渲染页面的时候将值计算并插入到页面中。

**提示：每一个绑定只能包含一个表达式**

## 计算属性

对于简单的操作，模版表达式可以很方便的实现。但是如果你的模版上有一些比较复杂的逻辑，你应该会用到计算属性 。来看看下面这个例子：

```js
<template>
  <container style="flex-direction: row;">
    <text>{{fullName}}</text>
    <text onclick="changeName" style="margin-left:10px;">CHANGE NAME</text>
  </container>
</template>

<script>
  module.exports = {
    data: {
      firstName: 'John',
      lastName: 'Smith'
    },
    computed: {
      fullName: {
        get: function() {
          return this.firstName + ' ' + this.lastName
        },

        set: function(v) {
          var s = v.split(' ')
          this.firstName = s[0]
          this.lastName = s[1]
        }
      }
    },
    methods: {
      changeName: function() {
        this.fullName = 'Terry King'
      }
    }
  }
</script>
```

在这里，我们定义了一个计算属性`fullName`，我们将会运用它的`getter`方法去拼接`firstName`和`lastName`。

另外当我们点击CHANGE NAME时，将会执行`changeName`方法，此时`setter`方法将会被调用，对应的`this.firstName`和`this.lastName`将会被更新。

提示：`data`和`methods`不能有重复字段。因为在整个代码执行的过程中，`this`关键字可以直接访问到它们。

## 数据绑定中的特殊属性

