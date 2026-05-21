# obra/superpowers 调研报告

> An agentic skills framework & software development methodology that works
> 调研时间：2026-05-22
> 来源：https://github.com/obra/superpowers

---

## 1. 项目概述

**一句话描述**：完整的软件开发方法论框架，将编码 Agent 打造成具有专业工程素养的开发团队成员——TDD、红绿重构、YAGNI、DRY、内省式自检。

**核心理念**：Give your agent Superpowers — 不是让 AI 随意写代码，而是训练它像高级工程师一样有纪律地工作。

**作者**：Jesse Vincent（Keyboardio）——著名开源开发者

---

## 2. 核心元数据

| 字段 | 值 |
|------|-----|
| 仓库 | obra/superpowers |
| 语言 | Markdown |
| License | MIT |
| 作者 | Jesse Vincent（Keyboardio 创始人） |
| 最新更新 | 2026（持续活跃） |
| 支持 Agent | 8种（Claude Code、Codex CLI、Codex App、Factory Droid、Gemini CLI、OpenCode、Cursor、GitHub Copilot CLI） |
| 安装方式 | Plugin Marketplace（Claude Code）、各 Agent 官方市场 |

---

## 3. 核心工作流

### 3.1 开发流程（核心 Loop）

```
1. brainstorm      → 设计评审（先问"你真正想做什么"）
2. writing-plans   → 生成实现计划（2-5分钟粒度任务）
3. executing-plans → 子 Agent 执行（可并发）
4. TDD             → 红绿重构循环
5. code-review     → 按严重性报告问题
6. finishing       → 合并/PR/清理
```

### 3.2 工作原理

**Phase 1：Design First（brainstorm）**

- AI 看到你要构建什么，不直接跳进去写代码
- 先通过提问提炼 Spec
- 把设计分块展示，确保可读可消化

**Phase 2：Implementation Plan（writing-plans）**

- 生成足够清晰的计划，供"有热情但品味差、缺乏判断力、无项目上下文、厌恶测试"的初级工程师执行
- 强调：红绿 TDD、YAGNI、DRY

**Phase 3：Execution（subagent-driven-development）**

- Agent 驱动子 Agent 开发流程
- 每个任务两阶段审查（Spec 合规 → 代码质量）
- 可并发执行或设检查点
- Claude 可以自主工作数小时不偏离计划

---

## 4. 内置 Skills

### 4.1 设计与计划

| Skill | 触发时机 | 功能 |
|-------|----------|------|
| brainstorming | 写代码前激活 | Socratic 设计细化，通过提问探索，方案分块展示 |
| writing-plans | 设计批准后激活 | 分解成 2-5 分钟可执行任务，每任务含文件路径和验证步骤 |
| subagent-driven-development | 计划激活后 | 每任务派生子 Agent，两阶段审查（Spec 合规 + 代码质量） |

### 4.2 测试与调试

| Skill | 触发时机 | 功能 |
|-------|----------|------|
| test-driven-development | 实现过程中激活 | RED-GREEN-REFACTOR 循环，写失败测试→看它失败→写最小代码→看它通过 |
| systematic-debugging | 调试时激活 | 4步根本原因分析（root-cause-tracing、defense-in-depth、condition-based-waiting） |
| verification-before-completion | 修复完成前激活 | 确认问题真正修复 |

### 4.3 协作

| Skill | 触发时机 | 功能 |
|-------|----------|------|
| requesting-code-review | 任务间激活 | 按严重性报告问题，Critical 阻塞进度 |
| receiving-code-review | 响应反馈 | 处理评审意见 |
| dispatching-parallel-agents | 并发执行 | 并发子 Agent 工作流 |
| finishing-a-development-branch | 任务完成时 | 验证测试，提供合并/PR/保留选项，清理 worktree |
| using-git-worktrees | 设计批准后 | 创建隔离 workspace（独立分支），验证干净测试基线 |

