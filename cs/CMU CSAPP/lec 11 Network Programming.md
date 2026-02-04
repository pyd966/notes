## The Client-Server Programming Model

我们把网络连接抽象成这样的模型：有一个 server 和一个 client， client 向 server 发送请求，server 通过一些内部运算之后，返回给 client 一个 response，之后等待 client 的下一个请求。

这样的模型在大多场景都是适用的。然而我们注意到模型中双方地位的不平等性，因此在绝对地位平等的场景中（端到端双向通信），我们的模型需要微调一下。

在网络的语境中，sever 和 client 都是 process 而非机器。机器被称作 hosts，一个 host 上可以同时运行很多 server 和 client，甚至于一对 server-client 可以在同一个 host 上运行。

## Networks

对 host 而言， network adaptor 就像是一个普通的 IO 设备。

组建一个网络，最简单的方法是用线直接把 host 连接起来。

如果我们想实现一个计算机组内的任意双方通讯，更经济一点的办法是设置一个“中转站”，所有信息先发给中转站，再由中转站转发。这就需要在真正的信息外附加上一些额外的信息，这些额外的信息遵守 protocol 规范。

这个中转站可以是 hub，它的功能是把从任意一方收到的消息发送给连接到 hub 上的所有 hosts。

也可以是 bridge，它可以把很多 hub 组建在一起，在发送的过程中不断学习，最终知道发送到某个特定 host 的信息该发给哪个 hub。

组建起来的网络叫做 LAN，因为通常而言这样的网络覆盖的地理范围小。

不同的 LAN 可以通过 router 连接起来，组成更大的网络，称为 WAN。

因为不同的 LAN 之间可能完全不兼容，使用截然不同的 protocol（比如，WiFi 和以太网连接），所以 router 还有一个任务：把 LAN1 发过来的 package 里的头删掉，加上 LAN2 的头再发给 LAN2.

## The Global IP Internet

在网络通信中，有非常多协议。

其中最重要的便是 TCP/IP 协议。事实上这是一套协议而非一个协议，包括：

- IP 协议，规定了如何确定网络中 host 的名称（IP 地址），提供最基础的 host-to-host 发送信息功能。
- UDP 协议，建立在 IP 协议之上，提供基础的 process-to-process 发送信息功能。
- TCP 协议，建立在 IP 协议之上，提供双向、可靠（保证接收）的 process-to-process 功能。目前使用最多的协议。

### IP Address

IP 地址是 32bit 用来标识 host 的数字。需要注意的是在报文中 IP 地址需要以网络序（大端序）储存。

IPv4 中的 IP 地址是 32bit 的，这意味着只有几亿个地址，很难满足实际需要。在现实中，通常是一个 IP 对应一个局域网，通过发送给这个局域网的不同端口来确定发给不同设备。

IPv6 的 IP 地址是 128bit 的，等升级到 IPv6 就不需要担心 IP 地址不够的问题了。

### Domain Name

记 IP 很麻烦，所以有一套系统 DNS (Domain Name System) 提供了域名跟 IP 之间的映射。

域名跟 IP 并非一一对应的，事实上它们是多对多映射，即一组域名跟一组 IP 之间存在映射关系。

DNS 服务由分布在全球的一套服务器成层级地提供。当你发起 DNS 服务请求时，计算机会先从本地缓存中查找，找不到再去根服务器，由根服务器返回一级域名 DNS 服务器的地址，由一级 DNS 返回二级域名的 DNS 服务器地址，一步步找下去。

### Internet Connections

计算机上可能运行着很多需要联网的服务，如何区分一条到达 host 的信息该发给哪个服务来处理？这就需要 port。

port 就是一个仅存在于软件层面的数，你可以把它想象成插座。

socket 可以用 socket address (`address:port`) 标识，你可以把它想象成插头。插头插到某个插座里之后，从这个插座传入的信息就会流经插头交由对应的程序处理。

在应用层面，server 跟 client 是通过 connection 通信的。

connection 是 process-to-process 的，它的端点是 socket。每个 connection 都可以用二元组 `(cliaddr:cliport, servaddr:servport)` 唯一确定。

## The Sockets

很多系统都提供了统一的 sockets interface，也就是一系列函数，来帮助我们进行网络相关的编程。下面是我们会用到的一些函数。

![[Pasted image 20260203172007.png]]

因为这是 note 而不是 manual，所以提到下面的函数的时候只会简单说一下它是干什么的。

### socket addr

有必要多说一句。

不同的协议用来表示 socket addr 的结构体并不相同，而远古的 C 语言没有 `void *`，对那些需要接受 socket addr 作为参数的函数而言，这就造成了一个问题。

解决方案很精妙：每个协议的结构体都把 结构类型、ip、port 这几项放到最开头，后面再放协议特有的内容。这样我们传递参数的时候只需要对指针进行强制类型转换。
### socket

创建一个 socket，返回一个 file descriptor 表示这个 socket。

### connect

client 端使用，提供 clientfd 和目标 socket addr，给 clientfd 分配一个临时 port 并尝试与目标进行连接。

### bind

提供 socketfd, socket addr，把 socketfd 绑定到目标上。

### listen

socket 创建之后默认是 active 状态，意思是说这个 socket 是用于客户端的。

使用 listen 后，socket 就变成 listening 状态，可以被服务器使用。

### accept

提供一个 listenfd，函数进入等待状态，直到有客户端发来连接请求，返回客户端的 socket addr 和一个新的 socketfd，可以直接把这个 socketfd 当成普通文件来进行通信。

为什么要提供一个新的 socketfd 呢？

因为通常而言，在同一时间一个服务器要服务很多客户端。通过使用不同的 socketfd，服务器端可以跟不同的客户端通信。

实现这个功能还需要多线程技术。

### getaddrinfo

各种协议很讨厌，手动填写 socket addr 也很麻烦。

getaddrinfo 可以从域名和服务名，直接得到对应的 socket addr。还有一些别的功能。

getaddrinfo 返回一个链表，每一项都是一个 socket addr。

我们可以很方便地直接使用这些 socket addr，而无需担心协议的问题。

### getnameinfo

基本上是 getaddrinfo 的反函数。

## Web

服务器可能提供很多服务，其中最常用的一种就是 web 服务。

web 服务说起来很简单，browser 拿着一个 URL 向服务器请求，服务器给出相应的响应，browser 把内容渲染显示出来。

常用的协议是 HTTP 协议。古老的 HTTP 协议一次只支持获得一个文件，随后连接关闭。新版的支持持久连接。

让 web 服务跟 ftp 服务不同的是 HTML (hypertext markup language)，本质上仍然是纯文本，只不过 browser 知道如何解析它。

HTTP 是通过类似文件读写的方法传递信息的，为了传送除了文本以外的内容，我们需要一套办法标识传递的各个部分分别表示什么类型的文件。这套标识系统是 MIME (multipurpose internet mail extensions)，使用原始的纯文本方法标记类型。

HTTP 请求内容是通过 URL 实现的，请求的文件可以分为静态 (static) 和动态 (dynamic) 两类。静态文件就是一个文件，动态文件是执行一个程序，把它的输出扔给客户端。URL 的第一个 `/` 并不表示目标机器的根目录，事实上目标机器技术上可以把任意目录解析到任意文件。URL 中的 `?` 后面包含一些参数，这些参数会作为动态文件执行的环境变量传递过去。

