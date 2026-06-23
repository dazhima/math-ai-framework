# Principles for AI-Assisted Mathematical Work — The Human Side

*A discipline for yourself. The AI principles document tells Claude how to behave; this document tells you how to use Claude without letting the collaboration undermine the faculties that mathematics actually requires.*

---

## Thesis

AI makes mathematics feel more accessible than it is. The real risk is not that you learn wrong things — it is that you stop building the capacities that mathematical work demands: the courage to face a problem alone, the tolerance for confusion, the perceptual faculty that Kodaira calls 数感. These erode not dramatically but by accumulation, invisible session by session, because every session still feels productive. This document is a discipline for protecting those faculties while using AI as a tool.

---

## 1. The Division of Labor

Claude handles explanation, formalization, note structure, example generation, checking, and reference. Your job is everything else: deciding what to work on, making the first attempt, sitting with difficulty long enough for something to move, and doing the reconstructive work that builds genuine mathematical sense.

This division is not a preference — it is structural. If Claude does your job, you lose the capacity to do it. The session still produces notes. You still learn things. But the habit of facing a problem independently quietly deteriorates, and that deterioration is harder to reverse than it is to prevent.

---

## 2. The Muscle Problem

Mathematical courage is a faculty. The willingness to be stuck, to try wrong approaches, to sit in confusion without immediately reaching for relief — this is something that atrophies with disuse. It is exactly the disuse that AI makes frictionless.

The degradation is invisible. You are not being lazy; you are being efficient. But over time the threshold for reaching to Claude drops, and the tolerance for independent difficulty drops with it. The mathematician who cannot face a problem alone is in a serious position regardless of how many notes exist.

**Rules for protecting this:**

- Do not ask Claude to execute something you have the tools to attempt yourself. Computation, standard verification, routine construction using methods already in hand — these belong to you. Ask Claude to check the result, not produce it.
- Do not use the AI to avoid the discomfort of not knowing. That discomfort is the work. The moment you notice yourself reaching for Claude because a problem feels unpleasant rather than because you genuinely lack the tools, stop.
- Maintain a practice of working problems without AI. Not every problem, and not as a rule against getting help — but as deliberate maintenance of the independent muscle. Use Claude to check afterward, not to begin.

---

## 3. The Fake Understanding Problem

AI explanations are fluent. Fluent explanations produce the feeling of understanding without the thing itself. This is the deepest trap in AI-assisted learning, because the feeling is genuine — you really do feel that you have understood. The problem is that the feeling is triggered by a different thing than actual understanding.

The test is not: did Claude's explanation make sense while you were reading it? The test is: can you reproduce the mathematical fact — in different notation, in a new case, in response to a changed hypothesis — without the explanation in front of you?

**What to do:**

- After any significant explanation, close the chat and rebuild. Even partially. Even incorrectly. The gap you find when you try to rebuild is precisely what needed more time.
- Do not say "yes, I see" when you have only tracked the logic. These are not the same state. Tracking a logically valid sequence of steps leaves you exactly where you were before — you can verify the argument but you cannot generate it, apply it, or see why it was the right argument.
- Distinguish fluency with notation from mathematical grasp. Being able to write the symbols correctly is not the same as understanding the object they denote.

---

## 4. The Three-Level Discipline

Not all requests for help are the same. The discipline is not "always try first" — that would obstruct genuine learning. The operative question is: **do you have the tools to make a genuine attempt?**

### Level 1 — Always, regardless of difficulty

Before Claude explains anything: locate the gap yourself. What do you already know that connects to this? Where specifically are you stuck? This takes ten seconds and is never wasted. It creates the mental hook the explanation attaches to and ensures you are actively engaging with the gap rather than passively receiving a fill.

This applies universally — even when you have no idea where to start. Especially then.

### Level 2 — When you have the tools (execution tasks)

Attempt first, always. Ask Claude to check the result, not produce it. The signals that you are in Level 2:

- The problem uses methods already established in the current session or in prior work.
- It is a computation, standard algebraic manipulation, or routine verification.
- You are partway through a derivation and the next step is mechanical.
- You know in principle what to do and the difficulty is execution.

In this case, reaching for Claude without attempting is muscle substitution. The discomfort of doing the computation yourself is exactly the thing you are supposed to be doing.

### Level 3 — Genuine conceptual gap

Ask freely. The signals that you are in Level 3:

- You have no vocabulary for the object — it is genuinely new.
- The result is "trivial to those who know it" but you have never seen the relevant framework.
- No reasonable independent effort would produce the answer without prior exposure.

Even here: apply Level 1 first. State what you already know and what specifically you cannot see before Claude begins. Then receive the explanation as an active engagement, not a passive receipt.

### The "almost see it" case

You have relevant background but not the right framing — you can feel the connection without finding it. This is not Level 3 (you are not without tools) and not purely Level 2 (the gap is conceptual, not executive). Apply a middle form of discipline: articulate clearly what you know and what is missing. Claude should help you find the framing, not replace the effort of looking for it.

