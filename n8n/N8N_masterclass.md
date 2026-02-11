<div align="center">

# n8n Automation Masterclass

![Status](https://img.shields.io/badge/Status-Beta-blue?style=for-the-badge) ![Phase](https://img.shields.io/badge/Phase-Integration-blueviolet?style=for-the-badge)

</div>

> **System Goal:** Standardize the rapid development of n8n workflows using Cursor, Antigravity, and MCP. Eliminate manual node dragging; prioritize code-first generation and architectural strictness.

---

## 1. Project Initialization & Architecture

### Step 1: Create the File Structure (Editor View)
Go to the Editor View and create these three items. This is your **"System Prompt"** equivalent.

**1. `system.md` (or `context.md`)** - The master instruction file.
**Content:**
```markdown
You are an autonomous agent using the WAT framework. Always check the workflows/ folder for SOPs before acting. Use the tools in tools/ for execution.
```

**2. `workflows/` Folder**
Create markdown files for your recurring tasks (e.g., `youtube_scrape_sop.md`).
> [!TIP]
> **Antigravity Superpower:** You can paste incredibly detailed, step-by-step logic here.

**3. `tools/` Folder**
Create your Python scripts here (e.g., `get_youtube_data.py`).
> [!NOTE]
> Antigravity agents have a built-in terminal and browser, so you don't always need a script for simple things (like "Go to Google and search X"), but for robust APIs (like YouTube Data API), Python scripts in this folder are best.

### Method 2: The "Explicit" Plan (WAT Framework)
If you want to force the agent to follow your specific plan file (like the video):

**Draft the Plan:** Create a file named `current_plan.md` in your root folder.

**Content:**
```markdown
# Project: YouTube Analysis
- [ ] Step 1: Run `tools/scrape_channels.py` to get data.
- [ ] Step 2: Use the 'Canvas Design' skill to generate a PDF.
- [ ] Step 3: Email the PDF to user.
```

---

## 2. Visual-to-Workflow Conversion

To bypass manual node placement, provide visual logic to the AI.

> [!TIP]
> Upload a screenshot of a flowchart to Cursor.
> **Command:** "Convert this visual logic into a valid n8n workflow JSON schema compatible with version 1.x."

---

## 3. Prompting Strategy

**Rule:** Workflows are functional transformations. Prompts must be structured as Input -> Logic -> Output.

### The Function Node Prompt
When generating code for an n8n Code Node, use high-density technical requirements.

> **Context:** Processing an array of objects from an HTTP Request node.
> **Logic:** Access items via `$input.all()`. Filter for `status === 'active'`.
> **Transformation:** Map objects to `{ user_id: id, contact: email }`.
> **Constraint:** Handle null values for the email field by assigning a placeholder.

---

## 4. MCP Server Setup

**Rule:** Utilize the Model Context Protocol (MCP) to allow the local IDE to interface directly with the n8n API.

### A. Environment Configuration
Add the following to the `claude_desktop_config.json` or Cursor MCP settings.

```json
{
  "mcpServers": {
    "n8n": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-n8n"
      ],
      "env": {
        "N8N_API_KEY": "YOUR_API_KEY",
        "N8N_HOST": "https://your-instance.n8n.cloud"
      }
    }
  }
}
```

### B. MCP Consultation
Use the MCP server to inspect existing workflows for refactoring.

> [!IMPORTANT]
> **Query:** "Retrieve workflow ID [ID] and identify nodes that can be replaced by a single Code node to reduce execution latency."

---

## 5. Execution Workflow

**Rule:** Follow a linear build-test-version cycle.

1.  **Define:** Update `project_mission.md` with the specific automation goal.
2.  **Plan:** Use a reasoning model to populate `todo.md`.
3.  **Generate:** Use Cursor Composer with Claude 3.5 Sonnet to produce JavaScript/JSON.
4.  **Deploy:** Import the generated JSON into n8n or paste code into function nodes.
5.  **Sync:** Use the MCP server to pull the final workflow back into the `workflows/` directory for version control.

---

## ❓ FAQ

### How do I make these tools?
Refer to the `tools/` folder documentation or check the "Antigravity Superpower" tip in Section 1.