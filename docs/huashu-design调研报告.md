# huashu-design 调研报告

> HTML-native design skill for Claude Code
> 调研时间：2026-05-22
> 来源：https://github.com/alchaincyf/huashu-design

---

## 1. 项目概述

**一句话描述**：一句话让 AI Agent 在 3-30 分钟内交付产品发布动画、可点击 App 原型、可编辑 PPT、印刷级信息图——不是"AI 做得还行"，是看起来像真实设计团队做的。

**作者**：花叔（Alchain Hust）

**License**：MIT（2026-05-14 开源）

**支持 Agent**：Claude Code、Cursor、Codex、Trae、OpenClaw、Hermes 等所有支持 markdown skill 的 Agent

---

## 2. 核心能力

| 任务 | 交付物 | 耗时 |
|------|---------|------|
| 可交互原型（App/Web） | 单文件 HTML · 真实 iPhone 边框 · 可点击 · Playwright 验证 | 10-15 分钟 |
| 幻灯片 | HTML deck + 可编辑 PPTX | 15-25 分钟 |
| 动效设计 | MP4（25fps/60fps 插值）+ GIF + BGM | 8-12 分钟 |
| 设计变体 | 3+ 方案并行 · 参数可调 · 跨维度探索 | 10 分钟 |
| 信息图 | 印刷级字体 · PDF/PNG/SVG 导出 | 10 分钟 |
| 设计方向顾问 | 5 大学派 × 20 种风格 · 推荐 3 个方向 | 5 分钟 |
| 5 维专家评审 | 雷达图 + Keep/Fix/Quick Wins | 3 分钟 |

---

## 3. 核心流程

### 3.1 5 步品牌协议（Brand Protocol）

当任务涉及具体品牌时，强制执行：

| 步骤 | 动作 |
|------|------|
| 1. Ask | 6 类资产清单：logo / 产品图 / UI 截图 / 色板 / 字体 / 品牌指南 |
| 2. Search | 官方渠道搜索（.com/brand、press、product pages 等）|
| 3. Download | 三条 fallback 路径下载资产 |
| 4. Verify + Extract | 验证 logo 精度、图片分辨率、UI 时效性 |
| 5. Freeze | 写入 brand-spec.md，固化所有路径 |

### 3.2 典型工作流

```
一句话需求
    ↓
5 大学派 × 20 风格 → 推荐 3 个方向
    ↓
并行生成 3 个 demo → 用户选择
    ↓
Playwright 验证点击交互
    ↓
导出 MP4/GIF/PDF/PNG/SVG
```

---

## 4. 与 open-design 的关系

huashu-design 是 open-design 的**上游设计哲学参考**：

open-design README 明确写道：
> [alchaincyf/huashu-design](https://github.com/alchaincyf/huashu-design) — the design-philosophy compass. Junior-Designer workflow, the 5-step brand-asset protocol, the anti-AI-slop checklist, the 5-dimensional self-critique.

**open-design 的 skills/daemon/src/prompts/discovery.ts** 直接引用了 huashu-design 的方法论。

---

## 5. 与 guizang-ppt-skill 的区别

| 维度 | huashu-design | guizang-ppt-skill |
|------|---------------|---------------------|
| **交付物** | 原型/动画/信息图/PPT | 单文件 HTML PPT |
| **交互** | ✅ 可点击 | ❌ 横向翻页 |
| **风格** | 5 大学派 × 20 风格 | 电子杂志风 + 瑞士风 |
| **平台** | Web/App 原型 | 演讲 PPT |
| **动画** | ✅ MP4/GIF 导出 | 横向翻页 + 低性能静态 |

---

## 6. 安装方式

```bash
npx skills add alchaincyf/huashu-design
```

---

## 7. 优缺点分析

### 优点

- **一句话交付**：不需要 Figma，不需要 After Effects
- **真实可交互**：Pixel-accurate iPhone 边框，Playwright 验证点击
- **品牌协议强制**：5 步确保不乱用品牌资产
- **MIT 许可**：完全开源，商业可用
- **多 Agent 支持**：Claude Code、Cursor、Trae、OpenClaw、Hermes 均可

### 缺点

- **需要 AI Agent 环境**：纯 Prompt 无法使用
- **中文文档为主**：英文用户可能有门槛
- **生成时间较长**：3-30 分钟，看复杂度

---

## 8. 参考链接

- GitHub：https://github.com/alchaincyf/huashu-design
- MIT License（2026-05-14 开源）
- Demo Gallery：见仓库 README