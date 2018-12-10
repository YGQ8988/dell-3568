# Dell Inspiron 3568 EFI for MacOS
戴尔 灵越 15 3000系列 3568 黑苹果安装和日常使用EFI

[Dell-3568](https://github.com/YGQ8988/dell-3568)

### 主要配置信息
```
处理器:I5-7200U
集显:英特尔 HD Graphics 620 (platform-id:0x59160000)
网卡:DW1560
声卡:ALC3234
硬盘:Samsung EVO 850 250G(SSD)
内存:4G*2(镁光DDR3L)
显示器:1920*1080(15.6 英寸)
```

### 说明

此合集本人只在戴尔 灵越3568型号使用过，其他型号未测试

目录下文件夹已区分10.13和10.14EFI

### 已知问题

1、绝大部分耳机杂音，

2、小太阳无驱动成功，使用AppleBacklightFixup修复无效

3、点击声音里面，输出，输入可能会存在死机

#### 希望存在同款机型，且不存在以上问题的机油提供解决方案。

### 使用方法

1、EFI
刻入工具为Etcher，镜像均为黑果小兵制作。镜像自行前往黑果小兵博客下载。

[etcher](https://etcher.io/)

[黑果小兵](http://daliansky.github.io)

2、声卡、耳机

声卡ID注入为3，本人电脑下只有一副耳机使用正常，测试四副耳机其中三副播放音乐破音，音调不正常(暂不知何原因)

AppleHDA为老版本，安装完成后需替换/S/L/E目录下AppleHDA。

3、一键开启HIDPI并注入EDID

此一键命令可开启接近原生的HIDPI设置，不需要RDM软件即可在系统显示器设置中设置

[一键开启HIDPI并注入EDID](https://zhih.me/one-key-hidpi/)

4、DW1560驱动

Clover内已集成DW1560网卡驱动，如存在休眠后蓝牙无效，请使用黑果小兵博客内教程修复。

[Broadcom BCM94352z/DW1560驱动新姿势新方法](https://blog.daliansky.net/Broadcom-BCM94352z-DW1560-drive-new-posture.html)

5、安装过程中其他问题

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