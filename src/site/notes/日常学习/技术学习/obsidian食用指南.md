---
{"dg-publish":true,"permalink":"///obsidian/","tags":["gardenEntry"]}
---

# 惯例废话
个人选择笔记方式的几大要点：
- 数据安全：数据一定要可以控制，而不是存在云端，因而放弃了幕布、flowus等软件。
- 支持同步：狡兔三窟，一定要随时保证有备份，免得哪天就折腾坏了，同时也是多端协同的基础。
- 格式通用：最好是markdown格式，且支持公式与emoji👏，不对markdown格式有较多侵入式，也因此放弃了语雀、飞书等。
- 易用好看：外貌协会会员，且一向偏好低门槛、开箱即用，因而最终在博客和obsidian之间选择了后者。当然，不愿折腾域名备案也是重要原因。
- 外部访问：分享链接最好不需要科学上网即可访问，因而放弃了notion。

# Callouts分类
-   note
-   abstract, summary, tldr
-   info, todo
-   tip, hint, important
-   success, check, done
-   question, help, faq
-   warning, caution, attention
-   failure, fail, missing
-   danger, error
-   bug
-   example
-   quote, cite
> [!example] 
> 这里是callout模块
> 支持**markdown** 和 [[Internal link\|wikilinks]]

# 必备插件
## Remotely Save
首先需要解决的就是同步备份问题，obsidian自带的同步功能是付费的，还好有良心插件Remotely Save。
利用Webdav，可以实现实时同步，常规操作通常是PC端编辑/查看→同步至网盘→移动端查看/少量编辑→同步的循环。
好的，仅凭这个就可以取代幕布、notion、印象笔记啥的了……

## QuickShare
快速分享，顾名思义。很多时候可能会想分享自己的记录，但意料之中地，obsidian自带的发布服务也是付费的，那么这个插件可以快速帮助创建一个30天内的私密分享链接。对于一个不常写笔记，同时记录库里也包括了一些仅给自己看的私密文档的人来说，这个插件基本替代了博客和在线云笔记的分享功能。

## Web Browser
顶级插件，在记笔记的时候难免需要搜索一些内容，同时笔记里也时常会插入一些URL，这个插件支持在obsidian中直接打开网页（而非是默认浏览器），或输入URL，或调用搜索引擎搜索。
美中不足的是，该插件目前还未上线市场，需要安装obsidian42-BRAT插件，并通过该插件安装未上线市场的插件，同时可能需要安装Custom Frames插件，毕竟Web Browser插件是基于此实现的。
> [!done] 2023.4.2补充
> 现有surfing插件，已上市场，并支持同样功能，使用这个可以替代需要连同自身一共三个插件的Web Browser了。

## Excalidraw
笔记友好，支持画板，便于手写✍️、绘制流程图等，启动略有性能问题🤯，但这个插件可以说很好弥补了自定义画板及手写这方面的不足。

## Style Settings
主题编辑插件，纷繁复杂的CSS不好修改，这个插件可以方便简单地修改主题的各项细节。

## Blue Topaz
obsidian两大推荐主题之一（另一款是折腾党专用的minimal，现在发现border也还可以，更新修bug速度超神），开箱即用，美观高可自定义化，同时具备了代码块高亮、加行号等基本功能，无需再安装对应插件。

## Annotator
PDF批注插件，使用时需要注意尽量不要更改PDF文件的位置，否则修改插件根据批注生成的文件相对麻烦。

## Table Generator
表格创建插件，类似typora。

# 可选插件
## Pandoc Plugin
经典插件，折腾导出万恶的office系列产品必备，无需多作解释。

## Floating Toc
浮动目录插件，在写长文时方便随时根据目录跳转。

## Enhancing MindMap
思维导图插件，支持markdown笔记和思维导图的互转，补全了相对幕布缺少的最后一个功能。

## Kanban
看板插件，可视化记录DDL的最佳方式，完成一件归档一件成就感MAX。

## Editing ToolBar
编辑工具栏，适用于markdown语法偏复杂或不熟悉时，类似语雀等在线文档的编辑栏，提供了标题、加粗、高亮、引用等基本操作，更可以自定义需要的操作。
当然，目前也存在性能问题，插件启动时间大约500ms上下。

## Privacy Glasses
模糊插件，两大作用。首先是保护了隐私，在写笔记中途开启可以防止他人查看。同时也是背诵神器，开启模糊效果，默背对应内容，鼠标移上去查看答案。

## Icon Folder
外貌协会专用，给文件夹单独或依赖规则增加图标，方便区分识别。

## Better Word Count
相比obsidian自带的字符统计，该插件提供了更完善的单词统计，毕竟字数不是关键，词数统计很多时候是更加有用的。

## Reading Time
根据笔记字符数或词数估计阅读时间⏳，博客的必备功能之一。

## Search On Internet
搜索插件，选中对应的内容，直接在新选项页调用搜索引擎，和Web Browser配合食用更佳。

## Calendar
日历插件，搭配daily notes可实现日记需求，适合写日报的场景😇。

## Emoji ToolBar
顾名思义，方便直接检索或选择对应的emoji，本质上和Editing ToolBar类似。

## Advanced Table
表格编辑快捷操作，对于频繁编辑添加md中表格场景适用。

## Weread Plugin
导入微信读书书籍元数据、划线和评论💬。

## Chronology
工作动态记录日历📅插件，如新建笔记、编辑笔记等。