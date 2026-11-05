# PMOHub for macOS

PMOHub 原版的 Apple Silicon macOS 适配版，界面已按原生 macOS 方向重新对齐。本仓库只发布可下载的二进制安装包和说明，不上传源码。

## 下载

### Rainy75 无光版有线适配

前往 [Rainy75 原生 Mac UI Release](https://github.com/CClishan/PMOHub-Mac/releases/tag/rainy75-v2.1.1-macos-arm64-ui) 下载：

- `PMOHub-Rainy75-macOS-arm64-2.1.1-ui.dmg`
- `PMOHub-Rainy75-macOS-arm64-2.1.1-ui.dmg.sha256`

### Aurora 80 / PMOHUB 固件

前往 [Aurora 80 Release](https://github.com/CClishan/PMOHub-Mac/releases/tag/v2.1.1-macos-arm64) 下载：

- `PMOHub-macOS-arm64-2.1.1.dmg`
- `PMOHub-macOS-arm64-2.1.1.dmg.sha256`

## 安装

1. 打开 DMG，将 `PMOHub.app` 拖入“应用程序”。
2. 首次启动若被 macOS 拦截，在“应用程序”中右键 `PMOHub`，选择“打开”，再确认“打开”。
3. 也可以前往“系统设置 > 隐私与安全性”，点击“仍要打开”。
4. 首次连接键盘时，允许应用访问 HID / 输入监控，并重新插拔键盘。

## Rainy75 功能

- Rainy 75 无光版 USB 有线连接。
- 标准 VIA 协议识别：VID `0x320F`、PID `0x5055`、协议 11、`8 x 16` 矩阵。
- 4 层键位读取。
- 单键改键：标准层和 Fn1 层均已实机验证，写入后可回读并恢复原值。
- 原生 macOS 窗控、应用菜单、`Command+,` 设置和 `Command+W` 关闭窗口。
- 设备中心、设备详情、设置页和关于页统一为原生 macOS 视觉方向。
- 主页、设置页和关于页使用居中的 macOS 标题栏，语言与主题控件靠右。
- 新安装默认浅色模式，已有深色偏好继续保留。
- 深色 / 浅色模式，主窗口、设置页和关于页同步切换。
- 关于页移除版本号，所有页面去除原版紫色视觉。
- 设备页补齐固定页脚，保留指定版权文案。
- Aurora 80 / PMOHUB 固件设备继续保留在设备中心。

## 适配方式

- 基于 PMOHub 原版 Electron 应用内的 `app.asar`，替换为 macOS arm64 Electron 运行时。
- 排除 Windows 专用原生模块，设备通讯继续使用 WebHID。
- 补充 macOS Bundle 信息、图标及 HID / 输入监控权限说明，并执行 ad-hoc 签名。
- 调整窗口、菜单、快捷键、滚动条、焦点环和减少动画行为，使其接近原生 macOS 交互。
- 基于原版 DOM 增加 macOS 兼容层，重做设备中心、双栏设备详情、设置页和关于页。
- 增加跨窗口深浅主题同步，修复设置页和关于页的主题加载异常。
- 为 Rainy 75 增加 VIA 路由、`8 x 16` 矩阵、4 层读取和单键写入处理，补充 QMK 键名映射。
- macOS 上关闭 Windows `.exe` 自动更新检查，改为提示从 GitHub Releases 手动下载。

本适配基于原版二进制和界面通讯层改造，没有上游源码，也没有重写或刷入 Rainy 75 固件。

## 兼容范围

- 仅支持 Apple Silicon（arm64），不支持 Intel Mac。
- 本版重点实测 Rainy 75 无光版、USB 有线、原厂 VIA 固件。
- Aurora 80 为此前 macOS 版本的已验证设备；本版未重新覆盖 Aurora 80 的全部功能。
- 未实测 Rainy 75 RGB 版、2.4G、蓝牙及其他 PMO / WOB 型号。
- 不支持 Rainy 75 刷写 PMOHUB 固件、恢复出厂、RGB 调节或无线连接配置。
- 改键前请自行记录原配置；不同批次或固件版本可能存在差异。

## 签名、公证与更新

当前版本没有 Developer ID 签名、Apple 公证和 macOS 自动更新源。

- 其他 Apple Silicon Mac 通常可以安装使用，但首次启动会被 Gatekeeper 拦截，需要按上面的方式手动放行。
- 企业设备、MDM 策略较严格的 Mac 可能禁止运行。
- 应用内更新检查已关闭，并提示从 GitHub Releases 手动下载；后续版本需要手动下载覆盖安装。
- 当前方式适合测试和社区分发，不适合作为无提示的一键安装正式发行版。

## 校验

Rainy75 原生 Mac UI 版 DMG SHA-256：

```text
40f8e3200da0a5734eec6026b15f38341c840f1248b109ddfc6aa8c16ae90ac8
```

Aurora 80 版 DMG SHA-256：

```text
84761dbd1a9f067fe8182a2f7507f25de7490da51131e2cd5b3fade00955cc44
```

请只从本仓库 Release 下载，并在终端核对：

```bash
shasum -a 256 PMOHub-Rainy75-macOS-arm64-2.1.1-ui.dmg
```

## 版权

PMOHub 版权所有，一切基于原版改造，仅适配 MacOS。本仓库仅分发二进制版本，不包含上游源码。
