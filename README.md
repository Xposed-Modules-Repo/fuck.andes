# Eta

> **主仓库：[Mangi-11/Eta](https://github.com/Mangi-11/Eta)**
>
> 源码、完整文档、使用说明与问题反馈均在主仓库维护。欢迎点一个 **Star ⭐**，这是我持续更新 Eta 的动力。

Eta 是一个面向已 Root Android 设备的第三方系统级 AI Agent。App 本体承载完整 Agent Runtime，统一编排结构化设备工具、GUI、内置浏览器、Android/Alpine 终端与 Skills，让模型不只会看着屏幕点击，也能直接调用系统能力、理解本机上下文并完成复杂任务。

当前 Xposed 入口适配覆盖 ColorOS 小布助手与 HyperOS 超级小爱；ColorOS 还支持 Gemini 与一圈即搜。ColorOS 和 HyperOS 是当前系统助手入口的适配范围，不是 Eta App 本体的设备支持边界。

## 核心能力

- **Agent Runtime**：持续编排模型与工具调用，支持任务取消、运行中补充指令、结果归档、状态恢复和外部系统助手入口
- **设备能力直达**：通过结构化工具设置闹钟与计时器、控制媒体和音量、读取设备状态、切换 Wi-Fi/蓝牙，并执行受边界保护的系统操作
- **个人上下文**：按需检索相册、文件、日历、联系人、通话、短信、通知历史、应用活动、健康摘要，以及 ColorOS 便签、录音摘要、小布记忆和个人订单
- **GUI 操作手机**：优先读取无障碍 UI 树，只有节点不足或任务依赖视觉信息时才按需获取原图；支持点击、长按、滑动、滚动、输入、启动 App 和系统按键
- **图片与文件理解**：读取系统相册 URI 或本机图片路径，也能发现 QQ、微信近期聊天图片缓存并交给视觉模型分析
- **Root 与 Linux**：使用 Android `user`/`root` Shell、文件工具和异步任务；可选安装 Alpine Linux，提供 Python、Git、Bash、jq、OpenSSL 和 SQLite 等工具
- **浏览器与 Skills**：在内置浏览器中读取和操作网页，按需安装、启用和读取 Skills，扩展 Agent 的任务方法与专业知识
- **长期记忆**：使用本机 `MEMORY.md` 保存稳定偏好和项目上下文，按需注入、支持编辑与清空，并通过 revision 与原子写入避免冲突
- **模型与 BYOK**：支持 OpenAI-compatible、Anthropic 协议，以及多个内置或自定义模型提供商；模型、API Key 与能力开关均由用户控制

## 系统助手与 Xposed 能力

### ColorOS

- 接管小布的文字、图片与有限多轮上下文，将请求交给 Eta Agent Runtime
- 接管原属小布的电源键与默认数字助理链路，让 ColorOS 可以直接唤起 Gemini
- 启用并修正 `contextual_search`，将手势条长按和双指识屏创建为一圈即搜入口

### HyperOS

- 接管超级小爱的文字请求与单张本地图片或截图，交给同一套 Eta Agent Runtime
- 接管前置检查失败时会回到原生小爱链路，避免影响未由 Eta 处理的请求

## 数据与权限边界

- 设备直达、敏感信息读取、敏感设备操作、浏览器与终端工具均可独立关闭
- 通知正文、短信验证码、Wi-Fi 密码、日志及个人上下文等敏感原始结果不会写入持久会话
- 私有数据库仅通过有界的只读临时快照查询，不修改原始数据，查询结束后清理快照
- GUI、Root、位置、通知与使用情况访问等能力仍需用户在系统或 Eta 中明确授权

## 运行要求

- Android 14（API 34）及以上
- 完整功能需要 Root，以及支持 libxposed API 102 的 LSPosed 环境
- 系统入口 Hook 依赖具体 ROM 与目标系统组件版本，系统或应用大版本更新后可能需要重新适配
- Agent 采用 BYOK，需要自行配置模型提供商、模型与 API Key

## 下载与升级

APK 请从本仓库 [Releases](https://github.com/Xposed-Modules-Repo/fuck.andes/releases) 下载。源码、完整安装步骤、界面预览与技术说明请查看 [Eta 主仓库](https://github.com/Mangi-11/Eta)。

> 从 1.5.1 或更早版本升级时请注意：Eta 2.0.0 起更换了签名证书，无法直接覆盖安装旧版，需要先卸载再安装。
