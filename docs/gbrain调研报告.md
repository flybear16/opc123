# garrytan/gbrain 调研报告

> Garry's Opinionated OpenClaw/Hermes Agent Brain
> 调研时间：2026-05-21
> 来源：https://github.com/garrytan/gbrain

---

## 1. 项目概述

**一句话描述**：Y Combinator CEO Garry Tan 的个人 AI Agent 生产大脑，17,888 页面、4,383 人、723 公司的知识图谱，21 个 Cron 任务自治运行，睡前 AI 摄入、醒来 AI 变强。

**核心理念**：Your AI agent is smart but forgetful. GBrain gives it a brain.

**定位**：自进化第二大脑，自链接知识图谱 + 混合搜索 + 自治修复，生产级验证（12天构建、正在运行中）。

---

## 2. 核心元数据

| 字段 | 值 |
|------|-----|
| 仓库 | garrytan/gbrain |
| 语言 | TypeScript / Shell |
| License | MIT |
| 最新版本 | v0.36.4.0 |
| 作者 | Garry Tan（Y Combinator President & CEO） |
| 依赖 | PGLite（2秒初始化）、pgvector、BM25 |
| 支持 Agent | OpenClaw、Hermes、Claude Code、Cursor、Windsurf |

---

## 3. 核心能力

### 3.1 自治循环（Sleep-Wake Loop）

```
Signal 检测 → 脑内搜索 → 响应 → 页面写入 → 自动链接 → 同步
（每次：脑优先 + 上下文知情 + 页面 + 定时边 + 时间线 + 反向链接）
```

- **Signal 检测器**：捕获每条消息中的想法、实体提及、待办事项
- **脑内优先查询**：任何外部 API 调用前先查本地大脑（最快、最便宜、最个性化）
- **自动链接**：页面写入时，无 LLM 调用，纯粹模式匹配 `[[wiki/people/bob]]` 语法提取实体引用
- **Cron 驱动**：夜间去重人员页面、修复引用、评分、找矛盾、预备明日任务

### 3.2 混合搜索架构

**搜索模式**：Vector (HNSW/pgvector) + BM25 关键词 + Reciprocal Rank Fusion + 来源层级增强 + 意图感知查询重写

**三种命名搜索模式**：conservative / balanced / tokenmax

**性能数据**：
- P@5: **49.1%**（图增强）vs 18.2%（图禁用）→ **+31.4 分**
- R@5: **97.9%**
- 击败 ripgrep-BM25 + 纯向量 RAG 相似幅度

### 3.3 自链接知识图谱

- **零 LLM 调用**：纯模式匹配提取实体引用
- **类型化边**：attended、works_at、invested_in、founded、advises、mentions 等
- **多跳遍历**：`gbrain graph-query people/garry-tan --depth 2`
- **+31.4 P@5 提升**：知识图谱是超越纯向量搜索的关键

### 3.4 自治修复（v0.36.4.0 新功能）

```bash
gbrain doctor --remediate --yes --target-score 90 --max-usd 5
```

- 计算依赖排序计划（sync → extract → embed → consolidate）
- 每步提交 Minion 任务
- 每步后重新检查分数
- 拒绝超出成本上限
- Cron 可无人值守运行

### 3.5 评估框架

| 评测 | 说明 |
|------|------|
| `gbrain eval longmemeval` | 对标公共 LongMemEval 基准 |
| `gbrain eval export + replay` | 捕获真实查询，回放验证代码变更 |
| `gbrain eval trajectory` | 公司时序历史，回归自动标记 |
| `gbrain founder scorecard` | 创始人准确率、一致性、增长方向、红旗检测 |

---

## 4. 技术架构

### 4.1 三种运行形态

| 形态 | 适用场景 |
|------|----------|
| **OpenClaw/Hermes Skillpack** | 已用 OpenClaw 或 Hermes 的用户（推荐 30 分钟安装） |
| **独立 Shell** | 任何 MCP 感知客户端（Claude Code、Cursor、Windsurf）或纯 shell |
| **HTTP MCP Server** | 团队共享，OAuth 2.1 + PKCE + DCR + 刷新令牌，/admin 仪表板 |

### 4.2 初始化

```bash
# OpenClaw/Hermes 用户
gbrain init --pglite
gbrain skillpack scaffold --all

# 独立 Shell
bun install -g github:garrytan/gbrain
gbrain init --pglite # 2秒启动，无服务器、无Docker
```

