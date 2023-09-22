---
{"dg-publish":true,"permalink":"/日常学习/Obsidian是如何成为博客的/","noteIcon":"1","created":"2023-09-20T21:35:09.212+08:00","updated":"2023-09-22T21:00:11.080+08:00"}
---


# 0. 一切的起源

众所周知，博客的部署、运营、维护和备案并不简单，如通常不会直接在管理系统后台写博文发布，而是选择其它功能更齐全，外观更美观的笔记软件完成后复制粘贴到后台发布，以及备案过期、域名过期、服务器过期等各种迁移问题。选择已有的产品如语雀、飞书等，又始终对数据安全和自定义度有所缺憾。对于 Notion，国内访问不友好始终是绕不开的问题。
与此同时，在实现了除文献外的记录 **ALL IN OBSIDIAN** 后，有一个明显的问题，就是发布功能是付费服务，并作为 obsidian 难得的盈利点，价格对本穷苦大学生而言并不友好。
幸运的是，Digital Garden 插件很好地解决了上面的两个问题，实现了从笔记到博客发布的一键式流程，尤其是无需操心格式差异（markdown 嵌入）问题。
<br>

# 1. 布告天下

## 1.1 旗开得胜

安装 Digital Garden 插件后，将这个[Github 库](https://github.com/oleeskild/digitalgarden)打开，选择 Deploy，平台选择的是 Vercel（免费版完全足够个人使用+用户量大解决疑难杂症容易）。
部署成功 ✅（status 转为 ready）后，在 Digital Garden 设置页设定好对应的配置，你就可以开始随心所欲发布文章了。主要通过笔记头部的 properties 控制，dg-publish 表示是否发布，dg-pinned 表示固定在文件目录树头部，dg-home 表示设置为起始页，tag 是自行添加的标签等等。
另外，每次更新也直接通过发布中心控制即可，界面友好美观易操作。
![image.png](https://s2.loli.net/2023/09/22/pqoEVcn8stIxUMy.png)

## 1.2 急转直下

然后，就遇到了一个很尴尬的问题，vercel 由于部分用户的滥用，已经基本被**墙**在外了，而博客发布就是给人看的，尤其是国内用户，显然无法接受……
好，就知道果然不可能那么顺利，慢慢来 😴

## 1.2 曲径通幽

首先，买个域名，反正自己博客肯定也要个好看点的域名，vercel 那一长串既不好记也不利于分享。国内各大厂商可买，Namesilo 等国外低价厂商也可，还可以剑走偏锋捞捞免费域名，不选.com 或者.cn 这种应该都挺便宜，一年几块钱。
初心别忘了，是为了国内更好地访问，因此使用 Cloudflare（海外 CDN）来解除封印，虽然 Cloudflare 被称为减速 CDN，但加上后访问 Vercel 的速度还算可以接受，而且白嫖要什么自行车，差不多够用就好。
所以只需要将域名从代理商转到 Cloudflare 接管并配置好 DNS（主要是 A 和 CNAME），其中涉及到 Vercel 域名的记得使用`cname-china.vercel-dns.com`。同样，Vercel 处也对应配上购买的域名，自动生成 SSL 证书并校验通过后，就可以尝试国内访问了，总体速度还行！（下图每次测试随机波动性较大，**仅供参考**）
![Snipaste_2023-09-20_22-23-13.jpg](https://s2.loli.net/2023/09/20/eDUvEgCncWSVwR1.jpg)

> [!hint]+ 一点建议
> 只需要文章发布功能，就可以到此为止了，后续章节仅供习惯折腾，并乐在其中的用户参考。
> <br>

# 2. 海纳百川

## 2.1 百家争鸣

博客是不可能缺少评论系统的，幸运的是，Digital Garden 插件提供了充足的**自定义空间**。本博客选用了[Waline](https://waline.js.org/)，优势是开箱即用，不需要额外折腾审核和数据存储等。同样，部署到 vercel，再借助域名和 Cloudflare 加速国内访问，这里给 Waline 的域名采用刚刚购买域名的二级域名即可。部署成功后，访问`{你的Waline域名}/ui/register`注册成为管理员，即可进入评论后台管理系统。
接着，就是将你的 Waline 系统嵌入到刚刚发布的博客页面中。参考官方文档，只需要在`{你的笔记路径}\src\site\_includes\components\user\common\footer`文件夹下建立一个`njk`后缀的文件，代码如下：

```html
<hr class="content">
<div class="content" id="waline"></div>
<link rel="stylesheet" href="https://unpkg.com/@waline/client@v2/dist/waline.css"/>

<hr class="content">
<div class="content" id="waline"></div>
<link rel="stylesheet" href="https://unpkg.com/@waline/client@v2/dist/waline.css"/>
    <script type="module">
        import { init } from 'https://unpkg.com/@waline/client@v2/dist/waline.mjs';
        init({
            el: '#waline',
            serverURL: $你的 waline 系统地址$,
            emoji: [
                '//unpkg.com/@waline/emojis@1.2.0/weibo',
                '//unpkg.com/@waline/emojis@1.2.0/bmoji',
            ],
            reaction: true,
            dark: 'auto',
        });
</script>
<hr>
```

其中，emoji 为评论系统可用备选表情，dark 为深色模式控制，reaction 则是文章末尾的用户反应，更多 Waline 配置可参考官方文档。

## 2.2 雁过留痕

实际上是比较鸡肋的功能，但既然 Waline 提供了，那用上无妨。如果是打算写在末尾，直接在刚才的 `njk` 文件内附加上如下代码即可。除此之外，受几枝插件的启发，在末尾也添上了[今日诗词 API](https://www.jinrishici.com/)的调用。

```html
<div class="content" align="center">
    <h3 id="jinrishici-sentence" class="content">正在加载今日诗词....</h3>
    <span id="poem_info"></span>
    <script src="https://sdk.jinrishici.com/v2/browser/jinrishici.js" charset="utf-8"></script>
    <script type="text/javascript">
        jinrishici.load(function(result) {
            var sentence = document.querySelector("#jinrishici-sentence")
            var info = document.querySelector("#poem_info")
            sentence.innerHTML = result.data.content
            info.innerHTML = '【' + result.data.origin.dynasty + '】' + result.data.origin.author + '《' + result.data.origin.title + '》'
        });
    </script>
    <h5 class="content">2022–2023 XRYU</h5>
    <script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>
    <span id="busuanzi_container_site_pv">本站总访问量<span id="busuanzi_value_site_pv"></span>次</span>
</div>
```

<br>
# 3. 精细入微

## 3.1 字字珠玑

同样，这次在 header 文件夹下新建对应的 `njk` 文件，引入对应的字体样式。然后在`{你的笔记路径}\src\site\styles\user`目录下新建 SCSS 文件，调用引用的字体即可。通过这种方式，即使是在 Digital Garden 更新文章发布的主题样式，也不会影响字体修改。如，修改字体为霞鹜文楷屏幕阅读版：

```html
<link rel="stylesheet" href="https://cdn.staticfile.org/lxgw-wenkai-screen-webfont/1.6.0/style.css" />
```

<br>
```scss
body {
    --font-default: "LXGW WenKai Screen", sans-serif;
}
```

## 3.2 黑白无间

Waline 配置好跟随系统切换深浅色模式后，主界面自然也要跟进，直接在 header 文件夹下加入脚本代码即可。

```html
<script>
    const darkMode = window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)');
    document.addEventListener("DOMContentLoaded", function() {
        // 判断是否匹配深色模式
        if (darkMode && darkMode.matches) {
            document.body.classList.add('theme-dark');
            document.body.classList.remove('theme-light');
        } else {
            document.body.classList.add('theme-light');
            document.body.classList.remove('theme-dark');
        }
    });
    // 监听主题切换事件
    darkMode && darkMode.addEventListener('change', e => {
        if (e.matches) {
            document.body.classList.add('theme-dark');
            document.body.classList.remove('theme-light');
        } else {
            document.body.classList.add('theme-light');
            document.body.classList.remove('theme-dark');
        }
    });
</script>
```

## 3.3 一字千金

粗略一看，官方竟然没有提供字数统计功能，那就只能自己手动写个勉强够用的了，加在 beforeContent 文件夹下最合适，同样是`njk`后缀文件。

```html
<span id="wordCount" style="color: var(--text-muted); font-size:14px;"></span>
<script type="text/javascript">
  document.addEventListener("DOMContentLoaded", function() { // 一定要注意判断是否加载完成！
    var count = 0; // 统计字数
    var str = document.getElementsByTagName("main")[0].innerHTML; // 网页文字包含标签
    var tmpDiv = document.createElement("div");
    tmpDiv.innerHTML = str;
    str = tmpDiv.textContent || tmpDiv.innerText || "";
    str = str.replace(/\ +/g,"");
    str = str.replace(/[\r\n]/g,"");
    count = str.length;
    var time = Math.max(Math.floor(count / 400), 1); // 阅读时间直接简单粗暴
    document.querySelector("#wordCount").innerHTML = String.fromCodePoint("0x1F4D6") + '本文约 ' + count + ' 字，预计阅读时间 ' + time + ' 分钟。';
  });
</script>
```

<br>
# 4. 微言大义

Memos，一个记录短灵感和备忘录的开源工具，使用 docker **一键部署**，和博客完美互补，GitHub 亦有移动端、小程序端、浏览器插件等多平台支持。

<iframe src="https://usememos.com/" allow="fullscreen" allowfullscreen="" style="height:100%;width:100%; aspect-ratio: 16 / 9; "></iframe>
