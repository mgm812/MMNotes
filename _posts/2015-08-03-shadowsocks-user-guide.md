---

layout:     post
title:      shadowsocks使用指南
category:   network
tag:        gfw

---

![shadowsocks]({{ site.baseurl}}/assets/2015-08-03-shadowsocks01.jpg)

### 购买指南

shadowsocks是一款通过代理来实现翻墙的服务，类似GoAgent；价格比较低廉1年的费用为99元RMB。可以前往[shadowsocks官网](https://shadowsocks.com/)购买，支持支付宝付款。

### Mac平台安装配置指南

首先下载安装[ShadowsocksX](https://github.com/shadowsocks/shadowsocks-iOS/wiki/Shadowsocks-for-OSX-Help)，然后打开`ShadowsocksX`导入配置。因为`ShadowsocksX`没有自动导入功能，所以需要手动导入，稍微有点麻烦。但`ShadowsocksX`提供`Scan QR Code from Screen`的功能，可以通过扫描屏幕中得二维码来导入配置。

### 通过ShadowsocksX上网

#### 浏览器和其他软件上网

打开ShadowsocksX，chrome浏览器如果使用了`Proxy SwitchySharp`，需要禁用，其他无需设置。

ShadowsocksX有`Auto Proxy Mode`和`Global Mode`两种模式，第一种模式是根据gfw列表来选择性的翻墙，第二种模式是全局模式，所有的请求都会走代理翻墙。

#### Terminal里设置代理翻墙

Shadowsocks官方提供了一种[方案](https://github.com/shadowsocks/shadowsocks/wiki/Using-Shadowsocks-with-Command-Line-Tools)。

首先，开启`ShadowsocksX`。本地端口运行在127.0.0.1:1080。

在Mac上安装`proxychains`：

~~~bash
brew install proxychains-ng
~~~

在`~/.proxychains/proxychains.conf`创建一个配置文件，内容如下：

~~~
strict_chain
proxy_dns 
remote_dns_subnet 224
tcp_read_time_out 15000
tcp_connect_time_out 8000
localnet 127.0.0.0/255.0.0.0
quiet_mode

[ProxyList]
socks5  127.0.0.1 1080
~~~

然后运行Terminal里运行命令`proxychains`，例如：

~~~
proxychains4 curl https://www.twitter.com/
proxychains4 git push origin master
~~~

或者代理bash：

~~~
proxychains4 bash
curl https://www.twitter.com/
git push origin master
~~~

有些命令自带设置socks代理的技能，就不必使用`proxychains`了，例如：

~~~
ALL_PROXY=socks5://127.0.0.1:1080 brew install git
curl www.google.com --socks5 127.0.0.1:1080
~~~
