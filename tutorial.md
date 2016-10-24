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

安装完成后，你可以在命令行窗口直接输入`weex`后按enter键来检查是否安装成功。正确安装后会显示如下内容：

```bash
Usage: weex foo/bar/your_next_best_weex_script_file.we  [options]

Options:
  --qr     display QR code for native runtime, 
  -o,--output  transform weex we file to JS Bundle, output path (single JS bundle file or dir)
  -s,--server  start a http file server, weex .we file will be transforme to JS bundle on the server , specify local root path using the option  
  ......
  --help  Show help         
  -h, --host [default: "127.0.0.1"]
```

如果一切正常，切换到你刚才存储tech\_list.we的文件目录，然后运行：

```bash
weex tech_list.we
```

你默认的浏览器会自动打开新的窗口并显示一下内容（在这之前你最好运行`weex --version`来检查你的Weex Toolkit 版本是否大于0.1.0）：

![](/assets/TB1y151LVXXXXXXaXXXoRYgWVXX-495-584.jpg)

## Weex语法简介

现在是时候来介绍语法了。

如`tech_list.we`文件中所示，Weex代码包含三个部分--**_template（模版）,style_**_（样式）_和**_script_**_（脚本）_，就好比web文件中的_html_,_css_和_javascript_一样。

Template是Weex的骨架，他由标签以及标签所包含的内容组成。

