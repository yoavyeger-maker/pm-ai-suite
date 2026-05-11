# PM AI Suite

A practical blueprint for Heads of Product who want to remove operational 
friction from their PM org and redirect time toward judgment, discovery, 
and decisions.

This is not a product. It is an open reference architecture — a set of 
Claude skills, n8n workflow specs, Jira and Confluence templates, and a 
Slack command layer that product teams can adopt, adapt, and extend.

---

## What this solves

Most PMs spend 60–70% of their time on translation work: writing tickets, 
formatting specs, summarizing sprints, chasing updates. That work has a 
structure that can be automated. This suite automates the structure and 
returns PM time to intent, signal, and decision quality.

The underlying model: the PM role is shifting from artifact producer to 
**Architect of Systems that Learn** — setting intent, governing guardrails, 
and feeding a flywheel of signal → execution → correction → memory.

---

## What is included

| Folder | Contents |
|--------|----------|
| `skills/` | Claude skill files for each automation — install directly into Claude Projects |
| `n8n-workflows/` | Workflow specs and setup instructions for n8n |
| `confluence-templates/` | PRD, decision log, and retro templates |
| `jira-templates/` | Ticket template with acceptance criteria, KPIs, and scope |
| `CLAUDE.md` | Global rules file for PM Claude sessions |

---

## Automations covered

1. Slack → Jira ticket factory
2. Weekly discovery brief
3. PRD first-draft generator
4. Sprint retro synthesis
5. Stakeholder update generator
6. Opportunity scoring (RICE)
7. Decision log
8. User feedback triage
9. Competitor intelligence brief
10. Definition-of-ready validator

---

## Toolchain

Slack · Claude · n8n · Jira · Confluence · Notion · Figma · Miro

---

## How to use this

**Option A — Install the Claude skills**
Open Claude, create a new Project, go to Project Instructions, and paste:

> "Load the skills from github.com/yoavyeger/pm-ai-suite/skills and follow 
> the CLAUDE.md rules for all PM tasks in this project."

Then add the relevant SKILL.md files as Project knowledge files.

**Option B — Use the templates directly**
Copy any template from `confluence-templates/` or `jira-templates/` into 
your own tool. No setup required.

**Option C — Deploy the full n8n layer**
Follow the setup guide in `n8n-workflows/README.md`. Requires an n8n 
instance, Slack app, and API tokens for Jira and Confluence.

---

## Full guide

Read the complete blueprint and architecture walkthrough at:  
[yoavyeger.com/pm-suite](https://yoavyeger.com/pm-suite)

---

## Author

Yoav Yeger — Product Director  
[yoavyeger.com](https://yoavyeger.com)
