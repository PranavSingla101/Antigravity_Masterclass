<div align="center">

# Antigravity Masterclass

</div>

> **The North Star**
> To create the definitive, living resource for **"Antigravity Coding"** — the art of using Agentic AI to achieve 10x developer velocity *without* sacrificing engineering quality. This repository is not just a tutorial; it is the **gold standard implementation** of the very concepts it teaches. The codebase itself serves as the primary lesson.

---

## Phase 1: Foundation & Philosophy

### Project Setup
To build "big," you must stop the agent from guessing. You need a rigid structure that screams context. don't dump everything in one big file. Ideally, your structure should look like this:

```text
/apps
  /web (Frontend)
  /api (Backend)
/packages
  /ui (Shared components)
  /db (Schema & types)
/context (THE BRAIN)
  project_goals.md
  architecture_decision_records.md
```

### Agent Rules
Rules You Enforce From Day 0:

- ❌ Agents do not invent architecture
- ❌ Agents do not choose libraries without approval
- ❌ Agents do not write code without a spec
- ✅ Agents must output artifacts before code
- ✅ Every feature has a verification method

### The "Context" Folder
This is your secret weapon. Never explain your project twice.

**Content Sovereignty & Domain Context Priming**
Use Antigravity's `.agrules` (or `.cursorrules` if using compatibility mode) to force the agent to read your context folder first.

> **The Prompt:**
> "Before answering, ingest context/project_goals.md and context/tech_stack.md. If my request contradicts these, stop and warn me."

Your workflow should look like:
`PLAN → SPEC → IMPLEMENT → VERIFY → REFINE`

**Key Files:**
- `project_goals.md`: Contains the "North Star"—User personas, primary KPIs, and non-negotiable constraints
- `tech_stack.md`: Hard constraints (e.g., "Use Tailwind, no raw CSS," "Use TanStack Query, no useEffect for fetching")

---

## Phase 2: Core Workflows

### The Artifact Protocol (Plan Mode)
**Rule:** Never let an agent switch to "Act" (Coding) mode without a signed-off Plan Artifact.

**Trigger:** "Enter Plan Mode. I need a Technical Spec for [Feature X]."

**The Output:** Demand the agent produce a `.md` file in an `artifacts/` folder (e.g., `artifacts/specs/feature-x-spec.md`).

**Review:** You read the markdown. If the logic is flawed, you edit the Markdown, not the code.

**Execute:** Only once the artifact is approved do you say:
> "Execute artifacts/specs/feature-x-spec.md"

**Planning Mode (The Architect):** Use this for the first prompt of any new feature. It forces the agent to generate a SPEC.md or plan artifact first.

### Fast Mode (The Intern)
Use this for fixes and tweaks. It skips the planning artifact and goes straight to file edits.

**Trigger:** "Fast Mode" toggle ON.

**Use Case:** "Change the button color to blue," "Fix the typo in the header," or "Restart the server."

**Chat Tip:**
> "Build a login form. Refer to the Supabase-Auth skill for the correct API syntax."

This forces the agent to load that specific context window, preventing it from hallucinating outdated API methods.

### Skills and Context Engineering
Generic LLMs write generic code. `SKILL.md` files are how you "fine-tune" the agent's behavior without training a model. You are creating a library of "Standard Operating Procedures."

**Defining Skills:** Create a folder `/.antigravity/skills/`. Inside, create markdown files for repeatable tasks.

**Example:** `/.antigravity/skills/create_endpoint.md`

**The Skill Trigger:** In your custom instructions, write:
> "If I ask for a specific task found in /.antigravity/skills, load that file into context immediately."

### Advanced Context Management (@ Mentions)
Just like in Slack or Discord, you can direct the agent's attention to specific files to save context window space.

**The @ Symbol:** Type `@` in the chat to open the file picker.

**The Strategy:** Don't say "Fix the bug in the auth."

> **The Advanced Prompt:**
> "Fix the logic error in @authController.ts regarding the session timeout. Reference @userModel.ts for the schema."

**Why:** This forces the agent to strictly focus on those files, reducing hallucination and preventing it from "refactoring" files you didn't want it to touch.

---

## Phase 3: Advanced Development Techniques

### 1. The "Senior Dev" Self-Roast (The Iteration Loop)
**The Concept:** AI agents are often "lazy". You have to bully them into excellence. Force the agent to switch personas from "Junior Coder" to "Senior Architect" before it applies the code.

> **The Cracked Prompt:**
> "Before you apply this code, act as a Staff Engineer at Google. Review your own plan above. Find 3 potential edge cases, security vulnerabilities, or logic gaps. Then, rewrite the plan to fix them."

### 2. The Model-Switching Relay (Speed vs. IQ)
You have access to different models (Gemini Flash, Claude 3.5 Sonnet/Opus) in the dropdown. Don't stick to one. Use them like gears in a car.

