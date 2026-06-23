# A Modular Framework for AI-Assisted Math Research

*Yan He — May 2026*

> **Non-authoritative — this is the human-readable essay.** For the binding rules see: format → `math-framework-spec.md`; pedagogy → `AI-human mathematical collaboration principles.md`; how-it-all-runs → `FRAMEWORK — operating manual.md`. Where this essay and those files differ, they win.

---

## Motivation

When working on a research paper, the background material is never flat. Understanding a single citation may require understanding several earlier results, each of which depends on further background. The natural structure is a tree — or more precisely, a directed acyclic graph — of mathematical facts, each with explicit dependencies. Yet most note-taking systems treat documents as an unstructured collection, leaving this dependency structure implicit and inaccessible to any collaborator, human or AI.

This framework makes the structure explicit. Every document is a node in a dependency tree, with machine-readable links to its parent context, its logical prerequisites, and the results that depend on it. The design is inspired by a principle familiar from scheme theory: there is no meaningful notion of an absolute object — a scheme is always a scheme *over a base*. Similarly, a research document is always a document *over its parent context*. This relativity is not a limitation but a feature: it means any subtopic can be promoted to its own self-contained subproject, equipped with its own context, while remaining anchored to the parent via a pointer.

---

## Document Structure

Each mathematical fact — a lemma, a computation, a definition — lives in its own file. The file has two parts.

The **frontmatter** is a small block of metadata encoding the document's position in the tree: its unique identifier, its status (`stub`, `in-progress`, `understood`), its parent node, its children, its logical prerequisites, and the results that use it. The distinction between *tree position* (`parent`/`children`) and *logical flow* (`depends_on`/`used_by`) is deliberate: a document may logically depend on something outside its own subtree, and the framework accommodates this without conflating the two relations.

The **body** follows a fixed template: a one-sentence *Goal* stating what the document establishes, a *Setup* section fixing notation, a *Derivation* consisting of numbered steps L1, L2, …, and a *Conclusion* stated as a self-contained block. The numbered steps serve a dual purpose: they provide fine-grained reference points for the annotation system described below, and they enforce a discipline of explicit reasoning in which no step is left unjustified.

The *Goal* and *Conclusion* fields are designed to be read in isolation. An AI generating slides, an outline, or a summary of the project reads only these two fields across all documents — it does not parse the derivations. This mirrors the structure of a well-written paper, where the abstract and theorem statements carry the mathematical content and the proofs provide verification.

---

## Annotation and Human-AI Dialogue

A central design goal is precise communication between researcher and AI. The standard difficulty in AI-assisted research is that feedback is coarse: "this proof is unclear" leaves the AI with no information about which step failed. The framework addresses this by attaching a checkbox to every numbered step. The researcher annotates as follows:

- ✓ on a step means it is understood.
- ? on a step, optionally followed by a comment, means something specific is unclear.

The AI reads the annotations and responds to the precise location of confusion. "I don't understand L7" identifies a single logical step — the commutativity of two differential operators, the application of a product rule — and the AI expands that step without re-explaining the entire argument. This granularity matches the natural granularity of mathematical reasoning.

---

## Subprojects and the Relativity Principle

When a document grows into a collection of related notes — reading a paper, developing a proof strategy, building background for a theorem — it becomes natural to promote it to its own *subproject*: a subfolder with its own CLAUDE.md (the AI's project context file), its own document tree, and its own focused scope.

The operation is deliberately relative. The subproject's CLAUDE.md contains three things: a pointer to the parent context, a declaration of the relevant working conventions (skills), and a lean summary of the subproject's goal and current status. It inherits nothing else from the parent — not the parent's full context, not its other subprojects, not its reference material. The parent pointer exists precisely so that broader context is reachable without being duplicated. This is the sheaf-theoretic intuition: work locally, glue via the restriction map.

The promotion of a document to a subproject is not an irreversible architectural decision. It is a practical response to complexity — the mathematical equivalent of promoting a technical lemma to a section, or a section to a paper.

---

## Naming and Navigation

Files are named `[Source] — [Mathematical content]`, where the source is the paper or context the content comes from (`BP08`, `B2`, `GZ-Ch7`) and the content is a brief description of what is being established. The source prefix makes the provenance of each fact immediately visible when browsing the folder. A subproject master document drops the source prefix and is named by its goal.

This naming convention, together with the frontmatter dependency graph, means that any document in the project is self-locating: its name tells you where the mathematics comes from, and its frontmatter tells you where it sits in the logical structure.

---

## Remark

The framework is not specific to any mathematical domain. It was developed in the context of several complex variables and algebraic geometry, but the design is domain-agnostic: the same structure of goals, numbered steps, annotations, and dependency links applies equally to algebra, topology, or analysis. The only assumption is that the work consists of understanding and building on existing results — which is to say, it applies to essentially all of mathematics.
