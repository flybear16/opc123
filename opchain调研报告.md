# opchain 调研报告

> Skills that ship — A skillchain and checkpoint protocol designed to get you from concept to production to ops
> 调研时间：2026-05-21
> 来源：https://opchain.dev

---

## 1. 项目概述

**一句话描述**：开源 Claude Code Skill 生态系统 + Checkpoint 协议，解决"AI 在对话之间失忆"的问题——忘记 spec、重复设计、重复提问。覆盖从概念到生产到运维的完整开发流程。

**核心理念**：If you've ever tried to build something real with Claude and watched it lose the plot between chats — forgetting your spec, redesigning what it already designed, repeating questions it asked an hour ago — opchain is what you've been looking for.

**官网**：https://opchain.dev

---

## 2. 核心元数据

| 字段 | 值 |
|------|-----|
| 类型 | 开源 Claude Skill 生态系统 |
| 语言 | Markdown（Skill 文件） |
| License | MIT |
| 最新更新 | 2026（持续活跃） |
| 核心特性 | Checkpoint 协议、跨会话记忆恢复 |

---

## 3. 核心设计

### 3.1 问题：AI 在对话之间失忆

- Chat 1：定义好 spec，开始设计
- Chat 2：AI 忘了 spec，重新问问题
- Chat 3：AI 重复设计之前设计过的内容
- Chat N：不断重复，效率归零

### 3.2 解决：Checkpoint 协议

```
Concept → Spec → Design → Build → Audit → Ship → Monitor → Migrate → Scale
    ↑                                                                            ↓
    ←←←←←←←←←←←←←←← 下次对话时恢复 Checkpoint ←←←←←←←←←←←←←←←←←←←←←
```

每个 Skill 专门负责一个环节（discovery、spec、design、build、audit、ship、monitor、migrate、scale），中央协调器路由它们。下次会话开始时，Claude 读取 Checkpoint，从断点恢复。

### 3.3 工作原理

1. **安装 Skills**：Claude Code 安装一套 Skills
2. **按名称触发**：每个 Skill 专注一个环节
3. **Checkpoint 保存**：每个环节结束时保存状态
4. **跨会话恢复**：下次对话 Claude 读取 Checkpoint，自动恢复上下文

---

## 4. 内置 Skills（Pipeline 覆盖）

| 阶段 | Skill | 说明 |
|------|-------|------|
| 发现 | discovery | 需求发现、问题识别 |
| 规格 | spec | 需求文档化、Spec 编写 |
| 设计 | design | 设计方案、设计评审 |
| 构建 | build | 代码实现 |
| 审计 | audit | 代码审查、安全审计 |
| 发布 | ship | 发布准备、部署 |
| 监控 | monitor | 运行时监控、日志分析 |
| 迁移 | migrate | 数据迁移、版本升级 |
| 扩展 | scale | 水平扩展、性能优化 |

---

## 5. 核心特性

### 5.1 Checkpoint 协议

**核心创新**：不是让 AI 自己记住，而是通过结构化 Checkpoint 文件让 AI 跨会话记住。

每个阶段结束时写入 Checkpoint 文件，包含：
- 当前进度
- 已完成事项
- 待办事项
- 关键决策
- 上下文状态

### 5.2 中央协调器

单一入口路由，按名称分发到正确的 Skill，不需要手动选择。

### 5.3 全流程覆盖

从 idea → production → ops，9 个环节全部覆盖，没有盲区。

---

## 6. 安装与使用

```bash
# 安装（假设通过 Claude Code marketplace）
# 详细安装命令需参考官方文档

# 使用流程
1. 安装 opchain skills
2. 开始新会话
3. Claude 自动读取 Checkpoint
4. 按名称触发需要的 Skill
5. 继续工作，Checkpoint 自动更新
```

> 注：opchain.dev 官网提到"No API keys. No SaaS. No vendor lock-in — every skill is a single Markdown file."，说明安装和配置极为简单。

---

## 7. 与 gstack / gbrain 的对比

| 维度 | opchain | gstack | gbrain |
|------|---------|--------|--------|
| **核心** | Pipeline + Checkpoint | 角色命令系统 | 知识图谱记忆 |
| **解决的问题** | 对话间失忆 | 单人像团队 | 长期记忆 |
| **Skill 数量** | 9 个阶段 Skills | 23 个命令 | 43 个 Skills |
| **Checkpoint** | ✅ 跨会话恢复 | ❌ | ✅ 知识图谱 |
| **适用场景** | 开发全流程 | CEO/创始人工作流 | 个人知识管理 |

**互补关系**：
- opchain = **开发流程**管理
- gstack = **决策/角色**系统
- gbrain = **记忆/知识**系统

---

## 8. 优缺点分析

### 优点

- **彻底解决 AI 失忆**：Checkpoint 协议让 AI 跨会话恢复上下文
- **全流程覆盖**：9 个阶段覆盖开发全生命周期
- **零依赖**：无 API Key、无 SaaS、无供应商锁定
- **纯 Markdown**：每个 Skill 是一个 Markdown 文件，易于理解、修改、扩展
- **中央协调器**：不需要手动选择 Skill，自动路由

### 缺点

- **GitHub 仓库未明确找到**：实际仓库 URL 需进一步确认
- **文档有限**：目前只有 opchain.dev 网站介绍
- **生态不完整**：刚发布不久，Skills 数量和质量有待验证
- **Claude Code 专用**：非通用设计，依赖 Claude 生态

---

## 9. 适用场景

- 长时间项目（跨多天/多周开发）
- 需要 Claude Code 记住每次对话进度的开发者
- 从 concept 到 production 到 ops 的完整流程管理
- 不想重复解释上下文的独立开发者

---

## 10. 与 opc123 的关联

opchain + opc-skills + gstack + gbrain = **完整 AI 开发栈**：

```
opc-skills（产品调研）
    ↓
gstack（工作流 + 角色）
    ↓
opchain（开发 Pipeline + Checkpoint）
    ↓
gbrain（知识记忆）
```

---

## 11. 参考链接

- 官网：https://opchain.dev
- GitHub 仓库：需进一步确认（搜索结果指向 opchain.dev 为主要入口）

---

## ⚠️ 注意

opchain 的 GitHub 仓库 URL 未能在本次调研中确认，官网 opchain.dev 是主要入口。建议访问官网获取最新安装方式和 GitHub 链接。