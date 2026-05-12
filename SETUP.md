# Setup Guide — PM AI Suite

There are three levels of setup. Start with Level 1. Add more only when you need it.

---

## Level 1 — Claude Skills (30 minutes, no infrastructure required)

This level gives your PMs enforced standards for their daily work using Claude Projects.

### 1. Create the Project
1. Open Claude and create a new Project named **PM Work**.
2. Open `CLAUDE.md` from this repo and paste the full contents into the **Project Instructions**.

### 2. Add the Skills
Upload each file from the `skills/` directory as a separate **Project Knowledge** file.

| Skill | What it does |
| --- | --- |
| `ticket-factory` | Converts a raw Slack request into a structured Jira ticket with user story, ACs, KPIs, Figma link, and scope. |
| `prd-generator` | Generates a first-draft PRD scaffold in Confluence format — PM completes judgment and customer evidence sections. |
| `discovery-brief` | Compiles a weekly discovery brief with open questions, research sessions, and data gaps from sprint context. |
| `opportunity-scoring` | RICE scoring with explicit assumptions and confidence levels — flags what to validate before committing. |
| `feedback-triage` | Classifies raw user feedback by type, severity, and segment — routes to Jira or flags as duplicate. |
| `ac-validator` | Quality gate before engineering handoff — validates ACs are testable, KPIs have targets, and Figma is linked. |
| `competitor-intelligence` | Synthesizes raw competitor updates into a strategic brief, stripping marketing fluff and assessing threat level. |
| `stakeholder-update` | Translates messy sprint notes into a crisp, executive-friendly update with strict Red/Yellow/Green status. |

### 3. Test
Paste a raw feature request into the chat and type `/ticket`. Confirm the output matches the Jira template structure.

---

## Level 2 — Templates in Jira and Confluence (1 hour, no infrastructure required)

This level ensures that tickets and documents created manually match the structure of those created by Claude.

### Jira
1. Install `jira-templates/ticket-template.md` as the default description on your **Story** issue type.
2. Install `jira-templates/bug-template.md` as the default description on your **Bug** issue type.

### Confluence
1. Create a new Space Template from `confluence-templates/prd-template.md`.
2. Create a new Space Template from `confluence-templates/decision-log-template.md`.
3. Create a new Space Template from `confluence-templates/retro-template.md`.

---

## Level 3 — Full n8n Automation (Half day, requires infrastructure)

This level wires Slack directly to Jira using n8n, allowing PMs to generate and create tickets without leaving Slack.

### 1. Infrastructure
*   Spin up an n8n instance ([cloud.n8n.io](https://cloud.n8n.io) or Railway self-hosted).
*   Create a Slack app with slash commands and incoming webhooks enabled.
*   Add your Anthropic API key to n8n credentials.
*   Configure your Jira API token in n8n.
*   Configure your Confluence API token in n8n (optional — only needed for brief automation).

### 2. Slack Channels
Create the following channels in your workspace:
*   `#pm-tickets` — receives Jira ticket confirmations
*   `#pm-discovery` — receives weekly discovery briefs
*   `#pm-intel` — receives competitor intelligence updates
*   `#product-updates` — receives stakeholder updates

### 3. Workflow Setup
1. Import `n8n-workflows/slack-to-jira-ticket-factory.json` into n8n.
2. Set your Jira Project Key in the **Create Jira Ticket** node.
3. Replace `your-domain.atlassian.net` in the **Slack reply** node with your actual Jira domain.
4. Activate the workflow.

### 4. Validation
1. Type `/ticket Add Google OAuth to the onboarding flow` in Slack.
2. Confirm a Jira issue is created with the full ticket template populated.
3. Confirm the Slack thread receives the Jira issue link and key.

---

## Done

You are set up with the PM AI Suite.

Full blueprint and architecture guide: [yoavyeger.com/pm-suite](https://yoavyeger.com/pm-suite)  
Repo: [github.com/yoavyeger-maker/pm-ai-suite](https://github.com/yoavyeger-maker/pm-ai-suite)  
Author: Yoav Yeger — Product Director
