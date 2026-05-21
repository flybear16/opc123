# dbskill 调研报告

> dontbesilent 商业诊断工具箱 · 从 12,307 条推文中提炼方法论
> 调研时间：2026-05-21
> 来源：https://github.com/dontbesilent2025/dbskill

---

## 1. 项目概述

**一句话描述**：dontbesilent 的商业诊断 Skills 工具箱，从 12,307 条推文中提炼方法论，做成 19 个 Agent Skill，覆盖商业诊断、内容诊断、执行力诊断、目标清晰化、交互式学习等全流程。

**核心理念**：诊断不再是单次问诊——存档、拉回、合并报告，跨会话持续跟踪。

**最新版本**：v2.9.1（2026-05-18）

---

## 2. 核心元数据

| 字段 | 值 |
|------|-----|
| 仓库 | dontbesilent2025/dbskill |
| 语言 | Markdown / Shell |
| License | CC BY-NC 4.0 |
| 作者 | dontbesilent（X、小红书、抖音） |
| 最新更新 | v2.9.1（2026-05-18） |
| 支持 Agent | Claude Code、Codex、Cursor、Trae Solo 等 |
| 知识原子 | 4,176 条（JSONL 格式） |

---

## 3. 核心 Skills（19个）

### 3.1 核心诊断流程

| Skill | 功能 |
|-------|------|
| `/dbs` | 主入口，自动路由到对的工具 |
| `/dbs-diagnosis` | 商业模式诊断。消解问题，不回答问题 |
| `/dbs-benchmark` | 对标分析。五重过滤，排除噪音 |
| `/dbs-content` | 内容创作诊断。五维检测 |

### 3.2 内容相关

| Skill | 功能 |
|-------|------|
| `/dbs-hook` | 短视频开头优化。诊断 + 生成方案 |
| `/dbs-xhs-title` | 小红书标题公式。75 个爆款公式匹配 |
| `/dbs-ai-check` | AI 写作特征识别。22 条特征扫描，只诊断不改 |

### 3.3 执行与目标

| Skill | 功能 |
|-------|------|
| `/dbs-action` | 执行力诊断。阿德勒框架 |
| `/dbs-goal` | 目标清晰化。把模糊目标审计成可检查的交付物 |
| `/dbs-slowisfast` | 慢就是快。摩擦建造资产，找到值得慢做的环节 |
| `/dbs-deconstruct` | 概念拆解。维特根斯坦式审查 |
| `/dbs-good-question` | 好问题生成器。把模糊问题改成 Agent 可推理的问题说明书 |

### 3.4 学习与存档

| Skill | 功能 |
|-------|------|
| `/dbs-learning` | 交互式学习。把课题拆成连续文章，根据反馈生成下一篇 |
| `/dbs-save` | 把诊断结论存档到本地（每次新增，不覆盖） |
| `/dbs-restore` | 拉出上次的存档，接着走 |
| `/dbs-report` | 把多次存档合并成一份可分享的 markdown 报告 |

### 3.5 聊天室

| Skill | 功能 |
|-------|------|
| `/dbs-chatroom` | 定向聊天室。多角色对话 + 判官总结 |
| `/dbs-chatroom-austrian` | 奥派经济聊天室。哈耶克 × 米塞斯 × Claude 三人对话 |

### 3.6 工具

| Skill | 功能 |
|-------|------|
| `/dbs-agent-migration` | Agent 工作台迁移。统一 Claude Code / Codex 双端 |

---

## 4. 核心创新

### 4.1 诊断状态管理三件套（v2.7.0）

```
诊断 → /dbs-save（存档）
    ↓
下次开新对话 → /dbs-restore（拉回）
    ↓
攒够多次 → /dbs-report（合并报告）
```

- **存档路径**：`~/.dbs/sessions/{项目名}/`
- **报告路径**：`~/.dbs/reports/{项目名}/`
- **项目隔离**：按当前目录名自动隔离，小红书诊断和线下课诊断不会混

### 4.2 Skill 自动推荐链路

每个 Skill 会根据当前诊断结果推荐下一步：

| 当前状态 | 推荐 |
|---------|------|
| diagnosis 发现方向成立但缺路径 | → benchmark |
| diagnosis 核心卡点是心理/执行 | → action |
| diagnosis 关键决策走捷径 | → slowisfast |
| 问题概念没定义清楚 | → deconstruct |
| "问题"是空转目标 | → goal |
| benchmark 找到对标后 | → content |
| content 需要标题 | → xhs-title |
| content 检测出 AI 味 | → ai-check |
| 有结论的节点 | → dbs-save |
| 说"上次""接着" | → dbs-restore |
| 攒 ≥3 份存档 | → dbs-report |