**The Strategy:**
- **Gear 1 (Gemini Flash):** Use for "grunt work." Scaffolding files, writing CSS classes, fixing typos, generating dummy data. Fast, cheap, low IQ.
- **Gear 2 (Claude 3.5 Sonnet/Opus):** Switch to this mid-chat for "brain surgery." Complex React state logic, database migrations, or debugging a race condition.

**The Workflow:** Start with Flash to build structure -> Switch to Claude for heavy functions -> Switch back to Flash for documentation.

### 3. The "Docs Injection" (Anti-Hallucination)
**The Strategy:** Don't ask "How do I use X?". Manually overwrite its training data with ground truth.

> **The Cracked Prompt:**
> "I am pasting the raw documentation for Stripe Connect v3 below. Read this into your context window. Do not write any code yet. Just confirm you understand the new parameter structure." [Paste Docs] "Now, using ONLY the documentation provided above, write the integration function."

### 4. The "Pseudo-Code Architect"
**The Concept:** For massive features, don't let it write code immediately. It will get lost in the syntax.

> **The Cracked Prompt:**
> "We are building the user referral system. Write the Pseudo-Code for the entire backend flow in the chat. Do not write real code. Use comments to explain the data flow."

### 5. The "Context Wipe" (The Reset Button)
**The Fix:** If the chat starts going in circles:
1. Type: "STOP."
2. Open a New Chat Window.
3. Type:
> "I have a project in the current directory. Read the file @auth.ts. It has a bug where X happens. Fix it."

### 6. The "UI Thief" (Pixel-Perfect Cloning)
**The Concept:** Don't describe a design with words. Use the vision capabilities to "steal" professional designs.
**The Cracked Workflow:** Take a screenshot of a website component you love. Paste it into the Antigravity chat.

> **The Prompt:**
> "Act as a Frontend Expert. Replicate this component exactly using Tailwind CSS. Do not improvise. Match the padding, border-radius, and font-weight visually. Output the code in a single React component."

### 7. The "Mock Data Factory" (Stress Testing)
**The Concept:** Force the agent to break your UI with massive datasets before you deploy.

> **The Cracked Prompt:**
> "Generate a seed script that populates the database with 50 users.
>
> User 1 should have a 100-character name.
>
> User 2 should have a missing profile picture.
>
> User 3 should have Chinese characters in their bio. Run the app and tell me which UI components break."

---

## Phase 4: Verification & QA

### Test-Driven Chat (The Guardrail Method)
**The Concept:** Force the agent to write the test first. It creates a rigid definition of "success".

> **The Cracked Prompt:**
> "We are building the calculate_tax function. Step 1: Write a Jest test file with 5 edge cases (negative numbers, zero, null). Step 2: Run the test (it should fail). Step 3: Write the function to pass the test."

### Vision Verification (The "Trust but Verify" Loop)
**The Concept:** Antigravity has a browser agent. Don't just trust it when it says "I fixed the button alignment." Make it prove it.

> **The Cracked Prompt:**
> "Take a screenshot of the current viewport. Analyze the screenshot pixel-by-pixel. Does the 'Submit' button have exactly 16px padding? If not, fix the CSS and screenshot again."

### Console Log Sherlock (Lazy Debugging)
**The Concept:** The agent can "see" the terminal output better than you can.

> **The Cracked Prompt:**
> "Run the build command. If it fails, capture the error log. Analyze the error log trace. Don't just fix it—tell me which file caused it and why the dependency conflict occurred."

### Automated Browser Testing
**The Goal:** Don't just ask for unit tests. Ask for "Click Paths."

> **The Prompt:**
> "After building the login feature, use the Browser Tool to: 1. Navigate to /login. 2. Enter valid credentials (user: test, pass: 123). 3. Verify the URL redirects to /dashboard. 4. Take a screenshot of the dashboard."

---

## Phase 5: God Mode

### MCP (Model Context Protocol) Integration
MCP is the bridge that lets the agent leave the IDE and touch your infrastructure.

**What MCP actually does:**
- Tails logs: `/var/log/app.log`
- Exposes DB schema: tables, indexes, constraints
- Agent reads directly

**Result:**
You say: "Investigate why checkout fails in prod."
The agent: Reads logs -> Checks schema -> Correlates error -> Proposes fix.
No screenshots. No pasting.

### Local LLM Integration
Install the "Cline" extension within Antigravity to connect with Ollama. This allows you to run local LLMs (like Llama 3) for free, offline coding, or to save API credits.

### Nano Banana (Image Generation)
Use the built-in image generator (Nano Banana) directly in the chat to create project assets like logos and avatars instantly, avoiding the need for external tools like Midjourney.