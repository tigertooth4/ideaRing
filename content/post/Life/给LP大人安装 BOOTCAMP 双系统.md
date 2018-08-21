---
title: "给LP大人安装 Bootcamp 双系统 "
date: "2018-05-01 16:14:00"
draft: false
author: "tt4"
---



如何安装 BOOTCAMP
=================

 

High Sierra 中的 BOOTCAMP 无法将超过 4G 的文件拷贝到 USB 中的 FAT
分区。所以必须要手动制作 Windows 启动盘了。这时候下载到一个合适的 ISO
文件就很重要了！可以下载我的百度网盘里面的 「重回井冈山.iso」。然后可以用
unetbootin 这款免费程序将 iso 镜像拷贝到优盘上。注意：优盘必须格式化为 FAT
格式，然后有主引导扇区。哦对了，最后还要把 Macbook Pro
需要的驱动文件也拷贝到优盘上（这些文件可以在苹果官网上面找到）。

 

然后在 Disk Utilities 中设定分区，开辟出一个 exFAT 的分区给 Windows（最好不要和
MacOS 的分区设成同样大小哦，否则安装的时候容易误操作哦）。

 

然后，重启电脑，按住 Option
键直到出现选择启动项。然后就照着屏幕上说的去做就好了。安装 Windows
完成后，别忘了安装 BOOTCAMP 需要的文件。

 

☺️

 

 
