# open-codesign 调研报告

> Open-source Claude Design alternative
> 调研时间：2026-05-21
> 来源：https://github.com/OpenCoworkAI/open-codesign

---

## 1. 项目概述

**一句话描述**：MIT 许可证的开源桌面应用，本地优先，一键导入 Claude Code 或 Codex API Key，Prompt → 原型 / 幻灯片 / PDF，支持 20+ 模型（Claude、GPT、Gemini、DeepSeek、Kimi、GLM、Ollama 等）。

**核心理念**：Your prompts. Your model. Your laptop. 不绑定单一模型、不强制云端工作流。

**定位**：对标 Claude Design + v0 (Vercel) + Lovable + Bolt.new 的开源替代品，MIT 桌面应用。

---

## 2. 核心元数据

| 字段 | 值 |
|------|-----|
| 仓库 | OpenCoworkAI/open-codesign |
| 语言 | TypeScript |
| License | MIT |
| 官方文档 | 含简体中文 |
| 最新版本 | v0.2.0 (2026-05-09) |
| 支持平台 | macOS 12+ · Windows 10+ · Linux (glibc ≥ 2.31) |
| 包管理 | Homebrew · Scoop · winget · AppImage · Deb · RPM |

---

## 3. 技术架构

### 3.1 核心技术栈

- **应用框架**：Electron（桌面应用）
- **AI 引擎**：pi-ai（嵌入式 AI 运行时）
- **核心循环**：流式 artifact → 沙箱 iframe 预览 → 5格式导出

### 3.2 差异化架构

open-codesign 是**桌面 Electron 应用**，自带完整 Agent 运行时；open-design 是**Web 应用 + 本地守护进程**，依赖用户已有的 CLI。这种差异决定了：
- open-codesign 开箱即用，不需要前置安装任何编码 Agent
- open-design 更灵活，适合已有成熟 Agent 工作流的开发者

### 3.3 设计产物生成流程

```
Prompt 输入 → Agent 规划（Todo）→ 自检 + 自我修正 → 
生成带 hover / tabs / empty states 的完整页面 → 
沙箱 iframe 实时预览 → 多格式导出
```

---

## 4. 核心功能

### 4.1 支持的模型（20+）

| 类别 | 模型 |
|------|------|
| Anthropic | Claude (直接 API Key) |
| OpenAI | GPT-4o, o1, o3 系列 |
| Google | Gemini 系列 |
| OpenAI 兼容 | OpenRouter, SiliconFlow, DeepSeek 等 |
| 本地 | Ollama（无需 API Key） |
| 订阅 | ChatGPT Plus / Pro / Team → Codex 模型直接使用 |

### 4.2 一键导入

- **Claude Code / Codex 配置**：一键导入现有配置，无需复制粘贴 Key
- **ChatGPT 登录**：OAuth 直接登录，使用 Plus 订阅的 Codex 模型

### 4.3 交互模式

| 功能 | 说明 |
|------|------|
| **Comment Mode** | 点击任意元素投放评论锚点，让 Agent 仅重写该区域 |
| **Tweaks Sliders** | AI 暴露可调参数（颜色、间距、字体），滑动实时微调 |
| **Agent Panel** | 实时显示 Todo、工具调用、生成进度，随时可中断 |
| **版本历史** | 每个迭代本地保存，随时切换历史版本 |

### 4.4 内置演示（15个）

landing page · dashboard · pitch slide · pricing · mobile app · chat UI · event calendar · blog article · receipt/invoice · portfolio · settings panel 等。

### 4.5 导出格式

HTML · PDF · PPTX · ZIP · Markdown

---

## 5. 与同类产品对比

