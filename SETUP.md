# Setup Guide — PM AI Suite

You are setting up Yoav's PM AI Suite on this machine.
Walk me through it step by step — describe what each one does 
and let me pick which ones I want.

---

## Step 1: Clone the Repo

Check if the repo is already cloned. If not, clone it:

git clone https://github.com/yoavyeger-maker/pm-ai-suite ~/Projects/pm-ai-suite

---

## Step 2: Add Plugin Marketplaces

These are registries that host Claude Code plugins. Add them both:

claude plugin add github:anthropics/claude-plugins-official
claude plugin add git:https://github.com/EveryInc/compound-writing-plugin.git

---

## Step 3: Install Plugins (Let Me Choose)

Present each plugin one at a time. Explain what it does and ask if I want it.

| Plugin | Command | What it does |
|--------|---------|--------------|
| knowledge-work (product-management) | `claude plugin enable product-management@claude-plugins-official` | 14 PM commands covering standups, sprint planning, retros, stakeholder updates, and opportunity scoring — the official Anthropic PM plugin |
| compound-writing | `claude plugin enable compound-writing@every-marketplace` | Enforces writing quality across PRDs, retros, and stakeholder updates — catches vague language, passive voice, and filler |
| frontend-design | `claude plugin enable frontend-design@claude-plugins-official` | Production-grade UI implementation skill — useful when briefing Figma-to-code handoffs |
| ralph-loop | `claude plugin enable ralph-loop@claude-plugins-official` | Runs Claude in a loop until a task is fully complete — useful for long ticket batches or multi-step PRD generation |
| plugin-dev | `claude plugin enable plugin-dev@claude-plugins-official` | Tools for building your own Claude Code plugins — use this when you want to extend the PM AI Suite with custom commands |

---

## Step 4: Install Skills (Let Me Choose)

Skills are prompt templates you invoke with slash commands.
Present each one and ask if I want it.

To install a skill, copy its folder into ~/.claude/skills/:

| Skill | Command | What it does |
|-------|---------|--------------|
| ticket-factory | `cp -r ~/Projects/pm-ai-suite/skills/ticket-factory ~/.claude/skills/` | Converts a raw Slack request into a structured Jira ticket with user story, ACs, KPIs, Figma link, and scope |
| prd-generator | `cp -r ~/Projects/pm-ai-suite/skills/prd-generator ~/.claude/skills/` | Generates a first-draft PRD scaffold in Confluence format — PM completes judgment and customer evidence sections |
| discovery-brief | `cp -r ~/Projects/pm-ai-suite/skills/discovery-brief ~/.claude/skills/` | Compiles a weekly discovery brief with open questions, research sessions, and data gaps from sprint context |
| opportunity-scoring | `cp -r ~/Projects/pm-ai-suite/skills/opportunity-scoring ~/.claude/skills/` | RICE scoring with explicit assumptions and confidence levels — flags what to validate before committing |
| feedback-triage | `cp -r ~/Projects/pm-ai-suite/skills/feedback-triage ~/.claude/skills/` | Classifies raw user feedback by type, severity, and segment — routes to Jira or flags as duplicate |
| ac-validator | `cp -r ~/Projects/pm-ai-suite/skills/ac-validator ~/.claude/skills/` | Quality gate before engineering handoff — validates ACs are testable, KPIs have targets, and Figma is linked |

---

## Step 5: Connect Your Toolchain (Optional)

If you want Claude to operate across Jira, Confluence, Notion, and Slack 
directly — not just generate structured text — set up the n8n layer.

Ask me if you want to set this up. If yes, follow the instructions in 
`n8n-workflows/README.md`.

Quick version:
1. Spin up an N8N instance (cloud.n8n.io or self-hosted via Railway)
2. Add API credentials: Jira, Confluence, Notion, Slack, Claude
3. Import the workflow JSON files from `n8n-workflows/`
4. Configure your Slack slash commands pointing to n8n webhook URLs
5. Set cron schedules to your team timezone (CET recommended)

The full setup guide with credential configuration is in `n8n-workflows/README.md`.

---

## Step 6: Configure Claude Project

1. Open Claude → Create a new Project named `PM Work`
2. In Project Instructions, paste the contents of `CLAUDE.md` from this repo
3. Add each `SKILL.md` file you selected above as Project knowledge files
4. Test with: `/ticket Add Google OAuth to the onboarding flow`

Claude should return a fully structured Jira ticket following the template.

---

## Step 7: Verify

After installation, run:

claude plugin list

Confirm all selected plugins are enabled.

Then test one skill end to end:

/ticket [describe any feature request in plain language]

You should get a structured Jira ticket back within seconds.

---

## Done

You are set up with the PM AI Suite.

Full blueprint and architecture guide: https://yoavyeger.com/pm-suite  
Repo: https://github.com/yoavyeger-maker/pm-ai-suite  
Author: Yoav Yeger — Product Director
