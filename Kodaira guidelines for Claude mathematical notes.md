# Kodaira on Mathematical Understanding: Guidelines for Claude Notes

Source: Kunihiko Kodaira, `惰者集：数感与数学`, scanned Chinese edition, located at:

`../[图灵新知] 小平邦彦 - 惰者集_ 数感与数学 (2017, 人民邮电出版社) - libgen.li.pdf`

Page convention: I cite the printed page number first, then the PDF page in parentheses. For the main text, `PDF page = printed page + 8`. The PDF is image-only, so the evidence below is based on OCR checked against page images. Short Chinese anchors are included only to identify the paragraph.

## How Claude Should Write Modular Math Notes

Claude should assume that real mathematical understanding is not passive reading, proof verification, or memorizing formal definitions. According to Kodaira, understanding happens when the reader reconstructs the proof, grasps the mathematical fact behind the theorem, forms a sensory/global image of the object, and has enough paced practice for this "mathematical sense" to develop.

The practical rule is:

> Write notes as guided reconstruction modules, not as polished encyclopedic summaries.

Each note should help the reader answer:

1. What is the mathematical phenomenon here?
2. What is the structural fact the theorem is really expressing?
3. Why are the definitions arranged in this order?
4. How would I rediscover or replay the proof?
5. What examples, pictures, or applications make the theorem feel inevitable?
6. What prerequisite sense must be strengthened before moving on?

## Evidence Cards

### 1. Understanding a math book requires rewriting and reordering

Location: "数学笔记", printed p. 002, PDF p. 10.

Anchor: "我会尝试在笔记本中抄写这些数学证明"; "调整章节顺序的笔记"; "真正掌握第一章的感觉".

Kodaira says that when repeated reading of a proof still does not make it meaningful, he copies the proof into a notebook, notices unsatisfactory points, searches for a better proof, and even rewrites the order of the chapter. Only after this reorganization does he feel he has truly grasped the chapter.

Guideline for Claude:

Do not merely explain the author's order. Reconstruct the dependency order that makes the concept intelligible. When writing notes, include a local "why this order" section and a "possible reordering" section if the original exposition is psychologically hard.

### 2. Understanding is not checking a proof; it is grasping the mathematical fact

Location: "数学笔记", printed pp. 003-004, PDF pp. 11-12.

Anchor: "从感觉上把握定理所要表达的数学事实"; "做笔记的目的不是为了背诵证明过程"; "详细分析定理所要表达的数学事实的结构".

Kodaira distinguishes verifying a proof from understanding a theorem. A proof can be correct while the theorem remains vague. Real understanding means grasping the mathematical fact expressed by the theorem, almost like grasping `2 + 2 = 4`. Notes are not for memorizing proof steps; they are for analyzing the structure of the mathematical fact.

Guideline for Claude:

For every theorem, separate:

- Formal statement
- Mathematical fact / phenomenon
- Structure of the fact
- Proof mechanism
- Applications or test cases
- What should become "obvious" after understanding

### 3. Mathematical sense develops through repeated practice

Location: "数学笔记", printed p. 004, PDF p. 12.

Anchor: "数学与钢琴也有共通的一面"; "每天也需要花时间去反复练习"; "培养把握数学事实的感觉".

Kodaira compares mathematics with piano. Technical skill requires repeated practice over time. This practice cultivates the sense needed to grasp mathematical facts.

Guideline for Claude:

Include small drills and reconstruction exercises inside notes. Do not treat exercises as optional decoration. A modular note should contain at least one "practice for sense" component: compute a toy case, restate a proof step, draw a diagram, verify a special case, or apply the theorem to a known example.

### 4. Mathematics is not logic; logic is only grammar

Location: "数学印象", printed pp. 004-006, PDF pp. 12-14; related version printed p. 018, PDF p. 26.

Anchor: "逻辑对于数学的作用类似于语法对于文学"; "数学在本质上与逻辑不同"; "数学是一门需要感觉的学科".

Kodaira argues that logic is necessary but not the essence of mathematics, just as grammar is necessary but not the essence of literature. The mathematician may think a proof was produced by logic, but Kodaira says mathematical sense guides the path and logic records it.

Guideline for Claude:

Do not begin with purely formal machinery unless the user already has the needed sense. Start with the phenomenon, picture, or motivating tension, then formalize. Treat logic as the final grammar of a thought, not as the source of the thought.

### 5. "Number sense" or mathematical sense is a perceptual faculty

Location: "数学印象", printed p. 005, PDF p. 13; expanded in "一位数学家的妄想", printed pp. 017-018, PDF pp. 25-26.

Anchor: "理解数学相当于'观察'数学现象"; "通过一定感觉所形成的感知"; "我将其称为'数感'".

Kodaira says understanding mathematics is like observing mathematical phenomena, but the observation is not visual. It is a perceptual faculty, close to vision, which he calls "数感". This faculty is distinct from logical reasoning.

Guideline for Claude:

Write notes that train mathematical perception. Use language like "what to notice", "what changes", "what stays invariant", "where the obstruction lives", and "what this object is trying to measure". These are not fluff; they are the bridge to mathematical sense.

### 6. A proof is a thought experiment that must be replayed

Location: "数学的唯一理解方法", printed pp. 011-012, PDF pp. 19-20.

Anchor: "数学的证明不是单纯的论证，还具有思考实验的意味"; "理解证明...是自己尝试重现思考实验的过程"; "理解也可以说是自身的体验".

Kodaira says skipping proofs gives only a shallow impression. To understand a math book, one must follow the proof step by step. But following a proof is not merely checking for errors; it is replaying the thought experiment that produced the proof. Understanding is a personal experience.

Guideline for Claude:

Write proofs as replayable experiments. Each proof module should include:

