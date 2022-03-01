# 7559黑苹果12.0.1

对没错，我已经在Dell_7559上成功安装了**Monterey**，现在，我再次把我使用的引导分享出来。OpenCore版本 0.7.4

### 11.01修正
今天拿电脑到公司用发现接HDMI显示器无信号，加上启动参数 agdpmod=vit9696 后解决

**先说几个值得注意的地方(请务必查阅此信息)**

- 之前我所发布的*i5*版的*BigSur*引导，被其他人盗版并在闲鱼、淘宝等平台出售，此种行径令人不齿，望诸位不要效仿，也希望各位在碰到同样使用7559机器黑苹果的小伙伴时，能主动提供帮助，只要分享给他此仓库的链接就好。

1. 我目前使用的7559是*i7*版，CPU型号为*i7-6700hq*，之前使用的*i5(6300hq)*的机器不在手边，故未能测试i5版是否能成功安装*Monterey*
2. 因未能测试*i5*版是否能成功安装，故而在引导目录中保留了*config.plist*与*config_i5.plist*，两者的区别在于，有无启用*i7*版的usb定制驱动
3. 如果你使用的是*i5*版的机器，请自行定制usb
4. 我更换了BCM94360Z3 白果网卡，驱动目录中没有intel网卡的驱动，如果你使用的是intel网卡，还请自行更换驱动，但BlueToolFixup.kext一定要保留
5. 我提供的引导文件会将电脑机型设置为*MacBookPro15,1*，安装*Monterey*之前，为避免出现问题，一定要先**登出AppleID**
6. 如果你拥有洗白过的三码(即支持iMessage与FaceTime等功能)，可在安装之前，将引导中的三码替换为自己的三码，注意**机型也要改为你三码所对应的机型**
7. 无论你是否拥有洗白过的三码，最好不要长期使用引导里的三码，安装成功之后自行更换即可
8. 在你更新三码之前，最好不要登录AppleID
9. *i5* 版，必须断开电池排线才能进入系统，推荐bios版本1.0.1、1.3.1
10. *i7* 版，推荐bios版本1.2.2，我所使用的就是此版本


# 必要准备

**安装/升级之前的必要准备**
修改bios设置，感谢7559黑果前辈[江南小虫虫](https://segmentfault.com/a/1190000020642944?utm_source=tag-newest)所作博客的指导

- 恢复BIOS默认设置 (开机按F2进入bios，按F9恢复默认设置)
- Advanced
  - VT for direct I/O —————— Disabled
  - SATA Operation —————— AHCI
  - SupportAssist System Resolution —————— OFF
- Security
  - Firmware TPM  —————— Disabled  
- Boot
  - Boot List Option —————— UEFI
  - Secure boot —————— Disabled
  - Load Legacy Option Rom —————— Disabled

# 升级/安装流程

**升级流程简单描述**

1. 制作引导盘
2. 放入我提供的引导
3. 选择要使用的配置文件，将其名称改为**config.plist**(*i7*版无需修改)
4. OTA升级
5. 重启时保证使用引导盘中的引导(开机按F10选择引导)，选择多出来的引导项 (以HD结尾)
6. 安装过程中会重启2~3次，每次都要保证使用引导盘中的引导
7. 不出意外的话，一个半小时之后，安装成功

**安装流程简单描述**

1. 黑果小兵的部落阁官网下载*Monterey*系统
2. 使用**balenaEtcher**软件制作安装盘
3. 替换OC分区中的引导
4. 开始安装
5. 重启时保证使用引导盘中的引导，选择多出来的引导项 (以HD结尾)
6. 安装过程中会重启2~3次，每次都要保证使用引导盘中的引导
7. 不出意外的话，一个半小时之后，安装成功

# 遇到的坑

## 安装中的坑

我在升级的时候盲目自信，没开-v，还在配置好引导之后脑抽去掉了两个ACPI改名补丁，然后OTA升级。结果进入不了系统，也看不到跑码，不知道问题出在哪。偏偏我的电脑是单苹果系统，就在我打算重装系统的时候才想起，我之前制作的PE引导盘还在，于是我进入PE，在openCore的引导参数里加上了-v，发现原因就是我去掉了那两个改名补丁。。。然后强制关机，开机，进PE，加上改名补丁，这才成功安装上。

## 安装好之后遇到的坑

蓝牙挂了，我在远景论坛、Github上下求索，才发现，[在 macOS 12 中，Apple 已经将部分蓝牙堆栈从内核空间改为用户空间](https://github.com/acidanthera/BrcmPatchRAM/blob/master/README_CN.md)，需要使用**BlueToolFixup.kext**来驱动蓝牙。


# 引导介绍

**引导文件目录**
![引导文件目录](https://github.com/worship76/dell7559_Hackintosh_Monterey/blob/master/monterey_images/引导目录.png)
确实没啥好介绍的，引导体积很小，只有7.7Mb，没有添加外观主题。
ACPI中的补丁都加了注释，用 open core configurator 打开就能看到。
Kernel中的驱动确实还能精简一下，不过也没必要
引导参数值得一提，我用到的参数有：

- -v: 啰嗦模式，如果出现意外，方便大家排查问题，安装成功之后可以自行删去
- brcmfx-aspm: 博通网卡专用，如果你没有使用博通网卡，请自行删去
- -wegnoegpu: 屏蔽独显

以下两个参数是在遇到显卡异常时使用
- agdpmod=vit9696: HDMI无效时使用
- igfxonln=1: 休眠唤醒后屏幕失真时使用

  Quirks的选项就不细说了，有兴趣的可以研究一下

# 成果展示

**终于到这一步了！！！**

* 概览
  ![概览](https://github.com/worship76/dell7559_Hackintosh_Monterey/blob/master/monterey_images/MacOS%20Monterey.png)
* 核显
  ![核显](https://github.com/worship76/dell7559_Hackintosh_Monterey/blob/master/monterey_images/核显.png)
* WiFi
  ![WiFi](https://github.com/worship76/dell7559_Hackintosh_Monterey/blob/master/monterey_images/WiFI.png)
* 蓝牙
  ![蓝牙](https://github.com/worship76/dell7559_Hackintosh_Monterey/blob/master/monterey_images/蓝牙.png)
* 音量调节
  ![音量调节](https://github.com/worship76/dell7559_Hackintosh_Monterey/blob/master/monterey_images/音量调节.png)
* 声音输入
  ![声音输入](https://github.com/worship76/dell7559_Hackintosh_Monterey/blob/master/monterey_images/声音输入.png)
* 声音输出
  ![声音输出](https://github.com/worship76/dell7559_Hackintosh_Monterey/blob/master/monterey_images/声音输出.png)
* USB定制
  ![USB定制](https://github.com/worship76/dell7559_Hackintosh_Monterey/blob/master/monterey_images/USB定制.png)
* 电池
  ![电池](https://github.com/worship76/dell7559_Hackintosh_Monterey/blob/master/monterey_images/电池节能选项.png)
* 触摸板
  ![触摸板](https://github.com/worship76/dell7559_Hackintosh_Monterey/blob/master/monterey_images/触摸板.png)
* 接力
  ![接力](https://github.com/worship76/dell7559_Hackintosh_Monterey/blob/master/monterey_images/接力.png)
* 隔空投送(需要白果网卡)
  ![隔空投送](https://github.com/worship76/dell7559_Hackintosh_Monterey/blob/master/monterey_images/隔空投送.png)
* 支持随航(需要白果网卡)
* 支持实况文本(限制机型，详情见官网)


**预祝各位升级/安装一切顺利**
**感谢在黑果路上所有帮助过我的小伙伴**
