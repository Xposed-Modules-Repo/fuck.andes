# Eta

Eta 是一个主要面向 ColorOS 16 的第三方 Android 系统级 AI Agent，App 本体是主要工作台。Agent 可以操作手机界面，也能像 Coding Agent 一样使用终端和文件系统完成任务。

项目重点支持 ColorOS 小布助手入口接管；在符合系统版本要求的其他 Root Android 设备上也可以直接使用 Eta App 本体，例如小米设备，但暂不提供对应厂商助手的入口接管。

## 核心能力

- **GUI 操作手机**：截图并读取无障碍控件，执行点击、长按、滑动、滚动、文字输入、启动 App、模拟按键和打开系统面板等操作
- **终端与文件工具**：在用户明确授权后执行 `user` 或 `root` Shell，读写文件、运行脚本、查看日志和管理异步任务；相关工具默认关闭
- **Android Shell**：用于操作系统、应用、日志、Magisk 和设备文件，并支持 Magisk、KernelSU 或 APatch 提供的 Root 环境
- **Linux 环境**：可选安装独立 Alpine Linux 工具环境，提供 Python、Git、Bash、jq、zip、OpenSSL 和 SQLite 等常用工具
- **Agent Runtime**：通过多轮工具调用持续观察、执行和校验，支持任务取消、运行中补充指令、结果归档和状态恢复
- **浏览器与 Skills**：支持后台加载网页、提取结构化内容和操作页面元素，并可按需安装、启用和读取 Skills
- **模型与 BYOK**：支持 OpenAI-compatible 与 Anthropic 协议，以及多个内置或自定义模型提供商

## ColorOS 系统入口

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
