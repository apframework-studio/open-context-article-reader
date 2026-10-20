# Open Context Article Reader 交接

**日期：** 2026-10-20

**仓库：** `apframework-studio/open-context-article-reader`，本地 `/Users/shoukai/githome/github/apframework-studio/open-context-article-reader`

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

## 验证记录

- Skill Creator `quick_validate.py` 对仓库根目录的结构校验：通过。目标目录的系统 `python3` 缺少 PyYAML，改用 `/Users/shoukai/.pyenv/versions/3.12.13/bin/python3` 完成校验；这不是 Skill 文件错误。
- 用 [Anthropic《Building effective agents》](https://www.anthropic.com/engineering/building-effective-agents) 做过独立行为试读：正文、主要章节和日期可读取；Skill 将其识别为技术实践建议，区分了作者的复杂度选择原则、分析者推断及文章未提供比较数据的经验性主张。依据试读反馈，进一步要求关键结论就近标记来源，并细化图书与超长单篇文章的边界。
- 商业类 [Paul Graham《How to Get Startup Ideas》](https://paulgraham.com/startupideas.html)：正文和注释可读；试读保留“强烈初始需求仍不足以单独证明商业前景”的限定，指出案例无法单独验证普遍结论。哲学/公共论证类 [Isaac Wiegman《Why Arguments (Almost) Never Work》](https://blog.apaonline.org/2024/04/10/why-arguments-almost-never-work-motivated-reasoning-and-persuasion/)：正文可读；试读区分本文的问题诊断与作者留待后文的解决方法。
- 不可访问 URL `https://example.invalid/not-an-article` 的实际访问失败；试读答复要求用户粘贴正文，没有虚构论点。图书长度请求被转交图书阅读流程。自编的低证据短文试读指出“效率提高 300%”的测量与研究出处缺失，没有从单个团队推断所有公司。
- 技术教程 [Josh W. Comeau《An Interactive Guide to Flexbox》](https://www.joshwcomeau.com/css/interactive-guide-to-flexbox/) 的正文和章节可读取。人工检查可还原从主轴/交叉轴到 `flex-basis`、增长/收缩和最小尺寸约束的概念递进；页面包含交互演示，但本次文本读取没有实际操作演示。因而补充了“无法检查嵌入内容时标明限制”的规则。
- 本轮对 `essay/` 的 54 篇 `.mdx` 正文与 54 份带元数据 `.md` 副本做了清点，并对 54 篇做标题与文本形态扫描（39 篇含代码围栏、51 篇含常见 MDX/JSX 开始标签、12 篇超过 2 万字符）；代表性正文试读覆盖 Harness² README、译编笔记、技术教程、PoC、商业方法和概念比较。`docs/phase-1-validation.md` 保存了具体问题、证据边界与短答。关联的 [Harness² 论文](https://arxiv.org/html/2610.14224v1)只用于 README 的外部核对：论文明确区分行为对比和正确性验证，也报告退化与计算成本。本轮没有运行 Harness² benchmark 或文章示例代码。
- 修改 `SKILL.md` 后运行 `/Users/shoukai/.pyenv/versions/3.12.13/bin/python3 /Users/shoukai/.codex/skills/.system/skill-creator/scripts/quick_validate.py .`：`Skill is valid!`。检查 frontmatter 触发描述：仍明确排除书籍、完整论文与写作/发布请求；新增仓库 README 边界在正文，不扩大触发条件。`https://example.invalid/not-an-article` 实际访问失败，试读仅要求提供正文，没有虚构作者观点。`git diff --check` 通过；提交前应再次运行。
- 这些是少量人工试读，不是自动化质量基准。跨语种内容与更多真实低质量博文仍需后续检验。

## 后续工作

- 用固定输入多次独立运行 Skill，并由人盲评主张归属、证据强度和遗漏，判断本轮规则在不同文章与模型上是否稳定；继续扩大到未试读的本地文章和真实低信息质量博文。
- 若需要跨 Agent 产品发布，核对对应产品的 Skill 安装方式及元数据要求；`agents/openai.yaml` 仅在有实际界面需求时添加。
- 公开前选择许可证、示例文章授权和中英文 README 策略。仓库可见性保持私有，除非用户另行要求。
