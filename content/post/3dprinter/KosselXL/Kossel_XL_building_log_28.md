---
title: "Kossel XL 构建记 (28) ---- The GCode Magic"
date: "2014-09-17 09:35:00"
tags: ["3DP", "Kossel", "Arduino","EndSwitch", "Wiring", "GCode","StepperMotor"]
draft: false
author: "tt4"
---
昨晚唯一成功解决的，就是电机的运转问题。在电机测试代码下，电机终于可以正常运转了！GCode 真是个神奇的东西，在 Pronterface 下，按钮几乎是个废柴，但是 GCode 却能让人看清楚系统的运转情况！比如，想要知道Endstop 是否工作正常，在 Marlin 的情况下，可以直接发送 M119。
