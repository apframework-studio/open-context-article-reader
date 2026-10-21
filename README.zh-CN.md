# Open Context Article Reader · 单篇文章阅读

语言：[English](README.md) · **简体中文**

**读懂一篇文章，也看清它的证据能支持到哪里。**

Open Context Article Reader 是一个仅包含说明文件的 Agent Skill，用于理解**单篇博文或网络文章**。它帮助你找出作者的问题和中心意思，用通俗语言解释少数关键概念，并区分原文主张、读者推断与尚未核实的地方。技术、商业、哲学及跨领域文章都在范围内。

## 使用方式

将本仓库作为 `open-context-article-reader` 加入所用 Agent 的 Skill 搜索路径，并保留 `SKILL.md` 与 `references/` 的相对位置。然后提供一篇文章的 URL、粘贴的正文、Markdown/MDX，或可读取的本地文本文件。

Skill 出现在技能列表后，可用下面的提示词快速理解文章：

> 使用 $open-context-article-reader 阅读这篇文章：〈文章 URL 或本地文件路径〉。请用一句话说清作者的中心意思，再选 3–5 个真正支撑它的要点；每点用通俗语言解释其含义和文中的具体做法或例子。指出作者陈述、你的推断与尚缺的证据，并标注对应章节。仅依据本文，控制在 400–600 字。

若有特别想弄懂的术语，可追加一句：

> 重点解释本文中的〈术语或问题〉。若这些词不在这篇文章中，请先说明，再按本文实际内容选择核心要点；不要沿用上一篇文章的概念。

尚未将 Skill 加入搜索路径时，可让 Agent 通过路径先阅读并按照本仓库的 `SKILL.md`。这样可以按文件执行，但不表示 Skill 已注册为可用 `$` 调用的项目。

## 阅读边界

- 先读正文，再提炼中心意思。若正文或承载关键证据的嵌入内容无法读取，要说明限制，不补造细节。
- 结语只是候选中心句，要用正文核对。案例、作者自述的结果、外部资料和本次独立核验应分别标明。
- 外部调研只回答具体缺口；也可以像上面的提示词一样，指定仅依据文章分析。
- 整本书、完整学术论文、批量订阅、自动写入知识库与文章发布不在范围内。本 Skill 不依赖 Open Context Forge 的 vault。

## 项目文件

- [`SKILL.md`](SKILL.md)：触发边界、阅读流程与证据规则。
- [`references/methodology.md`](references/methodology.md)：按需选用的文章分析问题。
- [`docs/design.md`](docs/design.md)：设计基线。
- [`docs/phase-1-validation.md`](docs/phase-1-validation.md)：试读案例及其限制。
- [`docs/HANDOFF.md`](docs/HANDOFF.md)：当前状态与待办事项。

本 Skill 无运行时服务或脚本。

## 开源协议

[MIT](LICENSE) © 2026 Shoukai Huang。文中链接的文章及其他第三方资料仍按各自权利人的条款使用；本仓库未收录其全文。
