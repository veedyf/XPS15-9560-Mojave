# XPS15-9560-Mojave

> xps15-9560 吃上黑果的 clover 配置，不方便下载的童鞋可以前往[yeliujun/XPS15-9560-Mojave](https://gitee.com/yeliujun/XPS15-9560-Mojave.git)

[English](README_EN.md) | [中文](README.md)

## 更新日志

### 2019-05-07
- 现在使用`VirtualSMC(1.0.3)`替代`FakeSMC`.
- 默认使用防误触的触摸板驱动 VoodooPS2Controller(1.9.2) + VoodooI2C(2.1.5).
- 更新Lilu系列驱动.
- 添加了博通蓝牙参数`bpr_probedelay=100` `bpr_initialdelay=300` `bpr_postresetdelay=300`.

更多详见[changelog.md](https://github.com/jardenliu/XPS15-9560-Mojave/blob/master/changelog.md)



## 配置

- CPU：Intel I7 7700HQ
- 内存：16G(8G\*2) 2400MHz DDR4
- 硬盘：东芝 NVMe 512G
- WIFI 网卡：已更换为博通 DW1830
- 屏幕分辨率：4K 触控屏

## 特性

- CPU: I7-7700HQ，已启用原生电源管理；多档变频正常，添加了`CPUFriendDataProvider.kext`,低频可到`800MHZ`，续航表现更好。
- 声卡: ALC298, 注入 ID：72，声音正常。耳机切换采用 ALCPluginFix。(Combo jack 在 Mojave 下面似乎失效了)
- 触摸板: 含触屏，使用`VoodooI2C`,支持 Mac 原生手势。缺点就是没有防误触
- WIFI: 原配 Killer 1535 无法驱动，更换 DW1830, 实现免驱。（DW1560 应该也可以正常使用）
- 蓝牙: 驱动正常，极少数情况下会设备丢失，handoff 也正常。（没测过 1535 的蓝牙）
- ACPI： 使用 hotpatch 进行热修复，亮度快捷键映射正常。
- USB: USB3 端口均正常使用; TYPE-C 可以热插拔使用；雷电 3 不支持热插拔
- 显卡：集显 HD630 注入`591B0000`正常驱动；独显 GTX 1050 无解。
- 读卡器：无法使用

## 升级教程

1. 下载仓库配置文件。
2. 将自己的三码替换到下 CLOVER 目录下的`config.plist`对应位置。
3. 把下载的 CLOVER 替换自己本地的 CLOVER 文件夹。
4. 升级完之后，可能会出现以下异常现象，如`亮度不能调节`等。打开`终端`运行`sudo kextcache -i /`命令，重建缓存，重启。

## 安装教程

实在不想写教程，可以参考小米笔记本 pro 的安装教程，详见[bilibili 小米 pro 教程](https://www.bilibili.com/video/av23052183)

## 提示

1. 不开启`FileValue加密`，不开启`FileValue加密`，不开启`FileValue加密`！！！

## 小问题处理方式

#### 1. 字体细、发虚

终端执行`defaults write -g CGFontRenderingFontSmoothingDisabled -bool NO`，注销再登录即可

#### 2. 1080P 开启 HIDPI

使用[xzhih/one-key-hidpi](https://github.com/xzhih/one-key-hidpi)

#### 3. 安卓 USB 网络共享

把`Post-install`里面的`HoRNDIS.kext`放入`CLOVER/kexts/Other`

### Wifi 蓝牙设置

1. 关闭 wifi 唤醒和小憩，`系统偏好设置` -> `节能` 取消两个选项卡中的`小憩`和`唤醒以供Wi-Fi网络访问`的勾选。
2. 关闭蓝牙唤醒电脑, `系统偏好设置` -> `蓝牙` -> `高级` 取消所有勾选。
3. **_非 DW1830_** 需要替换`Post-install/非DW1830BT/USBPower.kext`到`CLOVER/kexts/Other/`
4. **_DW1830_** 在 windows 下设置，设备管理器，右键 dw1830（即无线网卡）->属性->高级->Bluetooth Cooperation（前面 Bluetooth 一致，后边可能不同），设置为 disable

## 鸣谢

[RehabMan](https://github.com/RehabMan)、[Acidanthera](https://github.com/acidanthera)、[PMheart](https://github.com/PMheart)、[alexandred](https://github.com/alexandred)、[wmchris](https://github.com/wmchris)、[darkhandz](https://github.com/darkhandz)、[gunslinger23](https://github.com/gunslinger23)、[goodwin](https://github.com/goodwin)等

注：排名不分先后；如有遗漏，请勿见怪，感谢您的付出；
