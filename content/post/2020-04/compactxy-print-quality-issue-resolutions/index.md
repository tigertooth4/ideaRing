---
title: CompactXY 打印质量问题溯源
date: '2020-04-02T23:43:00+08:00'
draft: true
tags: ["3DP", "compactxy","DIY","make"]

---

你们可能知道，CompactXY 是我对 DICE 3D 打印机的一个更新版本（fork)。制作的初衷是为了能在不增加打印机本身体积的情况下，尽量增加可打印的体积。为了实现这个目的，我基本上把 DICE 原本的设计重新实现了一遍。从17年开始，花费了 3年多的时间，最终制作出了一台 CompactXY。 

可能的问题线索

1. TMC2130 驱动散热不够
2. 老旧的喷嘴、喉管、PTFE
3. OrangePi 散热不够
4. OctoPrint USB 数据传输问题
5. OctoPrint 本身问题