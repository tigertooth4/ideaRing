---
date: '2019-08-26T15:29:00+08:00'
draft: false
title: 试验 Ultimaker 固件模拟器
tags: ["Ultimaker","Simulator","Marlin","C++",]
---

觊觎 Ultimaker2Marlin 中的模拟器 (simulator) 已经有很长时间了，这是一款桌面应用，打开它以后可以模拟 UM2 的屏幕显示效果，甚至可以模拟打印机的升温、降温过程和打印头、平台的位置。

虽然每份 Ultimaker2Marlin 的源代码中都包含模拟器的全部源代码，但这部分功能却一直是非常神秘的存在，因为几乎没有人（也许夸张了点）懂得如何使用它。17年 UM 社区的一篇帖子曾经让我非常兴奋，因为这篇帖子详细描述了如何编译、运行模拟器代码。但是，那时的我一看到代码是在 Windows 下编译运行的就退缩了，因为手边并没有一台合适的运行 Windows 的机器 。有人要问了：难道你就没想过使用虚拟机吗？是的，当时的我确实脑子短路了，根本没想有虚拟机这回事。

直到不久前，我重新会看那篇帖子的时候，才想起来我其实是有 VMware Fusion 和 Windows 7 虚拟机的。正巧，一个群友想给 UM2 固件添加新的调平功能。我想这是个绝好的机会，既可以帮他的忙，也可以顺便改变一下我以前开发固件的操作方式。

于是，从重新温习17年的旧帖子开始，花了两天时间，我把 UM2 的模拟器搞通了。中间遇到了一些问题（在原帖中没有提及）我觉得有必要把解决方案记录下来，以备将来查阅。

前面的步骤完全仿照[17年的帖子: How to build Marlin the way tinkergnome and Ultimaker do it if you have windows](https://community.ultimaker.com/topic/16856-how-to-build-marlin-the-way-tinkergnome-and-ultimaker-do-it-if-you-have-windows/) . 

# 原理

利用 [SDL](https://libsdl.org/) （Simple Direct Media Layer）库，这个库的用途是：Simple DirectMedia Layer is a cross-platform development library designed to provide low level access to audio, keyboard, mouse, joystick, and graphics hardware via OpenGL and Direct3D. It is used by video playback software, emulators, and popular games including [Valve](http://valvesoftware.com/)'s award winning catalog and many [Humble Bundle](https://www.humblebundle.com/) games.

为了编译，我们要有一个工程文件，Ultimaker2Marlin 源代码中的 UltiLCD2_sim.cbp，这个工程文件是在 code::block 这款开发环境中建立的。这是一款轻量级、免费、跨平台、多语言的 IDE.

为了编译，我们还要有 C++ 的编译器，这里用了 g++，所以在 Windows 下需要使用 MingW32。

有了这三样东西，基本上就大功告成了，需要注意的只有 cbp 的编译、链接参数，这个将在后文中重点讲述。

# 准备工作

1. 下载 Ultimaker2Marlin 的源代码（原版的在[这里](https://github.com/Ultimaker/Ultimaker2Marlin) ，Mark2 版的在 [这里](https://github.com/TinkerGnome/Ultimaker2Marlin) ）。
2. 下载 MingW32，[这里](https://sourceforge.net/projects/mingw/files/)，完全不熟悉 MingW 的我发现 MingW 有点类似 Linux 下的包管理工具，下载它的包管理工具，并且安装 **mingw32-base** 和 **mingw32-gcc-g++** (gnu c++ 编译器) 后，就成功搭建了一个基本 gcc 的编译环境。
3. 下载 [Arduino IDE](https://www.arduino.cc/) （ 不要下载最新版，因为 Ultimaker2Marlin 不能在最新版下编译成功）下载 1.6.10 版即可。
4. 下载 SDL （注意 SDL 即可，不需要 SDL2 ），点 [这里](https://www.libsdl.org/download-1.2.php)，并翻到最后 Development Library, 下载 [MingW32 对应的开发库](SDL-devel-1.2.15-mingw32.tar.gz)。

# 后续工作

很遗憾，没有时间把它写完，只好等用空的时候再写。