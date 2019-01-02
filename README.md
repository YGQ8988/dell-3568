# Dell Inspiron 3568 EFI for MacOS
戴尔 灵越 15 3000系列 3568 黑苹果安装和日常使用EFI

[Dell-3568](https://github.com/YGQ8988/dell-3568)

### 主要配置信息

| 配件名      | 型号    |
| --------- | -------- | 
| CPU    | I5-7200U  |
| 显卡     | HD Graphics 620 (platform-id:0x191b0000)     |   
| 网卡     | DW1560 | 
| 声卡 | ALC3234    |
| 硬盘 | Samsung EVO 850 250G(SSD)    |
| 内存 | 4G*2(镁光DDR3L)    |
| 显示器 | 1920x1080(15.6 英寸)    |

### 说明

此合集本人只在戴尔 灵越3568型号使用过，其他型号未测试

目录下文件夹已区分10.13和10.14EFI

### 工作的功能

1、HDMI外接显示器正常(HDMI外放未测试，测试显示器纯显示器无喇叭)

2、自动锁屏休眠正常

3、盒盖休眠正常(但是好像不是立马休眠，需等待一段时间)，本人使用基本不休眠，不使用时锁屏或关机

4、喇叭外放最大音量正常，麦克风正常

5、集显驱动正常

6、电池驱动正常

7、无线网卡，蓝牙正常(已更换为DW1560)

8、摄像头正常

9、打印机正常

10、小太阳亮度调节正常

### 已知问题

1、绝大部分耳机破音，测试了四副耳机只有一副放音乐正常，其他均破音(如您仿冒声卡驱动成功后也存在耳机破音，可尝试万能声卡驱动，下文提供解决说明)

2、点击声音里面，输出，输入可能会存在死机

### 声卡决解方案(此方案本人未测试)

1、解压声卡文件夹下VoodooHDA-2.9.1.kext.zip

2、把VoodooHDA-2.9.1.kext驱动，直接放入EFI/CLOVER/kexts/Other目录内，同时把AppleALC.kext驱动移除Other目录

3、重启检验效果，(如该驱动耳机杂音，可远景论坛找寻低版本，稳定版)

### 10.14亮度调节

各位系统安装好后请查看/S/L/E目录下有没有：10.14亮度驱动目录下两个驱动，如果有的话理论使用我的10.14.2的EFI能直接驱动成功，如果没有请往下看。(反正我使用小兵的镜像安装完成后貌似没有这两个驱动文件，也可能是我误删了。)

将10.14亮度驱动目录下两个文件解压，放入/S/L/E目录下，重建缓存，再重启，看显示器下有没有显示亮度调节进度条。如果有说明驱动成功，快捷键的换需要Fn+F11及Fn+F12组合调节。(效果图见文末)

#### 希望存在同款机型，且不存在以上问题的机油分享解决方案。

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

3、声卡、耳机

注：如你安装完成后直接使用了万能声卡驱动，请参照上文声卡决解方案，使用万能声卡驱动可忽略此步骤

声卡ID注入为3，本人电脑下只有一副耳机使用正常，测试四副耳机其中三副播放音乐破音(暂不知何原因)

AppleHDA为老版本，安装完成后需替换/S/L/E目录下AppleHDA，替换完成后重构缓存

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

[10.14.2](https://daliansky.github.io/macOS-Mojave-10.14.2-18C54-official-version-with-Clover-4792-original-image.html)

[10.13.6](https://daliansky.github.io/macOS-High-Sierra-10.13.6-17G2112-Release-Special-with-Clover-4606-original-mirror.html)

### 效果图

![桌面](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E6%A1%8C%E9%9D%A2.png)

![菜单](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E7%A8%8B%E5%BA%8F.png)

![USB](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/USB.png)

![WIFI](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/WIFI.png)

![以太网](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E4%BB%A5%E5%A4%AA%E7%BD%91.png)

![储存](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E5%82%A8%E5%AD%98.png)

![内建显示器](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E5%86%85%E5%BB%BA%E6%98%BE%E7%A4%BA%E5%99%A8.png)

![声卡](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E5%A3%B0%E5%8D%A1.png)

![打印机](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E6%89%93%E5%8D%B0%E6%9C%BA.png)

![摄像头](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E6%91%84%E5%83%8F%E5%A4%B4.png)

![显示器](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E6%98%BE%E7%A4%BA%E5%99%A8.png)

![概览](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E6%A6%82%E8%A7%88.png)

![电源](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E7%94%B5%E6%BA%90.png)

![蓝牙](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E8%93%9D%E7%89%99.png)

![集显](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E9%9B%86%E6%98%BE.png)

![亮度1](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E4%BA%AE%E5%BA%A61.png)

![亮度2](https://github.com/YGQ8988/dell-3568/blob/master/%E6%95%88%E6%9E%9C%E5%9B%BE/%E4%BA%AE%E5%BA%A62.png)
