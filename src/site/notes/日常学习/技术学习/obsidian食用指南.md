---
{"dg-publish":true,"permalink":"/日常学习/技术学习/obsidian食用指南/","tags":["技术学习","gardenEntry","gardenEntry","gardenEntry","gardenEntry","gardenEntry","gardenEntry"],"noteIcon":"","created":"","updated":""}
---


# 惯例废话

个人选择笔记方式的几大要点：

- 数据安全：数据一定要可以控制，而不是存在云端，且支持狡兔三窟备份和同步，以此确保多端协同。因而放弃了幕布、flowus 等软件。
- 格式通用：最好是 markdown 格式，且支持公式与 emoji👏，不对 markdown 格式有较多侵入式，也因此放弃了语雀、飞书等。
- 易用好看：外貌协会会员，且一向偏好低门槛、开箱即用，因而最终在博客和 obsidian 之间选择了后者。当然，不愿折腾域名备案也是重要原因。
- 外部访问：平时记录、查看以及分享笔记，最好不需要科学上网，因而放弃了 notion。

# 基本特点

- markdown 语法
- 双向链接
- 数据全本地
- 高度自定义的主题和插件市场

# Callouts 分类

- note
- abstract, summary, tldr
- info, todo
- tip, hint, important
- success, check, done
- question, help, faq
- warning, caution, attention
- failure, fail, missing
- danger, error
- bug
- example
- quote, cite
  > [!example]
  > 这里是 callout 模块
  > 支持**markdown** 和 [[Internal link\|wikilinks]]

# 主题分享

## Style Settings

主题编辑插件，纷繁复杂的 CSS 不好修改，这个插件可以可视化地修改主题的各项细节。

## Border

主题界的新锐，特点是简洁、扁平化设计与强交互感，更新修 BUG 速度良心。

## Blue Topaz

obsidian 两大推荐主题之一，曾经的社区主题王，开箱即用，美观高可自定义化，同时具备了代码块高亮、加行号等基本功能，无需再安装对应插件。不过本极简主义觉得略花哨。

## Minimal

obsidian 两大推荐主题之一，折腾党专用，主打一个高度自定义，市场还有专属的主题可视化编辑插件 Minimal Theme Settings，Github 也有定制化后的成品配置文件分享。

# 功能插件

> [!important] 无论如何，请谨记：插件千般好，过多也难搞。

## 同步

### Remotely Save

首先需要解决的就是同步备份问题，obsidian 自带的同步功能是付费的，还好有良心插件 Remotely Save。
利用 Webdav，可以实现实时同步，常规操作通常是：🖥️PC 端编辑/查看 → 同步至网盘 →📲 移动端查看/少量编辑 → 同步的循环。
好的，仅凭这个就可以取代幕布、notion、印象笔记啥的了……
🔄 文件增多后同步偶尔卡顿/网络超时，不过基本还是可以满足日常使用。

### Obsidian Git

使用 Git 保存文档库，同步的另一种解决方案。不过在移动端暂时没有省事的同步操作，目前还是选择上一种同步方式。

## 浏览器

### Web Browser

顶级插件，在记笔记的时候难免需要搜索一些内容，同时笔记里也时常会插入一些 URL，这个插件支持在 obsidian 中直接打开网页（而非是默认浏览器），或输入 URL，或调用搜索引擎搜索。
美中不足的是，该插件目前还未上线市场，需要安装 obsidian42-BRAT 插件，并通过该插件安装未上线市场的插件，同时可能需要安装 Custom Frames 插件，毕竟 Web Browser 插件是基于此实现的。

> [!info] 2023.04.02 补充
> 现有 surfing 插件，已上市场，并支持同样功能 👍，使用这个可以替代需要连同自身一共三个插件的 Web Browser 了。
> 在 obsidian 内部分屏开网页+笔记页面的体验 MAX！

### Search On Internet

搜索插件，选中对应的内容，直接在新选项页调用搜索引擎，和 Web Browser/Surfing 配合食用更佳。

## 笔记增强

### Excalidraw

笔记友好，支持画板，便于手写 ✍️、绘制流程图等，启动略有性能问题 🤯，但这个插件可以说很好弥补了自定义画板及手写这方面的不足。