- The problem the proof is trying to solve
- The first idea one would try
- Why that idea is insufficient
- The key move
- The verification
- What experience the reader should now have

### 7. The whole pattern matters more than atomic decomposition

Location: "对'新数学'运动的批判", printed pp. 090-091, PDF pp. 98-99.

Anchor: "曲线绝不是分散的点集"; "没有形象相当于无法理解这个对象"; "从感觉上把握...全局上的模式".

Kodaira criticizes reducing a curve to a set of points when teaching. Mathematicians define a curve as a point set for rigor, but understanding the curve requires a sensory image of the whole curve. More generally, understanding a theory requires grasping the global pattern of the whole system.

Guideline for Claude:

Every major note should include a "global pattern" section before or after the formal definitions. For example: what is the object as a whole, what are its moving parts, what are its natural examples, and what pattern should the reader see before studying local technical details?

### 8. Logical foundations are not always educational foundations

Location: "对'新数学'运动的批判", printed p. 091, PDF p. 99; "令人费解的日本数学教育", printed p. 098, PDF p. 106.

Anchor: "作为分析结果的基础和作为教育出发点的基础完全不同"; "历史上较早出现的概念比逻辑上的基础概念更简单易懂".

Kodaira says modern mathematics may be structurally based on set theory, but that does not mean education should start from set theory. A foundation obtained by later analysis is different from a foundation suitable for learning. Learners often understand historically earlier concepts more easily than logically foundational ones.

Guideline for Claude:

When choosing module order, prefer psychological and historical accessibility over Bourbaki-style logical order. It is often better to introduce a concrete object, example, or classical theorem first, and only later explain the abstract foundation that organizes it.

### 9. Do not hurry: protect time for foundational sense

Location: "忘却原则的初等、中等教育", printed pp. 061-062, PDF pp. 69-70; related summary printed pp. 100-101, PDF pp. 108-109.

Anchor: "教学应遵循合理顺序"; "教学存在适龄期"; "牺牲了自主思考的时间"; "限定在最基础的数学领域，然后开展充分的教学".

Kodaira criticizes curricula that rush through too many topics too early. The result is not deeper learning but loss of independent thought. He argues for a reasonable order, readiness, and enough time on fundamental domains.

Guideline for Claude:

Write fewer, deeper modules. Do not stuff a note with adjacent theory just because it is related. If the user is building foundations, protect time for definitions, examples, proof reconstruction, and self-checks. A note should make clear what is being postponed and why.

### 10. Geometry and diagrams train creative mathematical perception

Location: "发明心理学与平面几何", printed p. 025, PDF p. 33.

Anchor: "平面几何需要观察图形并对其进行验证"; "帮助培养创造力的最好教材".

Kodaira connects plane geometry with the cooperation of visual pattern recognition and logical verification. Drawing auxiliary lines requires seeing the whole figure and making a synthetic judgment.

Guideline for Claude:

Whenever the topic has a geometric, diagrammatic, or structural visualization, include it. Even for abstract topics, create a "mental diagram": fiber/base, cone/special fiber/generic fiber, exact sequence, curvature matrix, envelope, filtration, or degeneration picture.

## Direct Instruction Block for Claude

When writing Yan's mathematical notes, follow these Kodaira principles:

1. Write for reconstruction, not passive reading.
2. Separate the theorem's formal statement from the mathematical fact it expresses.
3. Explain the structure of the fact before polishing the formal proof.
4. Treat proofs as replayable thought experiments.
5. Include examples, diagrams, and special cases to train mathematical sense.
6. Use logic as grammar, not as the first source of meaning.
7. Prefer psychologically natural order over purely formal order.
8. Protect depth and pacing; do not rush into adjacent abstractions.
9. Make global patterns visible before local technical decomposition.
10. Include small exercises or checkpoints so the user can test whether the fact has become graspable.

## Template for Future Modular Notes

Use this structure unless the topic demands otherwise:

1. **Phenomenon.** What mathematical phenomenon are we trying to see?
2. **Object Picture.** What is the mental/geometric/algebraic picture?
3. **Formal Setup.** Definitions and notation, introduced only as needed.
4. **Main Fact.** The theorem as a mathematical fact, not only as a sentence.
5. **Proof Experiment.** Motivation, failed naive attempt, key move, verification.
6. **Structure Analysis.** What parts of the theorem/proof carry the real content?
7. **Examples.** Toy case, classical case, and the case relevant to the current paper.
8. **Use in HTW/RWOT.** Where this module plugs into the larger proof architecture.
9. **Checkpoints.** Questions that test reconstruction and mathematical sense.
10. **Next Module.** What should be learned next, and what is intentionally postponed.

## Immediate Application to Current BP08 Notes

For the current BP08 Layer 0 work, especially the Schur complement item `D_{jk} >= 0`, Claude should not only say:

> The full Hessian of `phi` is positive semidefinite, so the Schur complement is positive semidefinite.

It should instead build the note like this:

1. **Phenomenon:** Joint plurisubharmonicity in `(t,z)` says the full mixed Hessian is positive.
2. **Matrix Picture:** Display the block Hessian in base/fiber variables.
3. **Optimization Meaning:** Explain the Schur complement as the leftover positivity after minimizing over fiber directions.
4. **Proof Experiment:** Take a tangent vector in the base, allow a compensating fiber vector, minimize the quadratic form, and see `D_{jk}` appear.
5. **Connection to BP08:** This is exactly the local positivity that survives after solving the fiber-direction correction by the Hörmander estimate.
6. **Checkpoint:** Ask Yan to explain why "subharmonicity" alone is too weak and why joint psh is the right hypothesis.

This follows Kodaira's rule: the note must make the mathematical fact visible, not merely verify a formal implication.
