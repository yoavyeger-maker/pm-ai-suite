# Contributing to the PM AI Suite

First, thank you for contributing. The goal of this project is to build a community-driven standard for how Product Managers operate in the AI era. We want to move the industry from manual artifact production to system architecture.

We welcome new skills, improvements to existing skills, and workflow templates.

## Core Philosophy

Before submitting a PR, ensure your contribution aligns with our core philosophy:
1.  **PMs are Architects, not Typists:** Skills should force the PM to provide judgment, strategy, and evidence. AI handles the formatting and structure.
2.  **No Hallucinations:** Skills must explicitly forbid the AI from inventing data, user quotes, or market facts.
3.  **Strict Quality Gates:** Outputs must be testable, actionable, and unambiguous.
4.  **Team-Agnostic:** Skills must work for any PM team, regardless of their specific product or industry.

## How to Contribute a New Skill

A "Skill" is a prompt template that enforces a specific standard for a PM task. 

To add a new skill:
1.  Create a new directory under `skills/` with a descriptive, hyphenated name (e.g., `skills/release-notes-generator/`).
2.  Create a `SKILL.md` file inside that directory.
3.  Your `SKILL.md` must follow the standard structure (see below).

### The Standard Skill Structure

Every `SKILL.md` file must contain the following sections:

1.  **Role Definition:** A one-sentence description of the persona the AI should adopt (e.g., "You are a strict quality gate...").
2.  **Rules:** Explicit constraints the AI must follow. This must include instructions on what to do if the input is vague or insufficient (e.g., "Ask up to two clarifying questions").
3.  **Output Format:** A strict markdown template for the output. Use `[PM TO COMPLETE]` placeholders for sections that require human judgment.
4.  **Example Input → Output:** A realistic, worked example showing exactly how the skill transforms raw input into the final structured output.

*Tip: Look at `skills/ticket-factory/SKILL.md` or `skills/prd-generator/SKILL.md` for the gold standard of what a skill should look like.*

## How to Contribute to Workflows or Templates

If you are contributing n8n workflows, Jira templates, or Confluence templates:
1.  Ensure no proprietary or company-specific data is included in the files.
2.  For n8n workflows, export the JSON and include a `README.md` in the same directory explaining how to configure the necessary credentials and webhooks.

## Pull Request Process

1.  Fork the repository and create your branch from `main`.
2.  If you've added a new skill, ensure it has been tested in Claude (or your LLM of choice) and consistently produces the desired output.
3.  Update the `README.md` to list your new skill or workflow if applicable.
4.  Submit a PR with a clear description of what the skill/workflow does and what problem it solves for PMs.

## Community and Collaboration

We believe AI is a tool for collective creation. If you have an idea for a skill but aren't sure how to write the prompt, open an Issue. We can collaborate to build it together.
