---
date: '2019-09-07T23:13:00+08:00'
draft: false
title: 如何给 OrangePi zero plus 增加热点功能
tags: ["OrangePi","Octoprint","hotspot","ssh","Marlin","WiFi"]
---

在之前的博文中，我介绍了如何在 OrangePi Zero plus 上安装 OctoPrint，以 OrangePi zero plus 的性能，运行 OctoPrint 还是绰绰有余的。可以通过 OctoPrint 完美控制打印机的各项功能。美中不足是，如果像我这样，把 OrangePi 安装到了打印机里面，那么当网络环境改变（比如带打印机外出），不方便连接网线的情况下，有没有事先登录过新环境的 WiFi的话，OctoPrint 几乎会变成废柴（因为无法从外部修改 OctoPrint 的设置，连接 WiFi 操纵打印机）。所以，这种情况下，最方便的还是让 OrangePi 自己变成一个热点。这样只需要用手机连接 OrangePi 的热点即可。

本文参考了[medium 用户 Kennethjiang 的文章]( https://medium.com/@kennethjiang/painless-wi-fi-for-octoprint-4e6b68005400)。

- 当然，如果事先知道陌生环境的 WiFi 账号密码，那只需要事先将新环境下的 WiFi 信息写入到 OrangePi 中即可。写入的办法是编辑 /etc/wpa_supplicant/wpa_supplicant.conf 文件 （sudo nano /etc/wpa_supplicant/wpa_supplicant.conf) 增加一组 network 的 SSID 和 psk 。

- 否则，那么就需要给 OrangePI 增加热点功能。当它搜索不到任何可用的 WiFi 时默认开启热点功能。

  要想这样做，我参考了上述链接。有如下几个步骤：

# 增加热点功能

1. 增加软件：

   ```powershell
   sudo apt-get update
   sudo apt-get install hostapd dnsmasq iw
   sudo systemctl disable hostapd dnsmasq
   ```

2. 配置 hostapd

   ```powershell
   sudo nano /etc/hostapd/hostapd.conf
   ```

   增加这样几行

   ```powershell
   interface=wlan0
   #driver=rtl871xdrv
   ssid=CompactXY-Hotspot
   hw_mode=g
   channel=6
   wmm_enabled=0
   macaddr_acl=0
   auth_algs=1
   ignore_broadcast_ssid=0
   wpa=2
   wpa_passphrase=1234567890
   wpa_key_mgmt=WPA-PSK
   wpa_pairwise=TKIP
   rsn_pairwise=CCMP
   ```

   保存文件后，

   ```powershell
   sudo nano /etc/default/hostapd
   ```

   将 `#DAEMON_CONF="/etc/hostapd.conf"` 改成 `DAEMON_CONF="/etc/hostapd/hostapd.conf"`

3. `$ sudo nano /etc/dnsmasq.conf` 将如下几行加到文件的末尾

   ```powershell
   #OctoHotspot Config
   
   #stop DNSmasq from using resolv.conf
   
   no-resolv
   
   #Interface to use
   
   interface=wlan0
   bind-interfaces
   dhcp-range=10.0.0.3,10.0.0.20,12h
   ```

4. `$ sudo nano /etc/network/interfaces` 将 wlan0 的 wpa-conf 语句注释掉

5. 增加一个脚本，当找不到合适的 WiFi 连接时启动热点

   ```powershell
   sudo nano /usr/bin/autohotspot
   ```

   copy-paste 如下代码

   ```powershell
   #!/bin/bash
   #
   createAdHocNetwork()
   {
       ip link set dev wlan0 down
       ip a add 10.0.0.5/24 dev wlan0
       ip link set dev wlan0 up
       systemctl start dnsmasq
       systemctl start hostapd
   }
   connected=false
   while read ssid
   do
       if iw dev wlan0 scan ap-force | grep $ssid > /dev/null
       then
           wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf > /dev/null 2>&1
           if dhclient -1 wlan0 && iwconfig wlan0 | grep $ssid > /dev/null
           then
               connected=true
               break
           else
               wpa_cli terminate
               break
           fi
       else
           echo "Not in range, WiFi with SSID:" $ssid
       fi
   done <<< "$(grep -i '^[^#].*ssid=' /etc/wpa_supplicant/wpa_supplicant.conf | sed -n 's/.*ssid="*\([^"]*\)"*/\1/ip')"
   if ! $connected; then
       createAdHocNetwork
   fi
   ```

   

   增加一项服务，并将下面的代码写入到 `autohotspot.service` 文件中

   ```powershell
   sudo nano /etc/systemd/system/autohotspot.service
   ```

   ```powershell
   [Unit]
   Description=Generates a non-internet Hotspot for ssh when no wifi network is in range.
   After=network-online.target
   [Service]
   Type=oneshot
   RemainAfterExit=yes
   ExecStart=/usr/bin/autohotspot
   [Install]
   WantedBy=multi-user.target
   ```

   激活服务使得在它启动的时候可以运行

   ```powershell
   sudo chmod +x /usr/bin/autohotspot
   sudo systemctl enable autohotspot.service
   ```

6. 下一次在启动 Octoprint 的时候如果找不到任何 WiFi，可以打开电脑寻找名为 CompactXY-Hotspot 的热点，密码为 1234567890，连上以后，Octoprint 的地址为 http://10.0.0.5/。

# 测试

今天启动机器发现，无论如何设置，OrangePi 都只会连接热点，不会连接 WiFi，并且 IP 地址是 169.254.7.49。初步判断是自动连接的脚本出了问题。待今后有时间我要做进一步的分析。

# 更新

也许应该参考这篇[文章](http://www.raspberryconnect.com/projects/65-raspberrypi-hotspot-accesspoints/158-raspberry-pi-auto-wifi-hotspot-switch-direct-connection) 。

