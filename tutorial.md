# 快速上手

我们将编写一个简单的列表，来展示Weex是如何使用的。 类似的列表经常能在电商类移动应用中见到。

## 开始

我们从一个列表项开始，这个列表项包含一个image（图片）和位于图片右侧的文字说明。

```css
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

你可以创建一个名为 tech\_list.we 的Weex文件（.we是我们推荐的文件后缀名）并将以上代码复制后粘贴入其中。

## 预览

文件建立完毕后，我们都会迫不及待的看到.we文件运行后的结果。但是在这之前，我们必须确保已经安装了依赖环境。

因为Weex工具都是使用Node.js所构建，我们首先需要安装Node，然后运行下面的代码，安装Weex命令行工具Weex Toolkit ：

```bash
npm install -g weex-toolkit
```

