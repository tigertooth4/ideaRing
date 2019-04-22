---
date: '2018-09-04T15:54:33+08:00'
draft: false
title: 如何在 OrangePiZeroPlus 上安装 Octoprint
tags: ["3DP","OctoPrint","armbian","DIY"]
---


1.  下载 Armbian 镜像 Armbian.com

2.  将镜像刻录到 MicroSD 卡上（我使用了刻录工具 Etcher)；

3.  将 MicroSD 卡插到 OrangePi 上，并将 OrangePi 连接网线、电源；

4.  待 OrangePI 的指示灯亮起以后，可以在路由器的登录页面后寻找 OrangePI，确定 IP
    地址

5.  ssh 到 OrangePI：

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    ssh root@192.168.3.63 -p 22
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    初始密码是：1234

6.  OrangePI 会提示修改密码并且新建用户，赋予 sudo 权限等；

7.  在 root 用户下，查看 OrangePI 是否可以正常联网；若显示 ping: \*\*\*: Name of
    service not known，则需要编辑 /etc/network/interfaces 添加 dns-nameservers
    8.8.8.8 8.8.4.4;

8.  在 root 用户下，

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    apt-get update
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    apt-get upgrade
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

9.  在 root 下，有一个配置工具 nmtui-connect 可以连接 WiFi，还有 armbian-config
    可以设置静态或动态 IP

10. 在 root 下，

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    sudo adduser octoprint
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

11. 接下来

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    sudo usermod -a -G tty octoprint
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    sudo usermod -a -G dialout octoprint
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

12. 然后

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    sudo adduser octoprint sudo
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

13. sudo vimudo 将我们 octoprint 的 sudo 设置写入：在此文件的最后添加：octoprint
    ALL=(ALL) NOPASSWD:ALL，然后 ctrl-o 回车写入，ctrl-x 退出；

14. 嗯，然后 sudo passed octoprint -d 重置密码过期信息

15. 然后安装所需的 git，python 工具：

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
       sudo apt-get install git python-pip python-dev python-setuptools psmisc virtualenv
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

16. 切换到我们刚才创建的 octoprint 账号：sudo su octoprint

17. 切换到 octoprint 的家目录 cd \~

18. wget https://pypi.python.org/packages/source/p/pyserial/pyserial-2.7.tar.gz
    ，这一步我直接使用了

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    sudo pip install pyserial
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

19. 下一步，git OctoPrint:

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    git clone https://github.com/foosel/OctoPrint.git
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

20. 当克隆完成后，进入 OctoPrint 目录：cd OctoPrint，用虚拟环境变量命令：
    virtualenv venv；

21. 成功完成后

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    ./venv/bin/python setup.py install
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

22. 好了！现在可以启动一下 OctoPrint 看看：

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    ~/OctoPrint/venv/bin/octoprint serve
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

23. 稍等片刻，看到 listening… 的字样以后就可以打开浏览器，输入 orangepi 的 ip
    地址后面跟着 :5000 端口，然后就可以一步一步设置 OctoPrint 了；

24. 我在用户名栏里面输入了我的拼音缩写，然后输入了密码；

25. 下面我们要拷贝一些文件，以使得 octoprint 可以在开机的时候启动；我们首先
    ctrl+z 结束 octoprint

26. 接下来将 octoprint 服务拷贝到启动服务目录

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    sudo cp ~/OctoPrint/scripts/octoprint.init /etc/init.d/octoprint
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

27. 赋予可执行权限

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    sudo chmod +x /etc/init.d/octoprint
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

28. 然后

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    sudo cp ~/OctoPrint/scripts/octoprint.default /etc/default/octoprint
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

29. 接着

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    sudo vim /etc/default/octoprint
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

30. 将 OCTOPRINT_USER=pi 改为 =octoprint

31. 将 DAEMON=… 取消注释，并且改为
    DAEMON=/home/octoprint/OctoPrint/venv/bin/octoprint

32. 然后保存退出

33. 最后我们要 push 这些更新到 default:

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    sudo update-rc.d octoprint defaults
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

34. 然后 sudo service octoprint start

35. 注意到做完这一套流程以后，octoprint
    的无线网络好像失效了，于是我们要采取下面的补救措施：

    1.  运行

        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
        sudo iwlist wlan0 scanning | grep ESSID
        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

        看到你网络里面所有的路由器名称

    2.  下一步，注意引号要使用英文的引号

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
         wpa_passphrase “你的 WiFi 名称” “你的 WiFi 密码” | sudo tee -a /etc/wpa_supplicant/wpa_supplicant.conf
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    这个会在你的 wpa_supplicant.conf 里面加上一段话类似于 network={ ssid=“…”
    \#psk=“”….}，把这里面的 \#psk 变成 psk 然后保存文件

    1.  在 /etc/network/interfaces 这个文件里面加上

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
        auto lo

        iface lo inet loopback
        iface eth0 inet dhcp

        allow-hotplug wlan0
        auto wlan0


        iface wlan0 inet dhcp
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

        然后重新启动 sudo reboot
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1.  而且，域名识别好像也没有启用（注意：更改域名的话要改 /etc/hostname 和
    /etc/hosts 两个文件里的域名，初识时为 orangepizeroplus，可以改为
    “你喜欢的任何名字”)

2.  然后：

    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
        sudo apt-get install avahi-daemon
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    这个的用处是在局域网里面广播域名，然后你就可以用
    “你喜欢的任何名字”.local:5000 去访问 octoprint 了！