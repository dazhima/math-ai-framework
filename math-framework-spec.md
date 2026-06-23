# Math Research Framework — System Spec

> **This file is the single source of truth for the *format* of the framework.**
> Naming, frontmatter, document templates, annotations, statuses, and CLAUDE.md rules are defined here and **nowhere else**. Skills and CLAUDE.md files should *point to this file*, not restate it. If you find these rules duplicated elsewhere, replace the duplicate with a pointer.
>
> Companion sources of truth (do not duplicate either):
> - *Why* the framework exists / how Claude should explain & write → `AI-human mathematical collaboration principles.md`
> - *How you (the human) should use Claude* → `Human principles for AI-assisted mathematical work.md`
> - *What gets read/activated when, and how to use it all* → `FRAMEWORK — operating manual.md`

---

## Core Idea

Documents form a **relative tree**. Every document has a parent and may have children. No absolute root. A document is always "a document over its parent." Any subtree can be promoted to its own self-contained subproject (see `subproject-init`).

The repository is a **codebase of understanding**: files are modules, dependencies are real, unresolved steps are real state. Research advances by **blackbox elimination** — recursively decomposing any result you can quote but not yet locally reconstruct.

---

## Two Document Types

| Type | Purpose | Body template |
|---|---|---|
| **module** | one mathematical unit; a cluster of labelled entries, addressed as one knowledge token | **Idea → (Setup) → Content (entries) → (Conclusion/Checks)** — only Idea + statements required; see template |
| **theorem** | assembled from modules; shows how they combine | Motivation → Statement → Idea of Proof → Proof |

`type:` is a frontmatter field (below). Choose `module` for understanding units, `theorem` for assembly nodes.

---

## File Naming

`[Source] — [Mathematical content].md`

- Source = paper citation: `BP08`, `B2`, `GZ-Ch7`, `HTW-Sec5`.
- Subproject master: drop the source, name by goal.
- Separator: em-dash ` — ` with spaces on both sides.
- Filenames encode **content only** — never hierarchy, status, or role (those live in metadata).

```
B2 — curvature computation.md
BP08-Lem2.3 — holomorphic lift.md
HTW-Sec5 — Second Main Theorem.md   ← a theorem document
```

---

## Frontmatter (every document, no exceptions)

```yaml
---
id: kebab-case-id
type: module | theorem
title: Full descriptive title
status: stub | in-progress | understood
parent: relative/path/or/id-of-parent
children:
  - child-id
depends_on:
  - logical-prerequisite-id
used_by:
  - downstream-id
---
```

- `parent` / `children` = **tree position**.
- `depends_on` / `used_by` = **logical flow** (may cross tree boundaries).
- `status`: `stub` (not started) · `in-progress` (being worked) · `understood` (reconstructible *at time of writing* — provisional, per the human principles).

---

## Module Body Template

**Who reads this.** The primary reader is the **math agent**, repeatedly — the human reads it roughly once. A module is the agent's *token space*: a unit of mathematical knowledge, addressed as one token but holding internal structure. Optimize for signal-per-token, not prose.

**A module is a cluster, not a proof.** Its body is a list of **labelled, addressable entries** — definitions, claims, constructions, examples, applications — each *optionally* carrying its own proof. A single-theorem note is just the degenerate case (one entry with its proof).

**Shape: Idea → (Setup) → Content → (Conclusion / Checks).** Only Idea and the entry statements are required; the rest is optional and the note *grows with `status`*: a `stub` is **Idea + statements** (quoted, proofs postponed — blackboxes to eliminate); reconstructing a blackbox attaches its proof.

