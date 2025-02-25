---
{"dg-publish":true,"permalink":"/日常学习/工具折腾/obsidian食用指南/","title":"Obsidian食用指南","tags":["Obsidian","折腾"],"noteIcon":"1","created":"2023-07-14T17:23:36.118+08:00","updated":"2025-01-01T10:50:48.975+08:00"}
---


# 惯例废话

个人选择笔记方式的几大要点：

- 数据安全：数据一定要可以控制，而不是存在云端，且支持狡兔三窟备份和同步，以此确保多端协同。因而放弃了例如有跑路前科的幕布和已经删了俄罗斯用户库的 notion。
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
  > [!example]-
  > 这里是 callout 模块
  > 支持**markdown** 和 [[Internal link\|wikilinks]]
<br>

# 主题分享

## Style Settings

主题编辑插件，纷繁复杂的 CSS 不好修改，这个插件可以可视化地修改主题的各项细节。

## Border

主题界的新锐，特点是简洁、扁平化设计与强交互感，更新修 BUG 速度良心。

## Maple

比较老资格的主题了，用过很长一段时间，和 Border 换着用。

## Minimal

obsidian 两大推荐主题之一，折腾党专用，主打一个高度自定义，市场还有专属的主题可视化编辑插件 Minimal Theme Settings，Github 也有定制化后的成品配置文件分享。
<br>

# 功能插件

> [!important] 无论如何，请谨记：插件千般好，过多也臃扰。

## 同步

### Remotely Save

首先需要解决的就是同步备份问题，obsidian 自带的同步功能是付费的，但是该付费功能并不是很稳定，虽然一直在更新但是不建议付费使用，还好有替代插件 Remotely Save。
利用 Webdav，可以实现实时同步，常规操作通常是：🖥️PC 端编辑/查看 → 同步至网盘 →📲 移动端查看/少量编辑 → 同步的循环。
好的，仅凭这个就可以取代幕布、notion、印象笔记啥的了……
🔄 文件增多后同步偶尔卡顿/网络超时，不过基本还是可以满足日常使用。

> [!bug]+ 2023.04.26 补充
> 😵 文件增多的时候越来越难用了，已经迁移至 Obsidian Git 和 Github 同步，同时移动端编辑通过 Seafile，查看通过 Digital Garden 发布的网站。

### Git

使用 Git 保存文档库，同步的另一种解决方案。不过在移动端暂时没有省事的同步操作，适合本【人不离电脑左右】人士。

## 浏览器

### Web Browser

顶级插件，在记笔记的时候难免需要搜索一些内容，同时笔记里也时常会插入一些 URL，这个插件支持在 obsidian 中直接打开网页（而非是默认浏览器），或输入 URL，或调用搜索引擎搜索。
美中不足的是，该插件目前还未上线市场，需要安装 obsidian42-BRAT 插件，并通过该插件安装未上线市场的插件，同时可能需要安装 Custom Frames 插件，毕竟 Web Browser 插件是基于此实现的。

> [!info]+ 2023.04.02 补充
> 现有 Surfing 插件，已上市场，并支持同样功能 👍，使用这个可以替代需要连同自身一共三个插件的 Web Browser 了。
> 在 obsidian 内部分屏开网页 + 笔记页面的体验 MAX！
> 唯一的缺点就是像知乎一类的可能会需要先登录。

### Search On Internet

搜索插件，选中对应的内容，直接在新选项页调用搜索引擎，和 Web Browser/Surfing 配合食用更佳。
不过实际使用频率较低，现已卸载。

### Convert Url To Preview

将选中的 URL 转换为设置好格式的 iframe 嵌入框，使用场景不多，但需要的时候就很省事。

### Paste URL into Selection

直接将外部链接粘贴到选中的文本变为超链接样式，在写笔记时使用频率其实还挺高的，有了链接方便以后溯源。

## 笔记增强

### Excalidraw

笔记友好，支持画板，便于手写 ✍️、绘制流程图等，启动略有性能问题 🤯，但这个插件可以说很好弥补了自定义画板及手写这方面的不足。

### Annotator

PDF 批注插件，使用时需要注意尽量不要更改 PDF 文件的位置，否则修改插件根据批注生成的文件相对麻烦。不过主要文献管理和批注还是直接仅基于 Zotero 搞了，没有联动 Obsidian，现已卸载。

### Enhancing MindMap

思维导图插件，支持 markdown 笔记和思维导图的互转，补全了相对幕布缺少的最后一个功能。

## 便捷记录

### Commander

在 obsidian 的侧栏、文件顶端、状态栏、右键菜单等各种地方添加命令快捷入口，图标自选，还可以建立【宏】，进而一键式完成组合操作。

### Floating Toc

浮动目录插件，在写长文时方便随时根据目录跳转。

### Editing ToolBar

编辑工具栏，适用于 markdown 语法偏复杂或不熟悉时，类似语雀等在线文档的编辑栏，提供了标题、加粗、高亮、引用等基本操作，更可以自定义需要的操作。
当然，目前存在性能问题，插件启动时间大约 500ms 上下。

> [!done]+ 2023.04.17 补充
> 当前性能问题已解决 👏，插件启动时间降低为原来的 1/10。
> 由于充分熟悉 Markdown 语法，这个插件就显得多此一举了，现已卸载。

### Duplicate Line

