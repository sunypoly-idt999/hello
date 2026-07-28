# Curriculum Note — The Ex3 Dependency

**Scaffold:** AI Literacy — Learner's Permit, 15-exercise, Spring 2026
**Occasioned by:** Rogers checkpoint submission (Ex1–11), reviewed 2026-07-28
**Scope:** Exercise 3 and its downstream references in Ex7, Ex8, Ex9

---

## The problem

Exercise 3 says:

> Choose any two of the following moves:
> - "I don't understand this." Ask for a different explanation. Don't accept the first re-explanation. Push again.
> - "My experience tells me otherwise." State what observation or prior learning contradicts the claim.
> - "This reading says something different." Paste a contradicting sentence from any source.
> - "Here's another model's response." Take the same prompt to a different AI, copy that response, ask this model to respond to it.

Exercise 7 then says: "Use one of the two moves from Exercise 3 to push on one of the versions." Exercise 8, Stage 3: "Use one of the two moves from Exercise 3 to push on something in the text."

Ex3 is therefore load-bearing for two later exercises. It doesn't read that way in the document — it reads as a self-contained pushback drill — but it is where a student's challenge repertoire is established for the rest of Phase II.

The failure mode is silent. A student who executes only one move in Ex3 hasn't broken Ex3 in any visible way — the artifact spec is a 3–4 sentence summary of the exchange, which one move produces perfectly well. But the downstream instruction becomes ill-formed, and the student resolves the ambiguity the only way available: by repeating the single move they have.

---

## Evidence from the Rogers portfolio

| Location | Move used |
|---|---|
| Ex3 turn 3 | M1 — "I don't understand this. Give me a different explanation." Stopped after first re-explanation. |
| Ex7 turn 2 | M1 — "I don't understand the version for the 10 year old. Give me a different explanation" |
| Ex8 turn 4 | M1 — "I don't understand this concept of 'black boxes' give me a different explanation." |
| Ex9 turns 11–12 | M1, and for the first time the second push: "I still dont understand, try and give me another explination" |

Four designated challenges across the portfolio, all the same move. M2, M3, and M4 were never used as named moves.

Two things are worth separating here. The student is plainly *capable* of the other moves — Ex5 and Ex6 contain unprompted experience-based pushback (the Clippy comparison, the agent skepticism, the challenge that invisible adaptation is a first step toward dark patterns), and Ex6 as a whole is a competent M4 in everything but label. So this is not a capability gap. It's an instruction-design gap: the repertoire the scaffold intends to build never got built, and nothing in the scaffold detected that.

The second observation: the "push again" behavior appears for the first time in Ex9, six exercises after it was assigned. Whatever produced it there — the reading being genuinely harder, or accumulated confidence — it wasn't Ex3.

---

## Three specific defects

**1. The moves are unnamed.** "The two moves from Exercise 3" is not a checkable reference. Nothing in Ex3 asks the student to record which two they chose, so by Ex7 neither the student nor the instructor can verify compliance without reading the Ex3 transcript. Numbering them — M1 Re-explain, M2 Experience Contradicts, M3 Source Contradicts, M4 Cross-Model — costs four words and makes every downstream reference auditable.

**2. "Push again" is trapped inside M1.** The instruction "Don't accept the first re-explanation. Push again" appears only in the M1 bullet. A student who selects M2 and M3 never encounters it. This is either a general principle of Ex3 that's been misfiled into one bullet, or an M1-specific requirement — the document doesn't say which, and the answer determines whether Rogers' Ex3 is one deficiency or two. It should be lifted out into the general instruction.

**3. Nothing forces range.** "Choose any two" permits two moves from the same register. In practice M1 is the lowest-friction option — it requires no source, no prior observation, no second model — so it will be chosen nearly always, and the second choice determines whether the student learns anything new. Requiring **M1 plus one of M2/M3/M4** guarantees the repertoire contains at least one move that isn't "explain it again."

---

## Proposed edits

Minimal, in order of value:

1. Number the four moves.
2. Change "Choose any two" to "Use M1 and one of M2, M3, or M4."
3. Move "Don't accept the first re-explanation. Push again" from the M1 bullet into the general instruction above the list.
4. Add one line to the Ex3 artifact spec: *state which moves you used.*
5. Change Ex7 and Ex8 to read "use a challenge move from Exercise 3" — so the instruction stays well-formed even if Ex3 was under-executed, while still pointing back at the repertoire.

Edit 4 is the one that makes the dependency visible to the instructor at review time rather than at Ex10.

**Open question on M4.** The cross-model move is functionally a miniature of Ex6's fork. Making it mandatory in Ex3 would seed Ex6 usefully — the student arrives already having compared two models' handling of the same prompt — but might also spend the surprise. Worth deciding deliberately rather than leaving it to student choice, since right now M4 is the least likely of the four to be selected and Ex6 lands cold as a result.

---

## The general pattern behind this

The Ex3 problem is one instance of something structural. In every exercise with more than one required prompt, the artifact only proves the *final* prompt ran. Middle steps leave no trace in `/artifacts`, and detecting them requires reading the transcript.

The Rogers submission has two more instances:

- **Ex10** omits the second required prompt entirely (the one about what a synthesis document should contain and the risks of relying on it). The closing artifact still looks complete, because the closing prompt asks for a tradeoff assessment and the model can produce one cold. The skipped prompt is invisible in the artifact.
- **Ex11** omits "Work through each level. After each, tell the model what was new versus what was already understood." The compiled document looks correct — four levels, clean, cited. The absent step is only detectable in the transcript.

Both omissions are of *middle* prompts, both are the conceptually load-bearing ones, and both are undetectable from the deliverable. That's a consistent shape, not three unrelated slips.

Two candidate fixes:

- **State the trace requirement.** For any exercise with more than one required prompt, add: *the transcript must show all prompts in this exercise.* Cheap, but relies on the reviewer reading transcripts.
- **Make the artifact carry its own manifest.** Have Phase II+ artifacts open with a one-line list of the prompts issued. Self-auditing, visible at a glance, and it doubles as prompting practice — the student has to articulate what they asked for.

The second is more intrusive but scales better once cohorts are larger than one.

---

## Toolkit note (Prerequisite 2)

Prerequisite 2 specifies that the instructor designates a transcript exporter and its configuration. The Rogers Gemini exports collapse markdown tables into unbroken strings — `Focus AreaCore Design Challenge**Trust & Transparency**AI can feel like a "black box"...` — which is severe enough in the Ex10 artifact to make it unreadable as a document.

This is not a student error, but it collides with the Phase III standard that artifacts are "the kind that would be submitted as coursework." Worth adding a per-model export configuration to the prerequisites, plus a one-line student check: *open the exported file and confirm tables survived before saving it to the workbench.*

Related and smaller: Ex9 is the same conversation as Ex8 continued, so `lp-ex8` is a strict subset of `lp-ex9`. Ex9 doesn't require a new conversation, so this is compliant — but the scaffold should say which it wants, since continuing produces cleaner cross-reading comparison while a fresh conversation produces cleaner per-reading transcripts.
