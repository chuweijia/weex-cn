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

如`tech_list.we`文件中所示，Weex代码包含三个部分--**_template（模版）,style_**_**（样式）**_和**_script_**_**（脚本）**_，就好比web文件中的_html_,_css_和_javascript_一样。

**Template**是Weex的骨架，他由标签以及标签所包含的内容组成。标签又分为两种：开标签和闭标签。我们把一对由开标签和闭标签组合的标签称为一组Weex标签。标签具有不同的_属性_，不同的属性代表不同的含义，例如`class属性`可以将相同的样式赋予多个标签，`onclick属性`让标签可以响应点击事件。

**Style**规定了Weex标签如何展示，我们跟你一样喜欢CSS，所以我们尽可能的跟CSS标准保持了一致。Weex样式支持非常多的CSS功能，如margin,padding,fixed等等。更妙的是，flexbox布局在Weex中也得到了很好的支持。

**Script**可以将数据和逻辑添加到标签之中，使你更方便的访问本地或远程数据并且动态的更新标签。当然，你也可以定义一些方法来让标签响应不同的事件。 Weex Script的组织方式遵循CommonJS module规范。

更多关于Weex语法的信息，可以点击[语法章节](/syntax.md)查看。

## 添加多个列表项

通常，一个列表不会仅有一个列表项，所以我们需要在我们的tech列表中添加更多的列表项。在你心爱的编辑器中打开`tech_list.we`文件，然后更新至如下代码：

```css
<template>
  <div class="container">
    <div class="cell">
        <image class="thumb" src="http://t.cn/RGE3AJt"></image>
        <text class="title">JavaScript</text>
    </div>
    <div class="cell">
        <image class="thumb" src="http://t.cn/RGE3uo9"></image>
        <text class="title">Java</text>
    </div>
    <div class="cell">
        <image class="thumb" src="http://t.cn/RGE31hq"></image>
        <text class="title">Objective C</text>
    </div>
   </div>
</template>

<style>
  .cell{ margin-top:10 ; margin-left:10 ; flex-direction: row; }
  .thumb { width: 200; height: 200; }
  .title { text-align: center ; flex: 1; color: grey; font-size: 50; }
</style>
```

现在，让我们来尝试使用Weex Native渲染器来渲染这个文件。再一次的打开你的终端并且切换到刚才保存`tech_list.we`文件的目录下，运行如下代码：

```bash
weex tech_list.we --qr -h {ip or hostname}
```

我们推荐使用`-h`命令符去指定你的本地IP地址或域名。

在终端窗口将会显示一个二维码，如下图所示：

![](/assets/tut-cli-qrcode.png)

这个二维码需要在[Weex Playground App](http://alibaba.github.io/weex/download.html)中工作。下载安装后，打开此APP，点击右上角的扫码图标扫描此二维码 ，如果运行成功，一个漂亮的列表将会显示在你的手机界面上。

![](/assets/tut-second.png)

在这里，我必须要强调一下，这是列表完全是由native view来渲染的，并非Webkit。相比之下，native view加载速度更快且耗费的内存更小。



