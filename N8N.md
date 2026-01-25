<div align="center">

# n8n Automation Masterclass

**The "Nervous System" for Agentic AI**  
*The art of offloading API integration, webhooks, and complex logic chains to n8n, keeping your codebase clean and your Agent focused.*

![Status](https://img.shields.io/badge/Status-Beta-blue?style=for-the-badge) ![Phase](https://img.shields.io/badge/Phase-Integration-blueviolet?style=for-the-badge)

</div>

---

## ⚡ Philosophy: The "Low-Code" Backend

In the **Antigravity** philosophy, code is a liability. The less code you write, the less you maintain.
n8n is not just an automation tool; it is the **Executor** for your Agent.

### Why n8n + Agents?
| Feature | Agentic Benefit |
| :--- | :--- |
| **Visual Logic** | Debugging complex flows (e.g., Stripe -> Discord -> DB) is instant. |
| **Context Saver** | Don't waste context window on API documentation. Just tell the agent: "Call the n8n webhook." |
| **Reliability** | n8n handles retries, errors, and rate limits better than a fragile LLM script. |

> [!IMPORTANT]
> **The Golden Rule:**
> If a task involves connecting 3+ external services (e.g., Gmail -> Sheets -> Slack), **DO NOT CODE IT.** Build an n8n workflow and have your Agent trigger it.

---

## 🏗️ The "Antigravity" Setup (Docker)

We do not use n8n cloud constraints. We run **Self-Hosted**.

### 📝 `docker-compose.yml` (Standard)
Save this in `/infra/n8n/docker-compose.yml`.

```yaml
version: '3.8'

services:
  n8n:
    image: n8n/n8n:latest
    ports:
      - "5678:5678"
    environment:
      - N8N_BASIC_AUTH_ACTIVE=true
      - N8N_BASIC_AUTH_USER=admin
      - N8N_BASIC_AUTH_PASSWORD=password # Change this!
      - WEBHOOK_URL=http://localhost:5678/
    volumes:
      - n8n_data:/home/node/.n8n

volumes:
  n8n_data:
```

> [!TIP]
> **Tunneling for Webhooks**
> To let external services (GitHub, Stripe) hit your local n8n, use `ngrok` or `cloudflared`.
> `npx ngrok http 5678` -> Use this URL in your n8n configuration.

---

## 🧠 Core Workflows

### 1. The "Agent Hand-off" (Webhook Receiver)
Instead of teaching the Agent how to authenticate with the Jira API, simply expose a clean Webhook.

**The Prompt:**
> "I have created an n8n webhook at `POST /webhook/create-ticket`. It accepts `{ title, description, priority }`. Please write a TypeScript function to POST to this URL."

**The n8n Flow:**
`Webhook Node` → `Jira Node` → `Slack Node` → `Respond to Webhook Node`

### 2. The "Context Fetcher" (RAG Helper)
Use n8n to scrape, parse, and clean data *before* giving it to the Agent.

**The Workflow:**
1.  **Agent Request:** Agent asks for "Latest Competitor Pricing".
2.  **n8n Action:** Scrapes 5 websites, cleans HTML, summarizes with OpenAI Node.
3.  **Result:** Returns clean JSON to the Agent.

---

## 🛠️ Skill: Create n8n Tool
*Instructions for creating a standard n8n-compatible tool function.*

### 📝 File: `/.antigravity/skills/n8n/create_webhook_tool.md`

```markdown
# Skill: Create n8n Webhook Tool

## Context
We need a standardized way to call n8n workflows from our App/Agent.

## Instructions
1.  **Define the Payload**: What data does n8n need? (Use Zod).
2.  **Create the Fetcher**: Write a simple `fetch` wrapper.
3.  **Error Handling**: Handle 4xx/5xx n8n errors gracefully.

## Template
```typescript
import { z } from "zod";

export const triggerN8nWorkflow = async (payload: any) => {
  const response = await fetch(process.env.N8N_WEBHOOK_URL, {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify(payload),
  });
  
  if (!response.ok) throw new Error("n8n Workflow Failed");
  return response.json();
}
```
```

---

## 🛡️ Best Practices

1.  **Always Return JSON**: Ensure the final node in n8n is "Respond to Webhook" returning `{ success: true }`.
2.  **Secure Your Webhooks**: Use a `secret` header token in your Agent calls and verify it in the n8n Webhook node.
3.  **Keep it Atomic**: One workflow = One distinct job (e.g., "Onboard User", not "Manage Entire System").

> [!WARNING]
> **Avoid "Loop of Death"**
> Do not let n8n trigger the Agent which triggers n8n indefinitely. Always set a `max_iterations` or loop guard.