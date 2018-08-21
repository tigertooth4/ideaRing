---
title: "Kossel XL 构建记 (26) Wiring, Bluetooth and Power switch"
date: "2014-09-16 09:35:00"
tags: ["3DP", "Kossel", "Arduino","Bluetooth","Rocker", "Switch", "Wiring", "Frame"]
draft: false
author: "tt4"
---

## 返工
返工! 又是返工! 这次的原因是发现 LCD 模块和 Ramps 板子用排插连在一起以后，盒子中部的空间因为有铝框架穿过，显然不够走线的了，如图:

![][img-1] ![][img-2] ![][img-3]

而且，原先的设计在走线的问题上也需要大费周章，铝型材的凹槽本来是用来走线的，但是原先的设计还要利用这个凹槽去固定防滚架，布线的空间非常紧张。于是迫不得已，只好把原先保护盒的设计推翻重来。。。


所以，返工的时候我考虑了一下，决定用铝型材的侧边凹槽来固定防滚架把防滚架，留下顶部和底部的凹槽用来走线。这样防滚架的开槽方向就要彻底改变，而且还要把整个盒子的尺寸增加，防滚架也要向下再扩展2cm，为了让整个保护盒不显得很大，还要重新设计整个保护盒的外部轮廓。。。设计的工作量不小，看看我之前不小心搞砸的一幅图，你们就知道这工作量还是不小的 ;-)

![][img-4]

好在昨天下定决心用一天时间专门解决这件事情，终于画出了第二稿。现在正在打印中啦！

 ![][img-5]


## 电源开关
电源开关部分对于我这个几乎不懂电路的人来说也是个棘手的问题。在某宝上订购的船型电源开关（Rocker switch）和电源插座套件还内置了 LED 灯和保险丝 (Fuse)。若只有电源插座我还会接，但四样放在一起我就不知所措了。

![][img-6] ![][img-7]

不过，经过一番逻辑分析，渐渐明白了电流要走保险丝的，所以应该把保险丝连在火线上，事实上这部分在套件上已经连好了。所以，我只要把保险丝的另外一段当做火线(L)就可以了。除了火线之外，还有零线(N)，经 Twitter 上某君提示，用万用表量了一下各个接头间的电阻，发现 LED 开关模块的两个相邻接口间的电阻是随开关状态改变的，这应该就是开关的接口了！

然后剩下的接口，我参考了亚马逊上一位用户提供的连接图。

![][img-8]

可以看到，开关部分实际上有两组簧片，分别需要跨接在零线和火线上，然后零与火之间跨接（并联）了 LED 灯。

经过一番分析，脑海里终于出现了一副大致完整的电路图的样子。确认逻辑合理了之后，就动手连线了，最后的连线图是这样的：

![][img-9]

然后顺便画了个开关盒子，这个是必须的，我可不想看到裸露的簧片和铝框架之间有任何的接触 :-|

## 蓝牙
蓝牙部分也有点波折，自从上次捣鼓清楚了以后就没想着有朝一日会再来一次。所以，不但没有记录，连资料也没有整理清楚。好在资料还在 -\_-b 而且当时也留了一些照片。

蓝牙部分需要先设置蓝牙的波特率(Baudrate)。刚买来的蓝牙模块应该是在默认的9600波特率。而一般我们在 3D 打印机上会使用 115200 或者 250000 这两个频率通讯，不过我买的这个最常见的蓝牙模块似乎不支持 250000 通信，所以只好设成 115200.

要设置成 115200，首先得利用 AT 指令和蓝牙模块通讯。例如 AT 回车，会返回 OK。AT+VERSION 会返回蓝牙模块的版本号。AT+NAMExxx 会将蓝牙模块的名称设置为 xxx 等等。设置波特率的 AT 指令是 AT+BAUDx，其中 x 是频率对应的 16 进制码。见下表：

Hex | BAUD
----|------
1   | 1200 bps
2   | 2400 bps
3   | 4800 bps
4   | 9600 bps
5   | 19200 bps
6   | 38400 bps
7   | 57600 bps
8   | 115200 bps
9   | 230400 bps
A   | 460800 bps
B   | 921600 bps
C   | 1382400 bps


要想使用 AT 指令，首先要把蓝牙模块接在 Ramps 板子上，接线方式是：蓝牙模块的 5V 和 GRD 分别接在下图中的 5V 输出和接地线上，RX 和 TX 分别接在图示的针脚上。见下图：

![][img-10]

然后把下面这段代码上传到 arduino 上，通过 arduino 的 Serial Monitor （Mac 用户在 Arduino 程序中使用快捷键 Shift+⌘+M 唤出 Serial Monitor ;注意波特率在下拉菜单中，应设为9600） 输入 AT 指令，来控制蓝牙模块。如果输入没有响应，可以先把 RX 和 TX 的接线对调看看，如果还不奏效就要观察 mySerial 是否已打开了（例如下面代码中的第 23 和 32 行）。

```c++:n
# include <SoftwareSerial.h>

char myChar ;

SoftwareSerial mySerial(65, 66); // RX, TX

void setup()
{
	// Open serial communications and wait for port to open:

	Serial.begin(9600);

 	if (!Serial){
 		Serial.println("Not connected!") ;
  	}

	// set the data rate for the SoftwareSerial port
  	mySerial.begin(9600); // change it to 115200 if you already set the baud rate to 115200

	Serial.println("Welcome! XJ.");
	Serial.println("Type AT Commands:");
	if (mySerial.available())
		Serial.println("my Serial is alive!");

}


void loop() // run over and over
{
	if (mySerial.available()){
		Serial.write(mySerial.read());
		Serial.println("mySerial works fine!");
  	}
	if (Serial.available()){
 		delay(10);
		mySerial.write(Serial.read());
	}
}
```

建议先用 AT 指令修改蓝牙设备的名称，例如 AT+NAMEKosselXL 就不错;-) 然后再修改波特率到 115200，例如 AT+BUAD8，不要把顺序反过来（波特率改掉以后旧的通讯端口就失效了:|）


接下去，再把 Marlin 或 Repetier 固件写到 Arduino 板上（记得拔下蓝牙连线）。今后使用蓝牙通信时，接线应该如下图所示

![][img-10]

好了，现在可以打开电源，用电脑寻找 Bluetooth 设备了。BTW：pin = 1234.


[img-1]:	/3DP/_images/DSC00593.jpg
[img-2]:	/3DP/_images/DSC00596.jpg
[img-3]:	/3DP/_images/DSC00597.jpg
[img-4]:	/3DP/_images/complexity.png
[img-5]:	/3DP/_images/DSC00594.jpg
[img-6]:	/3DP/_images/IMG_1132.jpg
[img-7]:	/3DP/_images/IMG_1131.jpg
[img-8]:	/3DP/_images/amazon-customer.png
[img-9]:	/3DP/_images/DSC00583.jpg
[img-10]:	/3DP/_images/Arduinomega1-4bluetooth.png
[img-11]:	/3DP/_images/Arduinomega1-4bluetoothUse.png
