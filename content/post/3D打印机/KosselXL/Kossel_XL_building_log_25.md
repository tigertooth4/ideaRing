---
title: "Kossel XL 构建记 (25) Fans on Arduino Board"
date: "2014-09-12 12:15:00"
tags: ["3DP", "Kossel", "Arduino","Mega","Electronics","Assembly"]
draft: false
author: "tt4"
---


我错了，原来Arduino 和 Ramps 合体时，Arduino 上的圆形 12V 输入不是接电源的正确位置（以前 Rostock
Mini 用这个位置插外接电源，是因为又加了一根连线，将 Arduino 上的电流引到了 Ramps 上来。）所以，正确的
做法应该使用 Ramps 上的 12V 电源接口供电，这样 Auduino 通过与 Ramps 的排线连接，获得电力。

目前我要确定，整个系统需要多少台风扇。看起来，挤出头部分需要两台 25x25 的（一台吹挤出头，另一台吹打印
件），电源部分需要1\~3台 40x40 的，电路部分需要两台 40x40 的散热，所以应该是 5\~7台。
