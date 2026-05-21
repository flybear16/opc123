# 完整 AI 开发栈

> 基于 opc123 项目调研整理 · 2026-05-21

---

## 1. 全景图

```
┌─────────────────────────────────────────────────────────────────────────┐
│                          AI 开发栈 · 七层架构                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  第七层 │  知识记忆    │  gbrain · Archive · dbskill/save            │
│         │              │  长期记忆 + 知识图谱 + 跨会话存档               │
│  ───────│──────────────│─────────────────────────────────────────────│
│  第六层 │  增长运营    │  opc-skills · dbskill · pm-skills           │
│         │              │  SEO · 内容营销 · 数据分析 · 北极星指标         │
│  ───────│──────────────│─────────────────────────────────────────────│
│  第五层 │  开发交付    │  opchain · gstack · open-design             │
│         │              │  Checkpoint · CI/CD · 测试 · 设计稿代码化      │
│  ───────│──────────────│─────────────────────────────────────────────│
│  第四层 │  产品设计    │  open-design · open-codesign                 │
│         │              │  原型 · 幻灯片 · PPT · 图片 · 视频生成         │
│  ───────│──────────────│─────────────────────────────────────────────│
│  第三层 │  战略规划    │  dbskill · pm-skills · gstack               │
│         │              │  商业模式 · PRD · OST · 竞品分析             │
│  ───────│──────────────│─────────────────────────────────────────────│
│  第二层 │  需求发现    │  opc-skills · dbskill · pm-skills           │
│         │              │  调研 · 假设验证 · 痛点发现 · 访谈            │
│  ───────│──────────────│─────────────────────────────────────────────│
│  第一层 │  模型路由    │  ds2api · 9router · OpenRouter              │
│         │              │  多Provider负载均衡 · 故障转移 · 协议转换       │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 2. 各层详解

### 第七层 · 知识记忆

> 让 AI Agent 记住一切，跨会话不遗忘

| 工具 | 定位 | 核心能力 | 适用场景 |
|------|------|---------|---------|
| [gbrain](https://github.com/garrytan/gbrain) | 自进化第二大脑 | 知识图谱 + 混合搜索 + 自治修复 | 所有人，长期记忆 |
| [dbskill/save-restore-report](https://github.com/dontbesilent2025/dbskill) | 诊断状态存档 | 存档 + 拉回 + 合并报告 | 商业诊断跨会话跟踪 |
| [archive (opc-skills)](https://github.com/ReScienceLab/opc-skills) | Session 存档 | Markdown 索引存档 | 调试经验积累 |

```
gbrain 典型用法：
Day 1 → gbrain ingest（摄入会议/笔记/推文）
Day 2 → gbrain search "上次讨论的定价策略"
Day 7 → gbrain doctor --remediate（自治修复，P@5 目标 90/100）
```

---

### 第六层 · 增长运营

> 产品上线后的用户获取与留存

| 工具 | 定位 | 核心能力 | 适用场景 |
|------|------|---------|---------|
| [opc-skills/seo-geo](https://github.com/ReScienceLab/opc-skills) | SEO + GEO 优化 | AI 搜索引擎优化 | 搜索流量获取 |
| [opc-skills/banner-creator](https://github.com/ReScienceLab/opc-skills) | 社交素材生成 | LinkedIn/GitHub/Twitter Banner | 内容营销 |
| [dbskill/content](https://github.com/dontbesilent2025/dbskill) | 内容诊断 | 五维检测 + AI 味识别 | 内容质量把控 |
| [dbskill/ai-check](https://github.com/dontbesilent2025/dbskill) | AI 写作检测 | 22 条特征扫描 | 避免 AI 生成内容 |
| [pm-skills/metrics-dashboard](https://github.com/phuryn/pm-skills) | 指标看板设计 | 北极星 + 输入指标 + 告警阈值 | 数据驱动增长 |
| [pm-skills/north-star](https://github.com/phuryn/pm-skills) | 北极星定义 | Outcome → Opportunities → Solutions | 增长聚焦 |

---

### 第五层 · 开发交付

> 从代码到生产的完整工程链路

| 工具 | 定位 | 核心能力 | 适用场景 |
|------|------|---------|---------|
| [opchain](https://opchain.dev) | Pipeline + Checkpoint | 9 阶段覆盖，跨会话恢复 | 任何复杂项目 |
| [gstack](https://github.com/garrytan/gstack) | 23 工具虚拟工程队 | /review · /qa · /ship · /canary | 快速迭代交付 |
| [open-design](https://github.com/nexu-io/open-design) | 设计稿代码化 | HTML/PDF/PPTX/MP4 导出 | 设计到代码 |
| [gstack/review](https://github.com/garrytan/gstack) | 代码审查 | OWASP + STRIDE 安全审计 | PR 质量把控 |
| [gstack/qa](https://github.com/garrytan/gstack) | 真实浏览器测试 | 打开真实浏览器测试 | 端到端验证 |
| [gstack/ship](https://github.com/garrytan/gstack) | 发布管理 | /land-and-deploy · /canary | 零停机发布 |

```
gstack 典型用法：
/office-hours 描述产品方向
/plan-ceo-review 战略审查
/review 任意分支代码审查
/qa staging URL 真实浏览器测试
/ship 发布准备
```

---

### 第四层 · 产品设计

> 快速原型 · 可视化 · 设计系统

| 工具 | 定位 | 核心能力 | 适用场景 |
|------|------|---------|---------|
| [open-design](https://github.com/nexu-io/open-design) | 开源版 Claude Design | 31 Skills · 72 设计系统 · 16 种 Agent | 有 Agent 经验的开发者 |
| [open-codesign](https://github.com/OpenCoworkAI/open-codesign) | 桌面版设计工具 | 20+ 模型 · 一键导入 · HTML/PDF 导出 | 不想装 CLI 的用户 |
| [open-design/media](https://github.com/nexu-io/open-design) | 媒体生成 | gpt-image-2 · Seedance 视频 · HyperFrames | 海报/视频/动图 |
| [opc-skills/logo-creator](https://github.com/ReScienceLab/opc-skills) | Logo 生成 | AI Logo + SVG 导出 | 品牌设计 |
| [opc-skills/banner-creator](https://github.com/ReScienceLab/opc-skills) | Banner 生成 | 多平台社交 Banner | 运营素材 |

---

### 第三层 · 战略规划

> 商业模式 · PRD · 产品路线图

| 工具 | 定位 | 核心能力 | 适用场景 |
|------|------|---------|---------|
| [dbskill/diagnosis](https://github.com/dontbesilent2025/dbskill) | 商业模式诊断 | 消解问题，不回答问题 | 方向不清时 |
| [dbskill/benchmark](https://github.com/dontbesilent2025/dbskill) | 对标分析 | 五重过滤 · 排除噪音 | 找模仿对象 |
| [dbskill/goal](https://github.com/dontbesilent2025/dbskill) | 目标清晰化 | 模糊愿望 → 可检查交付物 | 目标空转时 |
| [pm-skills/write-prd](https://github.com/phuryn/pm-skills) | PRD 撰写 | 结构化需求文档 | 需求文档化 |
| [pm-skills/product-strategy](https://github.com/phuryn/pm-skills) | 产品战略 | 9 区块战略画布 | 路线图规划 |
| [pm-skills/opportunity-solution-tree](https://github.com/phuryn/pm-skills) | OST 机会树 | Teresa Torres 方法 | 结果导向思考 |
| [gstack/plan-ceo-review](https://github.com/garrytan/gstack) | CEO 视角审查 | 重新思考产品方向 | 战略复盘 |

---

### 第二层 · 需求发现

> 用户调研 · 假设验证 · 痛点挖掘

| 工具 | 定位 | 核心能力 | 适用场景 |
|------|------|---------|---------|
| [opc-skills/requesthunt](https://github.com/ReScienceLab/opc-skills) | 需求调研 | Reddit/X/GitHub 需求挖掘 | 冷启动调研 |
| [opc-skills/producthunt](https://github.com/ReScienceLab/opc-skills) | 产品猎人 | PH 帖子/话题/用户搜索 | 竞品发现 |
| [dbskill/discover](https://github.com/dontbesilent2025/dbskill) | 发现入口 | 诊断 → 存档 → 推荐下一步 | 方向探索 |
| [pm-skills/brainstorm-ideas](https://github.com/phuryn/pm-skills) | 多视角头脑风暴 | PM/Designer/Engineer 三角 | 创意生成 |
| [pm-skills/interview-script](https://github.com/phuryn/pm-skills) | 访谈脚本 | JTBD 探测问题 | 用户访谈 |
| [pm-skills/identify-assumptions](https://github.com/phuryn/pm-skills) | 假设识别 | Value/Usability/Viability/Feasibility | 风险发现 |
| [pm-skills/prioritize-assumptions](https://github.com/phuryn/pm-skills) | 假设排序 | Impact × Risk 矩阵 | 优先级判断 |
| [pm-skills/brainstorm-experiments](https://github.com/phuryn/pm-skills) | 实验设计 | Alberto Savoia 精益实验 | 验证假设 |
| [opc-skills/domain-hunter](https://github.com/ReScienceLab/opc-skills) | 域名搜索 | 域名比价 + 品牌检查 | 品牌命名 |

---

### 第一层 · 模型路由

> AI 模型的负载均衡与故障转移

| 工具 | 定位 | 核心能力 | 适用场景 |
|------|------|---------|---------|
| [ds2api](https://github.com/CJackHwang/ds2api) | 协议转换中间件 | OpenAI/Claude/Gemini → DeepSeek 兼容格式 | 多 API 统一入口 |
| [9router](https://github.com/topics/9router) | 模型路由网关 | Combo 故障转移 · 健康监测 · 自动重排序 | 高可用 AI 服务 |
| [OpenRouter](https://openrouter.ai/) | 商业路由 | 多模型统一入口 · 按量计费 | 快速接入 |

---

## 3. 工具链路图

### 3.1 从 0 到 1（独立产品开发）

```
想法 → opc-skills/requesthunt（需求调研）
     → dbskill/diagnosis（方向验证）
     → dbskill/benchmark（找对标）
     → dbskill/goal（目标清晰化）
     → opc-skills/domain-hunter（域名）
     → opc-skills/logo-creator + banner-creator（品牌设计）
     → open-codesign（原型设计）
     → gstack/ship（开发交付）
     → gstack/qa（测试）
     → opc-skills/seo-geo（SEO 优化）
     → gbrain（积累知识）
