# opc123 - Open-source Product & Design Tools Research

> AI 开源设计工具 + Agent Skills 调研项目

---

## 📋 项目简介

opc123 是一个专注于 AI 开源设计工具和 Agent Skills 的研究项目，对标 Claude Design，调研市场上优秀的开源替代品。

---

## 📁 目录结构

```
opc123/
├── README.md
│
├── 🎨 设计工具
├── open-design调研报告.md      # Web + 本地 daemon，支持 16 种编码 Agent
├── open-codesign调研报告.md    # 桌面 Electron，自带 AI 运行时
│
├── 💼 工作流 & 角色
├── gstack调研报告.md           # YC CEO Garry Tan 的 23 工具虚拟工程团队
│
├── 🧠 记忆 & 知识系统
├── gbrain调研报告.md           # 自进化第二大脑，知识图谱 + 混合搜索
│
├── 🛠️ Agent Skills 生态
├── opc-skills调研报告.md       # 独立创业者 Skills 集合（12个）
├── opchain调研报告.md          # Checkpoint 协议，跨会话开发 Pipeline
└── dbskill调研报告.md          # dontbesilent 商业诊断工具箱（19个 Skills）
```

---

## 🔍 已调研项目

### 设计工具

| 项目 | 架构 | License | 亮点 |
|------|------|---------|------|
| [open-design](https://github.com/nexu-io/open-design) | Web + Daemon | MIT | 16 种 Agent、31 Skills、72 设计系统 |
| [open-codesign](https://github.com/OpenCoworkAI/open-codesign) | Electron | MIT | 桌面原生、20+ 模型、一键导入 |

### 工作流 & 角色

| 项目 | 作者 | 亮点 |
|------|------|------|
| [gstack](https://github.com/garrytan/gstack) | YC CEO Garry Tan | 23 工具命令，810× 效率提升 |

### 记忆 & 知识

| 项目 | 作者 | 亮点 |
|------|------|------|
| [gbrain](https://github.com/garrytan/gbrain) | YC CEO Garry Tan | 知识图谱 + 混合搜索，P@5 49.1% |

### Agent Skills 生态

| 项目 | 定位 | Skills 数量 | License |
|------|------|-------------|---------|
| [opc-skills](https://github.com/ReScienceLab/opc-skills) | 独立创业者 Skills | 12 个 | Apache 2.0 |
| [opchain](https://opchain.dev) | 开发 Pipeline + Checkpoint | 9 个阶段 | MIT |
| [dbskill](https://github.com/dontbesilent2025/dbskill) | 商业诊断工具箱 | 19 个 | CC BY-NC 4.0 |

---

## 💡 核心结论

### 工具选择

| 场景 | 推荐 |
|------|------|
| 有 Agent 工作流的开发者 | open-design |
| 不想装 CLI 的普通用户 | open-codesign |
| 创始人/CEO 高效工作 | gstack |
| 个人知识管理 | gbrain |
| 独立产品调研到设计 | opc-skills |
| 跨会话开发全流程 | opchain |
| 商业诊断与执行力 | dbskill |

### 完整 AI 开发栈

```
产品调研    → opc-skills（requesthunt、domain-hunter）
商业诊断    → dbskill（diagnosis、benchmark、action）
工作流角色  → gstack（23 工具命令）
开发 Pipeline → opchain（Checkpoint 协议）
知识记忆    → gbrain（知识图谱 + 混合搜索）
设计工具    → open-design / open-codesign
```

---

## 🛠️ 安装 Skills

```bash
# opc-skills（Claude Code）
/plugin marketplace add ReScienceLab/opc-skills
/plugin install requesthunt@opc-skills

# dbskill（Claude Code）
/plugin marketplace add dontbesilent2025/dbskill
/plugin install dbs@dontbesilent-skills

# gstack（Garry Tan 的配置）
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack

# gbrain（记忆系统）
bun install -g github:garrytan/gbrain
gbrain init --pglite
```

---

*调研时间：2026-05-21*
*维护者：opc123 team*
*GitHub：https://github.com/flybear16/opc123*