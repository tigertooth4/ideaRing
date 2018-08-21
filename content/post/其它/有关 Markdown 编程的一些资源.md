+++
title = "有关 Markdown 编程的一些资源"
date = "2013-03-13 22:58:40"
draft = false
tags = ["markdown"]
author = "tt4"
+++


也许我的程序中需要使用 markdown, 所以今天搜索了一些有关 markdown 解析的资源以备用：

*   Stack Overflow 中的讨论一：[http://stackoverflow.com/questions/1435288/what-is-the-simplest-implementation-of-markdown-for-a-cocoa-application](http://stackoverflow.com/questions/1435288/what-is-the-simplest-implementation-of-markdown-for-a-cocoa-application

*   Stack Overflow 中的讨论二：Markdown implementations for C/C++ [http://stackoverflow.com/questions/889434/markdown-implementations-for-c-c](http://stackoverflow.com/questions/889434/markdown-implementations-for-c-c

*   github/macdown: [https://github.com/cliss/Macdown/tree/master/Source](https://github.com/cliss/Macdown/tree/master/Source

*   github/markdownlive: [https://github.com/rentzsch/markdownlive](https://github.com/rentzsch/markdownlive

*   libsoldout: [http://fossil.instinctive.eu/libsoldout/index](http://fossil.instinctive.eu/libsoldout/index

*   github/sundown: [https://github.com/vmg/sundown](https://github.com/vmg/sundown

*   github/peg-markdown: [https://github.com/jgm/peg-markdown](https://github.com/jgm/peg-markdown

*   github/ghmarkdownparser: [https://github.com/OliverLetterer/GHMarkdownParser](https://github.com/OliverLetterer/GHMarkdownParser)

事实上，我在考虑我的程序的两种实现方法：

1.  NSTextView + Image Attachment : 这种方法较为简单，但是缺点是如果要改变样式非常困难（当然也可以考虑用 CSS 做为样式文件，当程序运行时解析这个文件

2.  NSWebView + CSS: 这种方法我还不清楚 webview 中是否允许直接编辑富文本

我的目标和灵感来自： [http://xiki.org/screencasts/](http://xiki.org/screencasts/)
