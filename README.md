# 问征夫以前路，恨晨光之熹微
   自bigsur问世之后，一直黑果心切，奈何遍寻不得前人开路，于是大刀阔斧自己动手。从我尝试安装BigSur开始，到自己动手配置OC引导，再到完善驱动各种打补丁，经历了实在很久的时间。  
   出乎我意料的是，从我自己动手配置到完善结束，只用了3天的时间，这要归功于[UP主-黑果铁锤哥的视频教程](https://www.bilibili.com/video/BV1DZ4y137XB)，以及[Github前辈们分享的补丁](https://github.com/daliansky/OC-little)，现在我把自己的配置文件分享出来，算是分享自己成功黑果的喜悦，也算是让7559这台经典机器在黑果历程中再进一步。  
   先说一下目前还存在的问题：
   * 必须热启动才能进入系统(_无解_)
   * 必须断开电池排线才能进入系统(_无解_。
   * 开机比较慢
   * Wifi 蓝牙相互干扰，要想连接新的蓝牙设备需要先关闭Wifi，不然可能搜索不到设备(_等待驱动优化_)
   * 电池电量显示不正确，一直是百分之一(开机之后可以接上电池排线)(2020/12/21，已解决，感谢大佬[Eaxyx(自语)](https://github.com/Eaxyx)的指导)
   * 不插电池找不到触摸板(_插上电池就行了_) 
   * HDMI接口不能使用(更新问题_2020/12/17)(2021/01/11 已解决，修改机型为带有HDMI接口的机型,感谢[UP主-DHWR刘海涛的视频教程](https://www.bilibili.com/video/BV1AT4y157oJ?from=search&seid=5700509783862820293)提供的思路)
   
   ------------------------------------------------------
   
  **我的电脑配置信息**  
![鲁大师截图](https://github.com/worship76/dell7559-hackintosh-bigsur-opencore/blob/master/images/电脑配置.jpg)  
_为防止图片加载失败，列出基本配置如下_  
1.型号:  Dell Inspiron 7559  
2.cpu:  intel i5-6300hq  Skylake  
3.主板:  100Series  
4.显卡:  hd530  
5.声卡:  ALC256  
6.网卡:  RTL8168/8111/8112  


  **BigSur设备截图**  
  * 概览  
  ![概览](https://github.com/worship76/dell7559-hackintosh-bigsur-opencore/blob/master/images/概览.png)
  * 核显硬件加速  
  ![核显硬件加速](https://github.com/worship76/dell7559-hackintosh-bigsur-opencore/blob/master/images/硬件加速.png)
  * 蓝牙  
  ![蓝牙](https://github.com/worship76/dell7559-hackintosh-bigsur-opencore/blob/master/images/蓝牙.png)
  * WiFi  
  ![WiFi](https://github.com/worship76/dell7559-hackintosh-bigsur-opencore/blob/master/images/WiFi.png)
  * 触摸板  
  ![触摸板](https://github.com/worship76/dell7559-hackintosh-bigsur-opencore/blob/master/images/触摸板.png)
  * 电池  
  ![电池](https://github.com/worship76/dell7559-hackintosh-bigsur-opencore/blob/master/images/电池.png)
  * USB  
  ![USB](https://github.com/worship76/dell7559-hackintosh-bigsur-opencore/blob/master/images/USB.png)
  * 小太阳  
  ![USB](https://github.com/worship76/dell7559-hackintosh-bigsur-opencore/blob/master/images/小太阳.png) 
  * 声卡  
  ![声卡](https://github.com/worship76/dell7559-hackintosh-bigsur-opencore/blob/master/images/声卡.png)

特别鸣谢[Eaxyx(自语)](https://github.com/Eaxyx)大佬帮助完善驱动，解决电池电量显示问题


