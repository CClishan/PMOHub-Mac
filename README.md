# PMOHub for macOS

PMOHub 原版界面的 Apple Silicon macOS 适配版。本仓库只发布可下载的二进制安装包，不上传源码。

## 下载与安装

前往 [Releases](https://github.com/CClishan/PMOHub-Mac/releases/latest) 下载：

- `PMOHub-macOS-arm64-2.1.1.dmg`
- `PMOHub-macOS-arm64-2.1.1.dmg.sha256`

安装步骤：

1. 打开 DMG，将 `PMOHub.app` 拖入“应用程序”。
2. 首次启动若被 macOS 拦截，在“应用程序”中右键 `PMOHub`，选择“打开”，再确认“打开”。
3. 也可以前往“系统设置 > 隐私与安全性”，点击“仍要打开”。
4. 首次连接键盘时，允许应用访问 HID / 输入监控，并重新插拔键盘。
5. 使用 USB 或 2.4G 连接；原版驱动无法识别蓝牙模式。

## 当前功能

- 设备中心：识别并显示兼容键盘的设备名称、电量和连接状态。
- 设备读取：已实测读取设备信息、功能信息及 4 层键位。
- 原版配置入口：保留按键配置、灯光配置、配置管理、屏幕及设置相关页面。
- macOS 窗口：原生红黄绿窗控、应用菜单、`Command+,` 设置和 `Command+W` 关闭窗口。
- 外观：支持深色/浅色模式，三个窗口同步切换并记住选择。
- 页脚：已移除备案号，保留 PMOHub 版权及 macOS 适配说明。

按键写入、灯光写入、保存、恢复出厂和固件刷写尚未完成实机验收，请先备份设备配置。

## 适配方式

- 基于原版 Electron 应用内的 `app.asar`，替换为 macOS arm64 Electron 运行时。
- 排除 Windows 专用原生模块，设备通讯继续使用 WebHID。
- 补充 macOS Bundle 信息、图标及 HID / 输入监控权限说明，并执行 ad-hoc 签名。
- 调整窗口、菜单、快捷键、滚动条、焦点环和减少动画行为，使其接近原生 macOS 交互。
- 增加跨窗口深浅主题同步，修复设置页和关于页的主题加载异常。

本适配只替换运行外壳与少量界面兼容层，不重写 HID 或固件协议。

## 兼容范围

- 仅支持 Apple Silicon（arm64），不支持 Intel Mac。
- 最低系统版本声明为 macOS 10.15，未做全版本兼容测试。
- 仅实测 `Aurora 80 / 极光 80`。
- 键盘必须已刷 PMOHUB 固件，不支持 VIA 固件。
- 其他 PMO 型号、蓝牙连接及其他 macOS 版本均未验证，不保证可用。

PMOHUB 固件会关闭 VIA 支持；刷写前请确认自己需要 PMOHUB 协议并保留可回退固件。

## 签名、公证与更新

当前版本没有 Developer ID 签名、Apple 公证和 macOS 自动更新源。

- 其他 Apple Silicon Mac 可以安装使用，但首次启动会被 Gatekeeper 拦截，需要按上面的方式手动放行。
- 企业设备、MDM 策略较严格的 Mac 可能禁止运行。
- 软件更新功能未接入 macOS，请忽略应用内更新检查；后续版本需要手动下载并覆盖安装。
- 当前方式适合测试和社区分发，不适合作为无提示的一键安装正式发行版。

## 校验

`v2.1.1-macos-arm64` 的 DMG SHA-256：

```text
84761dbd1a9f067fe8182a2f7507f25de7490da51131e2cd5b3fade00955cc44
```

请只从本仓库 Release 下载，并在终端核对：

```bash
shasum -a 256 PMOHub-macOS-arm64-2.1.1.dmg
```

## 版权

PMOHub 版权所有。本仓库仅分发基于原版改造、适配 macOS 的二进制版本，不包含上游源码。
