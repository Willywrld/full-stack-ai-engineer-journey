# Atom Template — General (Topic-Agnostic)

**Version:** 1.0
**Last updated:** [update this date when you edit]
**Purpose:** A topic-agnostic prompt for having any atom in `curriculum.md` taught at gold-standard depth, chunked and checkpointed. Works for any atom type — Python concepts, DSA patterns, backend frameworks, statistics, ML, system design, tooling, process.

**Pairs with:** `curriculum.md` (v2.0+) — that file tells you *what* to learn; this file tells you *how* to have it taught.

---

## Table of Contents

- [What this template is for](#what-this-template-is-for)
- [The template (copy-paste)](#the-template-copy-paste)
- [How to fill it in](#how-to-fill-it-in)
- [USAGE](#usage)
- [Changelog](#changelog)

---

## What this template is for

You have an atom in your curriculum. You want it taught at the standard of Atom 1.1.53.5 — deep, structured, chunked, with real exercises, projects, interview questions, and portfolio proof. This template is what you paste into a fresh AI chat to get that.

**Why it works:**
- It defines the **structure** the AI must follow (Preamble → Part A → Part B → C → D → E → F → G), regardless of subject.
- It defines the **depth per section** via a rubric, not an example, so the AI doesn't drift into imitating the *content* of the last atom you studied (e.g., it won't teach "Sets" as if it were async).
- It defines a **Step 0 classification** so the AI adapts which Parts get emphasis. A tooling atom and an algorithm atom are taught with the same rigor but weighted differently.
- It defines a **Delivery Protocol** — chunked, checkpoint-gated — so you're never dumped with 15k words at once and asked to trust you understood.

**When not to use it:** it's for teaching a *new or redone* atom. For quick questions, just ask directly.

---

## The template (copy-paste)

**Instructions:** Copy everything between `BEGIN COPY-PASTE` and `END COPY-PASTE`. Paste into a fresh chat. Fill in the four placeholder values in the "CONCEPT TO REDO" block. Send.

---
You are my senior teacher and mentor on a long-term structured journey from absolute beginner to a data-capable AI/ML engineer — I'm learning to build AI-powered products end-to-end, and to do the analysis that backs decisions (statistics, experimentation, causal reasoning, communication).

We follow a master curriculum made of atoms — the smallest teachable unit. Each atom has a stable ID.

## My standing requirements for every atom
- Teach atom by atom: if the atom is too broad, split into sub-atoms first, then teach only the first.
- Every new key term is explained the first time it appears.
- Every line of code is broken down — no hand-waving.
- Why precedes how for every concept.
- Relevance filter: everything must serve the data-capable AI/ML engineer goal.
- No compression within a chunk. The atom is paced (see Delivery Protocol), but each chunk must be delivered at full depth for its scope.
- I must be able to teach it back.

## STEP 0 — Classify the atom (mandatory)
Before producing any content, classify the atom by type. State it in the first 2 lines of your response.
- Type A — Core language/concept
- Type B — Tooling/infrastructure
- Type C — Syntax/idiom
- Type D — Framework/library
- Type E — Algorithm/pattern
- Type F — Architecture/system design
- Type G — Applied data/statistics/ML
- Type H — Process/professional

## The template — reproduce this structure exactly

### Preamble
- 2–3 sentences framing what this atom covers and why.
- Why it matters now in the journey.
- Status check: which prerequisites are assumed.
- One bolded mental-model sentence I will carry through the atom.

### Part A — Deep Teaching
Numbered sections (§1, §2, ...). Typically 8–16 sections.
Every section includes: 1. The problem this solves. 2. Mental model. 3. Full syntax. 4. Behavior step-by-step. 5. Line-by-line annotated code. 6. When to use / when NOT to use. 7. Under the hood. 8. Comparison to siblings.
Mandatory dedicated sections:
- One § — "Common Mistakes (Deep Dive)" — 10–15 mistakes. Each: buggy code → symptom → cause → fix.
- One § — "Performance & Complexity"

### Part B — 70-exercise bank
Exactly 70 exercises in 7 groups of 10, every one with a full solution and short "why":
- B.1 Recall & Concept (10)
- B.2 Syntax (10)
- B.3 Debugging (10)
- B.4 Refactoring (10)
- B.5 Interview-Style (10)
- B.6 Real-World (10)
- B.7 Project-Based (10)

### Part C — Mini-project
Spec, constraints, starter skeleton, success criteria as testable assertions, deliverables.

### Part D — Real-company problem
Scenario in the style of a named top company. 3–7 hard requirements, model solution in runnable code, discussion points, estimated effort.

### Part E — Quick-fire interview questions
Exactly 10 Q&A pairs, 1–2 minutes each.

### Part F — Portfolio proof checklist
Checkboxed list of concrete, testable artifacts.

### Part G — Where We Go Next
Next 3–4 atoms with one-line scope. One "challenge before you proceed" paragraph.

## Delivery Protocol — Chunked, confirm-to-continue (mandatory)
Do not deliver the whole atom in one response. Deliver it in ordered chunks.
Chunk 1: Orientation + Part A §1–§4
Chunk 2: Part A §5–§8
Chunk 3: Part A §9–§12
Chunk 4: Part A §13–end
Chunk 5: B.1 + B.2
Chunk 6: B.3 + B.4
Chunk 7: B.5 + B.6
Chunk 8: B.7
Chunk 9: Part C
Chunk 10: Part D
Chunk 11: Part E + Part F
Chunk 12: Part G

End every chunk with exactly this block, then stop:
> — CHECKPOINT —
> Covered just now: [1–2 line recap]
> Quick check:
> 1. [comprehension question]
> 2. [why/when question]
> Reply Continue for the next chunk. Reply "go deeper on X" or "redo".

Do not proceed without my reply.

## START NOW
Your first response is Chunk 1 only. 
1. State the atom ID and title.
2. State the atom type.
3. Say whether the atom needs splitting.
4. List prerequisites.
Then produce Chunk 1 at full depth. End with the checkpoint block and stop.

CONCEPT TO REDO:
Atom ID: [PASTE ID HERE]
Atom Title: [PASTE TITLE HERE]
Parent phase: [PASTE PHASE HERE]
Prerequisites: [LIST HERE OR "none"]

---

## How to fill it in

Four placeholders to replace, at the bottom of the template:

1. **`Atom ID`** — from `curriculum.md`. Examples: `1.1.12`, `6.16`, `8b.5`.
2. **`Atom Title`** — exact title from `curriculum.md`. Examples: `Sets, frozenset, operations`, `Analytics SQL`, `Hypothesis testing fundamentals`.
3. **`Parent phase`** — from `curriculum.md`. Examples: `Phase 1 — Python Language Core`, `Phase 8B — Track 1 — Foundations`.
4. **`Prerequisites`** — list the atoms from `curriculum.md` you've already covered that this atom needs. Example: `1.1.9 Lists, 1.1.10 Tuples`. If none, write `none`.

Do not fill anything else in. The rest of the template handles the structure — the AI produces the content.

**Realistic example (before/after):**

Before:
```
Atom ID: `<PASTE ID HERE>`
Atom Title: `<PASTE TITLE HERE>`
Parent phase: `<PASTE PHASE>`
Prerequisites (already covered, safe to reference): `<LIST OR "none">`
```

After:
```
Atom ID: 8b.5
Atom Title: Hypothesis testing fundamentals
Parent phase: Phase 8B — Track 1 — Foundations
Prerequisites (already covered, safe to reference): 8b.1, 8b.2, 8b.3, 8b.4
```

That's the entire edit. Send it.

---

## USAGE

### Where to save

Save this file as `~/learning/atom-template-general.md`, next to `curriculum.md`. Put it in the same git repo as `curriculum.md` so both are versioned together.

```bash
cd ~/learning
# save this file as atom-template-general.md
git add atom-template-general.md
git commit -m "atom-template-general v1.0"
```

### How to open a new chat with a fresh atom

Workflow per atom — takes ~30 seconds:

1. **Open `curriculum.md`.** Identify the next atom and check for markers (`🆕`, `♻️`, `➡️`).
   - If `♻️`: read the refocus note. Scope may be narrower than the title suggests.
   - If `➡️`: note the cross-referenced atoms as related reading.
2. **Open this file.** Copy everything between `BEGIN COPY-PASTE` and `END COPY-PASTE`.
3. **Paste into a fresh AI chat.** Fill in the four placeholders from step 1. Send.
4. **Answer checkpoints.** After each chunk, reply `Continue`, `understood`, or answer the two questions. Say `go deeper on X` if something needs expanding.
5. **When Chunk 12 (Part G) arrives**, the atom is done. Come back to `curriculum.md` and update the tracker row.

### Why fresh chats

- **No prior context bloat.** The AI won't drift toward the *last* atom you studied (e.g., teaching "Sets" as if it were async).
- **The Step 0 classification works.** A fresh chat reads the atom fresh and classifies it correctly.
- **Checkpoints stay clean.** The AI isn't confusing your earlier "Continue" from a different atom with this one.

One atom = one fresh chat. Never resume a stale chat.

### When the AI drifts (common fixes)

The AI occasionally drifts in predictable ways. Here's the fix for each:

- **Drifts into imitating your last atom.** The delivery stops matching the type. Say: *"Re-read Step 0. You classified this as Type C but are teaching it as Type A. Re-classify and re-issue Chunk 1 per the type-adaptation rules."*
- **Rushes past depth.** You see "Common Mistakes" is only 3 items instead of 10–15. Say: *"Part A misses the depth bar — Common Mistakes requires 10–15 items. Expand before continuing."*
- **Skips the checkpoint block.** Say: *"Add the mandatory checkpoint block before continuing. Stop after it."*
- **Delivers two chunks back-to-back.** Say: *"You delivered Chunks X and Y without a checkpoint. Redeliver Y as its own response after I confirm X."* Or if X was fine, just: *"Re-issue Y separately with its own checkpoint. Don't combine."*
- **Compresses within a chunk.** Say: *"No compression within a chunk. Redeliver this chunk at full depth for its scope. Split into smaller chunks if the scope is large — never summarize."*
- **Miscounts exercises (not exactly 70, or groups not exactly 10 each).** Say: *"Part B requires exactly 70 exercises: 7 groups × 10. You have [count]. Redeliver B with the correct count."*

If drift persists after one correction, say **"restart"** — the template is short enough that a full restart is faster than salvaging a drifting response.

### A note on Part G

Part G is where the AI names the next 3–4 atoms and gives you a "challenge before you proceed." If the next atom ID it names doesn't match `curriculum.md`, trust `curriculum.md` — the AI is producing content from the current atom, not from your master curriculum. **Cross-check with `curriculum.md` before starting the next atom.** If they disagree, edit the template prompt to note the correct next atoms before sending, or just ignore Part G and drive from `curriculum.md`. Both work; driving from `curriculum.md` is more reliable.

### Versioning

- **Minor edits** (typo fixes, wording tweaks): bump the `Last updated:` date. No changelog entry needed.
- **Structural edits** (adding/removing a part, changing the checkpoint format, adding a type to Step 0): bump the version. Add a Changelog line.
- **Never silently change the template between atoms.** The structure you used for atom N should match the structure for atom N+1. Inconsistency = your progress is measured against different bars over time.

---

## Changelog

- **v1.0** — Initial version. Topic-agnostic template with Step 0 classification (8 types), Type-adaptation rules, Delivery Protocol (12 chunks with mandatory checkpoints), Quality checklist, USAGE section with drift-fix playbook.

---

*End of atom-template-general.md*
```