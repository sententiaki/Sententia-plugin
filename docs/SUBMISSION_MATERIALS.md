# BetterCallClaude — Official Plugin Directory Submission Materials

Prepared for submission to Anthropic's official plugin directory.

---

## Plugin Name

`bettercallclaude`

## One-Line Description

Swiss Legal Intelligence — BGE/ATF/DTF precedent research, case strategy, legal drafting, and citation verification across all 26 Swiss cantons with Anwaltsgeheimnis privacy protection.

## Source Repository

https://github.com/fedec65/BetterCallClaude

## Category

Legal / Domain-Specific

## Website

https://bettercallclaude.ch

---

## What It Does

BetterCallClaude transforms Claude into a Swiss legal research and analysis assistant. It covers the full spectrum of Swiss legal work:

- **Precedent research** — Search BGE/ATF/DTF databases, cantonal court decisions, and federal legislation via 5 custom MCP servers connected to live Swiss legal databases (entscheidsuche.ch, Fedlex SPARQL, OnlineKommentar).
- **Case strategy** — Risk assessment, cost-benefit analysis, procedural pathway evaluation, and settlement modeling.
- **Adversarial analysis** — Three-agent workflow (advocate builds the case, adversary challenges it, judicial analyst synthesizes with Erwagung methodology and probability scores).
- **Legal drafting** — Contracts, court submissions, legal opinions with jurisdiction-aware terminology and citation formatting.
- **Citation verification** — Validate and convert citations between DE/FR/IT/EN formats across BGE/ATF/DTF reference systems.
- **Multi-agent workflows** — Pre-built pipelines for due diligence, litigation preparation, contract lifecycle, and real estate closings.
- **Privacy protection** — Built-in Anwaltsgeheimnis (attorney-client privilege, Art. 321 StGB) detection hook that intercepts privileged content before it leaves the local environment.

## Components

| Type | Count | Examples |
|------|-------|---------|
| Agents | 18 | Researcher, Strategist, Drafter, Advocate, Adversary, Judicial Analyst, Citation Specialist, Compliance Officer, Risk Analyst, etc. |
| Commands | 17 | `/legal`, `/research`, `/strategy`, `/draft`, `/cite`, `/adversarial`, `/briefing`, `/workflow`, `/translate`, etc. |
| Skills | 10 | Swiss legal research, strategy, drafting, citation formats, jurisdictions, privacy routing, adversarial analysis, etc. |
| MCP Servers | 5 | bge-search, entscheidsuche, fedlex-sparql, legal-citations, onlinekommentar |

## Key Differentiators

### 1. Only Swiss Legal Intelligence Plugin

No other Claude plugin covers Swiss law. BetterCallClaude provides deep coverage of federal and cantonal law across all 26 Swiss cantons, including court hierarchies, citation formats, and cantonal procedural specifics.

### 2. Multi-Lingual (DE/FR/IT/EN)

Matches Switzerland's official languages. Automatic language detection switches between BGE (German), ATF (French), and DTF (Italian) citation formats and legal terminology. English is supported as a working language with Swiss legal term mapping.

### 3. 5 Custom MCP Servers with Live Data

Connected to real Swiss legal databases — not static datasets. Servers query entscheidsuche.ch (cantonal and federal court decisions), the Federal Supreme Court BGE database, Fedlex SPARQL (federal legislation), legal citation databases, and OnlineKommentar (legal commentaries).

### 4. Professional Ethics Built-In

Attorney-client privilege (Anwaltsgeheimnis) protection is enforced automatically via a PreToolUse hook. The hook detects privileged content patterns in DE/FR/IT before any external tool call proceeds, prompting user confirmation. Three privacy modes: strict, balanced, cloud.

### 5. Adversarial Analysis Methodology

Three-agent adversarial workflow modeled on actual Swiss court deliberation: advocate builds the strongest case, adversary systematically challenges it, judicial analyst synthesizes using Swiss Erwagung (consideration) structure with calibrated probability scores.

### 6. Briefing Sessions with Cross-Session Persistence

Complex legal matters get a collaborative intake phase before agent execution. A specialist panel (2-5 agents) asks targeted questions, builds a precise execution plan, and supports pause/resume across sessions.

### 7. Open Source (AGPL-3.0)

Fully transparent codebase. Community-driven development. No vendor lock-in.

---

## Differentiation from Anthropic's Own Legal Plugin

| Aspect | Anthropic `legal` | BetterCallClaude |
|--------|-------------------|------------------|
| Scope | Generic (contracts, NDAs, compliance for in-house teams) | Swiss-specific (all 26 cantons, federal and cantonal law) |
| Languages | English | DE, FR, IT, EN |
| Data Sources | None (relies on Claude's training data) | 5 live MCP servers connected to Swiss legal databases |
| Precedent Research | No | BGE/ATF/DTF search with citation chain tracking |
| Privacy | No | Anwaltsgeheimnis (Art. 321 StGB) enforcement hook |
| Adversarial Analysis | No | Three-agent Erwagung methodology |
| Target Users | General in-house legal teams | Swiss lawyers and legal professionals |

The two plugins are complementary, not competing. BetterCallClaude targets a specific jurisdiction that the generic legal plugin does not cover.

---

## Technical Details

- **License**: AGPL-3.0
- **Runtime**: Node.js >= 18 (for MCP servers)
- **MCP servers**: Pre-compiled, included in plugin (no build step for users)
- **Plugin manifest**: `.claude-plugin/plugin.json` with full metadata
- **Hooks**: PreToolUse privacy detection via `hooks/hooks.json`
- **No hardcoded secrets**: All API keys via environment variables

---

## Form Field Suggestions

When filling out the submission form, use these prepared answers:

**Plugin name**: `bettercallclaude`

**Description (short)**: Swiss Legal Intelligence — BGE/ATF/DTF precedent research, case strategy, legal drafting, and citation verification across all 26 Swiss cantons.

**Description (long)**: BetterCallClaude transforms Claude into a Swiss legal research and analysis assistant. It includes 18 specialized agents, 17 commands, 10 skills, and 5 MCP servers connected to live Swiss legal databases. Coverage spans federal and cantonal law across all 26 Swiss cantons with multi-lingual support (DE/FR/IT/EN), adversarial analysis using Swiss Erwagung methodology, and built-in Anwaltsgeheimnis (attorney-client privilege) protection.

**Repository URL**: https://github.com/fedec65/BetterCallClaude

**Author**: Federico Cesconi

**Website**: https://bettercallclaude.ch

**Category**: Legal / Domain-Specific

**Keywords**: swiss-law, legal-research, bge-atf-dtf, litigation, legal-drafting, citation-verification, multilingual, compliance, data-protection, mcp-servers
