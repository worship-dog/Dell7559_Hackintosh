# 问征夫以前路，恨晨光之熹微
   自bigsur问世之后，一直黑果心切，奈何遍寻不得前人开路，于是大刀阔斧自己动手。从我尝试安装BigSur开始，到自己动手配置OC引导，再到完善驱动各种打补丁，经历了实在很久的时间。  
   出乎我意料的是，从我自己动手配置到完善结束，只用了3天的时间，这要归功于[黑果铁锤哥的视频教程](https://www.bilibili.com/video/BV1DZ4y137XB)，以及[Github前辈们分享的补丁](https://github.com/daliansky/OC-little)，现在我把自己的配置文件分享出来，算是分享自己成功黑果的喜悦，也算是让7559这台经典机器在黑果历程中再进一步。  
   先说一下目前还存在的问题：
   * 必须热启动才能进入系统
   * 必须断开电池排线才能进入系统
   * 开机比较慢
   * Wifi 蓝牙相互干扰，要想连接新的蓝牙设备需要先关闭Wifi，不然可能搜索不到设备
   * 电池电量显示不正确，一直是百分之一(开机之后可以接上电池排线)
   * 不插电池找不到触摸板
   * 亮度不能保存，每次开机回到默认亮度  
   
  **我的电脑配置信息**  
![鲁大师截图](https://github.com/worship76/dell7559_Hackintosh_BigSur/blob/main/电脑配置.jpg)  
_为防止图片加载失败，列出基本配置如下_  
1.型号:  Dell Inspiron 7559  
2.cpu:  intel i5-6300hq  Skylake  
3.主板:  100Series  
4.显卡:  hd530  
5.声卡:  ALC256  
6.网卡:  RTL8168/8111/8112  


  **BigSur设备截图**  
  * 概览  
  ![概览](https://github.com/worship76/dell7559_Hackintosh_BigSur/blob/main/概览.png)
  * 核显硬件加速  
  ![核显硬件加速](https://github.com/worship76/dell7559_Hackintosh_BigSur/blob/main/硬件加速.png)
  * 蓝牙  
  ![蓝牙](https://github.com/worship76/dell7559_Hackintosh_BigSur/blob/main/蓝牙.png)
  * WiFi  
  ![WiFi](https://github.com/worship76/dell7559_Hackintosh_BigSur/blob/main/WiFi.png)
  * 触摸板  
  ![触摸板](https://github.com/worship76/dell7559_Hackintosh_BigSur/blob/main/触摸板.png)
  * 电池  
  ![电池](https://github.com/worship76/dell7559_Hackintosh_BigSur/blob/main/电池.png)
  * USB  
  ![USB](https://github.com/worship76/dell7559_Hackintosh_BigSur/blob/main/USB.png)
  * 小太阳  
  ![USB](https://github.com/worship76/dell7559_Hackintosh_BigSur/blob/main/小太阳.png) 