---

## 5. 知识库

### 5.1 原子库（4,176 条知识原子）

结构化 JSON 格式：

```json
{
  "id": "2024Q4_042",
  "knowledge": "判断一个生意能不能做，必要条件之一是你能不能说出这个产品的颜色",
  "original": "...",
  "url": "https://x.com/dontbesilent/status/...",
  "date": "2024-10-01",
  "topics": ["商业模式与定价", "语言与思维"],
  "skills": ["dbs-diagnosis", "dbs-deconstruct"],
  "type": "anti-pattern",
  "confidence": "high"
}
```

**字段说明**：

| 字段 | 说明 |
|------|------|
| topics | 10 个主题分类（可多选） |
| skills | 关联的 Skill |
| type | principle / method / case / anti-pattern / insight / tool |
| confidence | high / medium / low |

### 5.2 Skill 知识包

每个 Skill 有 2 个知识包：
- **框架方法论**：诊断框架、公理体系
- **案例库**：真实商业案例和反面案例

### 5.3 不安装 Skill 也能用

| 场景 | 方式 |
|------|------|
| 给 AI 加商业诊断 | 把 diagnosis_公理与诊断框架.md 粘贴到 system prompt |
| 做 RAG 知识库 | 导入 atoms.jsonl 到向量数据库 |
| 只要案例 | 过滤 type: "case" 或 type: "anti-pattern" |
| 做 chatbot | 方法论做 system prompt + 原子库做 RAG |

---

## 6. 安装方式

### 6.1 Claude Code

```bash
# 添加市场
claude plugin marketplace add dontbesilent2025/dbskill

# 安装全套
claude plugin install dbs@dontbesilent-skills

# 更新
claude plugin marketplace update dontbesilent-skills
claude plugin update dbs@dontbesilent-skills
/reload-plugins
```

### 6.2 通用（一键安装）

```bash
npx -y skills add dontbesilent2025/dbskill -g --all
```

### 6.3 Trae Solo

下载最新的 `dbskill-v版本号.zip`，解压后里面是 19 个独立的 skill zip，逐个拖进「上传技能」窗口。

### 6.4 本地构建

```bash
bash tools/build-skills.sh
# 产物在 dist/skills/
```

---

## 7. 与 opc-skills 的区别

| 维度 | dbskill | opc-skills |
|------|---------|------------|
| **定位** | 商业诊断 + 执行力 | 产品调研 + 设计素材 |
| **方法论来源** | 12,307 条推文提炼 | 独立开发者实战 |
| **Skills 数量** | 19 个 | 12 个 |
| **核心功能** | 诊断→存档→报告 | 调研→域名→Logo→SEO |
| **知识库** | 4,176 条原子（开放） | 无公开知识库 |
| **License** | CC BY-NC 4.0 | Apache 2.0 |

**互补关系**：dbskill 负责商业诊断，opc-skills 负责产品执行。

---

## 8. 优缺点分析

### 优点

- **方法论扎实**：从 12,307 条推文提炼，不是概念包装
- **诊断链路完整**：direction → benchmark → content，逻辑严密
- **跨会话存档**：save/restore/report 解决 AI 失忆问题
- **Skill 自动推荐**：不需要用户手动选择下一步
- **知识库完全开放**：4,176 条原子可独立使用
- **多 Agent 支持**：Claude Code / Codex / Cursor / Trae Solo 均可

### 缺点

- **CC BY-NC 4.0**：非商业用途可用，商业需单独授权
- **中文为主**：推文来自 dontbesilent，主要中文内容
- **诊断偏主观**：基于个人经验，非通用框架
- **Skill 数量仍在增长**：v2.9.1 还在快速迭代

---

## 9. 适用场景

- 独立创业者/Solopreneur 做商业诊断
- 内容创作者做内容方法论审计
- 任何需要把模糊问题拆解成可执行方案的人
- 需要 AI Agent 有长期记忆和跨会话跟踪能力的场景

---

## 10. 参考链接

- GitHub：https://github.com/dontbesilent2025/dbskill
- Releases：https://github.com/dontbesilent2025/dbskill/releases
- 作者 X：https://x.com/dontbesilent
- 作者小红书：https://xhslink.com/m/637xuspR4iI