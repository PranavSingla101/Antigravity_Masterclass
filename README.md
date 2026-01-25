<div align="center">

# Antigravity Masterclass

**The Definitive Guide to Agentic AI Coding**  
*The art of using Agentic AI to achieve 10x developer velocity without sacrificing engineering quality.*

![Status](https://img.shields.io/badge/Status-Active-success?style=for-the-badge) ![Phase](https://img.shields.io/badge/Phase-Masterclass-blueviolet?style=for-the-badge)

</div>

---

## 🏛️ Phase 1: Foundation & Philosophy

### Project Setup
To build "big," you must stop the agent from guessing. You need a rigid structure that screams context. **Do not dump everything in one big file.**

#### The Ideal Structure

```text
/antigravity
├── /.github                # CI/CD workflows (Build, Test, Deploy)
├── /apps                   # DEPLOYABLE applications
│   ├── /web                # Main Next.js/React App (The Dashboard/Landing)
│   ├── /api                # Main Backend (Node, Python, or Go)
│   ├── /workers            # Background jobs/Queues (Redis consumers)
│   └── /docs               # Documentation site (e.g., Storybook or Docusaurus)
│
├── /packages               # SHARED internal libraries (The building blocks)
│   ├── /ui                 # Design System (Buttons, Inputs, Theme provider)
│   ├── /db                 # Database Schema (Prisma/Drizzle) & Client export
│   ├── /api-client         # Type-safe SDK to talk to your own API
│   ├── /utils              # Shared logic (Math, Date formatting, Regex)
│   ├── /types              # Shared TypeScript interfaces/Zod schemas
│   ├── /logger             # Standardized logging (Winston/Pino)
│   ├── /tsconfig           # Shared TypeScript configurations
│   └── /eslint-config      # Shared Linting rules
│
├── /infra                  # Infrastructure as Code
│   ├── /docker             # Dockerfiles & Compose
│   └── /terraform          # Cloud resources (AWS/GCP)
│
├── /context                # THE BRAIN (Read-only for Agent context)
│   ├── 00_project_goals.md # "What problem do we solve?"
│   ├── 01_tech_stack.md    # "We use Next.js 14, Tailwind, Postgres..."
│   ├── 02_conventions.md   # "Code style: Functional, Early returns, Zod validation"
│   ├── 03_roadmap.md       # Current phase active tasks
│   └── /adrs               # Architecture Decision Records (Why we chose X over Y)
│
├── package.json            # Root configuration (likely Turborepo or Nx)
├── turbo.json              # Build pipeline configuration
└── pnpm-workspace.yaml     # Workspace definition
```

#### Why this structure?

| Feature | Description | Benefit |
| :--- | :--- | :--- |
| **Code Reusability** | Shared logic lives in `/packages`. | Write once (DB, UI, Types) and import everywhere (Web, Mobile, Admin). |
| **Scalability** | Specific folders like `/web` and `/api`. | Prevents naming collisions. Accommodates multiple frontends/backends from day one. |
| **Separation of Concerns** | Strict isolation of logic. | You can't write DB queries in React components. Keeps architecture clean & testable. |

### Agent Rules
Rules you enforce from **Day 0**:

| ❌ Don't | ✅ Do |
| :--- | :--- |
| Agents do not invent architecture. | Agents must output artifacts before code. |
| Agents do not choose libraries without approval. | Every feature has a verification method. |
| Agents do not write code without a spec. | |

### The "Context" Folder
> [!IMPORTANT]
> **The Brain of Your Project.** With this folder, you never explain your project twice.

**Key Files:**

- **`02_conventions.md`**: Defines the "Laws of the Code".
    - Code style: Functional programming patterns.
    - Control flow: Using early returns.
    - Validation: Using Zod for schema validation.
    *Essentially, it tells the AI how to write code that aligns with established practices.*

- **`/adrs` (Architecture Decision Records)**:
    - **Definition**: Captures a single architectural decision (e.g., "Use Postgres").
    - **Content**: Context (problem), Decision (choice), Consequences (trade-offs).
    - **Value**: Prevents the Agent from refactoring code that exists for a specific, documented reason.

### Content Sovereignty & Domain Context Priming
Use Antigravity's `.agrules` (similar to `.cursorrules`) to force the agent to read your context folder first.

> [!TIP]
> **Coding Practice for Prompt**
> "Before answering, ingest `context/project_goals.md` and `context/tech_stack.md`. If my request contradicts these, stop and warn me."

**The Workflow:**
`PLAN → SPEC → IMPLEMENT → VERIFY → REFINE`

---

## ⚙️ Phase 2: Core Workflows

### The Artifact Protocol (Plan Mode)

> [!WARNING]
> **Rule:** Never let an agent switch to "Act" (Coding) mode without a signed-off Plan Artifact.

**Planning Mode (The Architect)**
Use this for the first prompt of any new feature. It forces the agent to generate a `SPEC.md` or plan artifact first.

- **What it is**: A Markdown file (e.g., `feature-x-spec.md`) in the `artifacts/` folder.
- **Its Job**: Separates Planning from Coding. Serves as a "Contract".
- **Trigger**: "Enter Plan Mode. I need a Technical Spec for [Feature X]."

**The Workflow Loop:**
1. **Demand Output**: `artifacts/specs/feature-x-spec.md`
2. **Review**: Edit logic errors in the Markdown, *not* the code.
3. **Execute**:
   > "Execute artifacts/specs/feature-x-spec.md"

### Fast Mode (The Intern)
Use this for fixes, tweaks, and maintenance. Skips the planning artifact.

- **Trigger**: "Fast Mode" toggle ON.
- **Use Case**: "Change button color", "Fix header typo", "Restart server".

> [!TIP]
> **Chat Tip (Prevent Hallucinations):**
> "Build a login form. Refer to the **Supabase-Auth skill** for the correct API syntax."

### Advanced Context Management (@ Mentions)
Direct the agent's attention to specific files to save context window space.

- **The Strategy**: Do NOT say "Fix the bug in the auth."
- **The Advanced Prompt**:
  > "Fix the logic error in `@authController.ts` regarding the session timeout. Reference `@userModel.ts` for the schema."

### Skills and Context Engineering
**SKILL.md** files are your "Standard Operating Procedures"—libraries of repeatable tasks.

- **Location**: `/.antigravity/skills/`
- **Example**: `/.antigravity/skills/create_endpoint.md`
- **Trigger**:
  > "If I ask for a specific task found in `/.antigravity/skills`, load that file into context immediately."

### The Model-Switching Relay (Speed vs. IQ)
Don't stick to one model. Use them like gears in a car.

| Gear | Model | Best For |
| :--- | :--- | :--- |
| **Gear 1** | **Gemini Flash** | Grunt work. Scaffolding, CSS, Typos, Dummy Data. (Fast & Cheap) |
| **Gear 2** | **Claude 3.5 Sonnet/Opus** | Brain surgery. Complex React State, DB Migrations, Race Conditions. |

**Strategy**: `Flash (Structure) → Claude (Logic) → Flash (Documentation)`

---

## 🚀 Phase 3: Advanced Development Techniques

### 1. The "Senior Dev" Self-Roast (The Iteration Loop)
> [!NOTE]
> AI agents are lazy. You must bully them into excellence.

> [!TIP]
> **The Cracked Prompt:**
> "Before you apply this code, act as a **Staff Engineer at Google**. Review your own plan above. Find 3 potential edge cases, security vulnerabilities, or logic gaps. Then, rewrite the plan to fix them."

### 2. The "UI Thief" (Pixel-Perfect Cloning)
Don't describe designs. Steal them using Vision.

> [!TIP]
> **The Cracked Prompt:**
> "Act as a **Frontend Expert**. Replicate this component exactly using Tailwind CSS. Do not improvise. Match the padding, border-radius, and font-weight visually. Output the code in a single React component."

### 3. The "Docs Injection" (Anti-Hallucination)
Manually overwrite training data with ground truth.

> [!TIP]
> **The Cracked Prompt:**
> "I am pasting the raw documentation for Stripe Connect v3 below. **Read this into your context window.** Do not write any code yet. Just confirm you understand the new parameter structure." [Paste Docs] "Now, using ONLY the documentation provided above, write the integration function."

### 4. The "Pseudo-Code Architect"
For massive features, avoid syntax traps by demanding pseudo-code first.

> [!TIP]
> **The Cracked Prompt:**
> "We are building the user referral system. Write the **Pseudo-Code** for the entire backend flow in the chat. Do not write real code. Use comments to explain the data flow."

### 5. The "Context Wipe" (The Reset Button)
If the chat circles, kill it.
1. Type: "STOP."
2. Open New Chat without history.
3. **Prompt**: "Read `@auth.ts`. It has a bug where X happens. Fix it."

### 6. The "Mock Data Factory" (Stress Testing)
> [!TIP]
> **The Cracked Prompt:**
> "Generate a seed script that populates the database with 50 users. 
> - User 1: 100-character name.
> - User 2: Missing pfp.
> - User 3: Chinese characters in bio. 
> Run the app and tell me which UI components break."

---

## 🛡️ Phase 4: Verification & QA

### Test-Driven Chat (The Guardrail Method)
Force the agent to define "success" before coding.

> **Prompt:** "We are building the `calculate_tax` function. **Step 1:** Write a Jest test file with 5 edge cases. **Step 2:** Run the test (it should fail). **Step 3:** Write the function to pass the test."

### Vision Verification (The "Trust but Verify" Loop)
Don't trust text confirmations. Trust pixels.

> **Prompt:** "Take a screenshot of the current viewport. Analyze the screenshot pixel-by-pixel. Does the 'Submit' button have exactly 16px padding? If not, fix the CSS and screenshot again."

### Console Log Sherlock (Lazy Debugging)
> **Prompt:** "Run the build command. If it fails, capture the error log. Analyze the error log trace. Don't just fix it—tell me which file caused it and why the dependency conflict occurred."

### Automated Browser Testing
Ask for "Click Paths," not just unit tests.

> **Prompt:** "After building the login feature, use the **Browser Tool** to: 1. Navigate to /login. 2. Enter valid credentials (user: test, pass: 123). 3. Verify the URL redirects to /dashboard. 4. Take a screenshot of the dashboard."

---

## ⚡ Phase 5: God Mode

### MCP (Model Context Protocol) Integration
The bridge that allows agents to leave the IDE and touch your infrastructure.

**Two Ways to Implement:**

1. **Adding Raw Prompt to File**  
   Create a specifically crafted file (JSON config or script) containing the raw prompt or instruction set for the MCP server.  
   *   **Use case**: Custom tools that require specific, unique logic not found elsewhere.
   *   **Method**: Define the raw prompts/tools in a file and point your agent configuration to run or read this file.

2. **Adding Already in Antigravity**  
   Utilize the MCP servers and tools that are already integrated or pre-configured within the Antigravity framework.  
   *   **Use case**: Standard operations (e.g., File system access, Git, Browser automation).
   *   **Method**: Simply enable or configure the existing servers in your settings; no new code required.

### Local LLM Integration
Install **Cline** to connect with Ollama. Run local LLMs (Llama 3) for offline, free coding.

### Nano Banana (Image Generation)
Use the built-in image generator (**Nano Banana**) to create assets (logos, avatars) instantly within the chat.