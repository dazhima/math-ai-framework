# A Framework for AI-Assisted Mathematical Research

*Yan He — June 2026*

---

Most mathematicians I know have almost no engagement with AI. This is understandable. The public conversation about AI and mathematics oscillates between two poles that are both unserious: AI that will "solve all of mathematics" within the decade, and AI as autocomplete that produces plausible-sounding nonsense. Neither pole invites a working mathematician to think carefully about what these tools are actually good for.

This document describes a practical framework I have developed over the course of research in several complex variables and algebraic geometry. It is not a manifesto. It is a working system — a set of conventions, document structures, and collaboration principles — designed to make AI genuinely useful for mathematical research without sacrificing the things that make mathematical work meaningful.

---

## The core problem

Mathematical understanding is not the ability to follow a proof. Kodaira calls the deeper thing 数感 — "mathematical sense" — a perceptual faculty that allows a person to *see* mathematical phenomena with something close to directness. An AI can produce a logically correct explanation; it cannot tell whether you have grasped the mathematical fact the explanation is trying to express. These are not the same thing, and the gap between them is where most AI-assisted mathematical work goes wrong.

The second problem is structural. Mathematical background is never flat. Understanding a single citation in a paper may require understanding several earlier results, each with further prerequisites. The natural structure is a directed graph of mathematical facts with explicit dependencies. Yet standard note-taking systems treat documents as an unstructured collection, leaving this dependency graph implicit and inaccessible — to an AI, and often to the mathematician as well.

This framework addresses both problems.

---

## The setup in one sentence

You keep a **math vault in Obsidian**. The framework lives inside it as a folder called `_framework/`. Each research project (a paper you are writing, a topic you are studying, a course you are teaching) is a subfolder of the vault. When you open Claude in a project folder, it reads the project's configuration, finds the framework, and knows how to work with you.

```
your-math-vault/
├── _framework/          ← this repository
├── my-paper/
│   ├── CLAUDE.md        ← project config (5 lines)
│   └── notes…
├── fourier-analysis/
│   ├── CLAUDE.md
│   └── notes…
└── …
```

This is the only infrastructure. There is no server, no plugin, no pipeline to set up.

---

## How to start

