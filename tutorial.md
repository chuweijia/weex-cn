# 快速上手

我们将编写一个简单的列表，来展示Weex是如何使用的。 类似的列表经常能在电商类移动应用中见到。

## 开始

我们从一个列表项开始，这个列表项包含一个image（图片）和位于图片右侧的文字说明。

&lt;template&gt;

 &lt;div class="container"&gt;

 &lt;div class="cell"&gt;

 &lt;image class="thumb" src="http:\/\/t.cn\/RGE3AJt"&gt;&lt;\/image&gt;

 &lt;text class="title"&gt;JavaScript&lt;\/text&gt;

 &lt;\/div&gt;

 &lt;\/div&gt;

&lt;\/template&gt;

&lt;style&gt;

 .cell { margin-top: 10; margin-left: 10; flex-direction: row; }

 .thumb { width: 200; height: 200; }

 .title { text-align: center; flex: 1; color: grey; font-size: 50; }

&lt;\/style&gt;

