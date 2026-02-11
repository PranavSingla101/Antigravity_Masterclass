# Formatting Rules & Visual Standards

> **System Goal:** Maintain a "Premium" aesthetic with strict adherence to GitHub Flavored Markdown (GFM). These rules govern readability, navigation, and structure.

---

## 1. Hierarchy & Structure
**Rule:** Use a strict heading hierarchy to create a scannable "skeleton" for the document.

* **`# H1` (File Title)**
    * **Usage:** Exactly **ONCE** per file at the very top.
    * **Format:** `# Title Name`

* **`## H2` (Main Sections)**
    * **Usage:** Denotes major topic changes or distinct modules.
    * **Format:** `## 1. Section Name`

* **`### H3` (Sub-sections)**
    * **Usage:** Specific strategies, actionable steps, or distinct parts of a concept.
    * **Format:** `### The Strategy Name`

* **`#### H4` (Granular Steps)**
    * **Usage:** Breaking down a complex instruction into parts.
    * **Format:** `#### Step 1: Action`

* **`**Bold**` (Key Terms)**
    * **Usage:** Use only for "Defined Terms" or new vocabulary when first introduced.

---

## 2. Alerts & Callouts (GFM)
**Rule:** Use standard GitHub Alerts to control flow. Do not use generic blockquotes for warnings.

> [!NOTE]
> Useful background info or sidebars.

> [!TIP]
> "Cracked" hacks, optimization secrets, or shortcuts.

> [!IMPORTANT]
> Core rules and non-negotiable standards.

> [!WARNING]
> Common errors or things that break the agent.

> [!CAUTION]
> Dangerous operations (e.g., deleting files, payment issues).

---

## 3. Code & Prompts
**Rule:** Separate instruction from execution. Always use syntax highlighting.

### A. Prompts
Use a labeled blockquote or specific code block to distinguish prompts from regular text.

**Format:**
```markdown
### 🧠 The Prompt
> **Copy this:** > "Act as a Senior Engineer... [Prompt Content]"
```

### B. Code Blocks
Always specify the language identifier (json, python, bash, markdown) for syntax highlighting.

**Format:**
```json
{
  "context": "strict",
  "optimization": true
}
```

---

## 4. Visual Elements
**Rule:** Prioritize visual density over walls of text.

### A. File Trees
Use `ASCII` format to show directory structure.

```text
root/
├── .cursor/
│   └── rules/           # Active rules
├── context/             # Knowledge base
└── README.md            # Entry point
```

### B. Tables
Use tables for comparing 3+ items with attributes.

| Feature | Description | Priority |
| :--- | :--- | :--- |
| **Context** | File awareness | High |
| **Rules** | Instruction set | Critical |

### C. Collapsible Details
Use HTML `<details>` tags for long logs, reference lists, or boilerplate code to keep the UI clean.

```html
<details>
<summary>Click to View Full Logs</summary>

[Log data here...]

</details>
```

---

## 5. Navigation & Links
**Rule:** Ensure the repo functions offline/cloned.

* **Relative Links:** Always use relative paths (e.g., `../context/file.md`), never absolute URLs for internal files.
* **File References:** When mentioning a filename in a sentence, format as inline code: `formatting_rules.md`.