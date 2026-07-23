# Eta

Eta 是一个第三方 Android 系统级 AI Agent。App 本体是主要工作台，可在小米等 Android 16 设备上独立使用，支持 GUI 操作、终端与文件工具、Skills、网页浏览和自定义模型提供商。

目前小布助手等系统入口接管主要面向 ColorOS 16；小米设备暂未接入小爱同学入口，但不影响直接使用 Eta App 本体。

项目同时保留 Xposed 系统能力：

- 接管小布的文字和图片请求，转交 Eta Agent Runtime 处理
- 接管电源键和默认数字助理链路，让 ColorOS 可以直接唤起 Gemini
- 启用并修正 `contextual_search`，将手势条长按和双指识屏创建为一圈即搜入口

## 运行要求

- Android 16（API 36）及以上，主要面向 ColorOS 16
- 支持 libxposed API 102 的 LSPosed 环境
- Agent 模型采用 BYOK，需要自行配置模型提供商、模型和 API Key

## 源码与反馈

源码、完整说明和问题反馈请前往：

<https://github.com/Mangi-11/Eta>

APK 请从本仓库 Releases 下载。

> 从 1.5.1 或更早版本升级时请注意：Eta 2.0.0 起更换了签名证书，无法直接覆盖安装旧版，需要先卸载再安装。

如果 Eta 对你有帮助，欢迎为主仓库点一个 Star ⭐，这是我持续更新的动力。
