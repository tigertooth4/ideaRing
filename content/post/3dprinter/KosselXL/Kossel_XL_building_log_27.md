---
title: "Kossel XL 构建记 (27) ---- The frustrating stepper motors"
date: "2014-09-17 09:35:00"
tags: ["3DP", "Kossel", "Arduino","Bluetooth", "Wiring", "Frame","StepperMotor"]
draft: false
author: "tt4"
---

## 步进电机和 A4988

先从步进马达说起吧！这两天一直饱受困扰！我觉得我的接线方式没有问题，可是把步进马达接到 Ramps 板的无论 X,Y, 还是 Z 接口上，都电机很异常。开始的时候是一阵抖动，然后貌似还闻到了一些焦糊的味道-.- 电源风扇也在狂转，好像是在输出很大的功率一样！看情况不妙，急忙关掉电源开关，之后无论怎么换接口，调整步进电机的线序，马达都不!会!转！

所以我花了一阵子来了解步进马达的基本知识： 在3D 打印机上面最常用的是 NEMA17 的两相四线 1.8 度步进的步进马达，所谓两相（2-phase），作为理科生，粗略的理解就是有两匝线圈吧！每匝都是电阻极小的铜导线，铜导线的两端引出的接线构成一对 (pairing)。 要检测哪两条线是一对，方法很简单，如果有万用表的话，可以测量一下任意两条线之间的电阻，电阻小的应该是一对；如果没有万用表也没关系，只需要把任意两条导线接在一起，根据电磁感应，如果两条导线接在一起的时候转动马达明显感到比以前费力的话，那么这两条线就是一对儿了。

关于电流和扭矩，我的理解是：电机标定的额定电流假设是 1.7A， 那么当输入电流接近额定电流时，应该能输出到最大扭矩，额定电压我也不知道有什么关系。如何知道当前输入给电机的电流是多少呢？在这个台湾朋友的[博客][1] 中有详细的解释，或者在创客基地的[博客][2] 中也有解释：基本上要测量 A4988 电机驱动芯片上的电压 V_ref，将万用表的两个针脚分别接在 A4988 的调压旋钮 和 A4988 的 GRD 针脚上。如果想调整电压，只要记住往顺时针方向旋转是增加电压就可以了，调节旋钮上有一个平的缺口，还是非常精确和灵敏的，转动的角度一般不超过360度，观察那个平的缺口的朝向，很容易判断出转动了多少。不过，最好还是去看 Pololu 的 A4988 [产品页][3]啦! 看到产品页上的电路图，我好像明白为什么了，我可能把1A-1B-2B-2A 的意义理解错了。也许 A 和 B 应该是一对的才对(额，等等，还要观察 Ramps 板子上的走线来确定是否是这样)。

![][img-1]

仔细看了 Pololu 的产品页，发现还有一种 [DRV8825][4] 驱动芯片，提供 1/32 的分度和更大的电流，某宝也有销售（比 A4988 略贵).

![][img-2]


根据产品页上的说明，在16分步时电机通过的电流有下面的计算公式：

```mathjax
I = V_{\text{ref}} \times 2.5 \times 0.7.
```
其中 V_ref 是 A4988 芯片上测得的电压， I 是电机通过的电流. 因此，对于我所使用的电机来说，由于相电流为 1.7A，所以16分步时要把电压设在 1V 左右即可。


## 步进马达的测试

在 Reprap Wiki 上面有测试步进电机的代码：


