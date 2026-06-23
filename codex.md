# codex.md — Codex instruction set

This is Codex's entry point for the math research vault (the Codex equivalent of CLAUDE.md). It is **global**: project-specific orientation lives in each project's own `CLAUDE.md` / `AGENTS.md`, which you read at startup.

## Purpose

Treat the vault as a **codebase of understanding**: files are modules, dependencies matter, unresolved steps are real state, refactors must preserve the mathematical graph. Your role is repository infrastructure — extraction, indexing, dependency-graph upkeep, consistency checks, restructuring — not replacing mathematical reasoning (that is the human + Claude).

## Startup routine

Before editing or reorganizing, read, in order:
1. The local `CLAUDE.md` (and `AGENTS.md` if present) of the project you're working in.
2. `_framework/math-framework-spec.md` — the note format (do not re-derive it).
3. `_framework/FRAMEWORK — operating manual.md` — how the system fits together.
4. Nearby modular notes relevant to the task.

## Format → spec (do not restate)

Naming, frontmatter, the module/theorem templates, the L-step annotation system (`√` / `?` / `//`), and CLAUDE.md rules are all defined in `_framework/math-framework-spec.md`. Follow that file exactly. When editing notes: preserve frontmatter and L-numbering, keep `Goal`/`Conclusion` synced with the body, never silently delete `?` / TODO / uncertainty markers, prefer small local changes over broad rewrites, and update `status` only when the mathematical state truly changed.

## Core operations

**Blackbox elimination.** A blackbox is a result that can be quoted but not locally reconstructed. Help by decomposing it into smaller modules, identifying missing prerequisites, extracting lemmas/computations into their own notes, and linking dependencies explicitly. Use cautious language: distinguish proved / assumed / quoted / unclear. Never mark unresolved mathematics as understood.

**Main process notes.** Each project may have a central orchestration note tracking the global reduction flow and pointing to subprojects. Keep it lean and navigational; put proof details in local modules.

**Subprojects.** When asked to "make X a subproject," follow the sequence in `math-framework-spec.md` (§ Skills → `subproject-init`): create the subfolder, migrate related files with wikilink redirects left behind, generate a lean local `CLAUDE.md` (parent pointer + relevant skills + lean status), and update the parent with a compact pointer. Inherit only necessary context.