**Prerequisites:** [Obsidian](https://obsidian.md) (for the vault) and [Claude](https://claude.ai/download) (desktop app with Claude Code).

**Step 1.** Clone this repository into your Obsidian math vault:
```
cd your-math-vault
git clone https://github.com/dazhima/math-ai-framework _framework
```

**Step 2.** Create a folder for your project and put a `CLAUDE.md` in it:
```markdown
# CLAUDE.md

parent: ../_framework/CLAUDE.md
skills: math-research-framework, math-human-discipline

## Goal
[One sentence: what this project is about.]

## Status
[What you are currently working on.]
```

**Step 3.** Open Claude in that project folder and start working. Say *"write a module on [topic]"* or *"let's work through [theorem]"*. Claude reads the configuration, activates the framework, and the session begins.

That is all. The principles, the note format, the pedagogy, and the human discipline are loaded automatically. You do not configure them; you just work.

---

## What the framework actually does

**A modular note system with explicit dependencies.** Every mathematical fact — a lemma, a computation, a definition — lives in its own file. Every file has machine-readable metadata encoding its position in the dependency tree: what it depends on, what depends on it, and where it sits relative to its parent context. The mathematical knowledge base becomes a codebase of understanding: modules, dependencies, and explicit state.

Research advances by **eliminating blackboxes**: any result you can quote but not yet reconstruct is a stub. Making it understood means working through it step by step until you can rebuild it independently. The notes track this state explicitly.

**A discipline for the human side.** The framework is not just a note format — it is a set of principles for how to use AI without letting it do the work that builds mathematical sense. The short version: attempt before asking, signal confusion precisely, never mistake a fluent explanation for genuine understanding.

**A protocol for precise human-AI dialogue.** Every numbered step in a derivation carries a checkbox. When something is unclear, you annotate the specific step with a `?` and a comment. The AI responds to exactly that step — not the whole argument. This granularity matches the natural granularity of mathematical reasoning.

**Collaboration principles for the AI.** The principles document tells Claude what mathematical collaboration actually requires: phenomena before formalism, global picture before local decomposition, proof as thought experiment rather than logical transcript, active diagnosis of understanding versus mere assent.

---

## The note format

Each note has two parts: **frontmatter** and **body**.

The frontmatter encodes position in the knowledge graph:

```yaml
---
id: curvature-computation
type: module
title: Curvature computation for the direct image bundle
status: in-progress
parent: ../CLAUDE.md
depends_on: [chern-connection, direct-image-bundle]
used_by: [nakano-positivity]
---
```

The body follows a fixed shape: **Idea → Setup → Content → Conclusion**. The *Idea* states what the note is about in one to three sentences, before any formalism. The *Content* is a list of labelled, addressable entries — definitions, claims, examples — each with its own compact justification. The *Conclusion* is a self-contained summary that can be read in isolation.

A note starts as a `stub` — the claim is stated, the proof is a blackbox. Understanding the mathematics means eliminating blackboxes: working through the steps, annotating confusion, rebuilding. A `stub` becomes `in-progress` becomes `understood`.

---

## The annotation system

Every numbered step in a proof carries a checkbox:

```
**L1.** The operator T commutes with the Laplacian.   — [ ] L1
**L2.** Therefore the spectrum of T is preserved.      — [ ] L2
**L3.** This forces the eigenvalue to be zero.         — [ ] L3
```

After working through the argument, you annotate:

```
— [x] L1  √
— [x] L2  ? // I don't see why commutativity forces spectrum preservation
— [x] L3
```

You say "L2" to Claude. It expands exactly that step. It does not re-explain the entire argument. When you have understood a step and can reconstruct it independently, the checkbox form is replaced by a single naturalized line — the step becomes background.

This is the mechanism by which a blackbox becomes a module: one step at a time, with precise localization of what remains unclear.

---

## The human side

The framework includes a discipline document for the human. This matters as much as the note format.

The deepest risk of AI-assisted mathematical work is not that you learn wrong things. It is that you stop building the faculties mathematical work requires: the tolerance for confusion, the courage to face a problem alone, the perceptual sense that grows only through sustained independent effort. These erode invisibly, session by session, because every session still feels productive.

The framework's rules are direct: do not ask Claude to execute something you have the tools to attempt yourself. Do not say "yes, I see" when you have tracked the logic without grasping the mathematical fact — these are not the same state. Close the chat after any significant explanation and try to rebuild, even partially, even incorrectly. The gap you find when you try to rebuild is exactly what needed more time.

AI explanations are fluent. Fluent explanations produce the feeling of understanding without the thing itself. The test is not whether Claude's explanation made sense while you were reading it. The test is whether you can reproduce the mathematical fact — in different notation, in a new case, in response to a changed hypothesis — without the explanation in front of you.

---

## What is in this repository

| File | Contents |
|---|---|
| `math-framework-spec.md` | The format specification: note templates, frontmatter schema, naming conventions, annotation system. |
| `AI-human mathematical collaboration principles.md` | How Claude should behave: phenomena first, global picture before details, proof as thought experiment, diagnosis of understanding. |
| `Human principles for AI-assisted mathematical work.md` | The human discipline: the muscle problem, fake understanding, the three-level division of labor. |
| `FRAMEWORK — operating manual.md` | Technical map: what gets read and activated when, the skill table, how subprojects fit together. |
| `USER MANUAL.md` | Practical how-to: common tasks, session habits, troubleshooting. |
| `CHANGELOG.md` | What changed recently. |
| `math-framework-human.md` | The essay version of this introduction, with more detail on the design rationale. |
| `Kodaira guidelines for Claude mathematical notes.md` | The synthesis behind the pedagogy principles, drawn from Kodaira's *惰者集*. |
| `Heuristics and techniques — a working catalog.md` | A growing catalog of transferable mathematical moves and lenses. |

---

## If you want to adopt only part of this

**Only the AI collaboration principles** (no note system, no Obsidian): the reusable instruction block at the end of `AI-human mathematical collaboration principles.md` can be pasted at the start of any Claude session. It encodes the core pedagogy in ten points.

**Only the human discipline**: `Human principles for AI-assisted mathematical work.md` stands alone. It requires no AI setup, no note format, no subproject structure. It is a discipline for protecting your mathematical independence while using any AI tool.

**Only the note format**: `math-framework-spec.md` describes the templates and frontmatter schema. It can be adopted independently of Claude and used with any note-taking or AI system.

---

## A note on scope

The framework was developed in the context of several complex variables and algebraic geometry — work on the Ross–Witt Nyström theorem, Ohsawa–Takegoshi extensions, Fourier analysis, and related background. But the design is domain-agnostic. The modular note structure, dependency graph, annotation system, and collaboration principles apply to any area of mathematics. The only assumption is that the work consists of understanding and building on existing results. That is essentially all of mathematics.

---

*Comments and questions: yanhe@gzhu.edu.cn*