```

### 3.2 PM 完整工作流

```
/discover（发现）
  brainstorm-ideas → identify-assumptions → prioritize-assumptions → brainstorm-experiments

/strategy（战略）
  product-strategy → competitive-analysis → market-sizing

/content（内容）
  hook（开头优化）→ ai-check（AI 检测）→ xhs-title（标题公式）

/save-restore-report（存档）
  跨会话跟踪，合并可交付报告
```

### 3.3 gstack + gbrain 组合（Garry Tan 装备）

```
gstack（工作流）
  /office-hours → /plan-ceo-review → /review → /qa → /ship

gbrain（记忆）
  夜间 ingest → 白天 search → Cron doctor --remediate → 持续进化
```

---

## 4. 一页速查表

| 需求 | 首选工具 | 备选工具 |
|------|---------|---------|
| **需求调研** | opc-skills/requesthunt | pm-skills/brainstorm |
| **商业诊断** | dbskill/diagnosis | dbskill/benchmark |
| **PRD 撰写** | pm-skills/write-prd | dbskill/content |
| **原型设计** | open-design（开发者） | open-codesign（普通用户） |
| **代码交付** | gstack（创始人） | opchain（复杂项目） |
| **知识记忆** | gbrain（知识图谱） | dbskill/save-restore |
| **SEO/增长** | opc-skills/seo-geo | pm-skills/metrics |
| **Logo/素材** | opc-skills/logo-creator | open-design/media |
| **模型路由** | 9router（自托管） | ds2api（协议转换） |

---

## 5. 安装命令速查

```bash
# === 第二层：需求发现 ===
opc-skills/requesthunt
/plugin marketplace add ReScienceLab/opc-skills
/plugin install requesthunt@opc-skills

