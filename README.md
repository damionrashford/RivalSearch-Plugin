# rival-search

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)
[![Claude Code Plugin](https://img.shields.io/badge/Claude_Code-Plugin-blueviolet?style=for-the-badge)](https://claude.ai/code)
[![MCP Powered](https://img.shields.io/badge/MCP-Powered-blue?style=for-the-badge)](https://github.com/damionrashford/RivalSearchMCP)
[![RivalSearchMCP](https://img.shields.io/badge/RivalSearchMCP-10_Tools-green?style=for-the-badge)](https://github.com/damionrashford/RivalSearchMCP)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin&style=for-the-badge)](https://www.linkedin.com/in/damion-rashford)

[![GitHub Stars](https://img.shields.io/github/stars/damionrashford/rival-search?style=social)](https://github.com/damionrashford/rival-search)
[![GitHub Forks](https://img.shields.io/github/forks/damionrashford/rival-search?style=social)](https://github.com/damionrashford/rival-search)
[![GitHub Issues](https://img.shields.io/github/issues/damionrashford/rival-search?style=social)](https://github.com/damionrashford/rival-search/issues)
[![Last Commit](https://img.shields.io/github/last-commit/damionrashford/rival-search?style=social)](https://github.com/damionrashford/rival-search)

**A Claude Code plugin that turns Claude into a full AI research team.**

> 🆓 **100% Free & Open Source** — No API keys, no subscriptions, no configuration. Install the plugin and start researching.

Powered by **[RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP)** — 10 free research tools across web, social, news, GitHub, academic, and document sources.

---

## ✅ What It Does

rival-search gives Claude Code a complete research intelligence platform:

- **10 research tools** via [RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP) — web search, social media, news, GitHub, academic papers, document analysis, and more
- **5 workflow skills** — slash commands that run multi-step research and produce structured reports
- **6 specialist agents** — AI research analysts that Claude invokes automatically based on your task
- **Portable hooks** — audit logging and quality gates that travel with the plugin

## 💡 Example Queries

Once installed, try these in Claude Code:

> "Research the current state of AI code generation tools"

> "/rival-search:competitive-intel Cursor"

> "/rival-search:fact-check 'OpenAI revenue exceeded $2 billion in 2024'"

> "/rival-search:due-diligence Anthropic"

> "/rival-search:trend-intel AI agents for software development"

---

## 📦 How to Get Started

### From Claude Code Marketplace (Recommended)

```bash
/plugin marketplace add damionrashford/rival-search
/plugin install rival-search@damionrashford-rival-search
```

### From Local Directory

```bash
git clone https://github.com/damionrashford/rival-search.git
claude --plugin-dir ./rival-search
```

That's it. The plugin auto-connects to the hosted [RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP) server. All 10 tools are available immediately — no setup, no API keys.

---

## 🛠 10 Research Tools (via RivalSearchMCP)

All tools are powered by **[RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP)** — zero authentication required.

### Search & Discovery

| Tool | What It Does |
|------|-------------|
| `web_search` | Multi-engine search across DuckDuckGo, Yahoo, and Wikipedia |
| `social_search` | Search Reddit, Hacker News, Dev.to, Product Hunt, Medium |
| `news_aggregation` | Aggregate news from Google News, DuckDuckGo News, Yahoo News |
| `github_search` | Search GitHub repositories with rate limiting |
| `map_website` | Intelligent website exploration and mapping |

### Content & Analysis

| Tool | What It Does |
|------|-------------|
| `content_operations` | Retrieve, analyze, and extract content from any URL |
| `document_analysis` | Extract text from PDFs, Word docs, and images with OCR |
| `scientific_research` | Academic papers (arXiv, Semantic Scholar) and datasets (Kaggle, HuggingFace) |

### AI Research

| Tool | What It Does |
|------|-------------|
| `research_topic` | End-to-end research workflow for quick topic analysis |
| `research_agent` | AI agent with autonomous multi-tool research |

---

## ⚡ 5 Slash-Command Skills

Skills are guided, multi-step research workflows. Each one orchestrates multiple [RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP) tools and produces a structured report with citations.

| Command | Description |
|---------|-------------|
| `/rival-search:research <topic>` | Comprehensive research with academic depth — papers, datasets, implementations |
| `/rival-search:competitive-intel <company or market>` | Company, product, market, or website intelligence with SWOT analysis |
| `/rival-search:due-diligence <company or person>` | Full due diligence with risk assessment — works for companies AND individuals |
| `/rival-search:trend-intel <topic>` | News digest + trend trajectory with velocity indicators and maturity assessment |
| `/rival-search:fact-check <claim>` | Cross-source claim verification with confidence scoring and evidence chains |

### Examples

```
/rival-search:research retrieval augmented generation
/rival-search:competitive-intel Vercel
/rival-search:due-diligence Y Combinator
/rival-search:due-diligence Jensen Huang
/rival-search:trend-intel AI agents for software development
/rival-search:fact-check "GPT-4 was trained on 1.8 trillion parameters"
```

---

## 🤖 6 Specialist Agents

Agents are automatically invoked by Claude when your task matches their expertise. Each agent has a defined methodology, quality gates, and preloaded skills.

| Agent | Specialty |
|-------|-----------|
| **research-analyst** | Lead researcher — deep multi-source investigation with 5-phase methodology |
| **competitive-intel** | Competitive intelligence — SWOT analysis, competitor profiling, market positioning |
| **fact-checker** | Verification specialist — cross-source claim verification, confidence scoring |
| **trend-analyst** | Trend spotter — trend identification, velocity tracking, trajectory projection |
| **content-strategist** | Content researcher — gap analysis, audience research, content brief creation |
| **due-diligence** | DD analyst — company/person investigation, risk assessment, red/green flags |

---

## 🔗 How It Works

The plugin bundles four components that work together:

1. **`.mcp.json`** — Connects to the hosted [RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP) server at `https://RivalSearchMCP.fastmcp.app/mcp`. All 10 tools are available automatically.

2. **`skills/`** — Five SKILL.md workflow files. Each defines step-by-step research instructions with exact tool parameters and output format.

3. **`agents/`** — Six specialist agents with full Claude Code frontmatter (tools, skills, hooks, memory). Claude invokes them when your task matches their expertise.

4. **`hooks/hooks.json`** — Portable event hooks for research audit logging and output quality validation.

---

## 📁 Plugin Structure

```
rival-search/
├── .claude-plugin/
│   ├── plugin.json            # Plugin manifest
│   └── marketplace.json       # Marketplace config
├── .mcp.json                  # MCP server → RivalSearchMCP.fastmcp.app/mcp
├── agents/
│   ├── research-analyst.md    # Lead researcher
│   ├── competitive-intel.md   # CI specialist
│   ├── fact-checker.md        # Verification specialist
│   ├── trend-analyst.md       # Trend spotter
│   ├── content-strategist.md  # Content researcher
│   └── due-diligence.md       # DD analyst
├── skills/
│   ├── research/              # Multi-source + academic research
│   ├── competitive-intel/     # Company, market & site intel
│   ├── due-diligence/         # Company & person investigation
│   ├── trend-intel/           # News + trend trajectory
│   └── fact-check/            # Claim verification
├── hooks/
│   └── hooks.json             # Audit & quality hooks
├── CLAUDE.md                  # Project instructions (for Claude)
├── LICENSE                    # MIT license
└── README.md                  # This file (for humans)
```

---

## 💬 FAQ

<details>
<summary><strong>Is rival-search really free?</strong></summary>

Yes! The plugin is MIT licensed and powered by [RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP), which is also 100% free. No API keys, no subscriptions, no hidden costs.

</details>

<details>
<summary><strong>Do I need API keys or configuration?</strong></summary>

No. Install the plugin and go. It auto-connects to the hosted RivalSearchMCP server. All 10 tools work immediately without any authentication.

</details>

<details>
<summary><strong>What Claude Code version do I need?</strong></summary>

Claude Code CLI v1.0.33 or later. The plugin uses standard Claude Code plugin features (agents, skills, hooks, MCP).

</details>

<details>
<summary><strong>Can I use individual tools without the skills?</strong></summary>

Absolutely. The skills are guided workflows, but you can ask Claude to use any RivalSearchMCP tool directly. For example: "Use web_search to find information about X" or "Search GitHub for Y."

</details>

<details>
<summary><strong>What's the difference between skills and agents?</strong></summary>

**Skills** are slash commands — you invoke them explicitly with `/rival-search:research <topic>`. They run a defined multi-step workflow.

**Agents** are invoked automatically by Claude when your task matches their expertise. You can also invoke them manually via `/agents`.

</details>

---

## 🤝 Contributing

Contributions are welcome! Whether it's adding new skills, improving agents, or fixing bugs.

1. **Fork the Project**
2. **Create your Feature Branch** (`git checkout -b feature/AmazingFeature`)
3. **Commit your Changes** (`git commit -m 'Add AmazingFeature'`)
4. **Push to the Branch** (`git push origin feature/AmazingFeature`)
5. **Open a Pull Request**

---

## 💡 Issues, Feedback & Support

Found a bug, have a feature request, or want to share how you're using rival-search?

- **Report a bug** — Help us improve
- **Request a feature** — Suggest new skills or agents
- **Share your use case** — Tell us what you're researching

👉 **[Open an Issue](https://github.com/damionrashford/rival-search/issues)**

---

## 🔗 Links

- **[RivalSearchMCP](https://github.com/damionrashford/RivalSearchMCP)** — The MCP server powering this plugin (10 free research tools)
- **[Plugin Repository](https://github.com/damionrashford/rival-search)** — This plugin's source code
- **[RivalSearchMCP Docs](https://damionrashford.github.io/RivalSearchMCP)** — Full documentation
- **[Claude Code](https://claude.ai/code)** — The CLI this plugin extends

---

## ⭐ Like this project? Give it a star!

If you find rival-search useful, please consider giving it a star. It helps others discover the project and motivates continued development!

---

## License

MIT — see [LICENSE](LICENSE) for details.
