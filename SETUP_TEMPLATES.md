# Template Setup Guide

This guide explains how to install the Jira and Confluence templates into your workspace. These templates are the exact formats that the Claude skills are trained to generate. By installing them in your systems of record, you ensure that human-written and AI-generated artifacts share the exact same structure.

## Jira Ticket Template

**File:** `jira-templates/ticket-template.md`

### How to install in Jira Cloud:
1.  Open your Jira project.
2.  Go to **Project settings** > **Issue types**.
3.  Select the issue type you want to apply this to (e.g., "Story" or "Task").
4.  If you are using the new issue view, you can set a default description.
5.  Copy the raw text from `ticket-template.md` and paste it into the default description field.
6.  Save your changes.

*Note: If your Jira instance does not support default descriptions natively, you can use a browser extension like "Jira Templates" or an app from the Atlassian Marketplace.*

## Confluence Templates

**Files:** 
*   `confluence-templates/prd-template.md`
*   `confluence-templates/decision-log-template.md`
*   `confluence-templates/retro-template.md`

### How to install in Confluence Cloud:
1.  Go to your Confluence Space.
2.  Click **Space settings** (the gear icon) in the sidebar.
3.  Under the "Look and feel" section, click **Templates**.
4.  Click **Create New Template**.
5.  Name the template (e.g., "AI Suite PRD").
6.  Copy the raw text from the corresponding `.md` file in this repo.
7.  Paste it into the Confluence editor. (Confluence usually auto-formats markdown on paste. If it doesn't, you may need to manually apply the headings and tables).
8.  Click **Save**.
9.  Repeat for the Decision Log and Retro templates.

### How to use them:
When a PM creates a new page in Confluence, they can now select your custom template from the template browser. If they used the Claude `prd-generator` skill, they can simply paste Claude's output directly over the template—the structure will match perfectly.

## Notion Alternative

If your team uses Notion instead of Confluence/Jira:
1.  Create a new page in Notion.
2.  Type `/template` to create a new template button, or create a new database template.
3.  Copy the markdown from the files in this repo and paste it into the Notion template block. Notion will automatically convert the markdown into blocks.
