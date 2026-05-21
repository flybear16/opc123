# khazix-skills 调研报告

> 教学用 Claude Code Skill / 脚本 demo 集合
> 调研时间：2026-05-22
> 来源：khazix 仓库（per-skill semver 打 tag）

---

## 1. 项目概述

**一句话描述**：教学用 Claude Code Skill 和脚本 demo 集合，按 per-skill semver 打 tag，方便管理和升级。

**定位**：Skill 开发者的学习参考 + Claude Code 插件开发示例。

---

## 2. 核心内容

根据 GitHub 搜索结果，khazix-skills 主要包含：

| 类型 | 说明 |
|------|------|
| **Claude Code Skill demo** | 各种 skill 的教学示例 |
| **per-skill semver** | 每个 skill 独立版本号，方便依赖管理 |
| **脚本集合** | Claude Code 环境下的实用脚本 |

---

## 3. 安装方式

参考标准 Claude Code skill 安装方式，khazix 约定的 semver 格式便于版本管理：

```bash
# 安装特定版本
npx skills add khazix/skills --skill <name>@<version>

# 如
npx skills add khazix/skills --skill demo-skill@1.0.0
```

---

## 4. 定位

khazix-skills 不是直接解决某个 PM 或产品问题的工具，而是** Skill 开发者的基础设施**——教你如何写 Skill、如何管理 Skill 版本、如何用 semver 约定。

---

## 5. 参考链接

- GitHub：搜索 `khazix` 或 `khazix-skills`