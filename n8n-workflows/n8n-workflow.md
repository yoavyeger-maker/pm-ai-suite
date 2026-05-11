# n8n Workflows

This directory contains pre-built n8n workflows that automate the PM AI Suite skills.

## Workflow 1: Slack-to-Jira Ticket Factory

This workflow allows anyone on your team to type a messy feature request into Slack using a slash command (e.g., `/ticket "We need a way to export the dashboard to PDF"`). 

n8n catches the command, sends the raw text to Claude along with the `ticket-factory` system prompt, parses the structured output, creates a perfectly formatted Jira ticket, and replies in Slack with the link.

### How to Install

1. **Import the JSON:**
   * Open your n8n instance.
   * Go to **Workflows** > **Add Workflow**.
   * Click the **...** menu in the top right and select **Import from File**.
   * Select `slack-to-jira-ticket-factory.json` from this directory.

2. **Configure the Slack Slash Command:**
   * Double-click the **Slack Slash Command** (Webhook) node.
   * Copy the "Test URL" (for testing) or "Production URL" (for live use).
   * Go to [api.slack.com/apps](https://api.slack.com/apps) and select your app.
   * Go to **Slash Commands** > **Create New Command**.
   * Set the command to `/ticket` (or whatever you prefer).
   * Paste the n8n Webhook URL into the "Request URL" field.
   * Save and reinstall the app to your workspace.

3. **Configure Anthropic (Claude) Credentials:**
   * Double-click the **Anthropic Claude** node.
   * Under Credentials, click **Create New**.
   * Enter your Anthropic API key (get one at [console.anthropic.com](https://console.anthropic.com)).
   * Save the credentials.

4. **Configure Jira Credentials:**
   * Double-click the **Create Jira Ticket** node.
   * Under Credentials, click **Create New**.
   * Enter your Jira email, API token (generate one at [id.atlassian.com/manage-profile/security/api-tokens](https://id.atlassian.com/manage-profile/security/api-tokens)), and your Jira domain (e.g., `your-company.atlassian.net`).
   * **Important:** Update the `Project` field in the node to match your actual Jira Project Key (e.g., `ENG` or `PROD`).

5. **Configure Slack Reply Credentials:**
   * Double-click the **Reply to Slack** node.
   * Under Credentials, click **Create New**.
   * Connect your Slack account using OAuth or a Bot Token.
   * Ensure your Slack bot has the `chat:write` scope.

6. **Activate:**
   * Toggle the workflow to **Active** in the top right corner of n8n.
   * Go to Slack and type `/ticket "your messy feature request here"`.

### Customizing the Prompt

If you want to modify how Claude writes the tickets, double-click the **Anthropic Claude** node and edit the `system` message. By default, it is loaded with a condensed version of the `ticket-factory` skill from this repository.
