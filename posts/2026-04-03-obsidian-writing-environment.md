---
title: Obsidian 写作环境搭建：6 款必备插件让博客管理效率翻倍
date: 2026-04-03
category: 效率工具
tags: [Obsidian, 博客, 效率, 插件, Markdown]
top: 0
---

前段时间 Obsidian 非常火，于是我决定上手学习一下。发现自己有挺多文章需要归纳和处理，所以准备花时间尝尝鲜。

折腾了一圈之后，发现这套组合比想象中顺手很多。这篇文章记录一下我的配置，顺便把迁移途中踩的几个坑也说清楚，希望能帮到同样想尝试的朋友。

## 为什么选择 Obsidian？

其实最主要的点，还是因为我想配合 AI 去使用。在 Obsidian 结合 AI 使用会非常便利，我也是看中了这一点，花了一些时间主动学习了这个工具。

Obsidian 的核心优势：

1. **本地存储** — 所有笔记都在本地，不依赖云服务
2. **Markdown 原生** — 格式通用，迁移方便
3. **双向链接** — 知识图谱功能强大
4. **插件生态** — 社区插件丰富，可定制性强

## 安装与主题配置

### 下载安装

直接搜索 Obsidian 即可，官方下载地址：[https://obsidian.md/download](https://obsidian.md/download)

### 主题推荐：AnuPpuccin

我尝试了好几个主题，最让我舒服的还是 **AnuPpuccin**。主要原因：

- 暗黑系风格和我的 IDEA 主题类似，视觉风格统一
- 下载量 80 万+，是 Obsidian 社区最受欢迎的主题之一
- 亮暗模式都好看，配色方案多
- 长时间写稿不容易眼睛疲劳

**配置方式**：点击左下角设置按钮 → 外观 → 主题设置 → 选择 AnuPpuccin

## 6 款必备插件配置

安装第三方插件需要先关闭安全模式。

### 1. Custom Attachment Location — 附件自动归类

**功能**：附件按笔记名自动归类到对应子文件夹。

**解决的问题**：以前图片全扔在 vault 根目录，找起来一团乱；装了这个之后，每篇文章的截图自动进 `assets/文章名/`，整洁很多。

**配置要点**：
- 设置附件存放位置
- 设置图片路径格式
- 确保 URL 格式符合标准 Markdown

### 2. Dataview — 笔记内容查询

**功能**：用类 SQL 语法查询笔记内容，适合做内容索引。

**使用场景**：
- 追踪文章状态（草稿、已发布、待发布）
- 汇总选题
- 统计标签分布

**示例查询**：
```dataview
TABLE status as "状态", date as "日期", category as "分类"
FROM "posts"
WHERE status = "草稿"
SORT date DESC
```

### 3. Enhancing Export — 多格式导出

**功能**：支持导出 PDF、HTML、ePub、Markdown 多种格式。

**使用场景**：偶尔要给人发一份格式整齐的文档，用这个比直接复制粘贴省事。

### 4. Git — 自动版本控制

**功能**：自动定时备份到 GitHub。

**为什么重要**：版本控制这件事以前全靠手动，某次误删了半篇稿子才意识到有多危险。装上之后基本不用管，按设定的时间间隔自动 commit，在哪台机器上都能拉到最新版本。

**推荐设置**：
- 编辑停止之后自动 push（我设置了一分钟后同步）
- 排除 `.obsidian` 和 `workspace.json`（避免冲突）

### 5. Local Images Plus — 图片本地化

**功能**：检测笔记里所有外链图片，自动下载到本地并更新链接。

**核心价值**：对从其他平台迁移过来的文章特别重要——导出的文章图片链接还指向服务器，服务器一旦停了图片就全挂。用这个插件一键本地化可以彻底解决问题。

### 6. Templater — 文章模板

**功能**：预设文章模板，新建文件自动套用。

**我的模板**：
```markdown
---
title: 
date: {{date}}
category: 
tags: []
status: 草稿
---

## 前言


## 正文


## 总结

```

配合 Dataview 查询能直接看到哪些文章的状态是"草稿"或"待发布"。

## 迁移途中踩的坑

### 坑 1：Halo 导出的是 HTML，不是 Markdown

**问题**：以为官方「文章导入导出」插件能直接导出 Markdown，结果打开一看全是 HTML。原因是 Halo 2.x 默认编辑器存储格式就是 HTML。

**解决方案**：用 Python 的 `markdownify` 库批量转换。

```python
from markdownify import markdownify as md
from bs4 import BeautifulSoup

with open('article.html', 'r') as f:
    html = f.read()
    
markdown = md(html)
with open('article.md', 'w') as f:
    f.write(markdown)
```

### 坑 2：HTML 转 Markdown 格式混乱

**问题**：用 Pandoc 转换，富文本 HTML 转出来格式一团糟，标题层级乱、列表嵌套出问题。

**解决方案**：换成 `markdownify + BeautifulSoup` 组合，效果稳定很多，基本不需要再手动修正格式。

### 坑 3：图片链接失效

**问题**：从 Halo 导出的文章，图片 URL 还是指向原服务器的。迁移完之后如果不处理，服务器一停图片就全挂。

**解决方案**：用 Local Images Plus 扫一遍，插件会自动把外链图片下载到本地，并把 Markdown 里的链接替换成本地路径。

## 我现在的工作流

### Halo → Obsidian 迁移流

```
导出 HTML → markdownify 批量转换 → 导入 Obsidian Vault → Local Images Plus 本地化图片
```

### Obsidian + Claude Code 创作流

```
分析已有文章风格 → 生成选题灵感 → 确认选题 → 生成大纲 → 确认结构 → 生成文章 → 导回 Halo 发布
```

选题和风格分析这两步现在基本交给 Claude Code 来跑，它能读完整个 vault 里的历史文章，总结出我的写作语气和高频话题，然后按这个风格出新文章。比自己一篇一篇翻快多了。

## 总结

这套配置没什么特别复杂的地方，核心就两件事：

1. **插件组合**把「文件管理乱」「备份靠手动」「图片会失效」这三个痛点全堵上了
2. **迁移的坑**主要在 HTML 转 Markdown 这一步，用对工具基本没什么大问题

如果你也在用 Halo 或其他平台写博客、想迁移到 Obsidian 管理，按这个流程来应该能少走不少弯路。

## 常见问题：隐私文档怎么处理？

很多人担心把 Obsidian 全部开放给 AI 会有隐私问题。这个问题在 V2EX 评论区也有人提到：

> **问**：Obsidian 中全部开放权限给 Claude 么？一些隐私文档咋处理？
>
> **答**：Claude Code 有权限控制，你可以自己授权什么文件夹它可以读取，哪些需要询问你。

**解决方案**：

1. **分文件夹授权** — 敏感文档放在单独文件夹，不给 AI 读取权限
2. **询问机制** — 设置某些文件夹访问时需要手动确认
3. **最小权限原则** — 只给 AI 工作必需的文件夹权限

这样既能享受 AI 辅助写作的便利，又能保护隐私文档安全。

---

**参考来源**：[V2EX](https://www.v2ex.com/t/1201962)