```markdown
---
[frontmatter]
technique: [optional tags → ../Heuristics and techniques — a working catalog.md]
---

# Title

## Idea
[What this knowledge unit is, why it's one coherent token, the moral gist.
1–3 sentences. Top retrieval surface — read before any formal statement.]

## Setup            ← optional: notation / definitions (+ a symbol table if many)

## Content          ← the heart: labelled, addressable entries (cite as C1, D1, E1, …)
**D1 (def).** [definition].
**C1.** [statement].
   *Why:* [one-line naturalized justification — the "understood" R-form].
**C2.** [statement].                       ← proof still being worked? use L-form:
   **L1.** [step] — [ ] L1
   **L2.** [step] — [ ] L2
**E1 (example).** [toy / limiting / special case].
**A1 (application).** [how it's used downstream / in the project].

## Conclusion       ← optional: self-contained summary blockquote (bottom retrieval surface)

## Checks / Connections / Postponed   ← all optional
```

**Entry kinds** are open: `C` claim, `D` definition, `E` example, `A` application, plus constructions/remarks as needed. Label them so other notes (or entries) can cite `module-id#C1`.

**Proof lifecycle.** An entry's proof starts as checkboxed **L-form** (`**L1.** … — [ ] L1`, being verified) and is *naturalized* to the compact **R-form** (`*Why:* one line`) once understood — the `codex-prompt` skill does this conversion. The `*Why:*` line carries the local heuristic-and-justification; the module-level **Idea** carries the global one. Together they are the "post-rigorous" twinning (`AI-human mathematical collaboration principles.md`) with no heavy per-step section.

**When a module sprawls** into many sub-topics (e.g. "Module 1 … Module 10"), that's the signal to promote it to a **subproject** (`subproject-init`). A pure index / "reading plan" note is a *main-process note*, not this template.

---

## Theorem Body Template

Four sections only. No Idea/Checks parts — a theorem is assembly; the modules carry the intuition.

```markdown
## Motivation     ← what it's about and why it exists (not the formal statement)
## Statement      ← the formal statement, all notation defined
## Idea of Proof  ← the insight that makes the proof inevitable; a reader who gets this is surprised by no step below
## Proof
*Step 1.* [content] → *[module-id]*
*Step 2.* [content] → *[module-id]*
∎
```

`depends_on` lists the modules whose results the proof uses.

---

## Annotation System

The human annotates each L-step after reading:

```
- [x] L3  √              ← understood
- [x] L5  ? // why X?    ← unclear, with a specific comment
```

When you see `?` on a line: expand **that line only**. Do not re-explain the whole document.
Never silently delete `?`, TODOs, or uncertainty markers — they are first-class state.

---

## AI-Readable Summary Surface

To summarize, build slides, or outline a project, read **only**:
- the **Idea** + the entry statements (and `status`) for modules, or
- the **Motivation** + **Statement** for theorems.

These are the top of every note by design — the agent's retrieval surface. Do **not** parse Proof bodies for summaries.

---

## CLAUDE.md (one per folder)

Contains exactly **three things**, ≤ ~40 lines of framework content:

1. `parent: ../CLAUDE.md`
2. Skill declarations — only skills relevant to this folder's work.
3. Lean local context: goal + current status + document tree.

Project-specific *mathematical* content (e.g. a sign/convention quick-reference) is allowed and exempt from the 40-line guide — but framework rules (this spec, the templates, the principles) must be **pointers, not copies**. If a CLAUDE.md restates the note template or the principles, trim it to a pointer.

---

## Skills (operations governed by this spec)

Each skill's own SKILL.md should state its trigger + unique behavior and then defer to this spec for format. See `FRAMEWORK — operating manual.md` for the full activation table.

- **`math-research-framework`** — standing rule. Apply when creating/editing any math document. Enforces this spec.
- **`subproject-init`** — operation. Trigger: "make X a subproject." Promotes a subtree to its own folder + lean CLAUDE.md, leaving wikilink redirects behind.
- **`codex-prompt`** — operation. Trigger: "send to Codex." Generates a paste-ready Codex prompt.
- **`sketch-proof`**, **`add-layout`**, **`md-to-html`** — presentation pipeline (raw proof → implication chain → laid-out slides → HTML).
- **`math-interview`** — trigger: "quiz me." Tests reconstruction.
- **`math-human-discipline`** — standing rule during any math session. Enforces `Human principles for AI-assisted mathematical work.md`.
