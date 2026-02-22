# Claude Code for Product Managers

> **You already use Claude. This is the version that actually knows your product.**

Most PMs use Claude like a smarter search engine — paste context, get output, repeat. Claude Code is different. It reads your files, remembers your product, connects to your tools, and runs multi-step workflows. The gap between an idea and a working prototype, a research question and a sourced analysis, a spec brief and a finished PRD — that gap just got a lot smaller.

This guide is for PMs who are ready to close it.

---

## What PMs Are Actually Doing With This

| The problem | The old way | With Claude Code |
|-------------|------------|-----------------|
| Write a PRD grounded in user pain | 2 hrs of synthesis + drafting | 20 min pipeline: research → JTBD → draft → review |
| Competitive analysis | 2 days, 5 tabs, one contractor | 34,000 Reddit comments in one session¹ |
| Answer a data question | Open a Jira ticket, wait 3 days | Ask your database in plain English, get the answer |
| Understand a feature technically | Schedule a meeting with an engineer | Ask Claude Code in Plan Mode — it reads the code |
| Write a spec that sounds like you | Generic AI output + heavy editing | CLAUDE.md knows your voice, your template, your product |
| Build a PowerPoint deck | 3 hours in Slides | Generate from your research files |

¹ Monday.com PM, one session. [Full story →](08-real-stories.md)

---

## The One Thing That Changes Everything

**`CLAUDE.md`** — a file you create once, in your project folder. Claude Code reads it automatically at the start of every session.

It contains your product vision, your users, your OKRs, your writing voice. Write it once. After that, Claude Code never needs you to explain your product again.

```markdown
# ShopFlow — Product Context

## Product Vision
ShopFlow helps small e-commerce operators manage inventory
without hiring a dedicated ops person. Primary users: founders
running stores with 50-500 SKUs.

## Core Users
Alex (Founder/Operator): primary pain = unexpected stockouts.

## Current Quarter
Q2 2026: Reduce stockout incidents by 40%.
Key bet: automated reorder suggestions.

## My Writing Voice
Direct. No jargon. Bullet-heavy. Always include acceptance criteria.
```

That's Level 1. There's a [Level 3 version](03-claude-md-for-pms.md) that defines specialist agent roles, context loading sequences, and response rules. Most PMs see a step-change in output quality at Level 3.

---

## Where to Start

**This week — in order:**

**1 → [Getting Started](01-getting-started.md)**
Install in 5 minutes. Run your first session. Learn Plan Mode — the safe, read-only way to understand your codebase without changing anything.

**2 → [CLAUDE.md for PMs](03-claude-md-for-pms.md)**
Write your product brain. Copy-paste the Level 3 template. Everything else in this guide builds on this file.

**3 → [Connect your tools](02-mcp-toolkit.md)**
Jira, Linear, Notion, Figma, Amplitude. Pick one and connect it. Takes 15 minutes. Verified installation steps for each.

---

**Once you're up and running:**

**4 → [The 9 PM Use Cases](04-pm-use-cases.md)**
PRD writing, competitive research, data analysis, prototyping, technical exploration, roadmap strategy. Every use case has real prompts you can run today.

**5 → [Compound Workflows](05-compound-mcp-workflows.md)**
When your tools talk to each other. Sprint health checks. Competitive intelligence pipelines. Release impact analysis. Full copy-paste prompts for all five.

**6 → [Orchestration Patterns](06-orchestration-for-pms.md)**
Sequential pipelines, parallel research, specialist + synthesizer. How to structure sessions so they produce compound intelligence, not just answers.

---

**Reference:**

| File | What's in it |
|------|-------------|
| [Tools & Integrations](07-tools-integrations.md) | Figma free/paid truth. PowerPoint situation. Data tools. |
| [Real Stories](08-real-stories.md) | 7 verified practitioners: names, sources, numbers. |
| [Workshop Exercises](09-workshop-exercises.md) | 10 exercises for teams. Timing + facilitator guide. |
| [Cheat Sheet](10-cheat-sheet.md) | Print this. Every command, MCP, agent role on one page. |

---

## The Tools You'll Connect

```
PROJECT MANAGEMENT        ANALYTICS
──────────────────        ─────────
Jira MCP           80★   Amplitude   (official Anthropic)
Linear MCP        129★   Google Analytics         177★
Notion MCP        206★   Mixpanel                  19★
GitHub Issues            Power BI                 200★

DESIGN                    RESEARCH
──────────                ────────
Figma MCP                 Bright Data   (scrape anything public)
  free: remote server     PowerPoint    (tfriedel/claude-office-skills)
  paid: desktop server    NotebookLM    (jacob-bd/notebooklm-mcp-cli)
```

