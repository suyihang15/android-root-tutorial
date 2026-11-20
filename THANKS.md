# 致谢

这份教程能写成、这台手机能 Root 成功，靠的是下面这些开源项目和工具的作者们。这里把它们的出处和作者列清楚，既是感谢，也方便你直接去官方渠道下载原版、避免被中间人塞进木马或卡密。

## 核心工具

### KernelSU

本教程采用的 Root 方案，内核级 su 实现。作者 **weishu（tiann）** 及社区贡献者。

- 项目地址：<https://github.com/tiann/KernelSU>
- 许可证：GPL 系开源协议

### Magisk（教程中作为对比方案提到）

用户态 root 方案的事实标准，作者 **topjohnwu**。

- 项目地址：<https://github.com/topjohnwu/Magisk>

### QtScrcpy

图形化的手机投屏 / 控机工具，教程里用来辅助操作。作者 **barry-ran**。底层基于 scrcpy。

- 项目地址：<https://github.com/barry-ran/QtScrcpy>

### scrcpy

QtScrcpy 的底层引擎，作者 **Genymobile（rom1v 等）**。

- 项目地址：<https://github.com/Genymobile/scrcpy>

### Android platform-tools（adb / fastboot）

全程刷写、校验用的命令行工具，由 **Google** 官方发布。

- 下载地址：<https://developer.android.com/studio/releases/platform-tools>

## 其他提到的项目

### LSPosed / Shamiko

教程在「过检测」部分提到的模块。**LSPosed 团队** 维护。

- LSPosed：<https://github.com/LSPosed/LSPosed>
- Shamiko：由 LSPosed 团队发布，用于隐藏 root / 解锁状态

## 第三方解锁工具

### Xiaomi-QC解锁BL工具 v2.5Plus

小米 / 高通平台的一键解锁 Bootloader 工具，作者为酷安 **「莫离然然」**。这是第三方、非官方的工具，属于灰色地带，请从作者官方渠道获取，注意甄别被二次打包、加卡密的假版本。工具内附带交流群信息和版本更新日志。

## 写在最后

以上项目的作者们基本都是以开源或免费的形式把工具分享出来，让普通用户也能折腾自己的设备。如果你觉得这份教程或这些工具有用，可以去对应的项目仓库点个 Star、给作者留句感谢——这就是对他们最好的支持。

如果你发现这里某个链接失效、或某位作者信息写错了，欢迎提 issue 指正。
