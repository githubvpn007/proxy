# proxy
proxy、proxy server、代理协议、代理服务器、代理协议说明、ss、ssr、v2ray、trojan、Clash 


<br/>

## 本项目不做VPN分享，如果您希望获得最佳的科学上网方案 [点击这里](https://github.com/githubvpn007/v2rayNvpn)  

<br/>

简介
----

现在最主流的科学上网技术有[clash/xary/SS/SSR/V2Ray/Trojan/Trojan-Go](#1)，至于其他的上网方式暂时不做讨论  


相信很多朋友都会有选择困难症，怎么才能让自己稳定快速的上外网呢？？  
每逢敏感期，都会处于失联状态，这种情况相信大家都不想出现，下面我们就对比下自建节点的常用方式及协议 

**通过下表对比：**  

|      项目名称        |         创建时间             |     支持协议             |       速度评分       |         推荐评分           |        推荐理由           |
|:---------------------:|:-------------------:|:---------------------:|:-------------------------: |:-----------------------: |:------------------------:|
|      Shadowsocks        |         2015年前             |     sock5             |       6       |         2           |        年份有点老，数据传输安全性不高      |
|      Shadowsocks-R      |         2016年前后             |     sock5+混淆协议       |      5       |         1      |     年份有点老，数据传输安全性不高    |
|      V2Ray      |        2019下半年             |     Blackhole <br/> Freedom <br/> HTTP <br/> MTProto <br/> Shadowsocks <br/> Socks <br/>VMess       |     1       |         4      |     V2ray比较成熟，自用1年半 支持的配套客户端是最多的，隐秘性良好 长期使用没有断过网    |
|      Trojan         |         2019年底             |     类似V2ray“WS+TLS”模式的精简版       |      2       |         3      |     相比V2ray，速度更快，更轻量级 相比trojan-go 比较老了，因此排名后面    |
|      Trojan-Go      |         2020年8月         |   类似V2ray“WS+TLS”模式的精简版    |    3    |      5    |   速度方面次于Xray、隐秘更强，客户端比较单一    |
|      [Xray](#!)      |         2020年11月         |   V2ray的升级版（包含V2ray所有协议） VLESS协议    |    4    |      5    |   Xray性能最好、速度更快，隐秘方面也是很不错 更新比较快，支持的客户端也多   |
|      Clash        |         2020 年末            |     支持SS/V2ray/Trojan协议         |       4       |         5           |        功能全面  性能好      |

<br/>



**什么是SS/SSR(最老)**  

SS 是 Shadowsocks 的缩写，中文名为影梭，是一种基于Socks5代理方式的加密传输协议，也可以指实现这个协议的各种开发包。Shadowsocks 仍然有不少国外社区成员在维护更新。后来贡献者Librehat也为Shadowsocks补上了一些数据混淆类特性，甚至增加了类似Tor的可插拔传输层功能。  

SSR 是 ShadowsocksR 的缩写，在Shadowsocks的基础上增加了一些数据混淆方式，修复了部分安全问题并提高QoS优先级。  

目前而两个用的人已经比较少了。

<br/>


**什么是V2RAY(使用最多)**  

V2Ray 是在Shadowsocks 被封杀之后，为了表示抗议而开发的，属于后起之秀，功能更加强大，为抗GFW封锁而生。V2Ray 现在已经是 Project V 项目的核心工具，而 Project V 是一个平台，其中也包括支持 Shadowsocks 协议。由于 V2Ray 早于 Project V 项目，而且名声更大，所以我们习惯称 Project V 项目为 V2Ray，所以我们平时所说的 V2Ray 其实就是 Project V  这个平台，也就是一个工具集。其中，只有 VMess协议是V2Ray社区原创的专属加密通讯协议，被广泛应用于梯子软件。  

V2Ray目前支持以下协议（截止到2019年12月）：  

- Blackhole：中文名称“黑洞”，是一个出站数据协议，它会阻碍所有数据的出站，配合路由（Routing）一起使用，可以达到禁止访问某些网站的效果。  
- Dokodemo-door：中文名称“任意门”，是一个入站数据协议，它可以监听一个本地端口，并把所有进入此端口的数据发送至指定服务器的一个端口，从而达到端口映射的效果。  
- Freedom：是一个出站协议，可以用来向任意网络发送（正常的） TCP 或 UDP 数据。  
- HTTP：超文本传输协议，是传统的代理协议  
- MTProto：Telegram 的开发团队开发的专用协议，是一个 Telegram 专用的代理协议。在 V2Ray 中可使用一组入站出站代理来完成 Telegram 数据的代理任务。目前只支持转发到 Telegram 的 IPv4 地址。
- Shadowsocks：最早被个人开发的科学上网梯子协议，但 V2Ray 目前不支持 ShadowsocksR。  
- Socks：标准 Socks 协议实现，兼容 Socks 4、Socks 4a 和 Socks 5，也是传统的代理协议。
- 是V2Ray 专用的加密传输协议，它分为入站和出站两部分，通常作为 V2Ray 客户端和服务器之间的桥梁。因为增加了混淆和加密，据说比 Shadowsocks 更安全。现在的机场支持 V2Ray，一般是指支持 VMess 协议。VMess 依赖于系统时间，请确保使用 V2Ray 的系统 UTC 时间误差在 90 秒之内，时区无关。在 Linux 系统中可以安装ntp服务来自动同步系统时间。  


截止到2019年12月，V2Ray 可选的传输层配置有：TCP、mKCP、WebSocket、HTTP/2、DomainSocket、QUIC。其中，mKCP、QUIC和TCP用于优化网络质量；WebSocket用于伪装；HTTP/2和DomainSocket用于传输以及TLS加密。

V2Ray不仅可以在传输层配置 TLS 使 HTTP 和 SOCKS 变成 HTTPS 和 SOCKS over TLS 协议，也可以使MTProto、Shadowsocks 和 VMess 通过传输层配置TLS加密伪装成 TLS 流量。所以，VMess 配置 TLS 加密是最常见的做法，但没人会对 Shadowsocks 使用 TLS 加密，因为这完全没意义。 


<br/> 

**什么是Xray(目前最快，最稳的方式)**  

Xray与V2Ray完全类同，Xray 是 Project X 项目的核心模块。因为Xray和XTLS黑科技的作者rprx曾经是V2fly社区的重要成员，所以Xray直接Fork全部V2Ray的功能，然后进行性能优化，并增加了新功能，使Xray在功能上成为了V2Ray的超集，且完全兼容V2Ray。

简而言之，Xray是V2Ray的项目分支，Xray是V2Ray的超集，就跟Trojan-Go和Trojan-GFW的关系类似，而且Xray性能更好、速度更快，更新迭代也更频繁。由于自V2ray-core 4.33.0 版本起，删除了XTLS黑科技，但仍然支持VLESS，所以是否原生支持XTLS是Xray和V2Ray最大的区别之一。  

<br/> 


**什么是Trojan、Trojan-Go**  

Trojan，原来多是指特洛伊木马，是一种计算机病毒程序。但是，我们今天所说的Trojan是一种新的科学上网技术，全称为Trojan-GFW，是目前最成功的科学上网伪装技术之一。你可以认为Trojan是V2Ray的“WS+TLS”模式的精简版，速度比V2Ray更快，伪装比V2Ray更逼真，更难以被GFW识别。  

Trojan工作原理：Trojan通过监听443端口，模仿互联网上最常见的 HTTPS 协议，把合法的Trojan代理数据伪装成正常的 HTTPS 通信，并真正地完整完成的TLS 握手，以诱骗GFW认为它就是 HTTPS，从而不被识别。Trojan处理来自外界的 HTTPS 请求，如果是合法的，那么为该请求提供服务，否则将该流量转交给Caddy、Nginx等 web 服务器，由 Caddy、Nginx 等为其提供网页访问服务。基于整个交互过程，这样能让你的VPS更像一个正常的web服务器，因为Trojan的所有行为均与 Caddy、Nginx等 web 服务器一致，并没有引入额外特征，从而达到难以识别的效果。  


**什么是Clash**  

Clash是一个跨平台、支持SS/V2ray/Trojan协议、基于规则的网络代理软件，功能强大、界面美观、支持订阅，尤其适合机场和付费服务使用。Clash功能全加颜值好看，使得Clash深受喜爱，有一大批死忠粉。


<br/>

总结
---
Shadowsocks/Shadowsocks-R/V2Ray/Trojan/Trojan-Go/Clash  是一个项目，也可以理解是一种协议。有的项目官方已经开发了对应的软件支持，有的项目软件支持比较差。  
也有一些软件已经支持多种协议。比如：v2rayN.exe  是v2ray项目的支持软件，但是现在v2rayN.exe 也支持Trojan的协议了

## [如果你想下载对应的工具请点击这里](https://github.com/githubvpn007/v2rayNvpn#%E5%B7%A5%E5%85%B7%E4%B8%8B%E8%BD%BD)
