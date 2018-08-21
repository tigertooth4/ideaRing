---
title: "自己建了一个SS"
date: "2015-10-03 12:15:00"
draft: false
tags: ["SS","VPN"]
author: "tt4"
---

趁着国庆假期，终于有时间把SS搞好了。自从上次qiang变高以后，就萌生了自己建站的念头。没有选择 Linode 的主机，因为树大招风嘛。选择了同样来自日本的 Conoha.jp 。选择了 50G SSD 和 1G 内存的日本主机，搭配 CentOS 7 操作系统。
整个建立虚拟主机的过程都比较顺利，付出了一个月 900 日元的代价。具体过程就不再赘述了。
下面主要说说建立 SS 的过程。我用的是 SS 的 Python 版。
# 安装SS
分两步，先安装 python 和 包管理工具 pip，再直接安装 ss，至于 ss 是什么，你懂的 ：）今后遇到 ss 的地方，请用你知道的单词代替（如果不明确指出，全用小写）。

首先连接到 conoha 的 VPS 服务器，使用 usr@ip 的方式
```sh
ssh root@VPS_IP
```
```sh
yum install python-setuptools && easy_install pip
pip install ss
```
安装到这一步的时候出现了 InsecurePlatformWarning 的警告，不知所措，google 了一下以后开始有病乱投医：
```sh
pip install pyopenssl ndg-httpsclient pyasn1
pip install libffi
pip install requests==2.5.3
pip install ss (这一步说 requirement already satisfied！)
```
# 建立 ss 配置文件
```sh
mkdir -p /etc/ss
vim /etc/ss/config.json
```
在 config.json 中输入以下内容：
```sh
{
 "server":"Conoha 的 server ip",
 "server_port":（端口，可以自己定义）,
 "local_address": "127.0.0.1",
 "local_port":1080,
 "password":"（你的连接密码）",
 "timeout":300,
 "method":"aes-256-cfb",
 "fast_open": false,
 "workers": 1
}
```
# 新建服务文件
```sh
vim /etc/systemd/system/ss-server.service
```
输入以下内容
```sh
[Unit]
Description=Ss Server
After=network.target

[Service]
Type=forking
PIDFile=/run/ss/server.pid
PermissionsStartOnly=true
ExecStartPre=/bin/mkdir -p /run/ss
ExecStartPre=/bin/chown root:root /run/ss
ExecStart=/usr/bin/ssserver (这里不替换) --pid-file /var/run/ss/server.pid -c /etc/ss/config.json -d start
Restart=on-abort
User=root
Group=root
UMask=0027

[Install]
WantedBy=multi-user.target
```
# 运行 ss 服务，设为开机自启动
```sh
systemctl start ss-server.service
systemctl enable ss-server.service
```
# 防火墙开启你指定的端口
```sh
firewall-cmd --permanent --add-port=指定端口/tcp
firewall-cmd --reload
```
# 如果要配置多用户，参考了 QQ 群中的代码
类似这样：
```sh
{
    "server":"0.0.0.0",
    "local_address":"127.0.0.1",
    "local_port":1080,
    "port_password":{
         "8989":"password0",
         "9001":"password1",
         "9002":"password2",
         "9003":"password3",
         "9004":"password4"
    },
    "timeout":300,
    "method":"chacha20",
    "fast_open": false
}
```