---

## 5. 与 gstack 的对比

| 维度 | superpowers | gstack |
|------|-------------|--------|
| **定位** | 软件开发方法论框架 | 虚拟工程团队角色扮演 |
| **核心理念** | TDD + 纪律约束 | 角色分工（CEO/Designer/QA等） |
| **作者** | Jesse Vincent（Keyboardio） | Garry Tan（YC CEO） |
| **强制力** | **强制执行**（不遵守则失败） | 推荐执行（通过角色对话） |
| **TDD** | ✅ 内置 RED-GREEN-REFACTOR | ❌ 无 |
| **子 Agent** | ✅ 并发驱动开发 | ❌ 无 |
| **YAGNI/DRY** | ✅ 内置检查 | ❌ 无 |
| **适合场景** | 专业工程团队 | 创始人/CEO 高效工作 |

**核心差异**：
- **superpowers**：像训练一个有纪律的高级工程师
- **gstack**：像指挥一个虚拟团队

---

## 6. 与 opchain 的对比

| 维度 | superpowers | opchain |
|------|-------------|---------|
| **Checkpoint 恢复** | ❌ 无 | ✅ 跨会话恢复 |
| **Pipeline 阶段** | 6 步（设计→计划→执行→测试→审查→完成） | 9 步（discovery→spec→design→build→audit→ship→monitor→migrate→scale） |
| **TDD 强制** | ✅ 红绿重构强制循环 | ❌ 无 |
| **子 Agent 并发** | ✅ 支持 | ❌ 无 |
| **适用场景** | 短周期开发（单次会话） | 长周期项目（跨多天） |

---

## 7. 安装方式

### Claude Code（Plugin Marketplace）

```bash
# 1. 注册市场
/plugin marketplace add obra/superpowers-marketplace

# 2. 安装插件
/plugin install superpowers@superpowers-marketplace
```

### Codex CLI

```bash
/plugins
# 搜索 superpowers，安装
```

### Cursor

```bash
/add-plugin superpowers
# 或在 plugin marketplace 搜索
```

### Gemini CLI

```bash
gemini extensions install https://github.com/obra/superpowers
gemini extensions update superpowers
```

### OpenCode

```bash
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md
```

---

## 8. 优缺点分析

### 优点

- **纪律严明**：不是让 AI 随意写，而是强制 TDD、红绿重构
- **子 Agent 并发**：多任务并发执行，提高效率
- **两阶段审查**：Spec 合规 → 代码质量，分层把关
- **多 Agent 支持**：8种主流编码 Agent 均可使用
- **自动触发**：Skills 在相关时机自动激活，不需手动调用

### 缺点

- **学习曲线**：需要理解 TDD、YAGNI、DRY 等工程纪律
- **中文资料少**：主要是英文文档
- **无跨会话记忆**：需要搭配 gbrain 等工具才能跨天工作
- **强制 vs 灵活**：对习惯自由发挥的团队可能觉得约束太多

---

## 9. 适用场景

- 专业软件工程团队，需要 AI 产出有质量保证的代码
- 需要 TDD 驱动开发的敏捷团队
- 想让 AI Agent 具有工程纪律（不是随意写代码）的场景
- 需要并发执行子任务的大型项目

---

## 10. 与 opc123 开发交付层的定位

**superpowers = 开发交付层的工程纪律工具**

```
opchain（Pipeline + Checkpoint）→ 解决"跨会话失忆"
superpowers（工程纪律）→ 解决"代码质量失控"
gstack（角色扮演）→ 解决"单人像团队"
open-design（设计到代码）→ 解决"设计稿转换"
```

---

## 11. 参考链接

- GitHub：https://github.com/obra/superpowers
- Plugin Marketplace：Claude Code 官方市场可直接安装
- 作者博客：https://blog.fsck.com
- 原始发布公告：https://blog.fsck.com/2025/10/09/superpowers/