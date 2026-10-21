# Open Context Article Reader 交接

**日期：** 2026-10-21

**仓库：** `apframework-studio/open-context-article-reader`

## 当前状态

- GitHub 仓库在本次初始化前为空，仍保持 `PRIVATE`。本地从远端克隆，首次提交 `df340bc` 已推送至 `main`，远端默认分支已核实为 `main`。
- 已通过 `codex app` 打开本地目录，并通过应用项目列表核实：`open-context-article-reader` 已注册为独立本地 Git 项目，可切换到该项目继续工作。
- 根目录 `SKILL.md` 是可独立使用的 Skill；`references/methodology.md` 收纳不同文章功能的分析视角。没有运行时服务、脚本或 vault 依赖。
- 第一阶段针对 `harness2` README 和本地 `essay/` 原始文章的领域问题、选样与人工试读见 `docs/phase-1-validation.md`。目录只作只读样本来源，没有纳入本仓库依赖或复制第三方正文。
- `docs/design.md` 是从 Open Context Forge 切换前草案移入的本仓库设计基线；`README.md` 面向使用者；`AGENTS.md` 约束后续协作。
- 用户的范围：单篇技术、商业、哲学等博文/网络文章；关注问题、观点、方法、证据、概念与局限。书籍另做 Skill，当前不关联知识库。DeepRead 仅作同类参考，不沿用其书籍场景或模式划分。

## 已选设计

1. 先确定文章的**领域、功能、信息状态**，然后按其目的选择论证、过程、决策或概念分析视角。
2. 关键结论区分原文陈述、基于原文的推断、外部资料和未知；正文不可得时不依标题代写理解。
3. 外部研究只为具体理解或验证缺口服务，并与作者观点分开。
4. 输出随用户目标和文章复杂度伸缩；不做无解释的质量总分，也不要求固定的 deep/map 模式。
5. 第一阶段将“谁提出主张”和“什么证据足以支持主张”分开。译编/笔记需要保留作者层级；教程、PoC 与经验文需要分清方案、文中报告的结果和本次独立验证。仓库 README 只作为有界说明文本，不能代替整仓库审计或完整论文阅读。
6. 用户用《QQ音乐 Harness Engineering 实践》的结语指出：仅还原架构与证据边界还不够，简版理解也应抓住作者明确的中心句，并把其中少数关键词回接正文，用通俗短句说明具体做法。结语只作候选中心，要核对正文；正文缺失时不补造细节。`SKILL.md` 的阅读步骤与输出形状已据此收紧。
7. 连续试读 QQ 音乐、Personal Agent 与《金刚经》商业类比三篇后，进一步明确：结尾的局部市场预测不应遮蔽全文主线；换文章时，若用户提示词仍带上一篇术语，应指出不匹配并以新文章为准。三篇阅读路径留在 `docs/phase-1-validation.md`，可复制提示词留在 `README.md`；运行入口不存三篇范文。
8. README 采用同组织 `open-context-clipper` 的双语入口形式：英文 `README.md` 为主入口，标题下链接 `README.zh-CN.md`；中文版提供返回英文版的链接。两版都覆盖用途、提示词、阅读边界和项目文件；中文提示词从原主 README 保留至中文版。

## 验证记录

