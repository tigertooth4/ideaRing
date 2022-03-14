---
title: "在 MacOS 上安装 Node.js 与 Slidev (用 Markdown 写 PPT)"
date: 2022-03-14T12:07:33+08:00
draft: false
tags: ["slidev","nodejs","ppt"]
---

# 为何要使用 Node.js

我并不是程序员，安装 Node.js 其实唯一的目的就是要使用 [slidev](https://sli.dev/) 这个包，它能方便的将 markdown 转为 ppt. 这样，我在 notion 上写的讲义就可以方便的先转换成 markdown， 再转成 ppt 了，省却了重新制作 ppt 的烦恼。看到公众号上的介绍，我其实是很期待使用 slidev 的。

# 安装 Node.js

[官网](https://github.com/nvm-sh/nvm)介绍说推荐使用 nvm 安装和更新 node.js，我也找到下面的网站，来学习如何安装 nvm. 

[](https://www.newline.co/@Adele/how-to-install-nodejs-and-npm-on-macos--22782681)

1. 首先安装 nvm (注意，newline.co 中的版本已经比较老了，所以最好用 github 官网提供的脚本)。 系统会自动更新 .zshrc 文件

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

1. 为保险起见，我还是重载了一下系统配置 

```bash
source ~/.zshrc
```

1. 检验安装  (应该打印出 nvm 字样来)

```bash
command -v nvm
```

1. 安装 Node.js

```bash
nvm install node
```

上述命令将默认安装最新的 node.js. 运行不到一分钟，安装成功了，显示的 node.js 版本为 17.7.1.

1. 安装 npm

```bash
nvm install-latest-npm
```

# 安装 sli.dev

[Sli.dev](http://Sli.dev) 官方有安装的详细说明 

[Slidev](https://sli.dev/guide/install.html)

如果只想试玩一下，可以用

```bash
npm init slidev@latest
```

它会上网下载很多额外的包，并询问你要生成的 ppt 的名称是什么，给你一个默认的 markdown 文件。这写都是在命令行完成的。若一切顺利，可以打开 [http://localhost:3030](http://localhost:3030) 查看 ppt. （事实上，我最需要的功能并不是在线播放，而是打印出来，变成 pdf 文件。这些也是可以实现的。可参见官网）

不过，我有很多不同的 ppt 要做，所以我选全局安装（估计是安装到我的系统里面）

```bash
npm i -g @slidev/cli
```

这样，每次要使用 [sli.dev](http://sli.dev) 的时候，只要

```bash
slidev
```

即可. 

Slidev 的使用逻辑是，寻找当前目录下的 [slidev.md](http://slidev.md) 文件，然后生成 ppt，通过 [localhost:3030](http://localhost:3030) 端口查看（PPT 中可以实现浏览全部页面，动画，批注）等等效果。操作是在命令行下实现的。

# 如何输出 PPT?

需要安装 `playwright-chromium`

```bash
npm i -D playwright-chromium
```

然后 

```bash
slidev export
```

即可