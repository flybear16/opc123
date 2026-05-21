# garrytan/gstack 调研报告

> Use Garry Tan's exact Claude Code setup: 23 opinionated tools as CEO, Designer, Eng Manager, Release Manager, Doc Engineer, QA
> 调研时间：2026-05-21
> 来源：https://github.com/garrytan/gstack

---

## 1. 项目概述

**一句话描述**：Y Combinator CEO Garry Tan 的个人 Claude Code 配置，将 AI 编码 Agent 变成虚拟工程团队——CEO 重新思考产品、工程经理锁定架构、设计师捕获 AI 垃圾、QA 打开真实浏览器测试。

**核心理念**：单人可以用正确工具比传统团队移动得更快。

**生产数据**：60天内完成 3 个生产服务、40+ 功能发布，2026 年效率是 2013 年的 **810×**。

---

## 2. 核心元数据

| 字段 | 值 |
|------|-----|
| 仓库 | garrytan/gstack |
| 语言 | Shell / Markdown |
| License | MIT |
| 作者 | Garry Tan（Y Combinator President & CEO） |
| 依赖 | Claude Code、Git、Bun v1.0+ |
| 安装时间 | 30 秒 |
| 最新贡献 | 2026 年 1,237 次提交 |

---

## 3. 核心角色（8个虚拟成员）

| 角色 | 职责 |
|------|------|
| **CEO** | 重新思考产品方向，战略审查 |
| **工程经理** | 锁定架构，/plan-eng-review |
| **设计师** | 捕获 AI 垃圾，/design-consultation、/design-shotgun、/design-html |
| **代码审查者** | 发现生产环境 bug，/review |
| **QA 负责人** | 打开真实浏览器测试，/qa |
| **安全官** | 运行 OWASP + STRIDE 审计 |
| **发布工程师** | 打包 PR，/ship、/land-and-deploy |
| **文档工程师** | 完整文档输出 |

---

## 4. 23 个工具命令

### 启动命令

| 命令 | 说明 |
|------|------|
| `/office-hours` | 描述你要构建的产品，获得初始建议 |
| `/plan-ceo-review` | CEO 视角审查功能想法 |

### 设计命令

| 命令 | 说明 |
|------|------|
| `/plan-design-review` | 设计评审计划 |
| `/design-consultation` | 设计咨询 |
| `/design-shotgun` | 快速设计草图 |
| `/design-html` | 生成 HTML 设计稿 |

### 工程命令

| 命令 | 说明 |
|------|------|
| `/plan-eng-review` | 工程评审计划 |
| `/review` | 任何分支的代码审查 |
| `/ship` | 发布准备 |
| `/land-and-deploy` | 落地部署 |
| `/canary` | 金丝雀发布 |
| `/benchmark` | 性能基准测试 |

### 运维命令

| 命令 | 说明 |
|------|------|
| `/browse` | 网页浏览（所有 web browsing 使用此命令） |
| `/connect` | 连接外部服务 |

---

## 5. 安装方式

```bash
# 1. 安装 gstack
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack
cd ~/.claude/skills/gstack
./setup

# 2. 在 CLAUDE.md 添加配置
# 添加 gstack 部分：
# - 所有 web browsing 使用 /browse skill
# - 不使用 mcp__claude-in-chrome__* 工具
# - 列出可用的 skills

# 3. 启动使用
/open office-hours  # 描述你要构建的产品
/plan-ceo-review    # CEO 视角审查
/review             # 代码审查
/qa                 # QA 测试
```

---

## 6. 效率数据

### vs 2013 Bookface

| 指标 | 2013（Bookface） | 2026（gstack） | 倍数 |
|------|------------------|---------------|------|
| 逻辑代码变更 | 14 行/天 | 11,417 行/天 | **810×** |
| 年总产出 | 2013 全年 | 2026 截至4月18日 | **240×** |
| 贡献次数 | 772 次 | 1,237 次（至今） | 1.6× |

> 注：逻辑代码变更排除了 AI 膨胀的 raw LOC，测量的是实际功能输出。

---

## 7. gstack 与 gbrain 的关系

**gstack** = **工作流 + 角色系统**（如何做事）

**gbrain** = **记忆 + 知识图谱**（记住什么）

两者互补：
- gstack 让 Agent **做**事（23 个技能命令）
- gbrain 让 Agent **记住**事（知识图谱 + 混合搜索）

Garry Tan 的完整 AI Agent 装备 = gstack（工作流）+ gbrain（记忆）。

---

## 8. 与 superpowers 的区别

| 维度 | gstack | superpowers |
|------|--------|-------------|
| **作者** | YC CEO Garry Tan | Jesse Vincent (Keyboardio) |
| **核心** | 角色扮演 + 23 个工具命令 | Agentic Skills 框架 |
| **目标** | 单人像团队一样工作 | 软件开发方法论 |
| **适用** | 有产品感的创始人/CEO | 专业工程师团队 |
| **技能数量** | 23 个命令 | 11 个 Skills |
| **工作流** | Slash 命令 | 自动触发 Skills |

---

## 9. 优缺点分析

### 优点

- **YC CEO 生产验证**：不是实验项目，是日均使用的工作流
- **零学习门槛**：30秒安装，30分钟见效
- **角色清晰**：不再对空 prompt，结构化输出
- **MIT 许可**：完全开源，可自由定制
- **效率提升 810×**：逻辑代码变更维度，已验证

### 缺点

- **平台锁定**：强依赖 Claude Code
- **角色主观**：Garry Tan 的 opinionated 风格，不一定适合所有人
- **无记忆系统**：需要搭配 gbrain 才能有长期记忆
- **缺少评估框架**：没有 gbrain 那种 Benchmark 对比

---

## 10. 适用场景

- 技术创始人/CEO，想要保持高 Ship 效率
- 初次使用 Claude Code，希望有结构化工作流指引
- 技术负责人/Staff 工程师，需要严格审查和 QA 自动化
- 想把 AI Agent 打造成虚拟工程团队的独立开发者

---

## 11. gstack + gbrain 组合使用

```
gstack（做）+ gbrain（记）
    ↓
单人 → 高效团队
```

Garry Tan 的 AI Agent 装备完整闭环：
1. `/office-hours` 定义方向（gstack）
2. `/plan-ceo-review` 战略审查（gstack）
3. `/review` 代码审查（gstack）
4. `/qa` 真实浏览器测试（gstack）
5. **gbrain** 记忆所有上下文
6. Cron 夜间 `gbrain doctor` 自治修复
7. 醒来比睡前更聪明

---

## 12. 参考链接

- gstack GitHub：https://github.com/garrytan/gstack
- gbrain GitHub：https://github.com/garrytan/gbrain
- LOC 争议说明：https://github.com/garrytan/gstack/blob/main/docs/ON_THE_LOC_CONTROVERSY.md
- 作者推特：https://x.com/garrytan