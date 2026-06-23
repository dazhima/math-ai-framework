# Heuristics & Techniques — a working catalog

> A framework-level resource: a catalog of **transferable mathematical moves** ("lenses") usable across fields. This is a *fourth concern*, distinct from the existing three — format (`math-framework-spec.md`), pedagogy (`AI-human…principles.md`), discipline (`Human principles…`). Those say *how to write/explain/study*; this says *what to try when you're stuck*.
>
> Seeded 2026-06-13 from the Tao-blog knowledge base (`../tao-blog/`); meant to grow as more transferable moves are harvested. Entries tagged ⟨Tao⟩ link to a post-note there.

## How to use it

A lens is a question you ask a stuck problem. When an argument is lossy, an object opaque, or a constant ugly, run down this list and ask which lens fits. Lenses are not theorems; they are *places to look*. In a session, naming the lens out loud ("this looks like a structure-vs-randomness split") is itself the move.

---

## The catalog

**Structure vs. randomness.** ⟨Tao⟩ Decompose a complicated object as *structured part + pseudorandom part + small error*; attack the two with disjoint toolkits (algebra/geometry vs. analysis/probability). Reach for it when an object is too complicated to handle whole. → `../tao-blog/technique/Tao — structure and randomness.md`

**Amplification / tensor-power.** ⟨Tao⟩ A lossy estimate hides unused symmetry; apply it to a transformed copy and optimize, or tensorize ($A^N\le C(N)B^N \Rightarrow A\le B$) to kill constants. Reach for it when you have a bound with a bad constant that *should* be sharp. → `../tao-blog/technique/Tao — amplification and the tensor power trick.md`

**Compactness & contradiction.** Replace a quantitative estimate by its qualitative limit: assume no uniform bound, extract a limiting object from a compactness argument, derive a contradiction. Reach for it to get *existence of a constant* when you don't need its value. (Trades effectivity for ease — note the cost.)

**Dimensional analysis / calibrate exponents.** Before proving an inequality, fix the exponents by scaling/units: both sides must transform the same way under the problem's natural rescalings. Reach for it to catch errors and *guess the right statement* before proving it.

**Generic → special transfer.** Prove a statement on a generic/limiting object (generic point, transcendence, semicontinuity, a Lefschetz/transfer principle) and descend to the case you want. Reach for it when the special case is rigid but a generic deformation is flexible. *(This is the move behind the workshop's `jet-differentials` "semicontinuity spreads vanishing from one example to generic" step.)*

**Probabilistic method.** To show an object with property P exists, show a random object has P with positive probability. Reach for it when explicit construction is hard but counting/averaging is easy.

**No self-defeating object.** Assume the extremal/maximal counterexample exists, then build from it a strictly better one — contradiction. Reach for it for "there is no largest/worst …" statements.

---

## Maintenance

New lenses arrive via the Tao-blog ingestion protocol (anything tagged `→ framework` whose content is a *technique*) and from Yan's own work. Keep each entry to: the move, when to reach for it, one pointer. If an entry grows into a real worked treatment, promote it to a `type: module` note in the relevant project and leave the one-liner here.