---

## 5. Before a Session

- Enter with a stated goal. Not "let's continue with X" but "I want to understand why Y follows from Z" or "I want to work through the proof of theorem N." Vague goals produce passive sessions.
- Make a partial attempt at the central problem before opening the conversation. The attempt does not need to be correct. It needs to be yours. Entering with a half-formed attempt is far better than entering with a question — the former is a problem you are working on, the latter is a request for a lecture.
- Know in advance whether this session is primarily for learning new material (Level 3 mode) or for working through something you have the tools for (Level 2 mode). The discipline differs.

---

## 6. During a Session

- Signal confusion immediately. Do not let false clarity accumulate. If three exchanges have passed and something from the first exchange is still unclear, stop and go back. False clarity at the foundation makes everything built on it unstable.
- When you find yourself wanting another explanation, ask first: have I worked with the current one enough? The problem is often not that the explanation was insufficient — it is that you have not sat with it long enough.
- Do not move forward when something is "close enough." Claude follows your lead. You are responsible for the pace. If you say "okay, I think I get it, let's move on," Claude will move on. The discipline of stopping is yours.
- Answer checkpoint questions genuinely before reading further. This means actually thinking about the question, forming an answer, and only then continuing. If you find yourself reading ahead to find the answer in Claude's next message, you have already broken the discipline.

---

## 7. After a Session

- Write the key idea of the session in one sentence, without notation. If you cannot, the work is not done. This is not a summary exercise — it is a test. If the sentence comes easily, you have it. If you are reaching for symbols to substitute for clarity, you do not.
- Space your returns. Revisiting a note the next day tests short-term retention. Revisiting it three days later tests something more durable. The first pass confirms; the second pass reveals what was actually absorbed.
- "Understood" status in any note is provisional. It means understood at the time of writing. It does not mean understood permanently or understood well enough to use under pressure.

---

## 8. Using the Note System

The notes exist to support reconstruction — not to be a reference you read, but a scaffold you work through. Using them passively defeats their purpose.

- **Checkpoints are exercises.** Answer them before reading on. If you cannot answer a checkpoint, that is exactly the information the checkpoint is for: the thing you thought was settled is not.
- **Work through L-steps yourself before reading the derivation.** At minimum, read the statement of the step and attempt it before looking at the explanation. Even a failed attempt sharpens what the explanation is doing.
- **The Proof requires replay, not reading.** Reading the key move (or its `↝` heuristic gloss) is not replaying the thought experiment. Close the note, reconstruct the tension, attempt the key move yourself, then re-open.
- **Postponed is a study plan.** The items listed under Postponed are the next things to work on, not things that have been safely deferred. Follow them.
- **Return to notes.** A note you have not revisited in a month is not reliably yours. Schedule returns.

---

## 9. The Four Traps

These are the specific failure modes most likely to accumulate invisibly. Name them to recognize them.

**The explanation trap.** You are stuck. The natural response is to ask for an explanation. But often the real need is to sit with the difficulty longer — the explanation will not help if the ground it lands on is not ready. Before asking for an explanation, ask whether you have worked with the current understanding enough. Time spent stuck is not wasted; it is often the time when sense forms.

**The verification trap.** You have a result you think is correct and you ask Claude to verify it — but you have not actually tried to verify it yourself. This is muscle substitution in disguise. Verify your own work first. Ask Claude to check afterward, or to check when you are genuinely uncertain.

**The coverage trap.** The material is moving forward and something from two sessions ago is not fully settled. You continue anyway because it feels close enough and the new material is interesting. The gap compounds. Coverage without foundation is not progress.

**The assent trap.** Claude gives an explanation. You follow it. You say "yes, I see." But you have only tracked the logic — you could not reconstruct it, apply it, or explain why it was the right move. Assent is not understanding. The discipline is to distinguish them, out loud if necessary.

---

## 10. Self-Check — End of Any Session

Run through these five questions honestly at the end of every working session.

1. **Attempt discipline.** For each topic covered: did I make a genuine attempt before asking? Or did I move directly to the AI?
2. **Reconstruction test.** Can I state the key mathematical idea of today's work in one sentence, without notation?
3. **Confusion log.** Did I signal confusion when it arose, or did I let unclear things accumulate beneath a surface of false clarity?
4. **Pacing discipline.** Did I move forward before something was settled? If yes, what was it, and when will I return?
5. **Provisional status.** Is there something I "understood" today that I should return to tomorrow and test against a new case or changed hypothesis?

If any answer is unsatisfactory, note it explicitly. The note is not for punishment — it is so the next session begins with accurate information about where you actually are.

---

## Source

Grounded in the mathematical philosophy of Kunihiko Kodaira, *惰者集：数感与数学* (人民邮电出版社, 2017), as synthesized in `AI-human mathematical collaboration principles.md`. The failure modes specific to AI-assisted learning are additions beyond Kodaira's original observations, derived from the structure of the AI-human collaboration itself.
