# Framework — Operating Manual

> The front door to your own framework. If you ever wonder *"what is actually read, activated, or used when I work?"* — this file answers it. It defines nothing itself; it **maps** where everything lives and how the pieces fire.

---

## 1. The model in one paragraph

Your vault is a **codebase of understanding**. Each note is a module in a dependency graph. You, Claude, and Codex collaborate on it: you own taste, direction, and the first attempt; Claude is the local reasoning engine and blackbox-eliminator; Codex is repository infrastructure (extraction, indexing, graph upkeep). Three concerns govern the work — *format*, *pedagogy*, *human discipline* — and each has exactly one source of truth.

---

## 2. The four sources of truth (one per concern)

| Concern | Single source of truth | Role |
|---|---|---|
| **Format** — naming, frontmatter, templates, annotations, statuses, CLAUDE.md rules | `math-framework-spec.md` | everything points here |
| **Pedagogy** — how Claude explains, writes notes, discusses proofs | `AI-human mathematical collaboration principles.md` | Claude-facing master |
| **Human discipline** — how *you* use Claude without eroding your own faculties | `Human principles for AI-assisted mathematical work.md` | human-facing master |
| **Orientation** — what's read/activated, how to use it all | `FRAMEWORK — operating manual.md` (this file) | the map |

Everything else is either a *pointer* to one of these, a *skill* (an operation), or *local project state* (a CLAUDE.md). Nothing else should restate format or principles.

---

## 3. What is read automatically, and when  ← the transparency answer

**At the start of a Claude session:** Claude automatically sees the **CLAUDE.md** of whatever folder(s) you're working in. That's the only thing loaded by default. Everything else enters the session through one of two doors:

1. **A skill fires** (because your request matches its description — see §4), pulling in whatever that skill references.
2. **The CLAUDE.md tells Claude to** read a specific file.

This is the key fact people miss: **your principles docs are NOT loaded just because they exist.** They reach a session only if (a) the project CLAUDE.md points to them, or (b) a skill that references them fires. So:

- Pedagogy is active when `math-research-framework` or `math-human-discipline` fires, *or* when CLAUDE.md says so.
- Your RWOT CLAUDE.md hard-wires this with: *"the math-human-discipline skill is always active."* That line is what makes the discipline reliably present — without it, you'd be depending on the skill description happening to match.

