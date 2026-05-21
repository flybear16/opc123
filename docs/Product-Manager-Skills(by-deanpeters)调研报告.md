# deanpeters/Product-Manager-Skills 调研报告

> Product Management skills framework built on battle-tested methods
> 调研时间：2026-05-21
> 来源：https://github.com/deanpeters/Product-Manager-Skills

---

## 1. 项目概述

**一句话描述**：49个实战验证的PM技能框架，6个工作流，方法论来自 Teresa Torres、Geoffrey Moore、Amazon、MITRE 等顶级来源。

**核心理念**：Help product managers become more awesome at their craft — and help them send the ladder down to others.

**版本**：v0.79（2026-05-15）

**方法论来源**：Teresa Torres（持续产品发现）、Geoffrey Moore（跨越鸿沟）、Amazon（Working Backwards）、MITRE（系统分析）

---

## 2. 核心元数据

| 字段 | 值 |
|------|-----|
| 仓库 | deanpeters/Product-Manager-Skills |
| 语言 | Markdown |
| License | CC BY-NC-SA 4.0 |
| 作者 | deanpeters |
| 最新版本 | v0.79（2026-05-15） |
| Skills数量 | 49个 |
| 工作流数量 | 6个 |
| 支持Agent | Claude Code、Cowork、Codex、OpenClaw、n8n 等 |

---

## 3. 技能包（Skill Packs）

### 3.1 Discovery Pack（发现包）

| Skill | 功能 |
|-------|------|
| brainstorm-ideas | 头脑风暴 |
| identify-assumptions | 识别假设 |
| prioritize-assumptions | 优先级排序假设 |
| brainstorm-experiments | 设计实验 |

### 3.2 Strategy Pack（战略包）

| Skill | 功能 |
|-------|------|
| product-strategy | 产品战略 |
| competitive-analysis | 竞争分析 |
| market-sizing | 市场规模估算 |

### 3.3 Delivery Pack（交付包）

| Skill | 功能 |
|-------|------|
| write-prd | 撰写PRD |
| plan-sprint | Sprint规划 |
| retrospective | 复盘 |

### 3.4 AI PM Pack（AI产品经理包）

| Skill | 功能 |
|-------|------|
| pm-skill-creator | 交互式创建新Skill（v0.79新增） |
| ai-pm-workflow | AI辅助PM工作流 |

### 3.5 Organic Growth Advisor

**v0.79新增**：McKinsey增长金字塔三层诊断（L2-L5）

---

## 4. v0.79 更新内容

### 新增

- **organic-growth-advisor**：McKinsey增长金字塔诊断，三问定位增长约束，推荐路径特定实验（New Segments / New Geographies / New Distribution / New Products）
- **pm-skill-creator**（@KNE-AI贡献）：交互式Skill创建工具，通过引导对话从头设计合规Skill
- **pm-skill-creator**：社区贡献的Skill创建器

### 修复

- **输入长度保护**：run-pm.sh增加 PM_MAX_INPUT 环境变量（@xiaolai）
- **路径遍历保护**：add-a-skill.sh增加adapter名称验证和路径遍历保护（@xiaolai）
- **plugin.json修复**：修复缺失的.claude-plugin/plugin.json导致Claude Code无法发现Skill的bug（@changyan01 @harley-chenhailin）

---

## 5. 安装方式

### Claude Code

```bash
# 添加市场
/plugin marketplace add deanpeters/Product-Manager-Skills

# 安装全套
/plugin install deanpeters/Product-Manager-Skills
```

### Claude Desktop / Web

下载 [pm-skills-starter-pack.zip](https://github.com/deanpeters/Product-Manager-Skills/releases/latest/download/pm-skills-starter-pack.zip)，解压后上传ZIP到Claude Skills。

### Codex

下载 [pm-skills-codex.zip](https://github.com/deanpeters/Product-Manager-Skills/releases/latest/download/pm-skills-codex.zip)

### 分包下载

| 包 | 下载 |
|---|------|
| Starter Pack | pm-skills-starter-pack.zip |
| Discovery Pack | 02-discovery-pack.zip |
| Strategy Pack | 03-strategy-pack.zip |
| Delivery Pack | 04-delivery-pack.zip |
| AI PM Pack | 05-ai-pm-pack.zip |
| All Skills | 99-all-skills-pack.zip |

---

## 6. 使用示例

```bash
# 完整发现周期
Use the Product Manager Skills to help me frame this product problem.

# 战略规划
/discover AI-powered meeting summarizer for remote teams

# 实验设计
/brainstorm experiments existing — We need to reduce churn in our onboarding flow

# 访谈准备
/interview prep — We're interviewing enterprise buyers about their procurement workflow
```

---

## 7. 与 phuryn/pm-skills 对比

| 维度 | deanpeters/PM-Skills | phuryn/pm-skills |
|------|------------------------|-------------------|
| **Skills数量** | 49个 | 65个 |
| **工作流数量** | 6个 | 36个 |
| **插件/包数量** | 6个包 | 8个插件 |
| **方法论** | Torres/Moore/Amazon/MITRE | Torres/Cagan/Savoia |
| **Skill自动加载** | ❌ | ✅ |
| **命令推荐链路** | ❌ | ✅ |
| **支持OpenClaw** | ✅ | ❌（不明） |
| **社区贡献** | ✅（v0.79有多人贡献） | ❌ |
| **License** | CC BY-NC-SA 4.0 | MIT |

**主要区别**：
- **phuryn**：更偏Agentic工作流，Skill自动加载，自动推荐下一步
- **deanpeters**：更偏方法论学习，框架更学术化，支持OpenClaw

---

## 8. 优缺点分析

### 优点

- **方法论来源顶级**：Torres/Moore/Amazon/MITRE，不是自己发明的方法
- **社区活跃**：v0.79有3位社区贡献者提交修复和新功能
- **支持OpenClaw**：对OpenClaw用户友好
- **分包下载**：可以只安装需要的包，不用全套
- **pm-skill-creator**：自己可以创建新的Skill，形成正循环

### 缺点

- **Skills数量少于phuryn**：49 vs 65
- **无自动推荐链路**：不如phuryn的Agentic体验流畅
- **CC BY-NC-SA 4.0**：非商业用途可用，商业需授权
- **Skill需要手动加载**：不如phuryn的自动加载方便

---

## 9. 适用场景

- 需要系统性学习PM方法论的产品经理
- 使用OpenClaw而非Claude Code的用户
- 只需要特定PM技能包（不想装全套）的场景
- 需要创建自定义PM Skill的团队

---

## 10. 参考链接

- GitHub：https://github.com/deanpeters/Product-Manager-Skills
- Releases：https://github.com/deanpeters/Product-Manager-Skills/releases
- pm-brain：https://github.com/phuryn/pm-brain（相关知识库）