```c++:n
#define X_STEP_PIN         54
#define X_DIR_PIN          55
#define X_ENABLE_PIN       38
#define X_MIN_PIN           3
#define X_MAX_PIN           2

#define Y_STEP_PIN         60
#define Y_DIR_PIN          61
#define Y_ENABLE_PIN       56
#define Y_MIN_PIN          14
#define Y_MAX_PIN          15

#define Z_STEP_PIN         46
#define Z_DIR_PIN          48
#define Z_ENABLE_PIN       62
#define Z_MIN_PIN          18
#define Z_MAX_PIN          19

#define E_STEP_PIN         26
#define E_DIR_PIN          28
#define E_ENABLE_PIN       24

#define Q_STEP_PIN         36
#define Q_DIR_PIN          34
#define Q_ENABLE_PIN       30

#define SDPOWER            -1
#define SDSS               53
#define LED_PIN            13

#define FAN_PIN            9

#define PS_ON_PIN          12
#define KILL_PIN           -1

#define HEATER_0_PIN       10
#define HEATER_1_PIN       8
#define TEMP_0_PIN          13   // ANALOG NUMBERING
#define TEMP_1_PIN          14   // ANALOG NUMBERING

void setup() {
  pinMode(FAN_PIN , OUTPUT);
  pinMode(HEATER_0_PIN , OUTPUT);
  pinMode(HEATER_1_PIN , OUTPUT);
  pinMode(LED_PIN  , OUTPUT);

  pinMode(X_STEP_PIN  , OUTPUT);
  pinMode(X_DIR_PIN    , OUTPUT);
  pinMode(X_ENABLE_PIN    , OUTPUT);

  pinMode(Y_STEP_PIN  , OUTPUT);
  pinMode(Y_DIR_PIN    , OUTPUT);
  pinMode(Y_ENABLE_PIN    , OUTPUT);

  pinMode(Z_STEP_PIN  , OUTPUT);
  pinMode(Z_DIR_PIN    , OUTPUT);
  pinMode(Z_ENABLE_PIN    , OUTPUT);

  pinMode(E_STEP_PIN  , OUTPUT);
  pinMode(E_DIR_PIN    , OUTPUT);
  pinMode(E_ENABLE_PIN    , OUTPUT);

  pinMode(Q_STEP_PIN  , OUTPUT);
  pinMode(Q_DIR_PIN    , OUTPUT);
  pinMode(Q_ENABLE_PIN    , OUTPUT);

   digitalWrite(X_ENABLE_PIN    , LOW);
    digitalWrite(Y_ENABLE_PIN    , LOW);
    digitalWrite(Z_ENABLE_PIN    , LOW);
    digitalWrite(E_ENABLE_PIN    , LOW);
    digitalWrite(Q_ENABLE_PIN    , LOW);
}





void loop () {

  if (millis() %1000 <500)
    digitalWrite(LED_PIN, HIGH);
  else
   digitalWrite(LED_PIN, LOW);

  if (millis() %1000 <300) {
    digitalWrite(HEATER_0_PIN, HIGH);
    digitalWrite(HEATER_1_PIN, LOW);
    digitalWrite(FAN_PIN, LOW);
  } else if (millis() %1000 <600) {
    digitalWrite(HEATER_0_PIN, LOW);
    digitalWrite(HEATER_1_PIN, HIGH);
    digitalWrite(FAN_PIN, LOW);
  } else  {
    digitalWrite(HEATER_0_PIN, LOW);
    digitalWrite(HEATER_1_PIN, LOW);
    digitalWrite(FAN_PIN, HIGH);
  }

  if (millis() %10000 <5000) {
    digitalWrite(X_DIR_PIN    , HIGH);
    digitalWrite(Y_DIR_PIN    , HIGH);
    digitalWrite(Z_DIR_PIN    , HIGH);
    digitalWrite(E_DIR_PIN    , HIGH);
    digitalWrite(Q_DIR_PIN    , HIGH);
  }
  else {
    digitalWrite(X_DIR_PIN    , LOW);
    digitalWrite(Y_DIR_PIN    , LOW);
    digitalWrite(Z_DIR_PIN    , LOW);
    digitalWrite(E_DIR_PIN    , LOW);
    digitalWrite(Q_DIR_PIN    , LOW);
  }


    digitalWrite(X_STEP_PIN    , HIGH);
    digitalWrite(Y_STEP_PIN    , HIGH);
    digitalWrite(Z_STEP_PIN    , HIGH);
    digitalWrite(E_STEP_PIN    , HIGH);
    digitalWrite(Q_STEP_PIN    , HIGH);
  delay(1);

    digitalWrite(X_STEP_PIN    , LOW);
    digitalWrite(Y_STEP_PIN    , LOW);
    digitalWrite(Z_STEP_PIN    , LOW);
    digitalWrite(E_STEP_PIN    , LOW);
    digitalWrite(Q_STEP_PIN    , LOW);

}
```

----

【更新】 今天终于把线序问题搞清楚了，电机也能正确工作了！实际上正确的解法是不要管 Ramps 板子上的顺序，直接看上述 A4988 的原理图，图上一对的接线是挨在一起的，那么接的时候也是。这样就对了。现在还剩下计算驱动电流的问题，待有时间继续研究！现在到了研究 Marlin 的时候了！我发现，固件上传以后，电机仍然不能正常工作，好像是限位开关已经被触发了，还得研究一下，说不定得要连上 z-probe 的限位开关才可以用。




[1]:	http://diy3dprint.blogspot.tw/2013/11/4988.html
[2]:	http://flyway97.blog.163.com/blog/static/2220320412013111910433463/
[3]:	http://www.pololu.com/product/1182
[4]:	http://www.pololu.com/product/2133

[img-1]:	/3DP/_images/A4988.png
[img-2]:	/3DP/_images/DRV8825.png
