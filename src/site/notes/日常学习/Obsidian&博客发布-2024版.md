---
{"dg-publish":true,"permalink":"/日常学习/Obsidian&博客发布-2024版/","title":"Obsidian&博客发布-2024版","tags":["Obsidian","折腾"],"noteIcon":"1","created":"2024-09-22T23:36:09.429+08:00","updated":"2024-09-27T11:41:40.164+08:00"}
---


# 起因

自从去年布好 Obsidian 写作 + Digital Garden 插件发布 + Vercel 部署 + CloudFlare CDN + Waline 评论的工作流后，今年只增加了一个简单的 AI 摘要功能，并没有折腾的欲望。
但是 2024.9 突然发现在某包邮区省份用流量访问受限了，查了一下大概是因为没有主动去挂上名所以容易被盯上，感觉这什么时候能解除也是玄学。于是开始准备备用站，因为并不想花钱购买一个域名，Github Pages 就成为了最好的选择。
那么既然要搞备用站了，为什么我不干脆从此开始双线运营，备用站为了网络友好，放弃使用过多的样式，也不需要评论功能。而主站就不用像之前一样总是在好看好用和高效访问中权衡拉扯，甚至还可以更新一些备用站没有的内容，备用站未来就作为可公开的内容或者直接切换成学术/简历形式。

# Digital Garden & Quartz

既然是双线运行的想法，那么简洁的备用站最好是完全只采用基础的 Markdown 语法，方便迁移，如果能够兼容 Obsidian 的一些特色就更好了（例如丰富多彩的 Callouts 和 数据人喜欢的 Dataview）。本来 Digital Garden 是完美符合要求的，但是网页首开速度实在是让 lighthouse 都落泪红温【物理】，并且该插件已经至少两三个月没有什么正常更新了，让我嗅到了一丝危机。于是我开始转向之前就看到过的 [Quartz](https://quartz.jzhao.xyz/)。
整体部署和迁移很简单，跟随文档一步步操作即可，只需要本地有 Node.js 环境。唯一的问题是本地 Obsidian 有很多文档是写给自己看的，并不想发布到网站上公开，之前 Digital Garden 是通过 front-matter 文档属性中的 `dg-publish` 操控，结果刚好发现了一款插件 [Enveloppe](https://github.com/Enveloppe/obsidian-enveloppe)，甚至它本身的文档也是用 Quartz 发布的，配置后就可以自动根据设置的文档属性标签将有更新的文档在目标 Github 仓库开一个 PR 并直接合并，这下就可以无缝切换了。虽然 Github 常常需要魔法，但是实际体验总体也还行。
至于 Digital Garden 就挂在个人二级域名下面吧，在插件兼容出现问题前也不会提前废掉。

# Waline & Twikoo

其实刚开始一直以为是 Waline 的 CDN 或者自身问题导致 Digital Garden 为主的前方案最终加载很慢，但是后来发现其实只是其中一个罢了。
在互联网浏览了一下，发现从 Waline 改回 Twikoo 的大有人在，甚至有完整的 [迁移经验帖](https://hugo.bnblogs.cc/waline%E8%AF%84%E8%AE%BA%E8%BF%81%E7%A7%BB%E5%88%B0twikoo/#%E5%AF%BC%E5%87%BAwaline%E8%AF%84%E8%AE%BA)，也是抱怨速度的居多。于是就丝滑地从 Waline 迁移回了 Twikoo，这次没用 Vercel 而是用的 Netlify 部署，发现后者的访问甚至顺畅一些，当然还是顺便用 [好心人维护的 CloudFlare 优选](https://xingpingcn.top/enhanced-faas-in-cn.html) 又套了一层。

# Astro & Fuwari

其实最开始想偷懒的，并没有强烈的换主站框架的意念，然后就一不小心刷到了 [一个博客](https://www.yoghurtlee.com/)，颜狗顿时心动，~~然后一打开关于还是清华佬。~~于是开始想办法搬运，毕竟备用站负责兼容，那么主站即使用一些基本 Markdown 不完整兼容的语法我也是可以接受的。仔细一看，其实是受 [Fuwari](https://fuwari.vercel.app/) 的启发魔改的，魔改的使用 hugo 的版本用户量少且直接搬运有问题了也麻烦，所以选择尝试原版使用 [Astro](https://astro.build/) 的模板。
但是捣鼓了一天，感觉迁移成本过高，尤其是怎么支持 Obsidian Callouts 和像表格怎么调好看还要摸索一下，并且我对 Astro 一窍不通（~~虽然我对其它前端知识也从来没有懂过全靠试错~~），所以准备后面摸鱼慢慢迁，实在不行用 hugo 版的实现也行。

# Hexo & Stellar

众所周知意外总是接踵而至的，在我搜各种教程的时候，又意外看到了 [另一个博客](https://xaoxuu.com/wiki/stellar/)。刚开始只是觉得 Stellar 这个主题名字很让我满意，随手点开了一些示例，发现居然支持 [Memos](https://www.usememos.com/)。虽然 Memos 更新非常不稳定，但是我选择停留在 0.18.1 老版本就没有这个问题了，移动端 APP 支持是最大的优势，双端同步的短想法收集是必要的，还没有朋友圈分组的麻烦和顾虑。好的，于是我立马*自然选择号 前进四*。
接下来就是顺利的按文档搭建迁移，整体过程在多个经验/魔改帖子的帮助下也很顺利，都列在最后的参考中了。以及 Hexo 总体还是和基本的前端三大件差不多的，这我（~~和 GPT~~）还是能信手拈来的。发布的话我还是选择 Enveloppe 插件，配置可以导入导出，和 Quartz 分开使用也行，比两个 Vault 方便。部署同样是依赖 Netlify + Cloudflare。
最后放一张测速截图吧，甚至和备用站难分伯仲，总之就是花了一周时间彻底改造好了双线方案。一时折腾一时爽，一直折腾火葬场！
<br>
![speedtest.png](https://s2.loli.net/2024/09/26/ewJxTFikEWRmuCS.png)

# 回旋镖

在又一次部署的时候发现意外又来了，触发了 [Netlify的身份验证](https://www.baiwulin.com/89.html)，好的，不想泄露个人信息，我现在觉得 Vercel 最好，立即跑回 Vercel 了。