**Install the official Anthropic PM plugin** — 6 pre-built PM slash commands:
```bash
/plugin install product-management
# Gives you:
# /pm:prd-create  /pm:feature-spec  /pm:user-story
# /pm:metrics-framework  /pm:competitive  /pm:roadmap-review
```

---

## Real People. Real Results.

> *"Where it used to be about influencing future changes through complex collaboration, it now revolves a lot around influencing through **building and creating**."*
>
> **Ondrej Machart** — Head of Product (non-engineer). Published an iOS app solo. Built TinyStakeholders.com (5,000+ readers). 13 projects total.
> [Full story →](08-real-stories.md)

---

> *"I went from asking my data team for reports to exploring data myself in real time."*
>
> **Dylan Colon** — PM at UKG

---

> *"We just want to make it much easier for non-programmers."*
>
> **Boris Cherny** — Anthropic, on launching Cowork (January 2026)

---

| Signal | Number |
|--------|--------|
| Time saved on competitive intel | **85%** (Reza Rezvani, enterprise PM) |
| Reddit comments analyzed in one session | **34,000** (Monday.com PM) |
| Anthropic's official PM plugin | **7,500 ★** on GitHub |
| Most-starred PM Claude Code course | **1,437 ★** (Carl Vellotti) |

---

## The Honest Answers

**"Do I need to know how to code?"**
No. Plan Mode lets you explore and understand your codebase without touching it. The prompts in this guide are written in plain English. The skill you need is evaluating whether output is good — which is already your job.

**"Does the Figma MCP cost extra?"**
The remote server is free on all Figma plans, including the free tier. The desktop server requires a paid Dev seat (~$12-35/mo). There's also a free community option that works with any plan. [Details →](07-tools-integrations.md#figma)

**"Can I generate PowerPoints?"**
Not natively in Claude Code CLI — that feature only shipped in Claude Desktop/Web. There's a community solution that works well. [Full workflow →](07-tools-integrations.md#powerpoint)

**"My company's AI policy is strict. Can I still use this?"**
Start with CLAUDE.md and no MCP connections. That's pure API text processing — same data path as Claude.ai, which your company likely already approved. Add integrations one at a time as you verify each is within policy. [Full breakdown →](01-getting-started.md)

**"I only have 30 minutes. Where do I start?"**
Write your CLAUDE.md. Just three sections: product vision, your core users, this quarter's focus. That file pays for the 30 minutes every single day after.

---

## What's in This Repo

```
CC-PM/
├── README.md                     ← You're here
├── 01-getting-started.md         ← Install, Plan Mode, first session
├── 02-mcp-toolkit.md             ← Every PM MCP, verified
├── 03-claude-md-for-pms.md       ← Level 1 → Level 3 templates
├── 04-pm-use-cases.md            ← 9 use cases, real prompts
├── 05-compound-mcp-workflows.md  ← 5 full multi-tool workflows
├── 06-orchestration-for-pms.md   ← Pipelines, agents, session patterns
├── 07-tools-integrations.md      ← Figma, PowerPoint, data tools
├── 08-real-stories.md            ← 7 verified PM stories + community
├── 09-workshop-exercises.md      ← 10 team exercises, facilitator guide
├── 10-cheat-sheet.md             ← One-page reference, print-ready
└── presentation.html             ← Slide deck: open in Chrome
```

**Bonus:** [`presentation.html`](presentation.html) is the full session slide deck. Open in Chrome → navigate with arrow keys → press `N` for speaker notes.

---

## Community & Further Reading

| Resource | What it is | Stars |
|----------|-----------|-------|
| [prodmgmt.world/claude-code](https://prodmgmt.world/claude-code) | 180+ PM skills, used by 500+ PMs | — |
| [ccforpms.com](https://ccforpms.com) | Interactive PM course by Carl Vellotti | — |
| [refoundai/lenny-skills](https://github.com/refoundai/lenny-skills) | 86 skills from Lenny's Podcast | 244★ |
| [deanpeters/Product-Manager-Skills](https://github.com/deanpeters/Product-Manager-Skills) | 42 PM skills | 132★ |
| [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins) | Official Anthropic PM plugin | 7,500★ |
| [carlvellotti/claude-code-pm-course](https://github.com/carlvellotti/claude-code-pm-course) | Most-starred PM Claude Code resource | 1,437★ |
| [Anthropic free course](https://anthropic.skilljar.com/claude-code-in-action) | Claude Code in Action | — |

---

*Built by [Rom Iluz](https://github.com/romiluz13), creator of [cc10x](https://github.com/romiluz13/cc10x). All data verified February 2026.*