**At the start of a Codex session:** Codex follows the startup routine in `codex.md` — it reads `CLAUDE.md`, `AGENTS.md`, `math-framework-spec.md`, `math-framework-human.md`, then nearby notes. (Codex does not see Claude's skills; `codex.md` is its equivalent instruction set.)

**Rule of thumb:** if you want something present in every session of a project, name it in that project's CLAUDE.md. Existence ≠ activation.

---

## 4. The skills — trigger / reads / produces

A skill becomes active when your phrasing matches its `description` (Claude recognizes the match and loads the skill's instructions). That description is the *only* trigger. You can read or edit any skill's description in **Settings → Capabilities**.

| Skill | Fires when you say… | Reads | Produces |
|---|---|---|---|
| `math-research-framework` | "write/edit a note", create any math doc | `math-framework-spec.md` | a note in canonical format |
| `math-human-discipline` | (standing) any math session | `Human principles…` | the 3-level discipline (attempt-first, gap-location, passive-session checks) |
| `math-interview` | "quiz me", "interview me", "test me" | the session so far | a structured Q&A |
| `sketch-proof` | "sketch this proof", "compress to implications" | the proof you give it | a terse `(A) ⟹ (B)` chain |
| `codex-prompt` | "send this to Codex", "write a Codex prompt" | the target note files | a paste-ready Codex prompt |
| `subproject-init` | "make X a subproject" | current CLAUDE.md + related files | subfolder + lean local CLAUDE.md + redirects |
| `add-layout` | "add layout", "make the layout file" | raw slide `.md` | `-layout.md` + a wireframe preview |
| `md-to-html` | "generate the HTML/slides" | layout `.md` | a self-contained HTML deck |

Two activation gotchas: (1) if two skills could match, the closest description wins — phrase requests toward the one you want; (2) "standing" skills (`math-research-framework`, `math-human-discipline`) are meant to be always-on, which is why they should be **declared in CLAUDE.md**, not left to chance matching.

---

## 5. How to use it properly — the operating loop

Skills are atomic on purpose. You get power by **composing** them for recurring jobs. The standard recipes:

- **Study a paper** → `math-human-discipline` (standing) → for each blackbox, write a `module` per `math-framework-spec` → `math-interview` to test retention → when a blackbox grows large, `subproject-init`.
- **Build background to a theorem** → top-down: write the `theorem` node first (Statement + Idea of Proof), then spawn the `module` children its proof depends on.
- **Prepare a talk / make a deck** → `sketch-proof` (compress each proof) → `add-layout` → `md-to-html`.
- **Offload grunt work** → `codex-prompt` (naturalizing checked steps, bulk frontmatter linking, PDF extraction).
- **Prepare for a conference** → the Talk-Prep Workout (see `../talks/.../00 — Talk-Prep Workout.md`) — itself a worked example of composing framework + interview + sketch-proof + codex-prompt.

Per-session hygiene (from the human principles): enter with a stated goal and a partial attempt; signal confusion immediately; end by stating the key idea in one sentence without notation.

---

## 6. Consolidation ledger — current files → role going forward

**Executed 2026-06-13.** The framework now lives in its own project, `_framework/` (this folder) at the vault root; every research project points up to it. What each file became:

| File | Was | Now |
|---|---|---|
| `math-framework-spec.md` | format, partial | **canonical — format SoT** (now upgraded: doc types, templates, statuses) |
| `AI-human mathematical collaboration principles.md` | pedagogy master | **canonical — keep as is** |
| `Human principles for AI-assisted mathematical work.md` | human master | **canonical — keep as is** |
| `FRAMEWORK — operating manual.md` | — | **canonical — this map** |
| `math-framework-human.md` | essay restating format+philosophy | **keep as a human-readable intro**, but add a header pointing to spec + principles as authoritative |
| `agents_md_for_modulized_math_research.md` | full restatement of philosophy + format | **trim to a pointer** to spec + principles + codex.md (it currently duplicates all three) |
| `codex.md` | Codex instructions, restates format | **keep** (Codex needs its own entry point) but **replace its format section with a pointer** to `math-framework-spec.md` |
| `AGENTS.md` (RWOT) | near-duplicate of CLAUDE.md (progress log) | **pick one as SoT.** Suggest: CLAUDE.md = Claude's, AGENTS.md = one-line pointer to it (or vice-versa). They will drift if both are kept full. |
| `RWOT/CLAUDE.md` | embeds full note template + 10 principles + quick reference | **trim**: replace the embedded *note template* and *principles* with pointers; **keep** the project-specific *Mathematical Quick Reference* (that's legitimate local content) |
| `math-research-framework` SKILL.md (+ other skills) | restate frontmatter/template | **edit in Settings → Capabilities**: shrink to "trigger + unique behavior + follow `math-framework-spec.md`". *(Skills are a read-only cache here; only you can edit them in Settings.)* |

**Structural fix (done):** these docs used to live inside `RWOT/` — a single project hosting global infrastructure. They now live in `_framework/` at the vault root, so RWOT, fouriernew, and the talks subprojects all point to one copy. RWOT is once again purely a research project.

**Remaining (your hand):** (1) the skills still restate format — shrink each SKILL.md in Settings → Capabilities to "trigger + unique behavior + follow `math-framework-spec.md`" (paste-text provided separately); (2) reconcile the divergent BP08 block flagged at the bottom of `RWOT/AGENTS.md` into `RWOT/CLAUDE.md`, then delete it.

---

## 7. Health rules (keep it consistent over time)

- **One concern, one file.** Format → spec. Pedagogy → AI principles. Discipline → human principles. If you see any of these restated elsewhere, replace with a pointer.
- **Existence ≠ activation.** To guarantee something is used in a project, declare it in that project's CLAUDE.md.
- **CLAUDE.md stays lean.** Pointer + skills + local status + (optional) project math reference. No framework boilerplate.
- **Edit triggers, not behavior, to fix activation.** If the wrong skill keeps firing, adjust its description in Settings → Capabilities.
