# guizang-ppt-skill 调研报告

> AI-agent Skill for generating polished HTML slide decks
> 调研时间：2026-05-22
> 来源：https://github.com/op7418/guizang-ppt-skill

---

## 1. 项目概述

**一句话描述**：适配 Claude Code / Codex 等 Agent 环境的网页 PPT 技能，生成单文件 HTML 横向翻页 PPT，内置两套视觉系统：电子杂志风 + 瑞士国际主义风格。

**作者**：歸藏（op7418），在"一人公司"等线下分享中沉淀，踩过的每个坑都写进了 checklist.md。

**定位**：第四层（产品设计）的演示文稿工具，也是 open-design deck mode 的上游参考。

---

## 2. 核心元数据

| 字段 | 值 |
|------|-----|
| 仓库 | op7418/guizang-ppt-skill |
| 语言 | HTML / CSS / JavaScript |
| License | MIT |
| 作者 | 歸藏（X：@op7418） |
| 内置版式 | Style A 10 种 / Style B 22 种 |
| 主题色预设 | Style A 5 套 / Style B 4 套 |
| 交付格式 | 单文件 HTML，无需构建 |

---

## 3. 两套视觉系统

### 3.1 Style A · 电子杂志 × 电子墨水

> 像 Monocle 贴上了代码，适合叙事、观点、个人风格表达

**特点**：
- 叙事感强，排版灵活
- 适合：线下分享、个人演讲、AI 产品发布、demo day

**10 种布局**：封面、章节、数据大字报、图文、图片网格、Pipeline、对比等

**5 套主题色**（电子墨水风格）

### 3.2 Style B · 瑞士国际主义

> 网格至上、单一高饱和锚点色、直角、发丝线、极致字号对比，适合事实、产品、分析、方法论表达

**22 个具名版式**（必须从 S01-S22 选择，不能临时发明）：

| 版式 | 用途 |
|------|------|
| Cover | 封面 |
| Statement | 核心观点 |
| KPI Tower | 指标展示 |
| Loop Diagram | 循环图 |
| Duo Compare | 双列对比 |
| Image Hero | 图片主视觉 |
| Closing Manifesto | 结尾宣言 |

**4 套锚点色**：克莱因蓝、柠檬黄、柠檬绿、安全橙

**设计约束**：
- 16 列 grid 锁定
- 直角色块、1px 发丝线
- 无阴影、无渐变、无圆角
- 中文字号收敛（大标题降一档）
- 图片槽位绑定（21:9 / 16:10 比例）

**校验命令**：
```bash
node scripts/validate-swiss-deck.mjs path/to/index.html
```

---

## 4. 核心功能

### 4.1 横向翻页

- 键盘 ← → 翻页
- 滚轮翻页
- 触屏滑动
- 底部圆点导航
- ESC 索引

### 4.2 多平台封面

同一套视觉规则生成：
- 公众号 21:9 封面
- 公众号 1:1 分享卡
- 小红书 3:4 封面
- 视频号横版封面

### 4.3 配图工作流

在 Codex 环境中用 GPT-Image 2.0 / GPT-M 2.0 生成：
- 信息图
- 流程图
- 系统关系图
- UI 情景图

按模板比例插入，确保风格统一。

### 4.4 低性能静态模式

按 B 键关闭 WebGL / Canvas 动画，退回静态背景，适合低性能设备演示。

---

## 5. 工作流程

```
需求澄清（7问清单）
    ↓
选择风格（Style A / Style B）
    ↓
拷贝模板（template.html / template-swiss.html）
    ↓
填充内容（主题节奏表 → 版式骨架 → 文案）
    ↓
可选配图（GPT-Image 2.0 / GPT-M 2.0）
    ↓
自检（Style A：清单检查 / Style B：脚本校验）
    ↓
预览（浏览器直接打开）
    ↓
迭代（inline style 改字号/高度/间距）
```

---

## 6. 安装方式

### Claude Code / Codex

```bash
npx skills add https://github.com/op7418/guizang-ppt-skill --skill guizang-ppt-skill
```

或直接把这段话发给 Agent：

> 帮我安装 guizang-ppt-skill。请把 https://github.com/op7418/guizang-ppt-skill 克隆到 ~/.claude/skills/guizang-ppt-skill，安装完成后检查 SKILL.md、assets/、references/ 是否存在。

### 触发关键词

- "帮我做一份杂志风 PPT"
- "帮我做一份瑞士风 PPT"
- "生成一个 horizontal swipe deck"
- "基于这篇文章做一份瑞士风 PPT，控制在 7 页左右，需要 2-3 张配图"

---

## 7. 与 open-design 的关系

**guizang-ppt-skill 是 open-design deck mode 的上游参考**：

open-design README 明确写道：
> [op7418/guizang-ppt-skill](https://github.com/op7418/guizang-ppt-skill) — the deck mode. Bundled verbatim under [skills/guizang-ppt/](https://github.com/nexu-io/open-design/blob/main/skills/guizang-ppt) with original LICENSE preserved

open-design 的 `skills/guizang-ppt` 即直接打包自本项目。

---

## 8. 优缺点分析

### 优点

- **单文件 HTML**：无需构建，浏览器直接打开，发送/演示/截图都方便
- **两套视觉系统**：叙事用 Style A，事实用 Style B，各司其职
- **瑞士风版式锁定**：22 个具名版式，避免临时发明导致风格失控
- **校验脚本**：Style B 有自动化校验，版式/图片槽位/对齐均可脚本检查
- **多平台封面**：一套视觉规则覆盖公众号/小红书/视频号
- **Agent 原生**：HTML/CSS 是文本，Agent 能直接读、改、验证

### 缺点

- **不适合大段表格**：信息密度不够
- **不适合培训课件**：需要高信息密度场景
- **不适合多人协作**：静态 HTML 无法多人实时编辑
- **需要 Agent 环境**：普通 Chatbot 难以稳定生成完整 deck

---

## 9. 适用场景

| 场景 | 推荐 |
|------|------|
| 线下分享 / 行业内部演讲 | ✅ Style A |
| AI 产品发布 / demo day | ✅ Style A |
| 方法论 / 产品分析 | ✅ Style B |
| 个人分享 / 观点表达 | ✅ Style A |
| 长文章变演讲 PPT | 先抽核心观点 → 6-10 页生成 deck |

---

## 10. 参考链接

- GitHub：https://github.com/op7418/guizang-ppt-skill
- 作者 X：https://x.com/op7418
- 飞书分享：zhenfund.feishu.cn