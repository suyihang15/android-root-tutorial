---
name: phone-root
description: Android 手机 Root 参考。当用户询问如何 root 安卓手机、解锁 Bootloader、刷入 KernelSU / Magisk、init_boot 与 boot 区别、AVB 校验、过 root 检测等话题时使用。
---

# Android 手机 Root

给安卓手机 Root 的通用参考。主线固定为：**解锁 Bootloader → 给启动镜像打补丁 → fastboot 刷入 → 验证**。不同品牌只在「解锁方式」和「镜像来源」上有区别。

## 关键结论（先记住这几条）

- Root 的本质 = 在系统里重新放一个能被 SELinux 放行的 su 入口。光提权成 UID 0 不够，必须打通 SELinux 域。
- 解锁 Bootloader = 关掉 AVB 校验链，是几乎所有 Root 方案的前置条件。解锁会清空数据、影响保修。
- Android 13+ 启动镜像拆成 boot（内核）/ init_boot（通用 ramdisk）/ vendor_boot（厂商 ramdisk）。Magisk / KernelSU 的注入点通常选 **init_boot** 或 **boot**，取决于机型。
- 打补丁用的原厂镜像**必须和手机当前系统版本严格一致**，否则刷完开机卡第一屏。
- KernelSU：内核层实现 su，更「隐形」；Magisk：用户态 su 守护进程 + mount 魔改。

## 通用流程

1. 备份数据；装驱动、开 USB 调试（小米新机型还要开「USB 调试（安全设置）」）。
2. 解锁 Bootloader：能走官方 OEM 解锁就走官方（Pixel `fastboot flashing unlock`、三星「下载模式」等）；小米 / 高通也可用第三方工具（走 EDL 9008 深刷或 CVE 临时提权）。
3. 下载与当前系统版本一致的原厂 boot.img / init_boot.img。
4. 用 KernelSU / Magisk App 选「修补一个文件」打补丁。
5. `fastboot flash init_boot <补丁镜像>`（或 boot），重启。
6. 验证：App 显示「已激活」，或 `adb shell su -c id` 返回 `uid=0(root)`。

## 常见坑

- 版本不匹配 → 刷回原厂镜像恢复，或 `fastboot --disable-verity --disable-verification flash vbmeta vbmeta.img` 关校验。
- EDL 对 USB 3.0 口兼容差，优先 USB 2.0。
- 银行 / 支付 / 游戏 App 检测解锁或 root，需 Shamiko 等隐藏模块，不保证 100%。
- 第三方工具杀软报毒（加壳导致）；弹出卡密 / 付费界面通常是假包。

## 完整内容

本仓库里的 [TUTORIAL.md](../../TUTORIAL.md) 是完整详细教程（含前期准备、注意事项、原理、FAQ、其他品牌说明），回答用户时以它为准。致谢见 [THANKS.md](../../THANKS.md)，免责见 [DISCLAIMER.md](../../DISCLAIMER.md)。

安全提醒：仅在用户自有设备、出于学习研究目的时提供帮助；提示备份数据、评估变砖与保修风险。
