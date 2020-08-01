# macOS 10.15 Catalina on LG Gram z980 series
## 电脑配置
| 规格     |      详细信息                                 |
| --------| ----------------------------------------    |
| 型号     | LG Gram 13/14/15 Z980 （15存需要自行定制USB口） |
| CPU     | 英特尔 酷睿 i5-8250U 处理器                     |
| 显卡     | UHD Graphics 620                             |
| 内存     | 板载 8G + Micron 16G DDR4 2400MHz             |
| 硬盘     | Intel SSD 760p series 512GB                  |
| 声卡     | Conexant CX8200                              |
| 网卡     | 英特尔 无线 8265 （已替换为 BCM94360CS2）        |

### 触摸板的问题解决了，可以正常使用

## 本项目不支持z990系列，请关注以下下路标
    z990系列的同学请关注 https://github.com/capricornlee/LG-Gram13-Z990
## 想尝试OpenCore的同学请关注（测试了一下目前bug比clover多点，还需要优化）
    z980 OpenCore https://github.com/suzuke/LG-Gram-13z980-Opencore

## 进一步提升体验配置（强烈推荐）
    解锁CFG Lock 开启Mac原生电源管理，DVMT开启64M，彻底根除偶尔卡死、频繁花屏的bug，降低整机功耗。
    方法：使用RU.efi修改BIOS配置
    完整教程可以参考，http://bbs.pcbeta.com/viewthread-1840558-1-1.html
    提取BIOS不需要看，只需要看后半部分即可。
    解锁CFG lock，找到 cpuSetup add:0x3c val: 1->0
    解锁DVMT  ,找到 saSetup add:0xDF, val: 1->2
    解锁后，请删除framebuffer-fbmem、framebuffer-stolenmem 两项显卡注入属性

## 关于WiFi的解决办法：
### 1、使用USB网卡
    使用免驱USB网卡（自行淘宝），打开内建网卡功能
### 2、通过M.2接口转接一张网卡
    lg gram 有两个m.2槽位，可以通过m.2 Mkey转接卡，转接一张BCM94360cs2，可在某宝购买 （ps.拆机失去保修，谨慎操作）
    硬盘位M.2不带USB接口，故无法使用蓝牙，需要自己进行焊接到主板，或者通过以下方法占用一个USB口。 
    转自https://github.com/ice-black-tea  的建议
  ![avatar](https://github.com/ShiningXu/LG-Gram-macOS/blob/master/bluetooth.png)
### 3、自带type-c网卡需要安装驱动
    请自行下载 https://github.com/ShiningXu/LG-Gram-macOS/blob/master/RTUNICv1.0.19.dmg

## 目前完成
  - 显卡正常，内屏显示正常，亮度调节正常；
  - CPU调频、电源管理正常；
  - 外接HDMI正常，可以同时使用内屏；
  - 声卡MIC正常，可使用音量调节+-快键、使用AppleALC 注入id:21；
  - 休眠睡眠唤醒正常，可使用FN+F4进行睡眠，键盘灯两档亮度正常；
  - Siri、iCloud、iMessage使用正常；
  - 电源正常，可显示电量
  - 键盘、摄像头等...都正常
  - I2C触摸板：勉强使用，存在单指卡死的BUG等，待驱动修复；

## 未解决问题
- Intel网卡、SD读卡器、指纹，全球无解；
- 遗留小问题
  - 无法使用FN 调节亮度（需要定制dsdt懒得弄了，可自定义系统快捷键解决）%


## added additional support
- From OpenIntelwireless
- heliport working (tested on lg gram 14 980)
- bluetooth working 
- trackpad full guesture support 

## working on 
- fn support (you can use karabiner-elements)
- airdrop will hopefully work (depends on the progress of openintelwireless)