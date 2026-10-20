# Open Context Article Reader

一个独立的 Agent Skill，用于理解**单篇博文或网络文章**。它帮助读者看清文章讨论的问题、作者的观点或做法、论证依据、关键概念和适用边界；支持技术、商业、哲学等领域。

## 使用方式

将本仓库目录作为 `open-context-article-reader` Skill 加入所用 Agent 的技能搜索路径，然后提供文章 URL、正文、Markdown 或可读取的本地文本文件。例如：

> 用 open-context-article-reader 帮我理解这篇文章：作者在解决什么问题？核心观点依据是什么？哪些背景和局限需要进一步核对？<文章 URL>

也可以要求“先给我三分钟的概要”“按概念学习方式讲解”或“重点检查论证”。Skill 会根据文章的功能和用户目标调整输出，不要求用户选择固定模式。

## 阅读范围

- 分析单篇文章的主题、问题、观点、结构、证据、概念与局限。
- 对关键缺失背景和时效性事实进行有针对性的外部核对，并区分原文、推断和外部资料。
- 正文无法获取时说明限制；不会仅凭标题或搜索摘要补写内容。

本项目暂不处理整本书、完整学术论文、批量订阅、长期知识库写入或文章发布。它不依赖 Open Context Forge 的 vault。

## 项目文件

- [`SKILL.md`](SKILL.md)：Skill 触发条件、阅读流程和输出约束。
- [`references/methodology.md`](references/methodology.md)：按文章功能选择分析方法。
- [`docs/design.md`](docs/design.md)：需求与设计基线。
- [`docs/HANDOFF.md`](docs/HANDOFF.md)：当前状态和后续工作。

目前仅有说明型 Skill，无运行时依赖或抓取服务。仓库保持私有；公开与许可证将在以后确定。