| 维度 | open-codesign | Claude Design | v0 (Vercel) | Lovable | Bolt.new |
|------|---------------|---------------|-------------|---------|---------|
| **开源** | ✅ MIT | ❌ | ❌ | ❌ | ❌ |
| **桌面原生** | ✅ Electron | ❌ Web | ❌ Web | ❌ Web | ❌ Web |
| **自备 Key** | ✅ 任意 provider | ❌ Anthropic | ❌ Vercel | ⚠️ 有限 | ❌ |
| **完全本地** | ✅ | ❌ 云端 | ❌ 云端 | ❌ 云端 | ❌ 云端 |
| **模型数量** | 20+ | 1 | 1 | 多 LLM | 多 LLM |
| **版本历史** | ✅ 本地 | ❌ | ❌ | ❌ | ❌ |
| **数据隐私** | ✅ 设备端 | ❌ 云处理 | ❌ 云处理 | ❌ 云处理 | ❌ 云处理 |
| **导出格式** | HTML/PDF/PPTX/ZIP/MD | ⚠️ 有限 | ⚠️ 有限 | ⚠️ 有限 | ⚠️ 有限 |
| **价格** | 免费（仅付模型费） | 订阅制 | 订阅制 | 订阅制 | 订阅制 |

---

## 6. 安装方式

### macOS

```bash
brew install --cask opencoworkai/tap/open-codesign
```

### Windows (Scoop)

```bash
scoop bucket add opencoworkai https://github.com/OpenCoworkAI/scoop-bucket
scoop install opencoworkai/open-codesign
```

### Linux (AppImage)

```bash
# 直接下载 .AppImage + chmod +x 即可
```

### 首次启动注意

macOS Sequoia 15+ 需要执行：
```bash
xattr -cr "/Applications/Open CoDesign.app"
```
然后正常双击运行。Windows SmartScreen 会拦截，点击"更多 → 仍要运行"即可。

---

## 7. 优缺点分析

### 优点

- **完全本地**： Electron 应用，数据不离开设备
- **多模型支持**：不绑定 Anthropic，任何兼容 API 均可使用
- **一键导入**：Claude Code / Codex / ChatGPT 配置秒级完成
- **桌面原生**：可离线运行，不依赖浏览器
- **版本控制**：本地保存每次迭代，方便回溯
- **开源 MIT**：透明可审计，可自编译打包

### 缺点

- **Electron 体积**：包体较大（通常 100MB+）
- **资源占用**：Electron + 内置 AI 运行时，内存占用较高
- **Skill 生态薄弱**：相比 open-design 的 31 个 Skills，open-codesign 更偏向通用原型
- **更新节奏**：两周一次迭代，版本尚在 0.x，功能稳定性有待验证

---

## 8. 与 open-design 的关系

open-codesign 是 open-design 的**直接上游参考**：

> open-design README 明确写道："[OpenCoworkAI/open-codesign](https://github.com/OpenCoworkAI/open-codesign) — the UX north star and our closest peer. The first open-source Claude-Design alternative."

两者核心差异：

| 维度 | open-design | open-codesign |
|------|-------------|---------------|
| **架构** | Web 应用 + 本地 daemon | 桌面 Electron 应用 |
| **Agent 依赖** | 需要已安装编码 CLI | 自带 pi-ai，无需前置依赖 |
| **Skills 数量** | 31 个内置 | 通用原型生成 |
| **设计系统** | 72 个企业级 | 基础设计系统 |
| **目标用户** | 有 Agent 工作流的开发者 | 不想装 CLI 的普通用户 |

---

## 9. 适用场景

- 不希望被任何云服务绑定的设计师/开发者
- 想用 Claude Design 但不想付订阅费的用户
- 需要本地离线生成设计稿的环境（无网络要求）
- 需要快速从 Prompt 生成可编辑 HTML/PDF 的办公场景

---

## 10. 参考链接

- GitHub：https://github.com/OpenCoworkAI/open-codesign
- 官网：https://opencoworkai.github.io/open-codesign/
- 快速开始：https://opencoworkai.github.io/open-codesign/quickstart
- 官方对比页：https://opencoworkai.github.io/open-codesign/claude-design-alternative
- v0.2.0 发布说明：https://github.com/OpenCoworkAI/open-codesign/releases/tag/v0.2.0