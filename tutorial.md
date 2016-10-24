# 快速上手

我们将编写一个简单的列表，来展示Weex是如何使用的。 类似的列表经常能在电商类移动应用中见到。

## 开始

我们从一个列表项开始，这个列表项包含一个image（图片）和位于图片右侧的文字说明。

```
<template>
  <div class="container">
    <div class="cell">
        <image class="thumb" src="http://t.cn/RGE3AJt"></image>
        <text class="title">JavaScript</text>
    </div>
  </div>
</template>

<style>
  .cell { margin-top: 10; margin-left: 10; flex-direction: row; }
  .thumb { width: 200; height: 200; }
  .title { text-align: center; flex: 1; color: grey; font-size: 50; }
</style>
```



