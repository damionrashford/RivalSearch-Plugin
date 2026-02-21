# Rival Search Plugin

**A Claude Code plugin with AI research agent skills powered by MCP.**

> No API keys, no subscriptions, no configuration. Install and start researching.

Powered by **[RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP)** — 10 MCP research tools across web, social, news, GitHub, academic, and document sources.

---

## What This Claude Code Plugin Does

This Claude Code plugin gives Claude a complete AI research platform — 10 MCP tools, 5 agent skills, and 6 specialist agents that work together to handle any research task.

- **10 MCP tools** via [RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP) — web search, social media, news, GitHub, academic papers, document analysis, and more
- **5 agent skills** — slash commands that run multi-step research workflows and produce structured reports
- **6 AI research agents** — specialist analysts that Claude invokes automatically based on your task
- **Portable hooks** — audit logging and quality gates that travel with the plugin

## Example Queries

Once this Claude Code plugin is installed, try these agent skills:

```
"Research the current state of AI code generation tools"
/rival-search:competitive-intel Cursor
/rival-search:fact-check "OpenAI revenue exceeded $2 billion in 2024"
/rival-search:due-diligence Anthropic
/rival-search:trend-intel AI agents for software development
```

---

## Getting Started

### Claude Code Marketplace (Recommended)

```bash
/plugin marketplace add damionrashford/rival-search
/plugin install rival-search@damionrashford-rival-search
```

### Local Directory

```bash
git clone https://github.com/damionrashford/rival-search.git
claude --plugin-dir ./rival-search
```

This Claude Code plugin auto-connects to the hosted [RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP) MCP server. All 10 tools work immediately — no setup, no API keys.

---

## MCP Research Tools

All 10 MCP tools are provided by [RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP) — zero authentication required.

| Tool | What It Does |
|------|-------------|
| `web_search` | Multi-engine search across DuckDuckGo, Yahoo, and Wikipedia |
| `social_search` | Search Reddit, Hacker News, Dev.to, Product Hunt, Medium |
| `news_aggregation` | Aggregate news from Google News, DuckDuckGo News, Yahoo News |
| `github_search` | Search GitHub repositories with rate limiting |
| `map_website` | Intelligent website exploration and mapping |
| `content_operations` | Retrieve, analyze, and extract content from any URL |
| `document_analysis` | Extract text from PDFs, Word docs, and images with OCR |
| `scientific_research` | Academic papers (arXiv, Semantic Scholar) and datasets (Kaggle, HuggingFace) |
| `research_topic` | End-to-end research workflow for quick topic analysis |
| `research_agent` | AI agent with autonomous multi-tool research |

---

## Agent Skills

This Claude Code plugin includes 5 agent skills — slash commands that orchestrate MCP tools into multi-step research workflows with structured reports and citations.

| Agent Skill | Description |
|-------------|-------------|
| `/rival-search:research <topic>` | Comprehensive research with academic depth — papers, datasets, implementations |
| `/rival-search:competitive-intel <company or market>` | Company, product, market, or website intelligence with SWOT analysis |
| `/rival-search:due-diligence <company or person>` | Full due diligence with risk assessment — works for companies and individuals |
| `/rival-search:trend-intel <topic>` | News digest + trend trajectory with velocity indicators and maturity assessment |
| `/rival-search:fact-check <claim>` | Cross-source claim verification with confidence scoring and evidence chains |

---

## AI Research Agents

This Claude Code plugin includes 6 AI research agents. Each agent has a defined methodology, quality gates, and preloaded agent skills.

| Agent | Specialty |
|-------|-----------|
| **research-analyst** | Lead researcher — deep multi-source investigation |
| **competitive-intel** | SWOT analysis, competitor profiling, market positioning |
| **fact-checker** | Cross-source claim verification, confidence scoring |
| **trend-analyst** | Trend identification, velocity tracking, trajectory projection |
| **content-strategist** | Content gap analysis, audience research, brief creation |
| **due-diligence** | Company/person investigation, risk assessment, red/green flags |

---

## How This Claude Code Plugin Works

1. **`.mcp.json`** — Connects to [RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP) via MCP at `https://RivalSearchMCP.fastmcp.app/mcp`. All 10 MCP tools available automatically.

2. **`skills/`** — Five agent skill files with step-by-step research workflows, exact MCP tool parameters, and structured output formats.

3. **`agents/`** — Six AI research agents with full Claude Code frontmatter (tools, agent skills, hooks, memory). Invoked automatically or manually.

4. **`hooks/hooks.json`** — Portable event hooks for audit logging and output quality validation.

---

## Structure

```
rival-search-plugin/
├── .claude-plugin/
│   ├── plugin.json            # Claude Code plugin manifest
│   └── marketplace.json       # Marketplace config
├── .mcp.json                  # MCP server → RivalSearchMCP.fastmcp.app/mcp
├── agents/
│   ├── research-analyst.md
│   ├── competitive-intel.md
│   ├── fact-checker.md
│   ├── trend-analyst.md
│   ├── content-strategist.md
│   └── due-diligence.md
├── skills/
│   ├── research/
│   ├── competitive-intel/
│   ├── due-diligence/
│   ├── trend-intel/
│   └── fact-check/
├── hooks/
│   └── hooks.json
├── CLAUDE.md
├── LICENSE
└── README.md
```

---

## FAQ

<details>
<summary><strong>Does this Claude Code plugin require payment?</strong></summary>

No. MIT licensed, powered by [RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP). No API keys, no subscriptions, no hidden costs.
</details>

<details>
<summary><strong>Do I need API keys?</strong></summary>

No. Install and go. This Claude Code plugin auto-connects to the hosted RivalSearchMCP MCP server.
</details>

<details>
<summary><strong>What's the difference between agent skills and agents?</strong></summary>

**Agent skills** are slash commands you invoke explicitly (`/rival-search:research <topic>`). **Agents** are invoked automatically by Claude when your task matches their expertise.
</details>

<details>
<summary><strong>Can I use MCP tools directly without agent skills?</strong></summary>

Yes. Agent skills are guided workflows, but you can ask Claude to use any RivalSearchMCP MCP tool directly.
</details>

---

## Contributing

Contributions welcome — new agent skills, AI research agent improvements, or bug fixes.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Issues & Feedback

**[Open an Issue](https://github.com/damionrashford/rival-search-plugin/issues)**

## Links

- **[RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP)** — The MCP server powering this Claude Code plugin
- **[RivalSearchMCP Docs](https://damionrashford.github.io/RivalSearchMCP)** — Full documentation
- **[Claude Code](https://claude.ai/code)** — The CLI this plugin extends

## License

MIT — see [LICENSE](LICENSE) for details.
