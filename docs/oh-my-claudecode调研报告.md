# oh-my-claudecode (OMC) 调研报告

> Teams-first Multi-agent orchestration for Claude Code
> 调研时间：2026-05-22
> 来源：https://github.com/topics/oh-my-claudecode

---

## 1. 项目概述

**一句话描述**：类比 oh-my-zsh 的 Claude Code 插件框架——将多个 AI Agent（Claude、Codex 等）编排成团队，协同完成软件开发全流程。

**核心理念**：Two AI models enter. Better code leaves.

**定位**：多模型编排框架，让不同模型做它最擅长的事。

---

## 2. 核心元数据

| 字段 | 值 |
|------|-----|
| 类型 | Multi-agent Orchestration Framework |
| 灵感来源 | oh-my-zsh |
| 定位 | Teams-first 多智能体编排 |
| 支持模型 | Claude（主力）、Codex（验证）|
| License | MIT（各仓库不同）|
| 生态规模 | 11+ 相关仓库 |

---

## 3. 核心生态项目

### 3.1 核心框架

| 项目 | 功能 |
|------|------|
| [jhcdev/omc-codex](https://github.com/jhcdev/omc-codex) | Cross-model 编排，Claude 构建 + Codex 验证 |
| [omc-visual](https://github.com/0ldManPlaying/omc-visual) | OMC 浏览器可视化界面 |
| [chan9yu/dotclaude](https://github.com/chan9yu/dotclaude) | OMC 多智能体编排 + plugins + hooks |

### 3.2 插件生态

| 项目 | 功能 |
|------|------|
| codebase-analysis-skill | 从源码生成深度技术文档，零幻觉 |
| ralph-super-simple | Phase-based 迭代执行模式 |
| omc-codex | Cross-model 编排，Claude vs Codex |
| oss-contribution-harness | 回归安全 OSS 贡献 pipeline |
| opencode-senate | OpenCode 自动 Agent 编排器 |
| spec-skill | OMC 的 Spec 驱动开发工作流 |
| vibe-coding-template | OMC + Codex/Gemini 多智能体编排引导模板 |

---

## 4. omc-codex 详解

### 4.1 核心思路

Claude 和 Codex 各有所长：

| 任务 | Claude 优势 | Codex 优势 |
|------|-----------|-----------|
| 规划与架构 | ✅ 深度推理 | - |
| 复杂实现 | ✅ 多文件上下文（ralph loop）| - |
| 快速修复 | - | ✅ 沙箱快速 |
| 架构设计 | ✅ deep reasoning | - |
| 对抗性审查 | - | ✅ 质疑姿态 |
| 结构化审查 | - | ✅ 快速 JSON 输出 |
| 合成与决策 | ✅ 优先级排序 | - |

**自动切换**：一方 rate limit 或不可用时，另一方自动接管。

### 4.2 核心命令

| 命令 | 功能 |
|------|------|
| `/omcx:forge` | 完整 pipeline：plan → blind TDD → build → stress harden → review → ship |
| `/omcx:pipeline` | 自动化 CI/CD 风格流水线 |
| `/omcx:auto-ralph` | Claude 磨 + Codex 验证，循环直到两者一致 |
| `/omcx:auto-plan` | Claude 设计 + Codex 审查 |
| `/omcx:auto-validate` | 双 Codex 审查 + Claude 合成优先修复计划 |
| `/omcx:team N:model:role` | 并发多 Agent，指定数量和角色 |
| `/omcx:stress` | 对抗性强化：Codex 攻击，Claude 防御 |

### 4.3 blind TDD 工作流

```
Claude Opus 规划架构
    ↓
Codex 写测试（blind — 从没见过 Claude 的计划）
    ↓
Claude 从测试构建（blind — 测试即 spec）
    ↓
Codex 对抗性攻击
    ↓
Claude 修复所有 Codex 发现的漏洞
    ↓
Codex 最终结构化审查
    ↓
结果：经过双 AI 模型验证的战斗级代码
```

### 4.4 自动容错

| 情况 | 行为 |
|------|------|
| Claude rate limit | Codex 接管 build/plan/fix |
| Claude 配额耗尽 | Codex 继续所有工作 |
| Claude 上下文限制 | Codex 处理剩余步骤 |
| Codex 不可用 | Claude agents 覆盖所有角色 |
| Codex auth 失败 | Claude code-reviewer + architect |
| 双双不可用 | 停止并报告，需人工介入 |

---

## 5. 与 superpowers / gstack / opchain 对比

| 维度 | omc-codex | superpowers | gstack | opchain |
|------|-----------|------------|---------|---------|
| **核心** | 多模型编排 | 工程纪律 | 角色分工 | Checkpoint 恢复 |
| **模型** | Claude + Codex | Claude | Claude | Claude |
| **独特价值** | 双模型对抗验证 | TDD 红绿重构 | YC CEO 经验 | 跨会话记忆 |
| **容错** | 自动模型切换 | 子 Agent 并发 | 角色路由 | Checkpoint |
| **适合** | 追求代码质量极限 | 专业工程团队 | 创始人/CEO | 长时间项目 |

---

## 6. 优缺点分析

### 优点

- **双模型互补**：Claude 深度推理 + Codex 快速验证
- **自动容错**：一方不可用时自动切换，工作不中断
- **blind TDD**：测试先行，代码从测试构建，无幻觉
- **对抗性强化**：Codex 攻击找漏洞，Claude 修复
- **多 Agent 并发**：可指定 N 个 Agent 并行执行
- **零门槛安装**：一条命令安装，自动配置

### 缺点

- **依赖双模型**：需要 Claude Code + Codex CLI 两套环境
- **资源消耗**：双模型运行成本较高
- **中文资料少**：英文为主
- **生态新**：刚起步，工具链不如 gstack 完善

---

## 7. 安装方式

```bash
# 一键安装 omc-codex
curl -fsSL https://raw.githubusercontent.com/jhcdev/omc-codex/main/install.sh | bash

# Claude Code 内
/reload-plugins

# 可选：安装 Codex CLI（完整功能）
npm install -g @openai/codex
codex login
```

---

## 8. 与 opc123 的定位

**omc-codex = 第五层（开发交付）的多模型对抗工具**

```
gstack（方向指挥）
superpowers（工程纪律）
opchain（Checkpoint 记忆）
omc-codex（双模型对抗验证）← 新增
```

---

## 9. 参考链接

- GitHub Topics：https://github.com/topics/oh-my-claudecode
- omc-codex：https://github.com/jhcdev/omc-codex
- omc-visual：https://github.com/0ldManPlaying/omc-visual
- dotclaude：https://github.com/chan9yu/dotclaude