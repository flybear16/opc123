# phuryn/pm-skills 调研报告

> PM Skills Marketplace: 65 PM skills + 36 chained workflows across 8 plugins
> 调研时间：2026-05-21
> 来源：https://github.com/phuryn/pm-skills

---

## 1. 项目概述

**一句话描述**：PM Skills 市集，65 个产品经理技能 + 36 个链式工作流，覆盖从发现到战略到执行到上市的完整流程。

**核心理念**：Generic AI gives you text. PM Skills Marketplace gives you structure.

**方法论来源**：Teresa Torres（持续发现）、Marty Cagan（Product Discovery）、Alberto Savoia（精益创业）

**支持 Agent**：Claude Code、Cowork为主，也兼容 Gemini CLI、OpenCode、Cursor、Codex CLI、Kiro 等

---

## 2. 核心元数据

| 字段 | 值 |
|------|-----|
| 仓库 | phuryn/pm-skills |
| 语言 | Markdown |
| License | MIT |
| 最新更新 | 2026（持续活跃） |
| Skills 数量 | 65 个 |
| 工作流数量 | 36 个 |
| 插件数量 | 8 个 |
| 安装方式 | Claude Code Plugin Marketplace |

---

## 3. 8 大插件（Plugins）

### 3.1 pm-product-discovery（产品发现）

**13 Skills + 5 Commands**

| Skill | 功能 |
|-------|------|
| brainstorm-ideas-existing | 现有产品的多视角头脑风暴（PM/Designer/Engineer） |
| brainstorm-ideas-new | 新产品初始发现头脑风暴 |
| brainstorm-experiments-existing | 为现有产品设计假设验证实验 |
| brainstorm-experiments-new | Alberto Savoia精益创业实验设计 |
| identify-assumptions-existing | 识别Value/Usability/Viability/Feasibility假设 |
| identify-assumptions-new | 识别8类风险假设（含GTM/Strategy/Team） |
| prioritize-assumptions | Impact × Risk矩阵 + 实验建议 |
| prioritize-features | 基于impact/effort/risk/战略对齐的优先级排序 |
| analyze-feature-requests | 按主题和战略匹配分析客户需求 |
| opportunity-solution-tree | Teresa Torres的OST（结果→机会→解决方案→实验） |
| interview-script | 结构化客户访谈脚本（JTBD探测问题） |
| summarize-interview | 访谈记录→JTBD + 满意度信号 + 行动项 |
| metrics-dashboard | 设计北极星指标 + 输入指标 + 告警阈值 |

**Commands**：`/discover`、`/brainstorm`、`/triage-requests`、`/interview`、`/setup-metrics`

### 3.2 pm-product-strategy（产品战略）

**12 Skills + 5 Commands**

覆盖：愿景制定、商业模式、定价、竞争格局扫描

### 3.3 pm-toolkit（产品工具包）

PM常用工具集

### 3.4 pm-market-research（市场调研）

市场调研相关Skills

### 3.5 pm-data-analytics（数据分析）

数据分析与指标相关Skills

### 3.6 pm-marketing-growth（营销增长）

营销与增长相关Skills

### 3.7 pm-go-to-market（上市策略）

GTM相关Skills

### 3.8 pm-execution（执行）

交付与执行相关Skills

---

## 4. 核心工作流

### 4.1 入口命令

| 命令 | 功能 |
|------|------|
| `/discover` | 完整发现周期：头脑风暴→假设映射→优先级→实验设计 |
| `/strategy` | 战略清晰化 |
| `/write-prd` | 撰写PRD |
| `/plan-launch` | 制定上市计划 |
| `/north-star` | 定义北极星指标 |

### 4.2 Skill 自动推荐链路

每个命令完成后，会推荐下一个逻辑步骤。例如：

```
/discover 发现方向成立但缺路径 → /strategy
/discover 发现用户需要GTM → /plan-launch
/strategy 发现需要市场数据 → pm-market-research
```

---

## 5. 与 deanpeters/Product-Manager-Skills 对比

| 维度 | phuryn/pm-skills | deanpeters/PM-Skills |
|------|-------------------|----------------------|
| **Skills数量** | 65个 | 49个 |
| **工作流数量** | 36个 | 6个 |
| **插件/包数量** | 8个 | 6个包（discovery/strategy/delivery/AI PM/all） |
| **方法论** | Teresa Torres/Marty Cagan/Savoia | Teresa Torres/Moore/Amazon/MITRE |
| **自动推荐链路** | ✅ 有 | ❌ 无 |
| **Skill自动加载** | ✅ 自动加载 | ❌ 需手动触发 |
| **支持Agent** | Claude Code/Cowork/其他 | Claude Code/Cowork/Codex/OpenClaw |
| **License** | MIT | CC BY-NC-SA 4.0 |

---

## 6. 安装方式

```bash
# Claude Code
# Step 1: 添加市场
claude plugin marketplace add phuryn/pm-skills

# Step 2: 安装所有插件
claude plugin install pm-toolkit@pm-skills
claude plugin install pm-product-strategy@pm-skills
claude plugin install pm-product-discovery@pm-skills
claude plugin install pm-market-research@pm-skills
claude plugin install pm-data-analytics@pm-skills
claude plugin install pm-marketing-growth@pm-skills
claude plugin install pm-go-to-market@pm-skills
claude plugin install pm-execution@pm-skills
```

### 其他 Agent（仅Skills）

```bash
# Gemini CLI
for plugin in pm-*/; do
 cp -r "$plugin/skills/"* ~/.gemini/skills/ 2>/dev/null
done

# OpenCode
mkdir -p .opencode/skills/
cp -r pm-*/skills/* .opencode/skills/
```

---

## 7. 优缺点分析

### 优点

- **数量最多**：65个Skills + 36个工作流，覆盖最全面
- **Skill自动加载**：对话中自动加载相关Skill，无需手动触发
- **命令流程完整**：/discover、/strategy、/write-prd、/plan-launch、/north-star 入口清晰
- **方法论扎实**： Teresa Torres OST、Marty Cagan Product Discovery、Alberto Savoia实验框架
- **自动推荐下一步**：Skill之间有推荐链路，不需用户自己判断

### 缺点

- **非CC BY-NC 4.0**：无明确License，但非完全开源
- **主要是Claude Code优先**：其他Agent支持Skills但不保证Commands完整
- **中文资料少**：英文为主
- **Skill数量多导致选择困难**：没有phuryn的自动加载，普通用户不知道用哪个

---

## 8. 适用场景

- 需要系统化产品发现流程的产品经理
- 希望AI Agent有结构化PM工作流的创始人/PM
- 需要从0到1做产品战略规划的场景
- 需要客户访谈、假设验证、实验设计的敏捷团队

---

## 9. 参考链接

- GitHub：https://github.com/phuryn/pm-skills
- pm-brain：https://github.com/phuryn/pm-brain