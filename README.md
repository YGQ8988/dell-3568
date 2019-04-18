# Dell Inspiron 3568 EFI for MacOS
戴尔 灵越 15 3000系列 3568 黑苹果安装和日常使用EFI

[Dell-3568](https://github.com/YGQ8988/dell-3568)

### 主要配置信息

| 配件名      | 型号    |
| --------- | -------- | 
| CPU    | I5-7200U  |
| 显卡     | HD Graphics 620 (platform-id:0x59160000)     |   
| 网卡     | DW1560 | 
| 声卡 | ALC3234(同ALC255)    |
| 硬盘 | Samsung EVO 850 250G(SSD)    |
| 内存 | 4G*2(镁光DDR3L)    |
| 显示器 | 1920x1080(15.6 英寸)    |

### 说明

此合集本人只在戴尔 灵越3568型号使用过，其他型号未测试

目录下文件夹已区分10.13和10.14EFI

### 工作的功能

1、HDMI外接显示器正常(HDMI外放正常)

2、自动锁屏休眠正常

3、盒盖休眠正常

4、喇叭外放最大音量正常，麦克风正常

5、集显驱动正常

6、电池驱动正常

7、无线网卡，蓝牙正常(已更换为DW1560)

8、摄像头正常

9、打印机正常

10、小太阳亮度调节正常(F11，F12调节)

### 耳机听歌只有伴奏没有人声优先尝试方案

直接解压ALCPlugFix.zip，再执行ALCPlugFix\alc_fix目录下install双击自动安装.command

感谢黑果小兵提供解决方案！！！

[传送门|ALCPlugFix](https://github.com/daliansky/ALCPlugFix)

### 如仿冒声卡存在问题可试用决解方案(此方案本人未测试)

1、解压声卡文件夹下VoodooHDA-2.9.1.kext.zip

2、把VoodooHDA-2.9.1.kext驱动，直接放入EFI/CLOVER/kexts/Other目录内，同时把AppleALC.kext驱动移除Other目录

3、重启检验效果，(如该驱动耳机杂音，可远景论坛找寻低版本，稳定版)



#### 欢迎同款笔记本分享安装，完善心得。本人QQ：898829225

#### 如您有更完善的EFI，可联系我，收录此Git仓库，方便更多的人使用黑苹果系统

### 使用方法

1、下载EFI

  一、首先保证电脑上已安装git功能，安装教程自行百度(已有此功能请直接走后续步骤)
  
  二、打开Git Bash窗口，执行以下命令
  ```
  git clone https://github.com/YGQ8988/dell-3568.git
  ```
  三、把需要使用的EFI文件名改为EFI，替换已刻入好的U盘内或安装完成后直接放入系统EFI目录
  
2、刻入U盘

刻入工具为Etcher，镜像均为黑果小兵制作。镜像自行前往黑果小兵博客下载。

[etcher](https://etcher.io/)

[黑果小兵](http://daliansky.github.io)

# 注以下为非必要操作，如安装完成后各功能正常，可以略过！！！

3、声卡、耳机

注：如你安装完成后直接使用了万能声卡驱动，请参照上文声卡决解方案，使用万能声卡驱动可忽略此步骤

声卡ID注入为3，本人电脑下只有一副耳机使用正常，测试四副耳机其中三副播放音乐破音(暂不知何原因)

AppleHDA为老版本，安装完成后需替换/S/L/E目录下AppleHDA，替换完成后重构缓存

缓冲注入教程参照：[Hackintool(原Intel FB-Patcher)使用教程及插入姿势](https://daliansky.github.io/Intel-FB-Patcher-tutorial-and-insertion-pose.html)

在终端依次执行以下命令
```
#!/bin/sh
sudo chmod -Rf 755 /S*/L*/E*
sudo chown -Rf 0:0 /S*/L*/E*
sudo chmod -Rf 755 /L*/E*
sudo chown -Rf 0:0 /L*/E*
sudo rm -Rf /S*/L*/PrelinkedKernels/*
sudo rm -Rf /S*/L*/Caches/com.apple.kext.caches/*
sudo touch -f /S*/L*/E*
sudo touch -f /L*/E*
sudo kextcache -Boot -U /
```

4、一键开启HIDPI并注入EDID

此一键命令可开启接近原生的HIDPI设置，不需要RDM软件即可在系统显示器设置中设置

[一键开启HIDPI并注入EDID](https://zhih.me/one-key-hidpi/)

5、DW1560驱动

Clover内已集成DW1560网卡驱动，如存在休眠后蓝牙无效，请使用黑果小兵博客内教程修复。

[Broadcom BCM94352z/DW1560驱动新姿势新方法](https://blog.daliansky.net/Broadcom-BCM94352z-DW1560-drive-new-posture.html)

6、安装过程中其他问题

参照黑果小兵博客内教程解决，传送地址如下。

[10.14.3](https://daliansky.github.io/macOS-Mojave-10.14.3-18D42-official-version-with-Clover-4859-original-image.html)

[10.14.2](https://daliansky.github.io/macOS-Mojave-10.14.2-18C54-official-version-with-Clover-4792-original-image.html)

[10.13.6](https://daliansky.github.io/macOS-High-Sierra-10.13.6-17G2112-Release-Special-with-Clover-4606-original-mirror.html)

### 更新说明
2019-03-07:
                紧随原作者脚步更新，更新clover主文件，修改核显名称，声卡ID。
                原EFI地址：[dell-7460-7560](https://github.com/xzhih/dell-7460-7560-hackintosh)

2019-01-18：
                替换原有EFI，复用： [xzhih](https://github.com/xzhih) 此GitHubEFI
                原EFI地址：[dell-7460-7560](https://github.com/xzhih/dell-7460-7560-hackintosh)
                修改部分：缓冲帧注入声卡ID：3，把触摸板驱动VoodooPS2Controller替换为ApplePS2SmartTouchPad

### 效果图

![概览](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E6%A6%82%E8%A7%88.png)

![wifi](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/WiFi.png)

![以太网](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E4%BB%A5%E5%A4%AA%E7%BD%91.png)

![内建显示器](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E5%86%85%E5%BB%BA%E6%98%BE%E7%A4%BA%E5%99%A8.png)

![声卡](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E5%A3%B0%E9%9F%B3.png)

![摄像头](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E6%91%84%E5%83%8F%E5%A4%B4.png)

![显卡](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E6%98%BE%E5%8D%A1.png)

![显示器](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E6%98%BE%E7%A4%BA%E5%99%A8.png)


![蓝牙](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E8%93%9D%E7%89%99.png)

![桌面](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E6%A1%8C%E9%9D%A2.png)


