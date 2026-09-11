<div align="center">

<img src="docs/img/logo.png" width="128" alt="LePlayer" />

# LePlayer

**以前用流媒体，后来开始自己存歌。**
**世界正在被算法趋同，我的喜欢拒绝同步。**
你的音乐，只属于你。

为听感而生的跨平台桌面音乐播放器
Kotlin × Rust 双引擎 · WASAPI 独占 bit-perfect 输出 · 源率直出 · 全格式 HiFi 解码

![Platform](https://img.shields.io/badge/Platform-Windows-blue)
![macOS/Linux](https://img.shields.io/badge/macOS%20%2F%20Linux-Coming%20Soon-lightgrey)
![Version](https://img.shields.io/badge/Version-v1.5.4-brightgreen)
![Kotlin](https://img.shields.io/badge/Kotlin-100%25-blueviolet)
![Rust](https://img.shields.io/badge/Rust-Audio-orange)

[🌐 在线预览](https://leplayer-studio.github.io/LePlayer/) · [核心特性](#核心特性--highlights) · [双引擎架构](#双引擎架构--dual-engine) · [下载安装](#下载安装--download)

<img src="docs/img/dark-library.png" width="860" alt="LePlayer 主界面预览" style="border-radius:12px;margin-top:20px;" />

</div>

---

## 为什么选 LePlayer？ / Why LePlayer?

- **bit-perfect 输出** — WASAPI 独占模式直通声卡，采样率自适应，源率直出零重采样损失
  - *bit-perfect output* — WASAPI exclusive mode feeds the DAC directly; auto sample-rate adaptation with source-rate-direct, zero resampling loss
- **Rust 原生引擎** — 原生音频底层 + 环形缓冲 + 欠载淡出保护，长时间播放稳定可靠
  - *Rust native engine* — native audio layer with ring buffer + underflow fade, stable for long sessions
- **原生 UI** — Compose Desktop + Material 3 原生渲染；深浅主题、动态取色、桌面歌词、迷你播放器一应俱全
  - *Native UI* — Compose Desktop + Material 3; light/dark themes, dynamic color, desktop lyrics, mini-player
- **专业音频管线** — 高质量重采样、严格背压控制、解码与输出解耦，听感经得起推敲
  - *Pro audio pipeline* — high-quality resampling, strict back-pressure, decode/output decoupled

## ✨ 核心特性 / Highlights

### 🔊 音频引擎 / Audio Engine

| 能力 | 说明 |
|---|---|
| WASAPI 双模式 | 共享模式（系统混音）+ 独占模式（bit-perfect） |
| 采样率自适应 | 自动检测设备原生采样率；支持源率直出（跳过重采样，零音质损失） |
| 高质量重采样 | 高精度 SRC 算法，防过冲削波 |
| 预填充启动 | 启动 / 切歌先填满缓冲再开流，消除空缓冲欠载 |
| 背压控制 | 写入速率严格跟随播放速率，节奏不受 GC 干扰 |
| 解耦架构 | 解码处理与音频输出分离，互不拖累 |
| Rust 底层引擎 | 原生音频输出，缓冲管理与欠载淡入淡出保护 |

### 🖥️ 界面交互 / UI & Interaction

- **Material 3 原生 UI** — 深浅主题 + 动态取色，Compose Desktop 原生渲染，不是套壳网页
- **全局右键菜单** — 播放 / 下一首 / 收藏 / 从列表删除 / 彻底删除源文件
- **桌面歌词 + 迷你播放器** — 独立歌词窗口与迷你模式，边干活边听歌
- **系统托盘集成** — 托盘图标随主题切换，托盘菜单快捷操作
- **智选引擎** — 基于播放统计的智能推荐，支持分享卡片生成
- **歌单管理** — 文件夹 / 曲风 / 艺术家 / 专辑批量添加，进度可见

### 🗂️ 数据管理 / Library

- **全量音乐库索引** — 歌曲 / 歌单 / 艺术家 / 专辑 / 播放历史
- **文件去重** — 基于内容哈希识别，重复文件不入库
- **增量扫描** — 万曲级音乐库（≥10000 首）高效增量更新
- **封面缓存** — 异步加载，内存 / 磁盘两级缓存

## 🎨 图标与主题 / Icons & Themes

默认桌面图标采用清新的**绿色渐变**版本：

<div align="center">

<img src="docs/img/icon-green.png" width="104" alt="LePlayer 绿色图标（默认）" />

</div>

- **绿色版**为当前默认桌面图标
- **深色版**适配深色主题；深色模式下**任务栏与系统托盘图标支持自定义换标**，与桌面风格保持一致（深色图标资源随后续版本补齐）

## 🏗️ 双引擎架构 / Dual-Engine

| 层 | 职责 |
|---|---|
| 🎨 Kotlin · 应用层 | Compose Desktop + Material 3 原生渲染 UI：音乐库 / 歌单 / 播放页 / 设置，深浅主题、动态取色、桌面歌词、迷你播放器、系统托盘 |
| 🦀 Rust · 音频引擎 | 原生音频输出层：WASAPI 共享 / 独占双模式、缓冲管理与欠载保护、全格式 HiFi 解码，为听感提供底层保障 |

Kotlin 与 Rust 各展所长——UI 用 Kotlin 快速迭代，音频链路用 Rust 守住稳定与音质。

## 🎧 听感保障 / Fidelity Guarantees

- **节奏稳定** — 播放节奏不受内存回收影响，长时间聆听不漂移、不卡顿
- **防爆音** — 缓冲水位实时监控，异常时自动淡入淡出，杜绝爆音与断裂
- **零损失输出** — 设备支持时直接以文件原始采样率输出，跳过重采样环节

## 📥 下载安装 / Download

> 当前仅发布 **Windows** 版本。

- **安装包**：[`LePlayer-Setup.exe`](https://github.com/LePlayer-Studio/LePlayer/releases/latest/download/LePlayer-Setup.exe)
  （最新版自动指向，无需手动更新）
- **当前版本**：v1.5.3 · 约 138 MB
- **SHA-256**：`61d8969985ca15be48298189666b7476ff0b903e93084f60e6f73e46c26cae69`
- **平台**：Windows x64（内置运行时，无需预装 Java 环境）

**安装 / Install**

1. 下载 `LePlayer-Setup-1.5.4.exe`
2. 右键 → **以管理员身份运行**（标准用户会弹出 UAC）
3. 跟随向导完成安装，首次启动会引导选择音乐文件夹

升级安装会保留原有音乐库与设置。 / Upgrading keeps your existing library and settings.

## 🆕 本次更新 v1.5.3 / What's New

- **任务栏与系统托盘图标现在跟随深浅主题切换**（此前界面切换后图标仍停留在旧主题）
  - *Taskbar & tray icons now follow the light/dark theme*
- **音频输出稳定性提升**：优化缓冲策略与数据链路，消除高负载下的断续与削波
  - *Improved audio stability: optimized buffering & pipeline, eliminating dropouts/clipping under load*

## 🗺️ Roadmap

- [x] v1.5.3 — 当前版本：采样率自适应 · 源率直出 · 智选引擎 · 桌面歌词
- [ ] EQ / DSP 音效链完善
- [ ] macOS / Linux 打包发布
- [ ] 歌词逐行滚动与翻译
- [ ] 更多主题与图标自定义

## 📄 许可证 / License

本软件为闭源专有软件，保留所有权利（All Rights Reserved）。
音频能力基于 **FFmpeg** 构建（LGPL v2.1），随安装包提供第三方组件许可证全文与声明：

- 安装后位置：`<安装目录>\app\resources\THIRD_PARTY_NOTICES.md`
- 许可证全文：`<安装目录>\app\resources\licenses\`

## 🤝 反馈支持 / Feedback

使用中遇到问题或有好想法，欢迎前往 [Issues](https://github.com/LePlayer-Studio/LePlayer/issues) 反馈，附上问题描述与复现步骤即可。

---

<div align="center">

**如果 LePlayer 对你有用，欢迎 Star ⭐ 支持**

Made with Kotlin & Rust

</div>

