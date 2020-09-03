---
title: 如何在 Mac 下安装 Manim
date: '2020-09-02T23:43:00+08:00'
draft: false
tags: ["Manim", "Math","3b1b"]
---

安装并使用 3b1b ([3blue1brown](https://www.blogger.com/)) 的数学可视化系统 [Manim@Github](https://github.com/3b1b/manim) 一直是我的一个愿望。可惜一直懒得动手，直到拖到现在😓。不过，今晚终于打算动手了！

参考了我保存许久的一个关于 Manim 安装的 [博客](https://repperiumsci.blogspot.com/2019/12/my-adventures-with-manim-part_22.html)，发现博主有了重大更新！为了方便爱好者们的使用，博主和其他一些小伙伴们 fork 了 3b1b 本身的代码，新建了一个 [社区版的 Manim](https://github.com/ManimCommunity/manim)。 这下就更方便了。于是，下面的安装流程，基本上参照 [社区版 Manim](https://github.com/ManimCommunity/manim) 的 [安装文档](https://manimce.readthedocs.io/en/latest/installation.html)。

# 一、安装过程

## （一）. 安装依赖的包

1. 安装 Homebrew (这部分由于我已经装过，故省略)

2. 安装 Cairo

   ```powershell
   brew install cairo
   ```

3. 安装 ffmpeg

   ```pow
   brew install ffmpeg
   ```

4. 安装 Sox (非必须)

   ```pow
   brew install sox
   ```

5. 安装 LaTeX （这一步基本上可以跳过了）。下面就是安装 TeXLive 的一些额外工具包：

   ```pow
   sudo tlmgr install standalone preview doublestroke relsize fundus-calligra \
   wasysym physics dvisvgm.x86_64-darwin dvisvgm rsfs wasy cm-super
   ```

可以运行 `ffmpeg --version`, `latex`, `sox` 等命令检查上述安装。

## （二）. 安装 Manim

为简便起见，我选择了通过 python 的包管理工具直接安装：

```pow
pip3 install manimce
```

# 二、Manim 的使用

根据文档所述，Manim 还是基于 python 的，它的使用有点像 LaTeX，首先建立一个文件夹，比如 `test`，然后将所有的代码、文件都放在这个文件夹中，并且使用 manim 编译。一段简单的代码如下所示 [^link],  让我来搬运一下！

```py
# scene.py
from manim import *

# all code must be contained inside the construct
# method of a class that inherits from Scene
class SquareToCircle(Scene):
    def construct(self):
        circle = Circle()                   # create a circle
        circle.set_fill(PINK, opacity=0.5)  # set the color and transparency
        self.play(ShowCreation(circle))     # show the circle on screen
```

将这段代码保存成 `test/scene.py` 后，就可以使用命令行来编译了：

```pow
manim scene.py SquareToCircle -pl
```

酷！实验成功！这里是真的要感谢 Manim 社区所有热心人的贡献🎉，是他们把安装使用过程讲解得如此清楚！此刻我的内心稍稍有点激动～

当然，冷静一下，看代码如此简单，实现的功能也不复杂。看来，真正的功夫是要下在如何讲故事，如何几何化上面，这方面我应该还有很长的路要走。

好了，今天就到这里了！Happy Manim ! Bye!

[^link]: 代码出自 https://manimce.readthedocs.io/en/latest/tutorials/quickstart.html

