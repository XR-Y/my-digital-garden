---
{"dg-publish":true,"permalink":"/README/","title":"Welcome!","tags":["home","gardenEntry"],"noteIcon":"1","created":"2023-07-14T17:22:00.770+08:00","updated":"2023-09-15T13:32:10.331+08:00"}
---


> [!cite] 把诗书马上，笑驱锋镝。✍️

👋 游客朋友，欢迎光临！
<pre class="dataview dataview-error">Evaluation Error: SyntaxError: Invalid regular expression: missing /
    at DataviewInlineApi.eval (plugin:dataview:18404:21)
    at evalInContext (plugin:dataview:18405:7)
    at asyncEvalInContext (plugin:dataview:18412:16)
    at DataviewJSRenderer.render (plugin:dataview:18436:19)
    at DataviewJSRenderer.onload (plugin:dataview:18020:14)
    at e.load (app://obsidian.md/app.js:1:720327)
    at DataviewApi.executeJs (plugin:dataview:18954:18)
    at Publisher.eval (plugin:digitalgarden:14418:23)
    at Generator.next (&lt;anonymous&gt;)
    at eval (plugin:digitalgarden:78:61)</pre>([\s\S]*?)```[\s]*/g, (a, b) => b)
//全局匹配删除线
.replace(/\~\~(.*?)\~\~/g, (a, b) => b)
//全局匹配无序列表
.replace(/[\s]*[-\*\+]+(.*)/g, (a,b) => b)
//全局匹配有序列表
.replace(/[\s]*[0-9]+\.(.*)/g, (a,b) => b)
//全局匹配标题
.replace(/(#+)(.*)/g, (a, b, c, d) => c)
//全局匹配摘要
.replace(/(>+)(.*)/g, (a, b, c) => c)
//全局匹配换行
.replace(/\r\n/g, "").replace(/\n/g, "").replace(/\s/g, "")
let wowWord = Math.floor(content.length / 10000)
let wowBook = ""
switch (true) {
	case wowWord >= 300:
        wowBook = "写完一本 司马光 的《资治通鉴》了！";
        break;
	case wowWord >= 150:
        wowBook = "写完一本 阿耐 的《大江东去》了！";
        break;
	case wowWord >= 125:
        wowBook = "写完一本 金庸 的《天龙八部》了！";
        break;
    case wowWord >= 100:
        wowBook = "写完一本 金庸 的《笑傲江湖》了！";
        break;
	case wowWord >= 85:
        wowBook = "写完一本 路遥 的《平凡的世界》了！";
        break;
	case wowWord >= 80:
        wowBook = "写完一本我国著名的四大名著之一《水浒传》了！";
        break;
    case wowWord >= 75:
        wowBook = "写完一本我国著名的四大名著之一《红楼梦》了！";
        break;
    case wowWord >= 70:
        wowBook = "写完一本我国著名的四大名著之一《西游记》了！";
        break;
    case wowWord >= 65:
        wowBook = "写完一本 老舍 的《四世同堂》了！";
        break;
	case wowWord >= 60:
        wowBook = "写完一本我国著名的四大名著之一《三国演义》了！";
        break;
    case wowWord >= 50:
        wowBook = "写完一本 陈忠实 的《白鹿原》了！";
        break;
    case wowWord >= 45:
        wowBook = "写完一本 霍达 的《穆斯林的葬礼》了！";
        break;
    case wowWord >= 43:
        wowBook = "写完一本 贾平凹 的《秦腔》了！";
        break;
    case wowWord >= 40:
        wowBook = "写完一本 闫真 的《沧浪之水》了！";
        break;
    case wowWord >= 35:
        wowBook = "写完一本 东野圭吾 的《白夜行》了！";
        break;
    case wowWord >= 34:
        wowBook = "写完一本 雨果 的《巴黎圣母院》了！";
        break;
    case wowWord >= 32:
        wowBook = "写完一本 吴敬梓 的《儒林外史》了！";
        break;
    case wowWord >= 31:
        wowBook = "写完一本 阿来 的《尘埃落定》了！";
        break;
    case wowWord >= 30:
        wowBook = "写完一本 茅盾 的《子夜》了！";
        break;
    case wowWord >= 28:
        wowBook = "写完一本 茨威格 的《昨日的世界》了！";
        break;
    case wowWord >= 26:
        wowBook = "写完一本 埃德加·斯诺 的《红星照耀中国》了！";
        break;
    case wowWord >= 25:
        wowBook = "写完一本 钱钟书 的《围城》了！";
        break;
    case wowWord >= 23:
        wowBook = "写完一本 简·奥斯汀 的《傲慢与偏见》了！";
        break;
    case wowWord >= 22:
        wowBook = "写完一本 加西亚·马尔克斯 的《百年孤独》了！";
        break;
    case wowWord >= 21:
        wowBook = "写完一本 老舍 的《骆驼祥子》了！";
        break;
    case wowWord >= 20:
        wowBook = "写完一本 刘慈欣 的《三体》了！";
        break;
    case wowWord >= 19:
        wowBook = "写完一本 卡勒德·胡塞尼 的《追风筝的人》了！";
        break;
    case wowWord >= 18:
        wowBook = "写完一本 沈从文 的《边城》了！";
        break;
    case wowWord >= 17:
        wowBook = "写完一本 萧红 的《呼兰河传》了！";
        break;
    case wowWord >= 16:
        wowBook = "写完一本 王小波 的《沉默的大多数》了！";
        break;
    case wowWord >= 15:
        wowBook = "写完一本 鲁迅 的《狂人日记》了！";
        break;
    case wowWord >= 14:
        wowBook = "写完一本 白先勇 的《台北人》了！";
        break;
    case wowWord >= 13:
        wowBook = "写完一本 曹禺 的《雷雨》了！";
        break;
    case wowWord >= 12:
        wowBook = "写完一本 余华 的《活着》了！";
        break;
    case wowWord >= 11:
        wowBook = "写完一本 鲁迅 的《彷徨》了！";
        break;
    case wowWord >= 10:
        wowBook = "写完一本 杨绛 的《我们仨》了！";
        break;
    case wowWord >= 9:
        wowBook = "写完一本 林海音 的《城南旧事》了！";
        break;
    case wowWord >= 7:
        wowBook = "写完一本 鲁迅 的《呐喊》了！";
        break;
    case wowWord >= 5:
        wowBook = "写完一本 埃克苏佩里 的《小王子》了！";
        break;
    case wowWord >= 3:
        wowBook = "写完一本 王小波 的《黄金时代》了！";
        break;
    case wowWord >= 1:
        wowBook = "写完一本 瞿秋白 的《多余的话》了！";
        break;
}

let totalMd = "👏 创建 " + allFile.length+" 篇文档，共 " + content.length + " 字，" + wowBook
dv.paragraph(totalMd)
```

- 🤔 关于我
  - NJU SE 在读 📖
  - 可以在[GitHub](https://github.com/XR-Y)找到我 👈
  - 实用主义践行者 🙌
  - 在极简主义和花里胡哨之间反复横跳 🤹
  - 随缘更新，佛系研学，率性生活 🎉
  
- 🌏 关于本站
	- 域名：Namesilo
	- 记录：Obsidian + 插件Digital Garden
	- 格式：Markdown
	- 项目：Github
	- 托管：Vercel
	- CDN：Cloudflare
	- 评论：Waline