# Skills, Plugins & PM Agents — The Part Everyone Misses

> CLAUDE.md is not the only way. Skills, plugins, and agents are how you
> turn Claude Code into a specialist that actually knows product management.

---

## What's the Difference? (The Mental Model)

| What | What it does | When it activates | Install |
|------|-------------|-------------------|---------|
| **CLAUDE.md** | Always-on project context | Every session, automatically | Create a file |
| **Skill** | Teaches Claude a specific workflow or framework | When relevant (ambient) or when invoked (command) | Copy a .md file |
| **Plugin** | Bundle of skills + commands + tool connectors | On install, persists | `/plugin install` |
| **Agent** | Specialist with a defined role, tools, and persona | You invoke it | `.claude/agents/` file |
| **MCP** | Connects Claude to external tools (Jira, Figma, etc.) | When connected | Config JSON |

**The key insight:** CLAUDE.md gives Claude context about YOUR product. Skills give Claude knowledge of PM craft — frameworks, workflows, best practices. You need both.

Skills load efficiently: Claude reads only a ~100-token description of each skill to decide if it's relevant, then loads full instructions only when needed. Your context window stays lean.

---

## The Anthropic Official PM Plugin (Start Here)

**GitHub:** github.com/anthropics/knowledge-work-plugins
**Stars:** 7,700+
**What it is:** 11 official role-based plugins, PM plugin included

```bash
# Install in Claude Code CLI:
claude plugin marketplace add anthropics/knowledge-work-plugins
claude plugin install product-management@knowledge-work-plugins

# In Claude Cowork: visual Plugins panel → browse → install
```

### PM Plugin Slash Commands

| Command | What it does |
|---------|-------------|
| `/product-management:write-spec` | Write a feature specification |
| `/product-management:roadmap` | Plan and structure a roadmap |
| `/product-management:user-research` | Synthesize user research findings |
| `/product-management:stakeholder-update` | Draft a stakeholder communication |
| `/product-management:competitive` | Run a competitive analysis |
| `/product-management:metrics` | Define success metrics for a feature |

### PM Plugin Connectors (pre-wired)

Slack · Linear · Asana · Monday · ClickUp · Jira · Notion · Figma · **Amplitude** · **Pendo** · **Intercom** · **Fireflies**

Note: Amplitude, Pendo, Intercom, and Fireflies — these are product analytics and user research tools. The official plugin is designed specifically for PMs.

### How Skills Work Inside a Plugin

The plugin structure is: skills + commands + connectors. Skills fire automatically when Claude detects you need them. Commands are slash commands you invoke explicitly. Both live in markdown files — no code, no infrastructure.

```
product-management/
├── .claude-plugin/plugin.json   # Manifest
├── .mcp.json                    # Tool connections (Jira, Figma, etc.)
├── commands/                    # /pm: slash commands
│   ├── write-spec.md
│   ├── roadmap.md
│   └── ...
└── skills/                      # Domain knowledge, fires automatically
    ├── spec-writing.md
    ├── user-research.md
    └── ...
```

---

## Claude Cowork — The Non-Terminal Option

> If you don't want to use the command line, Cowork is the right tool.
> Same model as Claude Code. Same skill format. Visual interface.

**Available:** Windows + macOS (Intel + Apple Silicon) — launched January 2026, full parity Feb 21, 2026.
**Requires:** Claude Pro, Max, Team, or Enterprise plan.

**What Cowork does that Chat doesn't:**
- Spawns parallel sub-agents for complex tasks
- Creates real files (.docx, .pptx, .xlsx, .pdf) delivered to your folder
- Runs multi-step workflows with visible progress tracking
- Ships with all 11 official plugins pre-installed (including PM)
- Visual Plugins panel for browsing, installing, and creating plugins

**The key difference for PMs:**
- Chat = ask a question, get an answer
- Cowork = describe work, get a deliverable

**Cross-compatibility:** Skills installed in Cowork work the same way in Claude Code CLI, and vice versa. Same format, fully compatible.

### Give Cowork Cross-Session Memory (2-minute setup)

