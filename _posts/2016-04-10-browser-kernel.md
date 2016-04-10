---
layout: post
title:  "浏览器内核及渲染简介"
date:   2015-04-10 22:21:49
categories: 前端
tags: 浏览器，前端
---


## 一、什么是浏览器内核
通常所谓的浏览器的内核也就是浏览器所采用的渲染引擎。渲染引擎决定了浏览器如何显示网页的内容和页面的格式信息。

## 二、常见的浏览器内核分类
* Trident: IE内核
* Gecko: FireFox内核
* Presto: Opera内核
* WebKit: safari,chrome内核

## 三、浏览器的渲染原理
页面渲染就是浏览器根据HTML代码根据CSS定义的规则显示在浏览器窗口中的过程。  

1. 用户输入网址（假设是个HTML页面，并且是第一次访问），浏览器向服务器发出请求，服务器返回HTML文件；
2. 浏览器开始载入HTML代码,发现<head>标签内有一个`<link>`标签引用外部CSS文件；
3. 浏览器又发出CSS文件的请求,服务器返回这个CSS文件；
4. 浏览器继续载入HTML中`<body>`部分的代码，并且CSS文件已经拿到手了，可以开始渲染页面了；
5. 浏览器在代码中发现一个`<img>`标签引用了一张图片，向服务器发出请求。此时浏览器不会等到图片下载完，而是继续渲染后面的代码；
6. 服务器返回图片文件，由于图片占用了一定面积，影响了后面段落的排布，因此浏览器需要回过头来重新渲染这部分代码；
7. 浏览器发现了一个包含一行JavaScript代码的`<script>`标签，赶快运行它；
8. JavaScript 脚本执行了这条语句，它命令浏览器隐藏掉代码中的某个`<div>（style.display=”none”）`。杯具啊，突然就少了这么一个元素，浏览器不得不重新渲染这部分代码；
9. 终于等到了 `</html>` 的到来，浏览器泪流满面……
10. 等等，还没完，用户点了一下界面中的“换肤”按钮，JavaScript 让浏览器换了一下 `<link>` 标签的 CSS 路径；
11. 浏览器召集了在座的各位 `<div><span><ul><li>` 们，“大伙儿收拾收拾行李，咱得重新来过……”，浏览器向服务器请求了新的CSS文件，重新渲染页面。

1）浏览器会解析三个东西:  
一个是 HTML/SVG/XHTML，事实上，Webkit 有三个 C++ 的类对应这三类文档。解析这三种文件会产生一个 DOM Tree。
CSS，解析 CSS 会产生 CSS 规则树。
Javascript，脚本，主要是通过 DOM API 和 CSSOM API 来操作 DOM Tree 和 CSS Rule Tree.  
2）解析完成后，浏览器引擎会通过 DOM Tree 和 CSS Rule Tree 来构造 Rendering Tree。注意：  
Rendering Tree 渲染树并不等同于 DOM 树，因为一些像 Header 或 display:none 的东西就没必要放在渲染树中了。
CSS 的 Rule Tree 主要是为了完成匹配并把 CSS Rule 附加上 Rendering Tree 上的每个 Element。也就是 DOM 结点。也就是所谓的 Frame。
然后，计算每个 Frame（也就是每个 Element）的位置，这又叫 layout 和 reflow 过程。  
3）最后通过调用操作系统 Native GUI 的 API 绘制。  

这里重要要说两个概念，一个是 Reflow，另一个是 Repaint。这两个不是一回事。
Repaint——屏幕的一部分要重画，比如某个 CSS 的背景色变了。但是元素的几何尺寸没有变。
Reflow——意味着元件的几何尺寸变了，我们需要重新验证并计算 Render Tree。是 Render Tree 的一部分或全部发生了变化。这就是 Reflow，或是 Layout。（HTML 使用的是 flow based layout，也就是流式布局，所以，如果某元件的几何尺寸发生了变化，需要重新布局，也就叫 reflow）reflow 会从 <html> 这个 root frame 开始递归往下，依次计算所有的结点几何尺寸和位置，在 reflow 过程中，可能会增加一些 frame，比如一个文本字符串必需被包装起来。
