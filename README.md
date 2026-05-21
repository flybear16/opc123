# opc123 - Open-source Product & Design Tools Research

> AI 开源设计工具调研项目

---

## 📋 项目简介

opc123 是一个专注于 AI 开源设计工具的研究项目，对标 Claude Design，调研市场上优秀的开源替代品。

## 📁 目录结构

```
opc123/
├── open-design调研报告.md      # Web + 本地 daemon 架构，支持 16 种编码 Agent
├── open-codesign调研报告.md    # 桌面 Electron 应用，自带 AI 运行时
└── README.md
```

## 🔍 已调研项目

| 项目 | 架构 | License | Stars | 亮点 |
|------|------|---------|-------|------|
| [open-design](https://github.com/nexu-io/open-design) | Web + Daemon | MIT | 40k+ | 16 种 Agent、31 Skills、72 设计系统 |
| [open-codesign](https://github.com/OpenCoworkAI/open-codesign) | Electron | MIT | - | 桌面原生、20+ 模型、一键导入 |

## 💡 核心结论

两个项目均定位为 Claude Design 的开源替代，但路径不同：

- **open-design**：更灵活，适合已有 Agent 工作流的开发者
- **open-codesign**：开箱即用，适合不想装 CLI 的普通用户

---

*调研时间：2026-05-21*
*维护者：opc123 team*