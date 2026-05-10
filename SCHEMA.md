# Wiki Schema

## Domain
AI/ML 工具、编码助手、浏览器自动化、知识管理、Web 开发 — 任何与 AI 工具链和开发者工作流相关的话题。

## Conventions
- File names: lowercase, hyphens, no spaces (e.g., `transformer-architecture.md`)
- Every wiki page starts with YAML frontmatter (see below)
- Use `[[wikilinks]]` to link between pages (minimum 2 outbound links per page)
- When updating a page, always bump the `updated` date
- Every new page must be added to `index.md` under the correct section
- Every action must be appended to `log.md`
- **Provenance markers:** On pages that synthesize 3+ sources, append `^[raw/articles/source-file.md]`
  at the end of paragraphs whose claims come from a specific source.
- **Language:** 内容可以用中文或英文，根据来源语言自然决定

## Frontmatter
  ```yaml
  ---
  title: Page Title
  created: YYYY-MM-DD
  updated: YYYY-MM-DD
  type: entity | concept | comparison | query | summary
  tags: [from taxonomy below]
  sources: [raw/articles/source-name.md]
  # Optional quality signals:
  confidence: high | medium | low
  contested: true
  contradictions: [other-page-slug]
  ---
  ```

## raw/ Frontmatter
```yaml
---
source_url: https://example.com/article
ingested: YYYY-MM-DD
sha256: <hex digest of the raw content below the frontmatter>
---
```

## Tag Taxonomy
- Tools: ai-tool, coding-assistant, browser-automation, design-tool, knowledge-mgmt, database, framework, tool, cdp, code-indexing, crawler, rust, self-healing, skill-system, visualization, worktree, backend, mcp, gui, ide
- People/Orgs: person, company, lab, open-source
- Techniques: prompt-engineering, fine-tuning, inference, alignment, debugging, agent, workflow, delegate, subagent, cron, kanban, orchestration, skill-discoverability, automation
- Concepts: operator-mode, codemaps, knowledge-graph, rag-alternative, ai-agent, browser, headless, llm-wiki, stealth, isolation, multi-agent, claude-code, anthropic
- Meta: comparison, timeline, controversy, prediction

## Page Thresholds
- **Create a page** when an entity/concept appears in 2+ sources OR is central to one source
- **Add to existing page** when a source mentions something already covered
- **DON'T create a page** for passing mentions
- **Split a page** when it exceeds ~200 lines
- **Archive a page** when its content is fully superseded

## Entity Pages
One page per notable entity. Include:
- Overview / what it is
- Key facts and dates
- Relationships to other entities ([[wikilinks]])
- Source references

## Concept Pages
One page per concept or topic. Include:
- Definition / explanation
- Current state of knowledge
- Open questions or debates
- Related concepts ([[wikilinks]])

## Comparison Pages
Side-by-side analyses. Include:
- What is being compared and why
- Dimensions of comparison (table format preferred)
- Verdict or synthesis
- Sources

## Update Policy
When new information conflicts with existing content:
1. Check the dates — newer sources generally supersede older ones
2. If genuinely contradictory, note both positions with dates and sources
3. Mark the contradiction in frontmatter: `contradictions: [page-name]`
4. Flag for user review in the lint report

## Graphify Integration
This wiki integrates with [Graphify](https://github.com/safishamsi/graphify) for knowledge graph visualization:
- Run `graphify ./raw` or `graphify .` to build/update the graph
- Output in `graphify-out/`: `graph.html`, `GRAPH_REPORT.md`, `graph.json`
- A cron job can run `graphify --update .` daily to keep the graph current
- The graph complements the wiki's manual cross-references with automated semantic connections