1. Enable Desktop Commander extension (Settings → Connectors → Browse → Desktop Commander)
2. Copy this to Settings → Cowork → Global Instructions:

```
## Memory Management
When you discover something valuable for future sessions — architectural decisions,
user research insights, product decisions, gotchas — immediately append it to
~/product-memory.md

Don't wait to be asked. Keep entries short: date, what, why.
Read this file at the start of every session.
```

This costs almost zero tokens and survives session resets.

---

## The PM Skills Libraries

### 1. Lenny's Podcast PM Skills
**Repo:** github.com/refoundai/lenny-skills
**Stars:** ~244
**Content:** 86 skills derived from Lenny Rachitsky's interviews with top PMs

```bash
/plugin marketplace add refoundai/lenny-skills
```

Skills cover: discovery, prioritization, writing, stakeholder management, metrics, launch. Based on interviews with PMs at Figma, Notion, Replit, Duolingo, and more.

---

### 2. Product Manager Skills (42 skills)
**Repo:** github.com/deanpeters/Product-Manager-Skills
**Stars:** 132
**Taxonomy:** Component / Workflow / Interactive

```bash
/plugin marketplace add deanpeters/Product-Manager-Skills
```

Organized as:
- **Component skills:** Frameworks, templates, checklists
- **Workflow skills:** End-to-end processes (discovery sprint, launch plan)
- **Interactive skills:** Guided exercises (user interview simulation, stakeholder alignment)

---

### 3. Awesome PM Skills (menkesu)
**Repo:** github.com/menkesu/awesome-pm-skills
**Content:** Curated PM frameworks as installable skills

Notable skills:

**Prioritization (RICE + Kano + Value/Effort):**
```
When activated, applies:
- RICE: (Reach × Impact × Confidence) / Effort
- Value vs Effort matrix (quick wins → do first; money pits → never)
- Kano: must-haves vs delighters vs performance features
- Shreyas Doshi's principle: "Saying no is the most underrated PM skill"
```

**Continuous Discovery (Teresa Torres):**
```
Weekly touchpoints → opportunity solution tree → assumption testing
Activates when you discuss discovery cadence, user interviews,
opportunity mapping, or assumption validation
```

---

### 4. Curated Product Skills (16 real frameworks)
**Repo:** github.com/assimovt/productskills
**Stars:** 11

```bash
/plugin marketplace add assimovt/productskills
```

Built on actual PM frameworks:
- **Mom Test** — how to run honest user interviews
- **Shape Up** — appetite-based scoping and betting
- **Obviously Awesome** — positioning and market category design
- **JTBD** — jobs-to-be-done discovery and framing
- **Continuous Discovery** — opportunity solution trees
- 11 more

---

### 5. BMAD PM Agent (John)
**Repo:** github.com/bmad-code-org/BMAD-METHOD
**Stars:** community with 1,500+ active issues

The BMAD Method includes a dedicated Product Manager agent (his name is John, 8+ years experience, "asks WHY? relentlessly like a detective").

```bash
npx bmad-method install
# Or: npx bmad-method install --modules bmm --tools claude-code --yes
```

**PM Agent Commands:**

| Trigger | Command | What it does |
|---------|---------|-------------|
| `CP` | Create PRD | Full facilitated PRD creation via structured workflow |
| `VP` | Validate PRD | Checks PRD is comprehensive, lean, cohesive |
| `EP` | Edit PRD | Updates an existing PRD |
| `CE` | Create Epics & Stories | Generates specs that drive development |
| `IR` | Implementation Readiness | Checks PRD + UX + Architecture are aligned |
| `CC` | Course Correction | Mid-implementation pivot when major changes needed |

**John's principles:**
- PRDs emerge from user interviews, not template filling
- Ship the smallest thing that validates the assumption
- Technical feasibility is a constraint, not the driver — user value first
- "Asks WHY? relentlessly — direct and data-sharp, cuts through fluff"