### Annotator

PDF 批注插件，使用时需要注意尽量不要更改 PDF 文件的位置，否则修改插件根据批注生成的文件相对麻烦。

### Enhancing MindMap

思维导图插件，支持 markdown 笔记和思维导图的互转，补全了相对幕布缺少的最后一个功能。

## 便捷记录

### Commander

在 obsidian 的侧栏、文件顶端、状态栏、右键菜单等各种地方添加命令快捷入口，图标自选，还可以建立宏一键式完成组合操作。

### Floating Toc

浮动目录插件，在写长文时方便随时根据目录跳转。

### Editing ToolBar

编辑工具栏，适用于 markdown 语法偏复杂或不熟悉时，类似语雀等在线文档的编辑栏，提供了标题、加粗、高亮、引用等基本操作，更可以自定义需要的操作。
当然，目前存在性能问题，插件启动时间大约 500ms 上下。

> [!done] 2023.04.17 补充
> 当前性能问题已解决 👏，插件启动时间降低为原来的 1/10。

## 表格功能

### Table Generator

表格创建插件，类似 typora。

### Advanced Table

表格编辑快捷操作，对于频繁编辑添加 md 中表格场景适用。

### Notion-Like Table

创建和 Notion 类似的表格，支持 Tag、Time、Number、Checkbox 等列类型，唯一是格式是 TABLE 文件，内部 JSON 格式，和插件耦合度较高，具备一定的转移成本。

## 功能增强

### Pandoc Plugin

经典插件，折腾导出万恶的 office 系列产品必备，无需多作解释。

### 盘古 PanGu

在英文字符和中文字符间增加空格，更加易于阅读，强迫症福音。

### Dataview

神级插件，用类 SQL 语言管理笔记，生成表格、卡片式视图，适合总览笔记记录情况，联合 Weread Plugin 插件管理读书笔记等。

### Kanban

看板插件 ✅，可视化记录 DDL 的最佳方式，完成一件归档一件成就感飞升。

### Privacy Glasses

模糊插件，两大作用。首先是保护了隐私，在写笔记中途开启可以防止他人查看。同时也是背诵神器，开启模糊效果，默背对应内容，鼠标移上去查看答案。

### Calendar

日历 📅 插件，搭配 Daily Notes 可实现日记需求，适合写日报的场景 😇。

### Emoji ToolBar

顾名思义，方便直接检索或选择对应的 emoji，本质上和 Editing ToolBar 类似。

### Weread Plugin

导入微信读书书籍元数据、划线和评论 💬。

## 发布分享

### QuickShare

快速分享，顾名思义。很多时候可能会想分享自己的记录，但意料之中地，obsidian 自带的发布服务也是付费的，那么这个插件可以快速帮助创建一个 30 天内的私密分享链接。对于一个不常写笔记，同时记录库里也包括了一些仅给自己看的私密文档的人来说，这个插件基本替代了在线云笔记的分享功能。

### Digital Garden

obsidian 白嫖发布的终极解决方案！可以自由选择需要发布的文档，支持 callouts，支持 obsidian 内各种主题展示。具体流程借助 Github 仓库和 Vercel 服务部署，一键式轻松发布，基本替代了博客，不再需要将文章搬运到博客服务或者折腾复杂易错的联动流程。

> [!help] 当前 Vercel 服务对应域名污染严重 ❌，国内访问不友好。
> 解决方案：💸 购买一个域名，同时在 Vercel 服务的基础上加一层 Cloudflare CDN，即可实现在可以接受的速度下访问发布的笔记，同时域名还是自有域名，完美。

## 博客衍生

### Better Word Count

相比 obsidian 自带的字符统计，该插件提供了更完善和可自定义范围的单词统计，毕竟字数不是关键，词数统计很多时候是更加有用的。

### Reading Time

根据笔记字符数或词数估计阅读时间 ⏳，博客的必备功能之一。

### Chronology

工作动态记录日历 📅 插件，如新建笔记、编辑笔记等。

## 外貌协会

### Icon Folder

外貌协会专用，给文件夹单独或依赖规则增加图标，方便区分识别。

### Status Bar Quote

在底部状态栏增加一句话，仅此而已。
