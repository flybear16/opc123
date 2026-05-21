# opc-skills 调研报告

> AI Agent Skills for Solopreneurs, Indie Hackers, and One-Person Companies
> 调研时间：2026-05-21
> 来源：https://github.com/ReScienceLab/opc-skills

---

## 1. 项目概述

**一句话描述**：面向独立创业者（Solopreneurs）、Indie Hackers、单人公司设计的 AI Agent Skills 集合，覆盖 SEO 优化、需求调研、域名搜索、Logo/Banner 设计、社交媒体内容获取等全流程。

**核心理念**：用正确的 Skills 让单人比团队更高效。

**官网**：https://opc.dev | **Skills 浏览器**：https://skills.sh/ReScienceLab/opc-skills

---

## 2. 核心元数据

| 字段 | 值 |
|------|-----|
| 仓库 | ReScienceLab/opc-skills |
| 语言 | Markdown / Shell |
| License | Apache 2.0 |
| 最新更新 | 2026-05-21 |
| 官方文档 | 英文 + 中文 |
| 支持 Agent | 16+（Claude Code、Cursor、Windsurf、OpenCode、Codex、Copilot、Gemini CLI 等） |

---

## 3. 内置 Skills 列表（12个）

### 3.1 SEO & 内容优化

| Skill | 功能 | 依赖 |
|-------|------|------|
| `seo-geo` | SEO & GEO 优化，适配 AI 搜索引擎（ChatGPT、Perplexity、Google） | 无 |

### 3.2 市场需求调研

| Skill | 功能 | 依赖 |
|-------|------|------|
| `requesthunt` | Reddit、X、GitHub 需求调研 | 无 |
| `producthunt` | Product Hunt 帖子/话题/用户/合集搜索 | 无 |

### 3.3 品牌 & 域名

| Skill | 功能 | 依赖 |
|-------|------|------|
| `domain-hunter` | 域名搜索、注册商比价、优惠码发现 | twitter, reddit |
| `logo-creator` | AI 生成 Logo、裁剪、去背景、SVG 导出 | nanobanana |
| `banner-creator` | GitHub/Twitter/LinkedIn Banner 生成 | nanobanana |

### 3.4 社交媒体内容

| Skill | 功能 | 依赖 |
|-------|------|------|
| `reddit` | Reddit 内容搜索（公开 JSON API） | 无 |
| `twitter` | Twitter/X 内容搜索（via twitterapi.io） | 无 |

### 3.5 图片生成

| Skill | 功能 | 依赖 |
|-------|------|------|
| `nanobanana` | Gemini 3 Pro Image（Nano Banana Pro）生成图片 | 无 |

### 3.6 知识管理

| Skill | 功能 | 依赖 |
|-------|------|------|
| `archive` | Session 学习与调试方案存档，Markdown 索引 | 无 |

---

## 4. 安装方式

### 4.1 Claude Code

```bash
# 添加 OPC Skills 市场
/plugin marketplace add ReScienceLab/opc-skills

# 安装特定 Skill
/plugin install requesthunt@opc-skills
/plugin install domain-hunter@opc-skills
/plugin install seo-geo@opc-skills

# 列出所有可用 Skills
/plugin marketplace list opc-skills
```

### 4.2 一键安装（通用）

```bash
# 安装所有 Skills
npx skills add ReScienceLab/opc-skills

# 安装特定 Skill
npx skills add ReScienceLab/opc-skills --skill reddit

# 安装到指定 Agent
npx skills add ReScienceLab/opc-skills -a droid
```

### 4.3 依赖安装

```bash
# domain-hunter 需要 twitter 和 reddit
npx skills add ReScienceLab/opc-skills --skill reddit --skill twitter --skill domain-hunter

# logo-creator 和 banner-creator 需要 nanobanana
npx skills add ReScienceLab/opc-skills --skill nanobanana --skill logo-creator --skill banner-creator
```

---

## 5. 支持的 AI 编码 Agent（16+）

Claude Code · Cursor · Windsurf · OpenCode · Codex · GitHub Copilot · Gemini CLI · Factory Droid · Droid · Roo Code · Kilo Code · Trae · Goose · 以及更多...

---

## 6. 与 opc123 的关联

### 6.1 互补关系

| opc123 调研内容 | opc-skills 提供 |
|----------------|----------------|
| open-design / open-codesign（设计工具） | logo-creator、banner-creator（设计素材生成） |
| gstack（工作流） | seo-geo、requesthunt（产品调研） |
| gbrain（记忆系统） | archive（Session 存档） |

### 6.2 完整产品开发栈

```
requesthunt（需求调研）
    ↓
domain-hunter（域名 + 品牌）
    ↓
logo-creator + banner-creator（品牌设计）
    ↓
seo-geo（SEO + AI 搜索优化）
    ↓
archive（知识存档）
```

---

## 7. 优缺点分析

### 优点

- **全流程覆盖**：从调研到设计到 SEO，一人完成所有非代码工作
- **多 Agent 支持**：不锁定单一工具，16+ AI 编码 Agent 均可使用
- **零 API 成本**：除 nanobanana（Gemini）外，大多依赖公开 API
- **安装简单**：一行命令即可完成
- **MIT 许可**：Apache 2.0，完全开源可定制

### 缺点

- **Gemini 依赖**：图片生成依赖 Gemini 3 Pro，需相关 API
- **第三方 API**：twitterapi.io 可能产生费用
- **Skill 数量有限**：目前 12 个，生态还在建设中
- **中文资料少**：主要是英文文档

---

## 8. 参考链接

- GitHub：https://github.com/ReScienceLab/opc-skills
- 官网：https://opc.dev
- Skills 浏览器：https://skills.sh/ReScienceLab/opc-skills
- DeepWiki：https://deepwiki.com/ReScienceLab/opc-skills
- Discord：https://discord.gg/Y2yBpRXvVa
- 作者推特：https://x.com/Yilin0x