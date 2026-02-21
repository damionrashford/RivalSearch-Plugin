# Rival Search Plugin — Project Brain

> This file is read by Claude when working in this project. It contains architecture, conventions, and tool references. For human-facing docs, see README.md.

## What This Plugin Does

This is a Claude Code plugin that gives Claude a full research team. It connects to [RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP) — a hosted MCP server with 10 free research tools, zero API keys.

The plugin provides: 5 workflow skills, 6 specialist agents, portable hooks, and the live MCP connection.

## Architecture

```
rival-search-plugin/
├── .claude-plugin/
│   ├── plugin.json           # Plugin manifest (name, version, component paths)
│   └── marketplace.json      # Marketplace distribution config
├── .mcp.json                 # MCP connection → https://RivalSearchMCP.fastmcp.app/mcp
├── agents/                   # 6 specialist agents (full frontmatter)
├── skills/                   # 5 slash-command workflows
├── hooks/
│   └── hooks.json            # Plugin-level event hooks
├── CLAUDE.md                 # This file
├── LICENSE                   # MIT license
└── README.md                 # Human-facing documentation
```

## Skills → Agent Mapping

| Skill | What It Does | Used By Agents |
|-------|-------------|----------------|
| `research` | Multi-source research + academic papers, datasets, implementations | research-analyst, content-strategist |
| `competitive-intel` | Company/market/website intelligence + SWOT | competitive-intel, due-diligence |
| `due-diligence` | Company OR person investigation + risk assessment | due-diligence |
| `trend-intel` | News digests + trend trajectory + velocity indicators | trend-analyst, content-strategist |
| `fact-check` | Claim verification + confidence scoring + evidence chains | fact-checker |

The `skills` field in agent frontmatter **injects full skill content** into the agent's context at startup.

## The 10 MCP Tools (Parameter Reference)

All tools are from [RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP). No auth required.

### web_search
Multi-engine search across DuckDuckGo, Yahoo, and Wikipedia.
- `query` (string, required): Search query
- `num_results` (int): Results per engine (default: 10)
- `extract_content` (bool): Extract page content from results
- `follow_links` (bool): Follow and extract linked pages
- `max_depth` (int): Link following depth

### social_search
Search Reddit, Hacker News, Dev.to, Product Hunt, and Medium.
- `query` (string, required): Search query
- `platforms` (array): `["reddit", "hackernews", "devto", "producthunt", "medium"]`
- `max_results_per_platform` (int): Results per platform (default: 10)
- `time_filter` (string): `"day"`, `"week"`, `"month"`, `"year"`

### news_aggregation
Aggregate from Google News, DuckDuckGo News, and Yahoo News.
- `query` (string, required): News search query
- `max_results` (int): Total results (default: 10)
- `time_range` (string): `"day"`, `"week"`, `"month"`

### github_search
Search GitHub repos (60 req/hour rate limit).
- `query` (string, required): Search query
- `sort` (string): `"stars"`, `"forks"`, `"updated"`, `"best-match"`
- `max_results` (int): Number of repos (default: 10)
- `include_readme` (bool): Include README content

### scientific_research
Academic papers and dataset discovery.
- `operation` (string, required): `"academic_search"` or `"dataset_discovery"`
- `query` (string, required): Research query
- `max_results` (int): Number of results
- `sources` (array): `["semantic_scholar", "arxiv"]` for papers; Kaggle/HuggingFace for datasets

### content_operations
Retrieve, analyze, extract, or stream web content.
- `operation` (string, required): `"retrieve"`, `"analyze"`, `"extract"`, `"stream"`
- For retrieve: `url`, `extraction_method` (`"markdown"`, `"text"`, `"html"`)
- For analyze: `content`, `analysis_type` (`"general"`, `"business"`, `"technical"`), `extract_key_points`, `summarize`
- For extract: `url`, `link_type` (`"all"`, `"internal"`, `"external"`), `max_links`

### map_website
Explore and map website structure.
- `url` (string, required): Website URL
- `mode` (string): `"map"`, `"research"`, `"docs"`
- `max_pages` (int): Pages to crawl
- `max_depth` (int): Crawl depth

### document_analysis
Extract text from PDFs, Word docs, text files, images (OCR).
- `url` (string, required): Document URL
- `max_pages` (int): Pages to process
- `extract_metadata` (bool): Extract document metadata
- `summary_length` (int): Summary word count

### research_topic
Quick end-to-end research workflow.
- `topic` (string, required): Research topic

### research_agent
AI agent with autonomous multi-tool research.
- `query` (string, required): Research question

## Conventions for Writing Skills

Skills live in `skills/<skill-name>/SKILL.md`.

Required frontmatter:
```yaml
---
name: skill-name
description: What it does. Use when [trigger].
argument-hint: "[what the user should provide]"
allowed-tools: mcp__RivalSearchMCP__web_search, mcp__RivalSearchMCP__social_search, Read, Grep, Glob, WebFetch, WebSearch
---
```

Rules:
1. `$ARGUMENTS` captures user input after the slash command
2. Number each step, specify exact MCP tool and parameters
3. End with a "Compile Report" step defining output sections
4. Require inline citations: `[Source Name](URL)`
5. Include "Report progress after each step"

## Conventions for Writing Agents

Agents live in `agents/<agent-name>.md`.

Required frontmatter:
```yaml
---
name: agent-name
description: What it does. Use proactively when [trigger].
model: inherit
tools: [Read, Grep, Glob, WebFetch, WebSearch, mcp__RivalSearchMCP__*]
disallowedTools: [Edit, Write, NotebookEdit]
skills: [skill-name]
mcpServers: [RivalSearchMCP]
memory: user
maxTurns: 40
hooks:
  Stop:
    - hooks:
        - type: prompt
          prompt: "Quality gate..."
          timeout: 15
---
```

Rules:
1. All research agents are **read-only** — disallow Edit, Write, NotebookEdit
2. Include a tool table mapping MCP tools to purposes
3. Define 4-6 phase methodology (scope → collect → validate → synthesize)
4. Define output format with numbered sections
5. Include guidelines for citations, objectivity, gap identification

## Conventions for Hooks

Plugin hooks: `hooks/hooks.json`. Three types:
- **command**: Shell command (JSON on stdin)
- **prompt**: LLM evaluates a condition → `{ok: true/false}`
- **agent**: Multi-turn subagent with tool access

Rules:
- Use `mcp__RivalSearchMCP__*` matcher for tool events
- Keep portable (macOS + Linux)
- Timeouts: 5s logging, 15s validation
- Use `jq` to parse JSON stdin

## Quality Standards

Every research output must:
1. Cite sources inline: `[Source Name](URL)`
2. End with a Sources section listing all URLs
3. Use structured headers
4. Distinguish facts vs opinions vs speculation
5. Flag information recency
6. Identify gaps — what couldn't be found
7. Use tables for comparisons

## Testing

```bash
claude --plugin-dir ./rival-search-plugin
```

Verify: skills appear as `/rival-search:*`, agents in `/agents`, MCP tools respond, hooks log to `/tmp/rival-search-audit.log`.

## Key Links

- Plugin manifest: `.claude-plugin/plugin.json`
- MCP connection: `.mcp.json`
- RivalSearchMCP: https://github.com/damionrashford/RivalSearchMCP
- MCP endpoint: `https://RivalSearchMCP.fastmcp.app/mcp`
