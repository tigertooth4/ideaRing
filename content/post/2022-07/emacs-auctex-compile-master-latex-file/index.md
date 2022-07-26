---
title: "在 Emacs + AucTeX 中编译主 LaTeX 文件"
date: 2022-07-26T12:12:00+08:00
draft: false
tags: ["knowledge","emacs","auctex","latex","masterfile","B.A.S.B.","日精一技"]
---

# 背景

尽管使用 Emacs + AucTeX 编译 TeX 文件已经十多年了，但非常惭愧的是我一直是用最最基本的功能，比如  `C-c C-c` 编译 LaTeX 文件，`C-c C-l` 查看编译错误信息等等，从来没有钻研探索过 AucTeX 的高级功能。因为平时使用的最多的还是单 TeX 文件的编译。偶尔需要编译包含多个 TeX 文件的文档时，每次都需要切换到主 TeX 文件然后再编译。

最近因为写讲义的原因，发现经常跳转到主文件太麻烦了，于是才想探索一下，看看 AucTeX 能否直接使用相同的快捷键编译主文件，省去每次跳转的步骤。经过简单的搜索以后，发现果然可以，只需要让 AucTeX 了解多文档的结构关系，设置清楚哪篇为主文档，哪些为辅助文档即可。

# 解决方式

比如，如果现有多篇 TeX 文档，其结构关系是 

> Main.tex
> 
> - ch0.tex
> - ch1.tex
> - …

则只需在每篇文档的 buffer 中使用快捷键 `C-c _`, AucTeX 就会提示你确认此 buffer 是否为主文档。

另一种做法是，在主 TeX 文档的 buffer 结尾加上 

```latex
%%% Local Variables:
%%% mode: latex
%%% TeX-master: t
%%% End:
```

在辅 TeX 文档的 buffer 结尾加上

```latex
%%% Local Variables:
%%% mode: latex
%%% TeX-master: "Main"
%%% End:
```

注意 Main 的结尾不加 .tex 。这样，无论是在编辑哪个文档，都可以使用 `C-c C-c` 直接对主文档进行编译了. 

最后，如果多篇文档的结构关系是 

> ./ Main.tex
> 
> - ./ch0/ch0.tex
> - ./ch1/ch1.tex
> - …

那么，只要把 `%%% TeX-master: “Main”` 改成 `%%% TeX-maser: “../Main”` 即可.