# 常见维护操作
升级 ss
```sh
pip install -U shadowsocks
```
卸载 ss
```sh
pip uninstall shadowsocks
```
停止 ss 服务
```sh
systemctl stop shadowsocks-server.service
```
# 让 Mail.app 复活
我用了 Proximac，但是，鉴于苹果在升级到 10.11 El Capitan 之后，不允许哪怕 root 用户修改 /usr，所以 homebrew 没办法用了。必须要先[修改权限](https://github.com/Homebrew/homebrew/blob/master/share/doc/homebrew/El_Capitan_and_Homebrew.md)。官方的解释请看[这里](https://developer.apple.com/videos/play/wwdc2015-706/)。
```sh
sudo chown $(whoami):admin /usr/local && sudo chown -R $(whoami):admin /usr/local
```
注意，要使 /usr/local/sbin 也在你的路径变量里面。因为我是用的 fish, 其环境变量是在 .config/fish/config.fish 里面设置。于是，添加这个路径可以这样写：
```sh
set PATH /usr/local/sbin $PATH
```
可以用  echo "$PATH" 来检查路径好了没。然后，我们来试试 homebrew 好了没。
[未完，待续...]
【更新】下面就是安装 proximac 了！我已经 fork 了[这个项目](https://github.com/tigertooth4/proximac)。根据作者的指导，第一步要安装 libuv 这个库。
```sh
brew install libuv
```
然后下载安装文件
```sh
curl -fsSL https://raw.githubusercontent.com/proximac-org/proximac-install/master/install.py |python
```
其实这一步就是从网上把写好的 zip 包下载下来，解压，改权限，放到 /usr/local/proximac 目录下面。最重要的就是 kext 内核扩展文件。运行 /usr/local/bin/proximac 的时候主要调用的是这个。但是，从 Mac OSX El Capitan 以后，系统引进了所谓 rootless 的特性，就是不再允许哪怕是 root 用户修改特定的系统文件（苹果这么做的原因可以参考[WWDC15的视频](https://developer.apple.com/videos/play/wwdc2015-706/)）

因此，如果想继续使用 proximac 只有一种办法，那就是禁用掉这个新特性，public beta 版本中的修改内核参数的方法在正式版中会失效，唯一的办法就是在启动的时候用 csrutil 这个工具:
1. 启动时按住 command+R 直到进入保护模式
2. 在保护模式中打开终端，输入如下指令 csrutil disable (注意：csrutil enable --without debug 这种写法将来恐怕也会失效，所以最好还是用 disable 这个选项）
3. 正常重启动
用了这招，proximac 就可以正常启动了！

![](~/屏幕快照 2015-10-05 上午12.25.28.png)


# 参考
- [IFshow（主要参考）](https://www.ifshow.com/centos-7-installation-and-configuration-shadowsocks/)
- [IFshow 优化](https://www.ifshow.com/centos-7-shadowsocks-optimization/)
- [史上最详细教程](http://shadowsocks.blogspot.jp/2015/01/shadowsocks.html)
- [破.前路的 CentOS7 libev 配置](http://hi-rain.com/2015/09/17/CentOS-7系统架设Shadowsocks-libev服务器/)
- [aa65535 的 gist](https://gist.github.com/aa65535/ea090063496b0d3a1748)
- [vfasky 的在 CentOS6 上部署（要用 iptables）](https://vfasky.com/2013-05-17/shadowsocks-centos6/)
- [teddysun 的一键安装脚本 libev 版](https://teddysun.com/357.html)
- [teddysun 的 python 版(含加密方式讨论)](https://teddysun.com/339.html)
- [CentOS 7 中使用的防火墙 firewalld 的使用说明](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/Security_Guide/sec-Using_Firewalls.html#sec-Introduction_to_firewalld)
- [Stackoverflow 中关于 InsecurePlatformWarning](http://stackoverflow.com/questions/29099404/ssl-insecureplatform-error-when-using-requests-package)
- [关于安装中的 InsecurePlatformWarning](http://urllib3.readthedocs.org/en/latest/security.html)
- [WWDC15](https://developer.apple.com/videos/play/wwdc2015-706/)
- [v2ex 上面的讨论](http://www.v2ex.com/tag/rootless)
- [Quora 上面的讨论](https://www.quora.com/How-do-I-turn-off-the-rootless-in-OS-X-El-Capitan-10-11)
- [Macworld 上面关于如何修改的讨论](http://www.macworld.com/article/2986118/security/how-to-modify-system-integrity-protection-in-el-capitan.html)
- [Apple 官方论坛上的讨论](https://forums.developer.apple.com/thread/3981)