**BMAD PRD Workflow:** Step-file architecture — each step loads only when needed. Follows: Discovery → Vision → Domain Analysis → Requirements Clarification → PRD Output. Never skips steps, never loads future steps prematurely.

---

## Purpose-Built PM Skill Systems

### slgoodrich/agents — AI PM Workflows
**Repo:** github.com/slgoodrich/agents
**Stars:** 27

A multi-agent PM system where a `product-manager` orchestrator routes requests to PM specialists:

- **market-analyst** — market research and competitive intelligence
- **user-researcher** — user interview synthesis, persona development
- **roadmap-strategist** — roadmap planning and prioritization
- **spec-writer** — feature specification and acceptance criteria
- **metrics-analyst** — KPI definition and measurement planning

When your question clearly fits one domain, Claude routes directly to the specialist. For complex questions, the orchestrator coordinates multiple specialists.

---

### valllabh/claude-agents
**Repo:** github.com/valllabh/claude-agents

8 enhanced agents including a `product-manager` agent with:
- `create-doc` workflow
- `prd-template` (structured PRD generation)
- Business analyst agent as companion

---

### iflow-ai/NioPD — Virtual Product Director
**Repo:** github.com/iflow-ai/NioPD

"Your Virtual Product Expert" — NioPD (Nio Product Director) provides on-demand product direction, strategic thinking, and PM coaching within Claude Code.

---

## The PRD Builder Skill

**Source:** github.com/cch96/claude-plugins
**Install via:** `npx skillfish add cch96/claude-plugins prd-builder`

A structured 4-stage PRD workflow:
1. **Background Understanding** — product vision, user pain points, market context
2. **Competitor Analysis** — differentiation mapping, competitive gaps
3. **Requirement Clarification** — P0/P1/P2 priorities, MVP scoping, risk assessment
4. **PRD Output** — complete PRD with scenarios and technical roadmap

Uses guided option-based dialogue (not open-ended prompting) — helps you make every decision before writing a word of the spec.

---

## Skills Marketplaces for PMs

Beyond the curated collections above, these marketplaces have PM-relevant skills:

### skills.sh (Vercel's Open Ecosystem)
**URL:** skills.sh

PM-relevant skills include:
- Product strategy frameworks
- Pricing strategy
- Launch playbooks
- Discovery interview guides
- PRD generator
- Analytics tracking setup
- Go-to-market planning

Works with 18+ AI agents. Install via: `npx skills add [skill-name]`

---

### skillhub.club
**URL:** skillhub.club
7,000+ AI-evaluated skills with quality scores. One-click install via desktop app. Search for: product, PRD, roadmap, user research, prioritization.

---

### skillsmp.com
**URL:** skillsmp.com
200,000+ skills indexed from GitHub. Searchable by category. The largest indexed collection.

---

### claudemarketplaces.com
**URL:** claudemarketplaces.com
Browse and discover plugin marketplaces you can add to Cowork or Claude Code CLI.

---

### sickn33/antigravity-awesome-skills
**Repo:** github.com/sickn33/antigravity-awesome-skills
**Stars:** 13,850
**Content:** 868+ battle-tested skills across 18+ AI agents

Includes role-based bundles. PM-relevant bundles:
- **Startup Founder** — strategy, GTM, fundraising
- **Marketing & Growth** — acquisition, retention, positioning

Works with Claude Desktop, Claude Code, Cursor, Gemini CLI, Codex, OpenCode.

```bash
git clone https://github.com/sickn33/antigravity-awesome-skills.git
cp -r antigravity-awesome-skills/skills/* ~/.claude/skills/
```

---

## Write Your Own PM Skill in 15 Minutes

A skill is a markdown file with a frontmatter header. That's it.

### The format:

```markdown
---
name: user-research-synthesis
description: Synthesizes user research findings into JTBD statements and pain clusters.
             Use when analyzing interview transcripts, support tickets, or survey data.
---

# User Research Synthesis

## When This Skill Activates

Claude uses this skill when you share:
- Interview transcripts or notes
- Support ticket exports
- Survey responses
- App store reviews
- User feedback in any form

## My Process

1. **Read all input material first** — don't start synthesizing until I've read everything
2. **Identify pain clusters** — group similar complaints, not just keywords
3. **Distinguish symptom from root cause** — users describe symptoms, I find causes
4. **Extract JTBD statements** — format: "When [situation], [user] wants [outcome] so they can [deeper goal]"
5. **Rank by frequency × severity** — frequency alone misses critical low-volume pain

## Output Format

### Pain Cluster Report
For each cluster:
- **Theme:** [1-line description]
- **Frequency:** [how often it appears]
- **Severity signals:** [language that indicates severity — workarounds, escalations, churns]
- **Best quote:** "[exact words, verbatim, with source ID]"

### JTBD Statements
For top 3 clusters:
> When [situation], [user type] wants to [motivation], so they can [outcome].

### What I Won't Do
- Summarize what you already know (you told me the input)
- Report raw counts without interpretation
- Use jargon like "user journey" without specifics
- Bury the most important finding at the bottom
```

**Install it:**
```bash
# Global (available in all sessions):
cp user-research-synthesis.md ~/.claude/skills/

# Project-level (this project only):
cp user-research-synthesis.md .claude/skills/
```

**Test it:**
```
"Here are 50 support tickets from last quarter. [paste or reference file]
Run the user-research-synthesis skill."
```

---

## The Full PM Skill Stack — What to Install

### Week 1 (Essential)
```bash
# Official PM plugin (6 commands, all connectors)
claude plugin marketplace add anthropics/knowledge-work-plugins
claude plugin install product-management@knowledge-work-plugins
```

### Week 2 (Frameworks)
```bash
# Lenny's 86 PM skills
/plugin marketplace add refoundai/lenny-skills

# Prioritization frameworks (RICE, Kano, Value/Effort)
/plugin marketplace add assimovt/productskills
```

### Week 3 (Specialist workflows)
```bash
# BMAD PM Agent (full PRD + epics workflow)
npx bmad-method install

# PM skills from menkesu collection
/plugin marketplace add menkesu/awesome-pm-skills
```

### Ongoing (Browse when needed)
- skills.sh — `npx skills add [skill-name]`
- skillhub.club — one-click install
- claudemarketplaces.com — discover new marketplaces

---

## Skills vs CLAUDE.md — When to Use What

| Use case | Use |
|----------|-----|
| Your product vision, users, OKRs | CLAUDE.md |
| Your writing voice and style | CLAUDE.md |
| Active decisions and team conventions | CLAUDE.md |
| RICE prioritization framework | Skill |
| PRD structure and workflow | Skill |
| User interview methodology | Skill |
| Competitive analysis process | Skill |
| Stakeholder communication templates | Skill |
| Jira / Amplitude / Figma connection | MCP |
| Full PM agent with memory and routing | Plugin |

**The combination:** CLAUDE.md tells Claude about your product. Skills tell Claude how to do PM work well. MCPs give Claude access to your data. Plugins bundle all three.

---

## Quick Reference: Install Commands

```bash
# Official Anthropic PM Plugin
claude plugin marketplace add anthropics/knowledge-work-plugins
claude plugin install product-management@knowledge-work-plugins

# Lenny's PM Skills (86 skills)
claude plugin marketplace add refoundai/lenny-skills

# Product Manager Skills (42 skills)
claude plugin marketplace add deanpeters/Product-Manager-Skills

# Curated frameworks (Mom Test, Shape Up, JTBD)
claude plugin marketplace add assimovt/productskills

# BMAD PM Agent (John — full PRD workflow)
npx bmad-method install

# PRD Builder (4-stage guided workflow)
npx skillfish add cch96/claude-plugins prd-builder

# Direct skill copy (global)
cp your-skill.md ~/.claude/skills/

# Direct skill copy (project-level)
cp your-skill.md .claude/skills/

# Browse what's installed
/plugin list
```

---

*Sources: github.com/anthropics/knowledge-work-plugins, productcompass.pm, skills.sh, skillhub.club, bmad-code-org/BMAD-METHOD*
