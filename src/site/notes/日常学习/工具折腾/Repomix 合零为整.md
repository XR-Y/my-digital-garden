---
{"dg-publish":true,"permalink":"/日常学习/工具折腾/Repomix 合零为整/","title":"Repomix 合零为整","tags":["LLM","折腾"],"noteIcon":"1","created":"2025-02-25T15:15:00.815+08:00","updated":"2025-02-25T17:36:27.042+08:00"}
---

这两天 Github Trends 里出现了个工具 [Repomix](https://github.com/yamadashy/repomix)，简单来说就是把整个仓库的各种信息整合成一个 XML/Markdown/Plain 文件，然后喂给模型，让模型充分了解仓库并尝试在后面的问答中寻找符合的关联，感觉是一个不错的提示模板设计案例。

![repomix.png](https://s2.loli.net/2025/02/25/VFRwoHUKd3bfCI4.png)

这个文件中，首先是一长段提示信息，包括目的介绍、文件组织格式说明、使用提示和注意事项。
```text
This file is a merged representation of the entire codebase, combined into a single document by Repomix.

================================================================
File Summary
================================================================

Purpose:
--------
This file contains a packed representation of the entire repository's contents.
It is designed to be easily consumable by AI systems for analysis, code review,
or other automated processes.

File Format:
------------
The content is organized as follows:
1. This summary section
2. Repository information
3. Directory structure
4. Multiple file entries, each consisting of:
  a. A separator line (================)
  b. The file path (File: path/to/file)
  c. Another separator line
  d. The full contents of the file
  e. A blank line

Usage Guidelines:
-----------------
- This file should be treated as read-only. Any changes should be made to the
  original repository files, not this packed version.
- When processing this file, use the file path to distinguish
  between different files in the repository.
- Be aware that this file may contain sensitive information. Handle it with
  the same level of security as you would the original repository.

Notes:
------
- Some files may have been excluded based on .gitignore rules and Repomix's configuration
- Binary files are not included in this packed representation. Please refer to the Repository Structure section for a complete list of file paths, including binary files
- Files matching patterns in .gitignore are excluded
- Files matching default ignore patterns are excluded

Additional Info:
----------------
```
按照上面的描述，第二部分就是仓库的一些基本信息。
接下来按默认顺序传入各个文件的相对路径名，因此实际使用该工具之前得先充分检查需要排除的文件。
有了展开的文件列表树之后，逐个传入对应文件的内容即可，repomix 还提供了如去除注释、去除空行、显示行号等配置可选项，这个部分也是整个文件中占据最多内容量的。
总的来说，功能实现相对简单。除网页端外，VSCode 中也提供了同样功能实现的插件。不过实际使用还是涉及不少细节处理，哪些文件需要排除，剩下的文件中有无隐私、链接以及正则表达式等可能出现安全风险和误导模型的内容。

比较巧合的是，刚好最近 Claude3.7 发布。除了符合直觉的混合推理能力外（估计已经有很多开始卷自适应深度思考的工作了），这一版本的 Claude 更关注现实软件问题的解决，甚至刻意减少了对数学竞赛问题的优化。感觉这可能才是我们普通人更想要的模型，毕竟也不会需要去问模型解决 IMO 世界难题。

![image.png](https://s2.loli.net/2025/02/25/R4HtzSxKqVkDOwv.png)

从图中可以看到，SWE-bench（选取自若干个 python 真实项目的 issues）的显著提升证实了在已有的框架上修复 issue 的 SOTA 能力。那么如果搭配上 Repomix 和 Trae，也就是结合全局理解和上下文窗口，可能能够获得更好的效果。
在不考虑隐私的情况下，AI 各种加持的能力已经越来越恐怖了，只能多尝试充分利用好 AI 工作流来避免被淘汰了。