- Skill Creator `quick_validate.py` 对仓库根目录的结构校验：通过。最初测试环境的系统 `python3` 缺少 PyYAML，改用已安装 PyYAML 的 Python 3.12 完成校验；这不是 Skill 文件错误。
- 用 [Anthropic《Building effective agents》](https://www.anthropic.com/engineering/building-effective-agents) 做过独立行为试读：正文、主要章节和日期可读取；Skill 将其识别为技术实践建议，区分了作者的复杂度选择原则、分析者推断及文章未提供比较数据的经验性主张。依据试读反馈，进一步要求关键结论就近标记来源，并细化图书与超长单篇文章的边界。
- 商业类 [Paul Graham《How to Get Startup Ideas》](https://paulgraham.com/startupideas.html)：正文和注释可读；试读保留“强烈初始需求仍不足以单独证明商业前景”的限定，指出案例无法单独验证普遍结论。哲学/公共论证类 [Isaac Wiegman《Why Arguments (Almost) Never Work》](https://blog.apaonline.org/2024/04/10/why-arguments-almost-never-work-motivated-reasoning-and-persuasion/)：正文可读；试读区分本文的问题诊断与作者留待后文的解决方法。
- 不可访问 URL `https://example.invalid/not-an-article` 的实际访问失败；试读答复要求用户粘贴正文，没有虚构论点。图书长度请求被转交图书阅读流程。自编的低证据短文试读指出“效率提高 300%”的测量与研究出处缺失，没有从单个团队推断所有公司。
- 技术教程 [Josh W. Comeau《An Interactive Guide to Flexbox》](https://www.joshwcomeau.com/css/interactive-guide-to-flexbox/) 的正文和章节可读取。人工检查可还原从主轴/交叉轴到 `flex-basis`、增长/收缩和最小尺寸约束的概念递进；页面包含交互演示，但本次文本读取没有实际操作演示。因而补充了“无法检查嵌入内容时标明限制”的规则。
- 本轮对 `essay/` 的 54 篇 `.mdx` 正文与 54 份带元数据 `.md` 副本做了清点，并对 54 篇做标题与文本形态扫描（39 篇含代码围栏、51 篇含常见 MDX/JSX 开始标签、12 篇超过 2 万字符）；代表性正文试读覆盖 Harness² README、译编笔记、技术教程、PoC、商业方法和概念比较。`docs/phase-1-validation.md` 保存了具体问题、证据边界与短答。关联的 [Harness² 论文](https://arxiv.org/html/2610.14224v1)只用于 README 的外部核对：论文明确区分行为对比和正确性验证，也报告退化与计算成本。本轮没有运行 Harness² benchmark 或文章示例代码。
- 修改 `SKILL.md` 后运行 Skill Creator 的 `quick_validate.py .`：`Skill is valid!`。检查 frontmatter 触发描述：仍明确排除书籍、完整论文与写作/发布请求；新增仓库 README 边界在正文，不扩大触发条件。`https://example.invalid/not-an-article` 实际访问失败，试读仅要求提供正文，没有虚构作者观点。`git diff --check` 通过；提交前应再次运行。
- 2026-10-21 的追加用例与人工复测见 `docs/phase-1-validation.md`：“QQ 音乐”全文先提取中心意思，再对四个结语短语给出正文支持的简短解释；仅有结语的缺失正文场景保留四项主张，但不补造目录、字段或门禁细节；另用 Foundation Sprint 检查不会强制凑固定条数。上一轮实际答复遗漏结语展开，构成这次修改的可观察基线。仍需要固定输入的独立重复运行检验稳定性。
- 三篇连续真实试读的输入、中心句取法、正文回查和证据界限已整理进 `docs/phase-1-validation.md`；Personal Agent 用例明确暴露了沿用旧术语的提示词风险，《金刚经》用例检验跨领域类比与案例证据的分界。新增规则是对可观察风险的窄幅保护，尚未进行修改后多次独立模型运行。
- 本次改动后运行 Skill Creator 的 `quick_validate.py .`，结果为 `Skill is valid!`；`git diff --check` 通过。手动对照三篇已读全文与仅有 QQ 音乐结语的缺失正文场景，检查新规则不会要求补造正文信息；frontmatter 仍明确排除整本书、完整论文及写作/发布请求。这是规则与既有试读的人工核对，不是修改后重新运行的独立模型评测。
- README 双语整理后核对了两个文件中的 12 个相对 Markdown 链接，目标均存在；`git diff --check` 通过。该次整理只改文档，没有改动 Skill 阅读行为。
- 这些是少量人工试读，不是自动化质量基准。跨语种内容与更多真实低质量博文仍需后续检验。

## 公开准备检查（2026-10-21）

- 仓库自身内容采用与 `open-context-clipper` 逐字一致的 MIT `LICENSE`，版权行为 `Copyright (c) 2026 Shoukai Huang`；中英文 README 已链接协议。外部文章与论文仍归各自权利人，本仓库只保留链接、少量短语和自行撰写的分析，没有第三方文章全文。
- 核对本次提交前全部 3 个现有提交的文件名与内容：没有文章原文文件、`.env`、私钥或常见凭据特征；当时已跟踪文件都是 Markdown 与 `.gitignore`。旧版 `docs/HANDOFF.md` 在历史提交中包含本机用户目录路径，当前版本已移除；路径本身未包含凭据，但公开 Git 历史时仍可见，不为此重写历史。
- 当前 9 个 Markdown 文件中的 15 个相对链接均有本地目标；`LICENSE` 与 Clipper 的文件比较一致；Skill Creator `quick_validate.py .` 返回 `Skill is valid!`；`git diff --check` 通过。`.DS_Store` 由 `.gitignore` 排除，未纳入 Git。
- GitHub 仓库目前仍为 `PRIVATE`，默认分支为 `main`，描述与 topics 为空。公开时可使用描述 `An Agent Skill for understanding one web article, its core ideas, and evidence limits.`，topics 可设为 `agent-skills`、`article-reading`、`reading-comprehension`；远端可见性尚未变更。

## 后续工作

- 用固定输入多次独立运行 Skill，并由人盲评主张归属、证据强度和遗漏，判断本轮规则在不同文章与模型上是否稳定；继续扩大到未试读的本地文章和真实低信息质量博文。
- 若需要跨 Agent 产品发布，核对对应产品的 Skill 安装方式及元数据要求；`agents/openai.yaml` 仅在有实际界面需求时添加。
- 新增示例文章时继续控制短摘录范围；可按需要补充仓库描述与 topics。仓库可见性保持私有，除非用户明确要求变更。
