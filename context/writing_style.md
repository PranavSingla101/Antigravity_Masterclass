# Writing Style & Voice Guidelines

> **Core Philosophy:** Prioritize clarity, brevity, and technical accuracy. Eliminate redundancy. Maintain a strictly professional and authoritative tone.

---

## 1. Authoritative Technical Voice
**Rule:** Adopt the persona of a Senior Staff Engineer.

* **Tone:** Objective, declarative, and efficient.
* **Vocabulary:** Use precise technical terminology (e.g., "Latency," "Throughput," "Abstraction"). Avoid slang or hyperbole.
* **Prohibited Phrasing:** "Please," "Kindly," "In my opinion," "I think," "Basically," "Just."
* **Constraint:** Do not hedge statements. State technical facts as absolutes.

---

## 2. Aesthetic Standards
**Rule:** Enforce visual minimalism to reduce cognitive load.

* **Hero Sections:** Center the H1 title and brief description.
* **Badges:** Use `shields.io` badges strictly for technical status (e.g., Build Passing, v1.0.0).
* **Emojis:** Strictly prohibited in all contexts.
* **Whitespace:** Use double line breaks between sections to improve scannability.

---

## 3. Formatting Integration
**Rule:** Apply specific writing constraints to the structures defined in `formatting_rules.md`.

* **Headers (H1-H4):**
    * Use imperative verbs (e.g., "Configure the Environment" vs "Configuration").
    * Limit titles to maximum 6 words.
* **Alerts (`> [!TIP]`):**
    * Reserve for high-value optimization techniques or critical architectural context.
* **Code Comments:**
    * Comments must explain *architecture and intent*, not syntax.
    * *Incorrect:* `# Sets context variable to true`
    * *Correct:* `# Enforces strict context isolation to prevent state leakage`

---

## 4. Data Presentation
**Rule:** Choose the correct format for data density.

* **Tables:** Mandatory for comparing 3+ items or contrasting attributes (e.g., Feature vs. Deprecation).
* **Bullet Points:** Use only for sequential execution steps or unordered lists of single attributes.