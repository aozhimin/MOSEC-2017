# MOSEC-2017

<p align="center">

<img src="Images/banner.jpg" alt="MOSEC" title="MOSEC"/>

</p>

第三届MOSEC移动安全技术峰会之旅

MOSEC 到2017年已经举办了三届，不过这一届的议题盘古团队没有参加。

## 致辞

这次 MOSEC 的主持人是王铁磊，关注 iOS 越狱领域的读者对他应该都不会陌生，他是盘古团队的首席科学家，还是上海犇众信息技术有限公司的联合创始人，多次在Blackhat、CanSecWest、PoC、XCon等业界安全峰会报告。

### 360
接下来是360的首席安全官谭晓生发言，介绍安全会议，办成精品会议，干货满满，希望与会嘉宾有所收获，网络安全火爆，也遇到很大的挑战，安全首先是要为业务服务，会遇到业务发展和安全的一个权衡。网络安全市场不到400亿，启明星辰20亿，不是一个爆发暴富的行业，沉浸在安全技术方向，网络安全攻防失衡，一家公司一个团队没有办法解决网络安全遇到的问题。

## Android应用签名的枷锁与革新

百度安全实验室，百度首席安全 Android 签名的痛，苦和未来，


### QA

百度以前签名是交由各产线管理，现在准备收回安全管理部门通过 **OASP** 平台进行管理。

## 现代iOS系统溢出缓解机制

<p align="center">

<img src="Images/luca.jpg" />

</p>

第二场议题是由年仅20岁的意大利天才黑客，Yalu 的作者 Luca Todesco 带来的现代iOS系统溢出缓解机制。

开场 Luca 简单介绍了自己，喜欢做安全研究相关的工作，在几个公开的 iOS 越狱工具都做了贡献，闲暇时间私下会越狱相关，包括最新版本 iOS 和 PS4。此外还提及他曾在 Twitter 上惹怒了一个德国人，他口中的德国人就是 Stefan Esser‏。

<p align="center">

<img src="Images/luca1.jpeg" />

</p>


Luca 介绍了 iOS 史前时期的安全机制，iPhone OS 1.0所有都在 root 权限下运行，没有代码签名和沙箱。通过混淆来加密 OS 镜像文件。在 iOS 5出现了用户态的 ASLR，iOS 6出现内核态的 ASLR，并且区分了用户和内核的地址空间。其中大部分的防护机制都是基于沙盒的。

现代 iOS 安全方面，有些利用缓解策略已经实现了，iOS 10 在安全方面取得胜利，比如对堆采取了一些强化措施来避免 zone confusion 和错误使用 kfree 的攻击。事实是：Apple 并没有主动推出利用缓解，他们只是等 Ian Beer 放出新的利用，然后做一些小的改动来使利用变得没什么作用。

### Code Integrity

#### Kernel

在内核层面，Apple 在 iOS 9 上首次启用了 KPP(Kernel Patch Protection)，不过仅限在 arm64 机器上，这是因为 KPP 需要借助64位机器上的安全芯片来实现。WatchTower 就是 iOS 上 KPP 的具体实现。iPhone 7使用硬件加强了保护，错误的被称为 AMCC，据传正确的名字应该是"SiDP"。

#### WebKit

JIT(Just-in-time)即时编译对于高效执行 JavaScript 代码是必要的，这种代码签名正常过于宽松，JIT 编译器会生成新的和未签名的代码。假设一名攻击者可以管理一个"write-anywhere"的攻击，那么也就意味着他能够执行任意代码。存储区被标记为读、写和执行权限，区分权限的方式可以有效杜绝利用数据区域执行代码的攻击，在 iOS 10 中 Apple 将编译 JavaScript 放在仅允许执行的存储区之中。任何进程都无法从这个区域读取和写入数据。

### Data Protection

Secure Enclave 是 Apple A7(iPhone 5s 使用的处理器)或更高版本 A 系列处理器中集成的协处理器。它是独立的安全加密模块，每个 Secure Enclave 在制造过程中都预置了 UID（唯一 ID），这个 ID 无法从系统的其他部分访问，而且就连 Apple 也没办法获取。

主要用于处理指纹相关的数据，保证用户的指纹信息不被任何第三方窃取。工作原理大致是 Secure Enclave 接收到来自 Touch ID 传感器的指纹数据，确认是否匹配，处理器和 Touch ID 传感器之间的通信通过串行外围接口总线实现。处理器将数据转发到 Secure Enclave，但处理器本身无法读取这些数据。


### The cold，hard truth

所有的安全策略最终都是无用的，"Bulletproof JIT" 可能是最好的缓解措施，尽管它现在没用，但是未来会比 KPP 更有意义。Secure Enclave 会使得加大攻击者的攻击成本，然而，以色列的移动设备取证公司 Cellebrite 已经支持 iPhone 设备的解锁和取证。

<p align="center">

<img src="Images/luca2.jpeg" />

</p>

### Attacks

#### WatchTower


### QA

没有问题

## 天空之城－飞控安全攻防剖析

### QA

没有问题

## Pwning苹果手表

### QA

没有问题

## 伤痕累累的Android Wi-Fi驱动 - 从本地提权到远程攻击

### QA

Q:没太听清楚，提问者问了大概是代码中的漏洞需不需通过一个工具来检测

A:不需要，基本上从代码审计的层面就可以发现出来

## 幻象之盒

### QA

没有问题

## iOS 10内核安全漫谈

### QA

Q：Luca 提问，问题的意思是为什么没有放出来详细案例。

A：主要是为了保护客户的隐私。

## 闭幕
在最后一个议题 KeenLab 结束后，蚂蚁金服负责人进行会议结语，总结了面向未来的安全展望，提出了安全在互联网领域会变得越来越重要，从前安全上出现问题，可能只是要了钱，
但是随着万物互联，未来安全出现问题，就很可能要了命。