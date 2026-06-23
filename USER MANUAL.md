# User Manual — the math research framework

*For Yan. The practical how-to: open this when you want to **do** something. It points to the authoritative docs rather than restating them.*

- Want the rules? → `math-framework-spec.md` (format) · `AI-human mathematical collaboration principles.md` (pedagogy) · `Human principles for AI-assisted mathematical work.md` (your discipline).
- Want the technical map (what's read/activated when, full skill table)? → `FRAMEWORK — operating manual.md`.
- Want to **work**? → you're in the right file.

---

## 1. The idea in one sentence

Your vault is a **codebase of understanding**: each note is a module in a dependency graph, you advance by *eliminating blackboxes* (decomposing anything you can quote but not yet reconstruct), and every project is "a project over the shared framework in `_framework/`."

## 2. The layout you actually need to remember

```
math/
├── _framework/        ← the rules (this folder). You rarely edit these.
├── RWOT/, fouriernew/, convex-geometry/, talks/, review/ …  ← your projects
└── CLAUDE.md          ← vault root; points down to projects, up to nothing
```

Each project has a `CLAUDE.md` = `parent:` line + `skills:` line + `framework:` pointer + lean local status. Nothing more. Each note is a `.md` module/theorem following the spec.

---

## 3. How to do the common things ("I want to…")

Each task is triggered by **saying the phrase to Claude** — that's what fires the right skill.

### …start working in a project
Just open a Claude session in that folder. Claude auto-reads its `CLAUDE.md`. If you want pedagogy/discipline on from the first message, the CLAUDE.md must declare the skills (RWOT does: "math-human-discipline always active"). *Existence ≠ activation.*

### …understand a paper / kill a blackbox  → write a module
Say: *"write a note on [topic]"* or *"let's make a module for [result]."*
What happens: the `math-research-framework` skill fires → asks the **Step 0 questionnaire** (5 quick questions to calibrate) → builds a `type: module` note per the spec (Idea → labelled entries (Content) → optional Conclusion/Checks; grows with status).
Your job: answer Step 0 honestly, and *attempt the L-steps yourself before reading them.*

### …record a result assembled from modules  → write a theorem
Say: *"write the theorem note for [X]."*
You get a `type: theorem` note: Motivation → Statement → **Idea of Proof** → Proof (each step → a module id). The modules carry the intuition; the theorem just assembles them.

### …tell Claude exactly what you don't understand
In the note, mark the L-step: `- [x] L5  ? // why does the product rule apply here?`
Then say *"L5."* Claude expands **only that step** — not the whole note. Mark understood steps `√`. Never delete a `?` you haven't resolved.

### …split something that got too big  → subproject
Say: *"make [X] a subproject."*
The `subproject-init` skill creates `X/`, moves the related files (leaving `[[wikilink]]` redirects so nothing breaks), writes a lean `X/CLAUDE.md` (parent pointer + relevant skills), and points the parent at it.

### …test whether it actually stuck
Say: *"quiz me"* / *"interview me on [topic]."*
The `math-interview` skill runs a mixed Socratic/MCQ/open review. Use it the day after, and again a few days later — that gap is the real retention test.

### …make a talk or slides
Pipeline: *"sketch this proof"* (`sketch-proof` → terse `(A)⟹(B)` chain) → write raw slide markdown → *"add layout"* (`add-layout` → wireframe) → *"generate the HTML"* (`md-to-html` → deck). View HTML at 150% zoom; print to A4 landscape PDF.

### …offload grunt work to Codex
Say: *"send this to Codex"* / *"write a Codex prompt to naturalize these steps."*
`codex-prompt` produces a paste-ready prompt. Codex is for infrastructure (extraction, indexing, bulk linking, consistency) — not for the mathematical reasoning, which stays with you + Claude.

### …prepare for a conference
Use the Talk-Prep Workout (`talks/…/00 — Talk-Prep Workout.md`) — a worked recipe composing several skills. Front door is its `03 — Tracker.md`.

---

## 4. How to run a session (the 4 habits that matter most)

From `Human principles for AI-assisted mathematical work.md` — the short version:

1. **Enter with a goal and a partial attempt.** "I want to see why Y follows from Z," not "let's continue." A half-formed attempt beats a question.
2. **Attempt before asking** when you have the tools. Ask Claude to *check*, not *produce*. (Claude will gently push back if you skip this — that's the `math-human-discipline` skill, not an accident.)
3. **Signal confusion immediately** with a `?`. Don't let false clarity compound.
4. **End with one sentence, no notation.** If you can't state today's key idea cleanly, the work isn't done yet.

The deeper trap list (explanation / verification / coverage / assent traps) is in §9 of the human principles doc.

---

## 5. How activation works (the 3 facts that remove the mystery)

1. **At session start, Claude auto-reads only the project's `CLAUDE.md`.** Everything else loads via a skill firing or a pointer in that CLAUDE.md.
2. **A skill fires when your wording matches its `description`** — nothing else triggers it. Standing skills (`math-research-framework`, `math-human-discipline`) should be *declared in CLAUDE.md* so they don't depend on phrasing.
3. **Principles/spec are not auto-loaded.** They enter a session through a skill that references them, or a CLAUDE.md pointer.

Full read-order and the skill trigger/reads/produces table: `FRAMEWORK — operating manual.md` §3–§4.

---

## 6. Troubleshooting

| Symptom | Cause | Fix |
|---|---|---|
| Claude wrote a note in the wrong format | the framework skill didn't fire | say "follow the framework" / check the project CLAUDE.md declares `math-research-framework` |
| Pedagogy/discipline absent | not declared, phrasing didn't match | add the skill to the project CLAUDE.md (as RWOT does) |
| Wrong skill keeps firing | description overlap | edit the skill's `description` in Settings → Capabilities (not its body) |
| A rule feels duplicated across files | drift starting | delete the copy, leave a pointer — one concern, one file |
| A link broke after moving a file | explicit path reference | move with a `[[wikilink]]` redirect, or update the path |
| Edited a skill but nothing changed | edited the body, not the trigger | the `description` controls firing; the body controls behavior |

---

## 7. Quick reference card

**Frontmatter (every note):**
```yaml
id: kebab-case
type: module | theorem
title: Full title
status: stub | in-progress | understood
parent: ../CLAUDE.md      # or parent id
depends_on: [ids]         # logical prereqs (may cross the tree)
used_by: [ids]
```

**Statuses:** `stub` (untouched) · `in-progress` (working) · `understood` (reconstructible *now* — provisional).

**Annotations:** `√` understood · `? // comment` unclear here · never delete an open `?`.

**Naming:** `[Source] — [content].md` with the em-dash ` — ` (subproject master: drop the source).

**Read only these for summaries/slides:** module `Goal` + `Conclusion`; theorem `Motivation` + `Statement`. Never parse derivations.

**Trigger phrases:** "write a note/module" · "write the theorem note" · "L5" (expand a step) · "make X a subproject" · "quiz me" · "sketch this proof" · "add layout" · "generate the HTML" · "send to Codex".
