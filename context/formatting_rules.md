# 🎨 Formatting Rules & Visual Standards

> **Purpose:** This document acts as the "Design System" for our documentation. Since the entire repository functions as a comprehensive README, strict adherence to these formatting rules is critical for readability, navigation, and maintaining the "Premium" aesthetic.

---

## 1. Hierarchy & Structure (The Skeleton)

To ensure clear navigation across the "Masterclass" content, we use a strict heading hierarchy. 

- **`# H1` (File Title)**  
  *Usage:* **ONCE per file**. This is the main title.  
  *Style:* Centered (if possible via HTML) or plain text.  
  *Example:* `# Antigravity Masterclass`

- **`## H2` (Main Sections / Concepts)**  
  *Usage:* The primary divisions of the document. These denote major topic changes.  
  *Style:* Standard Markdown.  
  *Example:* `## 1. Context Sovereignty`

- **`### H3` (Sub-sections / Strategies)**  
  *Usage:* Specific actionable strategies or distinct parts of a concept.  
  *Style:* Standard Markdown.  
  *Example:* `### The "Context First" Strategy`

- **`#### H4` (Detailed Steps / Components)**  
  *Usage:* Breaking down a strategy into granular steps.  
  *Style:* Standard Markdown.  
  *Example:* `#### Step 1: Create the file`

- **`**Bold**` (Key Concepts)**  
  *Usage:* Highlight "Defined Terms" or "Cracked" vocabulary when first introduced.  
  *Example:* "This is known as **Context Sovereignty**."

---

## 2. Alerts & Callouts (The Attention Grabbers)

We use **GitHub Flavored Markdown** alerts to control the reader's flow and highlight critical information.

### Usage Guide

- **`> [!NOTE]`**  
  *Use for:* Background context, "good to know" info, or sidebars that aren't critical to the immediate action.

- **`> [!TIP]`**  
  *Use for:* "Cracked" hacks, optimization secrets, or shortcuts. **This is where the high-value alpha goes.**

- **`> [!IMPORTANT]`**  
  *Use for:* Core rules and non-negotiable protocols. (e.g., "Always verify before running").

- **`> [!WARNING]`**  
  *Use for:* Common pitfalls, errors to avoid, or things that will break the agent.

- **`> [!CAUTION]`**  
  *Use for:* Destructive actions or dangerous operations.

---

## 3. The "Cracked" Components (Prompts & Examples)

We separate instruction from execution carefully.

### A. Prompts
Prompts must be distinct and copy-paste friendly. Use a labeled code block or a specific blockquote style.

**Format:**
```markdown
### 🧠 The Prompt
> **Copy this:**  
> "Act as a Senior Engineer... [Prompt Content]"
```

### B. Examples (Code & Config)
Always specify the language syntax highlighting.

**Format:**
```markdown
### 📝 Example: `.cursorrules`
```json
{
  "context": "strict"
}
```
```

---

## 4. Visual Enriched Elements

### A. File Trees
Use `ASCII` or standard tree format to show directory structure. This is crucial for "Context" explanations.

```text
root/
├── .cursor/
│   └── rules/           # Where the magic happens
├── context/             # The brain
└── README.md            # The face
```

### B. Badges (Shields.io)
Use badges under H1 titles to denote status or tech stack.

`![Status](https://img.shields.io/badge/Status-Active-success)`

### C. Tables
Use tables instead of lists when comparing 3+ items with attributes.

| Feature | Description | Importance |
| :--- | :--- | :--- |
| **Context** | The file awareness | High |
| **Rules** | The instruction set | Critical |

### D. Collapsible details
Use `<details>` and `<summary>` for large blocks of reference text or logs to keep the page clean.

```html
<details>
<summary>View Full Logs</summary>

Line 1...
Line 2...

</details>
```

---

## 5. Navigation Constraints

- **Relative Links Only:** Always link using relative paths (`../context/file.md`) so the repo works offline/cloned.
- **Explicit File References:** When mentioning a file in text, format it as code: `formatting_rules.md`.

---
*Follow these rules to ensure the "Antigravity Masterclass" remains a premium, high-signal resource.*
