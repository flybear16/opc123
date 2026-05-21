# open-design 调研报告

> Local-first, open-source alternative to Claude Design
> 调研时间：2026-05-21
> 来源：https://github.com/nexu-io/open-design

---

## 1. 项目概述

**一句话描述**：开源、本地优先的 Claude Design 替代品，将 16 种 AI 编码 Agent（Claude Code、Codex、Cursor 等）作为设计引擎，通过 31 个可组合 Skills 和 72 个企业级设计系统驱动设计工作流。

**核心理念**：不重复造轮子——最强的编码 Agent 已经在你的电脑上，把它们接入设计工作流，而不是再造一个 Agent。

**定位**：Web 部署、BYOK（自带 Key）、本地运行，设计产物优先（artifact-first）。

---

## 2. 核心元数据

| 字段 | 值 |
|------|-----|
| 仓库 | nexu-io/open-design |
| 语言 | TypeScript |
| License | MIT |
| Stars | 40,000+（两周内达成） |
| 官方文档 | 10+ 语言（含简体中文） |
| 更新频率 | 高频迭代，0.8.0 即将发布 |
| 官网 | https://open-design.ai/ |

---

## 3. 技术架构

### 3.1 核心设计

```
用户 Prompt → 5个视觉方向选择 → TodoWrite 计划流 →
项目文件夹生成（模板 + 布局库 + 检查清单）→
Agent 预检（5维自检）→ <artifact> 沙箱 iframe 渲染
```

### 3.2 四大多层依赖

| 来源 | 贡献内容 |
|------|----------|
| [alchaincyf/huashu-design](https://github.com/alchaincyf/huashu-design) | 设计哲学罗盘：Junior-Designer 工作流、5步品牌资产协议、抗 AI 垃圾检查清单、5维自检 |
| [op7418/guizang-ppt-skill](https://github.com/op7418/guizang-ppt-skill) | 幻灯片模式：杂志风格布局、WebGL hero、P0/P1/P2 检查清单 |
| [OpenCoworkAI/open-codesign](https://github.com/OpenCoworkAI/open-codesign) | UX 标杆：流式 artifact 循环、沙箱 iframe 预览、5格式导出（HTML/PDF/PPTX/ZIP/Markdown） |
| [multica-ai/multica](https://github.com/multica-ai/multica) | 守护进程架构：PATH 扫描 Agent 检测、本地守护进程作为唯一特权进程 |

### 3.3 支持的编码 Agent（16个）

Claude Code · Codex CLI · Devin for Terminal · Cursor Agent · Gemini CLI · OpenCode · Qwen Code · Qoder CLI · GitHub Copilot CLI · Hermes (ACP) · Kimi CLI (ACP) · Pi (RPC) · Kiro CLI (ACP) · Kilo (ACP) · Mistral Vibe CLI (ACP) · DeepSeek TUI

---

## 4. 核心功能

### 4.1 Skills（31个内置技能）

**原型模式（27个）**
web-prototype · saas-landing · dashboard · mobile-app · gamified-app · social-carousel · magazine-poster · dating-web · sprite-animation · motion-frames · critique · tweaks · wireframe-sketch · pm-spec · eng-runbook · finance-report · hr-onboarding · invoice · kanban-board · team-okrs 等

**幻灯片模式（4个）**
guizang-ppt · simple-deck · replit-deck · weekly-update

按场景分组：design / marketing / operation / engineering / product / finance / hr / sale / personal

### 4.2 设计系统（72个企业级）

内置 129 个设计系统，包括：
Linear · Stripe · Vercel · Airbnb · Tesla · Notion · Anthropic · Apple · Cursor · Supabase · Figma · Xiaohongshu 等

### 4.3 媒体生成

| 类型 | 模型 | 用途 |
|------|------|------|
| 图片生成 | gpt-image-2 (Azure/OpenAI) | 海报、头像、信息图、插画地图 |
| 视频生成 | Seedance 2.0 (ByteDance) | 15秒电影感文字转视频 / 图转视频 |
| 动态图形 | HyperFrames (HeyGen) | HTML→MP4 运动图形（产品展示、动态字体、数据图表、社交叠加） |

**提示词模板库**：93个可复制提示词（43个 gpt-image-2 + 39个 Seedance + 11个 HyperFrames）

### 4.4 视觉方向（5个流派）

Editorial Monocle · Modern Minimal · Warm Soft · Tech Utility · Brutalist Experimental

每个流派配备确定性 OKLch 色板 + 字体栈。

### 4.5 设备框架

iPhone 15 Pro · Pixel · iPad Pro · MacBook · Browser Chrome（像素级精确）

### 4.6 导入导出

- **导入**：支持 Claude Design 导出 ZIP 直接导入，Agent 继续编辑
- **导出**：HTML / PDF / PPTX / MP4 / ZIP / Markdown

---

## 5. 本地运行机制

### 5.1 启动方式

```bash
pnpm tools-dev
```

单一入口，管理 start / stop / run 生命周期。

### 5.2 守护进程架构

本地守护进程在项目文件夹中生成 CLI，Agent 获得真实的 Read / Write / Bash / WebFetch 能力，针对真实磁盘环境操作。

### 5.3 BYOK 代理层

协议特定的 API 代理 `/api/proxy/{anthropic,openai,azure,google,ollama,senseaudio}/stream`，支持粘贴 baseUrl + apiKey 后选择模型，内部 IP/SSRF 在守护进程边缘阻止。

### 5.4 数据持久化

SQLite 数据库（`.od/app.sqlite`），存储：projects · conversations · messages · tabs · saved templates。

---

## 6. 与 Claude Design 对比

| 维度 | open-design | Claude Design |
|------|-------------|----------------|
| **开源** | ✅ MIT | ❌ 闭源 |
| **自托管** | ✅ 可本地部署 | ❌ 云端-only |
| **模型选择** | ✅ 16种 Agent + 6种 API | ❌ 仅 Anthropic |
| **自备 Key** | ✅ BYOK，每层可替换 | ❌ 付费订阅 |
| **Skills 数量** | 31 个内置 | 限定 |
| **设计系统** | 72 个企业级 | 封闭生态 |
| **更新速度** | 活跃迭代（两周 40k Stars）| 官方周期 |

---

## 7. 优缺点分析

### 优点

- **完全开源 MIT**：代码透明，可自由定制
- **本地优先**：数据不出本机，保护隐私
- **多 Agent 支持**：不锁定单一工具，PATH 自动检测
- **设计系统丰富**：开箱即用 72 个企业级设计系统
- **媒体生成集成**：图片 + 视频 + 动图全覆盖
- **社区活跃**：两周 40k Stars，发展迅猛

### 缺点

- **依赖本地 Agent**：没有安装编码 CLI 就没有设计引擎
- **前端要求**：需要 Node.js + pnpm 开发环境
- **Electron 缺失**：目前是 Web 应用，无桌面客户端
- **复杂度高**：Skills + 设计系统 + 多 Agent 组合，学习曲线较陡

---

## 8. 适用场景

- 有多个编码 Agent（Claude Code、Cursor 等）且希望统一设计工作流的团队
- 对数据隐私有要求，不希望设计素材上云的团队
- 需要快速生成高质量设计稿（Web 原型、幻灯片、PPT）的个人开发者
- 设计系统有品牌规范需求的企业

---

## 9. 参考链接

- GitHub：https://github.com/nexu-io/open-design
- 官网：https://open-design.ai/
- 官方文档：https://github.com/nexu-io/open-design/blob/main/QUICKSTART.md
- Discord 社区：https://discord.gg/qhbcCH8Am4
- X（推特）：https://x.com/nexudotio