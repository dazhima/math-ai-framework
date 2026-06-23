# Framework CHANGELOG

A running log of framework changes. **To bring a stale chat up to speed: paste the latest entry (or say "read `_framework/CHANGELOG.md` and re-read the spec").** Newest first.

---

## 2026-06-14 — Overhaul: dedicated framework project, new module template, slide pipeline

Your loaded context may be stale. Re-read these first (single source of truth; ignore older copies and memory):
- `_framework/FRAMEWORK — operating manual.md` — what's read/activated when; the map
- `_framework/math-framework-spec.md` — format (THE source of truth)
- `_framework/AI-human mathematical collaboration principles.md` — pedagogy
- `_framework/Human principles for AI-assisted mathematical work.md` — human discipline
- Codex: also `_framework/codex.md`

**Changes:**

1. **Framework is its own project, `math/_framework/`** (it used to live inside `RWOT/`). Every project's CLAUDE.md points up to it. Do not restate framework rules in any CLAUDE.md or skill — point to the spec. Humans start at `_framework/USER MANUAL.md`.

2. **New module template** (replaces Phenomenon → Object Picture → Derivation → Proof Experiment → Conclusion → Checkpoints). A module is a **cluster of labelled entries** (a knowledge token), not a single proof:
   - Shape: **Idea → (Setup) → Content → (Conclusion / Checks)**. Only Idea + the entry statements are required; the rest is optional and grows with `status` (a `stub` = Idea + statements only).
   - Content = labelled, addressable entries: `C1` claim, `D1` definition, `E1` example, `A1` application. Cite as `module-id#C1`.
   - Proof lifecycle: working steps are **L-form** (`**L1.** … - [ ] L1`, checkboxed); once understood, naturalize to **R-form** (`*Why:* one line`). The `codex-prompt` skill does this conversion.
   - Retrieval surface for summaries/slides = **Idea + the entry statements**; never parse proofs.
   - Notes already in the OLD template are kept as-is; only NEW notes use this.

3. **New artifact:** `_framework/Heuristics and techniques — a working catalog.md` (transferable "moves"/lenses). Tag a module with `technique:` in frontmatter to link it.

4. **New subproject:** `math/tao-blog/` — a living knowledge base following Terence Tao's blog, feeding the framework.

5. **Slide pipeline rebuilt.** The human authors a proof as **nested bullets** (indentation = resolution depth: depth 0 = Step, 1 = Observation, ≥2 = Explanation; `{result}` = result box; `(∗)` = tag; `$$…$$` = equation box). Then:
   - `add-layout` = cheap preview gate: shows an in-chat widget AND writes `<name>-layout.md` (editable bullets + an auto ASCII wireframe).
   - `md-to-html` = deterministic render via `fouriernew/resolution-render.py` (KaTeX). No design at this step.
   - Old ASCII `[TAG]` layout-authoring is retired. Engine + demo: `fouriernew/resolution-render.py`, `fouriernew/test-resolution.{md,-layout.md,html}`.

Confirm you've re-read the spec before creating or editing any note.