### 4.3 向量模型（v0.36.2.0 新默认）

**ZeroEntropy**（自研）：
- Embedding：zembed-1（1280d，Matryoshka）
- Reranker：zerank-2

| 对比 | 速度 | 成本 | 胜率（20 queries） |
|------|------|------|-------------------|
| ZeroEntropy | 442ms | $0.05/M | 11/20 |
| OpenAI | 973ms | $0.13/M | - |

60% 的 top-1 结果在使用 reranker 后被重新排序。

---

## 5. 43 个内置 Skills

Skills 路由在 `skills/RESOLVER.md`，覆盖：

| 类别 | Skills 数量 |
|------|------------|
| Signal 捕获 | signal detection |
| Ingest | idea / media / meeting 摄入 |
| Enrich | 实体丰富化 |
| Brain Ops | 脑操作 |
| Citation Fixer | 引用修复 |
| Daily Task Manager | 每日任务管理 |
| Cron Scheduler | Cron 调度 |
| Reports | 报告生成 |
| Voice | 语音 |
| Soul Audit | 灵魂审计 |
| Eval Framework | 评估框架 |
| Migrations | 数据迁移 |

---

## 6. 数据模型

### 6.1 实体类型

- **Pages**：17,888 个页面（人员、公司、笔记、会议等）
- **People**：4,383 人
- **Companies**：723 公司
- **Chronological Facts**：时序事实（## Facts 格式，支持 mrr、arr、team_size 等指标断言）
- **Typed Edges**：attended、works_at、invested_in、founded、advises、mentions

### 6.2 评分机制

| 指标 | 说明 |
|------|------|
| claim accuracy | 主张准确性 |
| consistency | 一致性 |
| growth direction | 增长方向 |
| red flags | 红旗检测 |

---

## 7. 与通用 RAG 对比

| 维度 | gbrain | 通用 RAG |
|------|--------|----------|
| **搜索方式** | Vector + BM25 + Graph + RRF | 纯向量检索 |
| **P@5** | 49.1% | 18.2% |
| **知识图谱** | 自链接，零 LLM 调用 | 无 |
| **自治修复** | `--remediate --target-score 90` | 手动 |
| **Cron 驱动** | 21 个任务夜间运行 | 无 |
| **实体关系** | 类型化边多跳遍历 | 平面检索 |
| **作者** | YC CEO 生产自用 | 通用方案 |

---

## 8. 安装方式

### 快速安装

```bash
# 方式1：OpenClaw/Hermes（推荐）
gbrain init --pglite
gbrain skillpack scaffold --all

# 方式2：独立 Shell
bun install -g github:garrytan/gbrain
gbrain init --pglite
gbrain doctor  # 验证健康状态

# 启动 MCP Server
gbrain serve        # stdio MCP（Claude Desktop / Code / Cursor）
gbrain serve --http # HTTP MCP + OAuth 2.1 + Admin 仪表板
```

### MCP 客户端

支持：Claude Desktop、Claude Code、Cursor、ChatGPT、Perplexity、Cowork

---

## 9. 优缺点分析

### 优点

- **YC CEO 生产验证**：不是概念项目，是日均运行的生产系统
- **知识图谱增强检索**：+31.4 P@5 提升，显著优于纯向量 RAG
- **零 LLM 调用图谱构建**：自动链接，不消耗 token
- **自治修复**：成本可控的自我优化，90/100 分目标
- **多跳推理**：回答"谁在 Acme AI 工作"这类需要关系推理的问题
- **ZeroEntropy 自研模型**：2.2× 速度、2.6× 成本优势

### 缺点

- **PGLite 起步**：大规模企业部署需切换到完整 PostgreSQL
- **学习曲线**：43 个 Skills + RESOLVER 路由，需要理解才能定制
- **平台锁定**：主要是 OpenClaw/Hermes 生态
- **中文文档**：目前以英文为主

---

## 10. 适用场景

- 需要个人知识管理 + AI Agent 记忆系统的个人用户
- 有大量人员/公司关系需要管理的投资人、创始人
- 希望 AI Agent 具有长期记忆和上下文的企业团队
- 对标 ChatGPT/Perplexity 的私有知识库场景

---

## 11. 参考链接

- GitHub：https://github.com/garrytan/gbrain
- 评估数据：https://github.com/garrytan/gbrain-evals
- ZeroEntropy：https://dashboard.zeroentropy.dev
- 文档：https://github.com/garrytan/gbrain/blob/master/llms.txt