# Open Context Article Reader

Language: **English** · [简体中文](README.zh-CN.md)

**Understand one article, including what its evidence can and cannot support.**

Open Context Article Reader is an instruction-only Agent Skill for reading a single blog post or web article. It helps you identify the author's question and central takeaway, explain a few essential ideas in plain language, and separate the article's claims from your own inferences and open questions. It works across technical, business, philosophical, and mixed-topic writing.

## Use the Skill

Make this repository available as `open-context-article-reader` in your agent's Skill search path. Keep `SKILL.md` and `references/` together. Then provide one article URL, pasted text, Markdown/MDX, or a readable local text file.

For a quick, article-only reading, use this prompt after the Skill appears in your agent's Skill list:

> Use $open-context-article-reader to read this article: 〈article URL or local file path〉. Give me its central takeaway in one sentence, then explain 3–5 essential points in plain language. For each point, say what it means here and which step, mechanism, or example in the article makes it concrete. Cite the relevant section. Briefly distinguish the author's claims, your inferences, and what remains unverified. Keep it concise and use only this article.

To focus on a particular idea, add:

> Focus on 〈term or question〉 if it appears in this article. If it does not, say so briefly and choose the article's own core points; do not carry over terms from a previous article.

If the Skill has not been added to the search path, ask your agent to read and follow this repository's `SKILL.md` by path. That uses the file as instructions but does not register the Skill for `$` invocation.

## Reading boundaries

- The Skill reads the article body before summarizing it. If the body or an important embedded element cannot be accessed, it states the limit rather than filling in missing details.
- A conclusion is a candidate for the central takeaway, checked against the rest of the article. Examples, author-reported results, outside findings, and independent verification remain distinct.
- External research addresses a specific gap when needed. You can request an article-only reading as in the prompt above.
- Full books, full academic papers, batch feeds, automatic knowledge-base writes, and article publishing are outside this Skill's scope. It does not depend on the Open Context Forge vault.

## Project files

- [`SKILL.md`](SKILL.md) — invocation boundary, reading workflow, and evidence rules.
- [`references/methodology.md`](references/methodology.md) — questions for different article types, read only when useful.
- [`docs/design.md`](docs/design.md) — design baseline.
- [`docs/phase-1-validation.md`](docs/phase-1-validation.md) — sample reading cases and their limits.
- [`docs/HANDOFF.md`](docs/HANDOFF.md) — current state and open work.

This Skill has no runtime service or scripts.

## License

[MIT](LICENSE) © 2026 Shoukai Huang. The linked articles and other third-party sources remain under their respective owners' terms; their full text is not included in this repository.