习惯了 VS Code/JetBrains 等工具提供的快捷键复制上一行功能，在完成特定格式的笔记时很有帮助。后来发现这个功能在笔记时还是用得少，不像写代码经常可能有相似的逻辑语句，现已卸载。

### Text Generator

AIGC 插件，可以续写、总结、打标签和起标题等，配好模型 API 即可。虽然完全不会使用 AI 生成笔记内容，但是搞一个 AI 摘要发布到网站上还挺有意思的。

## 表格功能

### Table Generator

表格创建插件，类似 typora。
在 Obsidian 史诗级更新表格功能体验后已经完全不需要，现已卸载。

### Advanced Table

表格编辑快捷操作，对于频繁编辑添加 md 中表格场景适用。
在 Obsidian 史诗级更新表格功能体验后已经完全不需要，现已卸载。

### DataLoom

创建和 Notion 类似的表格，支持 Tag、Time、Number、Checkbox 等列类型，唯一是格式是 TABLE 文件，内部 JSON 格式，和插件耦合度较高，具备一定的转移成本。用来记录一下付费订阅项目的到期时间或者投简历的情况还是挺不错的，毕竟比纯 Markdown 的表格好看一些，但是迁移是个问题。

## 功能增强

### Pandoc Plugin

经典插件，折腾导出万恶的 office 系列产品必备，无需多作解释。

### 盘古 PanGu

在英文字符和中文字符间增加空格，更加易于阅读，强迫症福音。后来找到了功能更全面的，建议使用 Linter。

### Linter

格式化插件，功能明显比盘古更多，可自定义程度更高。

### Dataview

**神级插件**，用类 SQL 语言管理笔记，生成表格、卡片式视图，适合总览笔记记录情况，联合 Weread Plugin 插件管理读书笔记等。

### Kanban

看板插件 ✅，可视化记录 DDL 的最佳方式，完成一件归档一件成就感飞升。

### Privacy Glasses

模糊插件，两大作用。首先是保护了隐私，在写笔记中途开启可以防止他人查看。同时也是背诵神器，开启模糊效果，默背对应内容，鼠标移上去查看答案。

### Dust Calendar

符合中国习惯的日历 📅 插件，相比 Calendar 插件多了节气和节假日调休情况。搭配 Daily Notes 可实现日记需求，适合写日报的场景 😇，虽然我并不怎么写日记。

### Emoji ToolBar

顾名思义，方便直接检索 🔍 或选择对应的 emoji，还是能够丰富笔记的同时便捷不少。

### Weread Plugin

微信读书骨灰级用户的福音，导入微信读书书籍元数据、划线和评论 💬。

### Image Auto Upload Plugin

自动将复制粘贴的图片上传到图床 🖼️（借助 PicGo），并复制对应链接到剪切板，极大地方便了带图 Markdown 文件的多平台查看和迁移。

### Novel Word Count

在文件目录树的每一栏增加对应的字数/笔记数/词数等统计，各笔记情况一目了然。

## 发布分享

### QuickShare

快速分享，顾名思义。很多时候可能会想分享自己的记录，但意料之中地，obsidian 自带的发布服务也是付费的，那么这个插件可以快速帮助创建一个 30 天内的私密分享链接。对于一个不常写笔记，同时记录库里也包括了一些仅给自己看的私密文档的人来说，这个插件基本替代了在线云笔记的分享功能。

### Digital Garden

Obsidian 白嫖发布的终极解决方案！可以自由选择需要发布的文档，支持 callouts，支持 obsidian 内各种主题展示。具体流程借助 Github 仓库和 Vercel 服务部署，一键式轻松发布，基本替代了博客，不再需要将文章搬运到博客服务或者折腾复杂易错的联动流程。

> [!help]+ 当前 Vercel 服务对应域名污染严重 ❌，国内访问不友好。
> 解决方案：💸 购买一个域名，同时在 Vercel 服务的基础上加一层 Cloudflare CDN（**需要全代理，而不能仅 DNS 解析**），即可实现在可以接受的速度下访问发布的笔记，同时域名还是自有域名，完美。
> 另外，Digital Garden 支持自定义插件，因此可以使用 Waline 作为 💬 评论系统插件，不过无备案采用国际版的话同样需要 Vercel 服务的基础上增加一层 Cloudflare CDN。

> [!success] 最新版本基本完全支持 Dataview 插件下的原样呈现发布，🫡致敬！

## 博客衍生

### Better Word Count

相比 obsidian 自带的字符统计，该插件提供了更完善和可自定义范围的单词统计，毕竟字数不是关键，词数统计很多时候是更加有用的。

### File Info Panel

比 Better Word Count 更详细的单个文档信息统计，包括词频、外部链接收集等，基本可以替代原生字符统计功能和 Better Word Count 插件（已卸载）。

### Reading Time

根据笔记字符数或词数估计阅读时间 ⏳，博客的必备功能之一。

>[!info]+ 2023.10.11 更新
> Novel Word Count 更新已包含预估阅读时长，Reading Time 插件已失去意义。

### Chronology

工作动态记录日历 📅 插件，如新建笔记、编辑笔记等，类似 GitHub 时间轴和热力图。

## 外貌协会

### Iconize

外貌协会专用，给文件夹单独或依赖规则增加图标，方便区分识别。

### Status Bar Quote

在底部状态栏增加一句话，仅此而已。

### File Color

设置文件目录树颜色，便于区分。

### heti

中式排版美观插件，没仔细查看过源码，安装了以后似乎对宽屏显示器写文章更友好。