# === 第三层：战略规划 ===
dbskill（诊断/目标/Benchmark）
/plugin marketplace add dontbesilent2025/dbskill
/plugin install dbs@dontbesilent-skills

pm-skills（PRD/OST/战略）
/plugin marketplace add phuryn/pm-skills

# === 第四层：设计 ===
open-design
pnpm tools-dev

open-codesign
brew install --cask opencoworkai/tap/open-codesign

# === 第五层：开发交付 ===
gstack
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack

opchain（Checkpoint）
# 访问 https://opchain.dev 获取安装方式

# === 第七层：知识记忆 ===
gbrain
bun install -g github:garrytan/gbrain
gbrain init --pglite
```

---

## 6. 总结

**核心逻辑**：

1. **第一层（模型）**是基础设施，决定你能用多便宜多稳定
2. **第二层（需求）**决定你做的东西是不是真的有人要
3. **第三层（战略）**决定你做的方向对不对
4. **第四层（设计）**决定你能不能快速验证产品形态
5. **第五层（开发）**决定你能不能高效交付
6. **第六层（增长）**决定你能不能获客
7. **第七层（记忆）**决定 AI 能不能越用越聪明

**推荐的最小装备**：

```
模型路由：9router 或 ds2api
需求发现：opc-skills/requesthunt
商业诊断：dbskill（diagnosis + benchmark + action）
原型设计：open-codesign
代码交付：gstack
知识记忆：gbrain
```

---

*本文档基于 opc123 项目调研生成*
*https://github.com/flybear16/opc123*