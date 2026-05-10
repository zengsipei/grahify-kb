# Wiki Knowledge Base

This project has an LLM Wiki knowledge base and a Graphify knowledge graph.

## Hermes 编码准则

当在 Hermes 中执行编码任务时（terminal、patch、write_file、read_file、search_files、delegate_task 等）：
- 用 read_file 读文件，不要 cat；用 search_files 搜内容，不要 grep；用 patch 改文件，不要 sed
- 合并相邻工具调用，减少延迟；patch 优先于 write_file
- 只改任务相关的行，不顺手优化相邻代码
- 改完就跑验证命令，用 todo 追踪步骤

## LLM Wiki (manual curation)

- **Location:** `/opt/data/workspace/wiki/`
- **Schema:** Read `SCHEMA.md` before any wiki operation
- **Index:** `index.md` lists all pages with summaries
- **Log:** `log.md` tracks all changes (append-only)

Rules:
- Always orient yourself first: read SCHEMA.md + index.md + recent log.md
- Create pages only for entities/concepts that appear in 2+ sources or are central
- Every page must have YAML frontmatter (title, created, updated, type, tags, sources)
- Every page must link to at least 2 other pages via [[wikilinks]]
- Tags must come from the taxonomy in SCHEMA.md
- Never modify files in `raw/` — they are immutable sources
- Always update index.md and log.md after any change

## Graphify (automated knowledge graph)

- **Graph output:** `graphify-out/` (90 nodes, 94 edges, 11 communities)
- **Visualization:** `graphify-out/graph.html` — interactive D3 force-directed graph
- **Report:** `graphify-out/GRAPH_REPORT.md` — god nodes, surprising connections, knowledge gaps

Rules:
- Before answering architecture or codebase questions, read `graphify-out/GRAPH_REPORT.md`
- For cross-module "how does X relate to Y" questions, prefer graphify query over grep
- After modifying content, run `PYTHONPATH=/opt/data/workspace/graphify python3 -m graphify update .` to keep the graph current

## Integration

The wiki (manual) and graphify (automated) complement each other:
- Wiki provides curated pages with human-quality cross-references and provenance
- Graphify provides automated semantic connections and community detection
- Raw sources in `raw/articles/` feed both systems