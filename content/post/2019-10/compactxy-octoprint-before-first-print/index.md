---
title: 多灾多难的 CompactXY 终于快迎来第一次打印了
date: '2019-10-05T22:15:00+08:00'
draft: false
tags: ["CompactXY", "Marlin2.0", "OctoPrint"]
---

本以为 CompactXY 所有问题都基本搞定了，没想到 Marlin2.0 还是让我们掉到了坑里，这次是因为 load/unload filament，OctoPrint 中的 change filament 插件并没有按照我所预想的方式工作，unload filament 时一切正常，但 load filament 只能让耗材前进几厘米. 原以为是固件中关于 change filament 部分的设置不太对，于是我想还是先升级一下固件看看. 

所以就产生了另一个问题：机器已经全部安装好了，外部并没有留 usb 接口，如何给机器刷新固件呢？灵机一动，想到 OctoPrint 也许有插件能够完成此事，查询之后发现，还真有固件更新的插件，可是它要输入固件所在的路径，这怎么写呢？原以为这是固件在电脑上存储的目录，实际上应该是固件想要存储到的路径（固件应该是应该存储在主板的 sd 卡上），这块 sd 卡并不是运行 octoprint 的那块 sd 卡，octoprint 是安装在香橙派上的，而香橙派与主板通过 usb 线相连. 研究了一下，发现香橙派上的 armbian 系统可以 mount 主板上的那块 sd 卡，只需要先 ssh 到香橙派上，然后找到那块主板上的 sd 卡，并挂载，具体的过程如下

```bash
fdisk -l # list all mountable devices, let's say sd card may be called /dev/sda1
mkdir /mnt/SD # create a directory under /mnt 
mount -t vfat -o rw /dev/sda1 /mnt/SD
```

本以为这样应该没有问题了，可是谁知道将这个目录填写到到 octoprint 的固件更新插件里却发现这个目录不可写. 仔细想了想，发现 octoprint 账户并不是直接使用的 armbian 的 root 账户，所以上述操作实际上只适合 root 账户，并没有给 octoprint 账户写入的权限，既然问题找到了，改如何解决呢？

又经过一番搜索后，我找到了答案：

```bash
mount -t vfat -o rw,umask=000 /dev/sda1 /mnt/SD
```

就可以赋予任何用户读写的权限，这样做虽然有一定风险，但对我来说，已经是可以接受的答案了！当然，今后还可以考虑在 armbian 系统启动时自动加载这块 sd 卡，但就现在来说，暂且不深究了！

成功刷新了固件后，发现 load filament 的问题仍然存在. 于是我查看了一下 marlin-bugfix 2.0 的源代码，我的版本比较老旧了，但我即使翻出较新的固件，也仍能发现 change filament 这部分简直太坑爹了. 首先，lcd 菜单上的 change filament 基本上是废柴；其次，configuration_adv.h 中明明可以设置载入耗材时的加速度，但在执行时，却根本没有地方使用过这个加速度的参数. 难怪 load filament 会这么诡异. 

顺便说说 marlin 在处理更换耗材这件任务时的过程，首先 retract 一点点距离，然后 park nozzle 到指定的 x y z 处，unload filament ( 这里没有加速度，只有预设的速度 (feedrate) 会起作用.)，之后便是加热喷嘴；然后停住等待用户按键后插入耗材然后 load 指定的长度（这一步在 lcd 上进行操作时无效）最后会 purge 掉一些耗材（从喷嘴流出来）直到用户按停止为止.

本来这个过程大体是没问题的，但无奈 lcd 菜单系统并不完善. 那么该如何解决呢？之后我发现，更换耗材的 G-Code M600 可以跟许多参数，这些参数可以明确的指定退出/导入耗材时应该使用的量. 经试验发现，使用命令直接更换耗材是没问题的. 这条 G-Code 命令为 

```
M600 L460 T0 U460; Lxxx代表导入的耗材长度，Uxxx 代表退出的耗材长度，T0 代表 0 号挤出机
```

但注意，使用之前要先将喷头加热到指定温度.

至此为止，最重要的问题解决了，也许明天就可以进行第一次打印试验了！