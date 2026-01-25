# Project Goals: Antigravity Masterclass

## 1. The North Star (Vision)
To create the definitive, living resource for **"Antigravity Coding"** — the art of using Agentic AI to achieve 10x developer velocity *without* sacrificing engineering quality. This repository is not just a tutorial; it is the **gold standard implementation** of the very concepts it teaches. The codebase itself serves as the primary lesson.

## 2. User Personas (Target Audience)
*   **The 10x Senior Engineer**: Already precise with code, but wants to offload cognitive load and "grunt work" (scaffolding, types, boilerplate) to AI to focus on high-level architecture and complex logic.
*   **The Solopreneur / Indie Hacker**: Needs to bridge the gap between idea and shipped product in days, not months. Uses AI to fill skill gaps (e.g., a Backend dev successfully building a beautiful UI).
*   **The "Hello World" Escaper**: A developer tired of basic AI demos who needs to understand how to handle large files, complex contexts, and production constraints with Agents.

## 3. Core Objectives & KPIs
*   **Zero "Toy Examples"**: Every workflow and code snippet must adhere to production standards (Error handling, Type safety, Scalability).
*   **Reproducibility**: "Cracked Prompts" and workflows must be deterministic and reliable.
*   **Self-Documentation**: The repository structure (`/context`, `/skills`, `/agent`) must implicitly teach the user how to structure their own Agentic projects.
*   **Visual Evidence**: Success is not just compiling code; it is verified visually (screenshots, videos) in the browser.

## 4. Non-Negotiable Constraints (The Rules)
1.  **The Artifact Protocol**: Agents **NEVER** code without a spec. We must produce an artifact (Plan, Markdown Spec) *before* touching source files.
2.  **Context Sovereignty**: Agents do not guess. They must ingest `project_goals.md` and `tech_stack.md` before answering complex queries.
3.  **Senior Standards Enforcement**:
    *   No `any` types.
    *   No `console.log` debugging in finalized code (Use proper Loggers).
    *   No "magic numbers" or hardcoded strings.
4.  **Visual QA Mandatory**: If it's a UI change, the Agent must "look" at it (Browser Tool) to verify pixel-perfect implementation.
5.  **Test-Driven Mental Model**: Define the success criteria (Tests/Specs) *before* generating the implementation code.

## 5. Strategic Implementation Phases
Aligned with `roadmap.md`, the project evolves through these stages:

### Phase 1: The Foundation (Context & Mindset)
*   Establish the "Brain" of the project (`/context` folder).
*   Define the rigorous file structure that helps Agents navigate (`/apps`, `/packages`).
*   **Goal**: A user cloning the repo immediately understands *where* everything is and *why*.

### Phase 2: Tool Mastery
*   Mastery of the IDEs: Cursor & Windsurf.
*   Shortcuts, keybindings, and configuration for maximum speed.
*   Integration of Local LLMs (Ollama) for privacy and cost-efficiency.

### Phase 3: The Workflow Library
*   **The UI Thief**: Methodology for converting screenshots directly into clean Tailwind logic.
*   **Test-Driven Chat**: Using AI to write Jest/Vitest suites to "trap" the logic before implementation.
*   **Console Log Sherlock**: Automated log analysis and root-cause finding.

### Phase 4: Advanced Architectures (God Mode)
*   **MCP (Model Context Protocol)**: Connecting Agents to live infrastructure (Postgres, Docker, Logs).
*   **Autonomous Agents**: Building loops where the agent plans, executes, and verifies its own work.

## 6. Success Criteria
The project is successful when a user can:
1.  Clone the repo.
2.  Read the `README.md` and `context` files.
3.  Immediately start building a complex application using the "Antigravity" workflows with **50-80% less manual typing** than traditional methods.
