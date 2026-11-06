[🏠 Home](../../README.md) | [🗺️ Curriculum](../../CURRICULUM.md#phase-1--python-foundations) | **Phase 1**

# 1.1 Syntax, indentation, comments, statements

**Atom ID:** 1.1  
**Atom type:** C (Syntax)  
**Parent phase:** Phase 1

**Jump to Section:**
- [Preamble & Atom Map](#preamble--atom-map)
- [§1 — Syntax, Statements, Expressions](#1--syntax-statements-expressions)
- [§2 — Indentation](#2--indentation)
- [§3 — Comments](#3--comments)
- [§4 — Quotes, Literal vs. Evaluated, Multi-Argument print](#4--quotes-literal-vs-evaluated-and-multi-argument-print)
- [§5 — Blank Lines](#5--blank-lines)
- [§6 — Tabs vs. Spaces, TabError](#6--tabs-vs-spaces-and-taberror)
- [§7 — Escape Sequences and Raw Strings](#7--escape-sequences-and-raw-strings)
- [§8 — Line Continuation](#8--line-continuation)
- [§9 — Semicolons](#9--semicolons)
- [§10 — Triple-Quoted Strings](#10--triple-quoted-strings-and-the-not-a-comment-trap)
- [§11 — REPL vs. Script Execution](#11--repl-vs-script-execution)
- [§12 — Execution Model](#12--the-execution-model-parse-then-execute)
- [§13 — Error Categories](#13--error-categories-the-diagnostic-vocabulary)
- [§14 — File Encoding and Smart Quotes](#14--file-encoding-and-smart-quotes)
- [Common Mistakes](#common-mistakes-58)
- [Performance & Complexity](#performance--complexity)
- [Gate 3 — Gap Check](#gate-3--gap-check-for-atom-11)
- [Mini Status](#mini-status-where-this-puts-you)
- [Part B — Anchor Project](#part-b--anchor-project-service-status-card)
- [Part C — Project Bank](#part-c--progressive-project-bank)
- [Part D — Domain Coverage Matrix](#part-d--domain-coverage-matrix)
- [Part E — Interview-Style Problems](#part-e--interview-style-problems)
- [Part F — Quick-fire Q&A](#part-f--quick-fire-qa)
- [Part G — What To Do Now](#part-g--what-to-do-now)
- [Part H — Where We Go Next](#part-h--where-we-go-next)

---

## Preamble & Atom Map

### Preamble

This atom teaches the "grammar" of Python: how to write instructions the computer can read, how layout matters, and how to leave human notes. By the end you will build a **professional status card / CLI banner / receipt printer** — real, small artifacts that engineers actually write on day one of a job — using nothing but `print`, strings, and expressions.

**Mental model (one line):** *Python reads your file like a strict recipe — spelling, punctuation, line layout, and "ignore this note" markers all matter — and the parser checks the whole recipe before the cook starts.*

**Prerequisite Check** — I assume you can:
- Run Python somewhere (REPL `>>>` or a `.py` file in an editor).
- Open a text editor and save a file.
- Understand a program is a sequence of instructions.
- **Not yet** need: variables, data types, conditionals, loops, functions, lists.
- Accept `print(...)` as a beginner "display this" command for now (full behavior comes later).

If any of these is wrong, pause and adjust.

### Gate 1 — Atom Map

**A. NAMED (from title):** syntax, indentation, comments, statements, expressions → §1–§3.

**B. ADJACENT MUST-COVER:** whitespace asymmetry, case sensitivity, quote matching, literal vs. evaluated, multi-arg `print`, blank lines, tabs/spaces + `TabError`, escape sequences + raw strings, line continuation, semicolons, triple-quoted strings + "not a comment" trap, REPL vs. script, execution model, error categories, encoding basics → §1–§14.

**C. DEFERRED (tracked in `deferrals.md`):** variables (1.2), data types (1.3), operators in depth (1.4), f-strings (P2), docstrings (P3), type hints (later), regex (P4), file I/O (P6).

**D. FIRST-HOUR COLLISIONS (all covered):** nothing prints / `Print` NameError / missing paren / leading space / `#` inside string / mismatched quotes / smart quotes / mixed tabs+spaces / Windows path / `\` with trailing space / REPL-vs-script surprises / triple-quote-as-comment / `,` vs `;`.

**Anchor project direction:** *Service Status Card* (`status_card.py`).

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

# Part A — The Concept Ladder

## §1 — Syntax, Statements, Expressions
*(plus the two traps that bite first: whitespace and case)*

### 1. The problem this solves
You want a computer to display text and compute numbers. The computer can't read English. It needs a **fixed, unambiguous way to write instructions** — one that doesn't require it to guess. That fixed way is Python's *syntax*. Without it, every program would need its own dictionary.

### 2. Mental model
Think of an English sentence. **Syntax** = grammar. A **statement** = a complete sentence that *does* something ("Display this"). An **expression** = a phrase that *is worth something* ("2 + 3" is worth 5). Every program is a sequence of statements, and statements often *contain* expressions.

### 3. Full syntax — the three things you need right now
```python
print("literal text") # statement: display some text
print(2 + 3)          # statement: display the result of an expression
```

- `print` — the **command name**. Python knows this name; it displays whatever is inside the parentheses.
- `(...)` — **parentheses** wrap "what to display." They must be opened and closed.
- `"..."` — **quotes** mark literal text. Everything inside is text, not code.
- `2 + 3` — an **expression**. Python evaluates it (→ `5`) *before* `print` receives it.

Two facts about **whitespace** you will hit today, not in a later phase:
```python
print("Hi")       # ✓ canonical
print ( "Hi" )    # ✓ valid --- spacing BETWEEN tokens is ignored
 print("Hi")      # ✗ IndentationError --- leading space is grammar
```

And one fact about **case**:
```python
print("Hi")       # ✓ the name Python knows
Print("Hi")       # ✗ NameError --- names are case-sensitive
```

### 4. Behavior step-by-step
For `print(2 + 3)`:
1. Python **splits** the line into tokens: `print`, `(`, `2`, `+`, `3`, `)`.
2. It **checks grammar**: `print` + `(` + expression + `)` — valid statement.
3. It **evaluates** the expression `2 + 3` → `5`.
4. It **executes** the statement: displays `5`.

This is the crucial order to burn in: **grammar check first, evaluation second, display last.** That ordering is *why* a syntax error anywhere in a file blocks the whole file — we'll formalize that in §12. For now, just notice the order.

### 5. Line-by-line annotated code
```python
print("Hello, world!")
print(2 + 3)
```
- **Line 1** — `print` is the name. `("Hello, world!")` is the argument: one string. The quote characters are not part of the displayed text — they mark the beginning and end. Output: `Hello, world!`
- **Line 2** — `print` again. The argument this time is `2 + 3`, an **expression** with no quotes. Python evaluates `2 + 3` → `5`, then `print` displays `5`. If you had written `print("2 + 3")` — with quotes — Python would display the *text* `2 + 3`, not the number `5`. **Quote presence, not intent, is what decides literal vs. evaluated.** We'll flesh this out in §4.

### 6. When to use / when NOT to use
**Use `print`** whenever a human needs to *see* something: status messages, results, diagnostics. That is its only job.

**Do not use `print`** to store a value for later, or to build up a string piece-by-piece — it only *displays*, it doesn't *remember*. (Memory in Python comes from **variables**, which we'll learn in Atom 1.2.)

### 7. Sibling comparison (the four pairs beginners conflate)
- **Statement vs. expression** — a statement *does* something; an expression *is worth* something. `2 + 3` produces a value; `print(2 + 3)` performs a display action *and* contains the expression `2 + 3`. A statement can contain an expression. It cannot contain another statement.
- **Syntax vs. semantics** — syntax = "is the grammar valid?" semantics = "what does it mean?" `print("Hi")` is valid syntax *and* its meaning is clear. `print("Hi"` is invalid syntax — meaning never gets evaluated. `print("Hi"); print(unknown)` is valid syntax with a runtime problem (the name `unknown` doesn't exist).
- **SyntaxError vs. NameError** — the first is a *grammar* failure detected before any line runs; the second is a *runtime* failure that occurs after the program started. At Phase 1, almost every "my program doesn't run" bug is the first, and almost every "it ran for a bit and then broke" is the second.
- **Python's case sensitivity vs. English's tolerance** — in English, "Hello" and "hello" are the same word. In Python, `print` and `Print` are *different names*. `print` exists. `Print` does not. This is the single most common Phase-1 `NameError`.

### 8. 🔓 Unlocks
- **R0 (nano-drills):** verifying the single-rule behavior of `print`, quotes, and basic expressions.
- **R1 (first junior ticket):** printing the first banner line of the anchor project — but only *one* line so far.

You cannot yet build more than one line correctly. That's fine. §2 is what turns "one line" into "a valid file."

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## §2 — Indentation

### 1. The problem this solves
A program with more than one statement needs Python to know where each statement starts and ends. Many languages use `{ }` or `begin`/`end` markers. Python chose **leading whitespace** — the spaces at the very start of a line — to decide. That's a design choice with trade-offs, and it's why a single stray space at column 0 can break your whole file.

### 2. Mental model
Indentation is **the margin of the page**. Lines that start at the **same left position** belong to the same level. At the top of a program (no `if`, no `for`, nothing yet), all lines start at **column zero** — no leading spaces.

Later, when we learn blocks in Phase 2, indented lines will mean "inside this block." For now, the rule is simpler: **top-level lines get zero leading spaces.**

### 3. Full syntax
```python
print("first")
print("second")
print("third")
```
All three start at column 0. No spaces before `print`. That's the canonical top-level shape you'll see in every Phase-1 Python file.

### 4. Behavior step-by-step
For ` print("oops")` (one leading space):
1. Python's parser reads the line and inspects the leading whitespace.
2. At top level, no indentation is expected. It sees 1 space.
3. It looks for a *block header* (an `if`, `for`, `def`, etc.) that would justify this indentation. There is none.
4. It raises `IndentationError: unexpected indent`. **Parsing fails; the program does not run.**

### 5. Line-by-line annotated code
**Valid:**
```python
print("first")
print("second")
```
- **Line 1** — starts at column 0. Valid top-level statement.
- **Line 2** — starts at column 0. Valid top-level statement.

**Invalid:**
```python
print("first")
 print("second")
```
- **Line 1** — valid.
- **Line 2** — starts with one space before `print`. Parser sees indentation with no block open. Raises `IndentationError`. **Neither line prints** — because parsing fails before any execution.

### 6. When to use / when NOT to use
**Use indentation** deliberately: as a way of saying "these lines are at the same level." Top-level lines all line up at column 0.

**Do not** indent top-level lines "to make them look nice." In Python, a leading space is a *grammatical statement*, not cosmetic. The cosmetic part is the *spaces between tokens*, which we covered in §1 — those are ignored. This asymmetry (between = ignored, before = grammar) is the single most important thing to internalize about Python source layout.

> **[Deferred → Phase 2:** When we learn `if`/`for`, indentation becomes *required* inside a block. The rule doesn't change — indentation still *means* "block membership" — but you'll start intentionally writing it instead of erasing it. Nothing in Atom 1.1 requires indentation.**

### 7. Sibling comparison
- **Leading whitespace vs. spaces between tokens** — the first is grammar (unexpected indent = error); the second is cosmetic (`print ( "Hi" )` is valid). Nothing else in Python confuses beginners faster than this pair.
- **Leading whitespace vs. spaces inside a string** — `" DataTool"` has two spaces that are *text*, not indentation. Different concept entirely, covered properly in §4.
- **Indentation vs. blank lines** — blank lines are *not* indentation; the parser ignores them for level purposes. We'll cover blank lines properly in §5. For now, just don't confuse "empty line" with "line that starts with a space."

### 8. 🔓 Unlocks
- **R1 (multi-line tickets):** you can now write files with several statements and have Python accept them.
- **Part of the anchor project:** the top-of-file banner, the title, the author line — all must sit at column 0.

You still can't *comment* your code (that's §3) and you can't yet *evaluate* values alongside literal labels (§4). But the skeleton of the anchor project is now buildable.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## §3 — Comments

### 1. The problem this solves
Code communicates to two audiences: the computer, and the human who will read it later (including **you in three weeks**). The computer needs grammar. The human needs *why*. Python lets you put human-readable notes in a file that the computer **ignores completely** — so the note costs nothing at runtime but pays for itself in comprehension.

There's also a smaller use: temporarily **disabling a line** while testing without deleting it. Same mechanism (`#`), different intent.

### 2. Mental model
A comment is a **sticky note on the code**: visible to humans, invisible to the machine. When the parser reaches the `#` (outside a string), it stops reading that line — the rest is a note.

### 3. Full syntax
```python
# This whole line is a comment
print("Hello") # This part after # is a comment
```
Two shapes:
- **Full-line comment** — `#` is the first non-space character. Python ignores the entire line.
- **Inline comment** — `#` comes *after* code on the same line. Python runs the code, then ignores everything from `#` onward.

### 4. Behavior step-by-step
For `print("Hello") # greeting`:
1. Parser reads `print`, `(`, `"Hello"`, `)` — a complete statement.
2. Parser sees `#` **outside any string** — the comment marker.
3. It discards the rest of the line, up to the newline character.
4. Execution proceeds: `Hello` displays. The text ` greeting` never touches the machine.

Critical detail: the `#` must be **outside quotes**. Inside quotes it's just a character. We'll hammer this in §4, but flag it now.

### 5. Line-by-line annotated code
```python
# Print the current banner line
print("=== DataTool ===") # header
```
- **Line 1** — first character is `#`. Entire line ignored. It documents *why* the next line exists.
- **Line 2** — `print("=== DataTool ===")` executes → displays `=== DataTool ===`. Then `#` begins. The text ` header` (including the space after `#`) is discarded. Note that the space after `#` is **convention**, not a rule — `#header` is also valid — but it's universal style, so use it.

### 6. When to use / when NOT to use
**Use comments to say *why*,** not *what*. `# increment counter by 1` is noise (the code already says that). `# off-by-one fix: sum starts at 0 not 1 because index is exclusive` is valuable — it records a decision.

Also use comments to **temporarily disable a line** while testing. Never leave that in a commit.

**Do not** use comments:
- To restate obvious code.
- As a substitute for readable code — if you feel the need to explain *what* a line does, consider rewriting the line to be self-explanatory first.
- As a log of your emotional state (`# I hate this line`) — you will not be the only reader.
- As "block comments" via triple-quoted strings — a common trap we'll address in §10.

### 7. Sibling comparison
- **Comment vs. string literal** — `# hi` is a comment (invisible to Python). `"# hi"` is a string (a real value with the characters `# hi`). Same three characters, two completely different things. This is the "fence rule" — inside quotes, every special character stops being special.
- **Comment vs. `print` output** — a comment never appears on screen. A `print` call produces output. If you see `# hi` printed on the terminal, that `#` was **inside a string**, not a real comment.
- **Comment vs. triple-quoted string (preview, deferred)** — `"""..."""` looks like a block comment but is a **string value** that gets constructed and then thrown away. Real comments disappear; fake ones still execute as objects. Formal coverage in §10.
- **Comment vs. docstring (Phase 3)** — `"""..."""` at the top of a *function* or *module* becomes an attached documentation string, retrievable via `help(...)`. That's the payoff. Not now.
- **Full-line vs. inline comments** — full-line for "why this block exists"; inline for "why this specific line does what it does." Keep inline comments short; if you need three sentences, move it to a full-line above.

### 8. 🔓 Unlocks
- **R1 ticket: adding an explanation to a printed banner.**
- **R4 anchor variant: audit-comment mode** — a compliance-style variant of the anchor where the file must include both an inline "verified by ops" comment *and* a full-line "purpose" comment, and the test is that they do **not** appear in the output.
- **The professional habit** that separates "my script works" from "my script is reviewable."

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## §4 — Quotes, Literal vs. Evaluated, and Multi-Argument `print`

### 1. The problem this solves
You saw in §1 that `print("2 + 3")` displays text and `print(2 + 3)` displays `5`. That's the atom's single most important distinction, and it deserves its own section. You'll also discover that `print` can take **more than one thing** inside its parentheses — which is the only way (until Phase 2's f-strings) to display a label *and* a computed value on the same line.

### 2. Mental model
Quotes are a **fence**. Inside the fence, Python is blind — every character is text. Outside the fence, Python reads grammar. Adding or removing quotes changes the *category* of what's inside, not just its appearance.

### 3. Full syntax
```python
print("literal text") # one argument: a string
print(2 + 3)          # one argument: an expression → 5
print("Result:", 2 + 3) # two arguments: string, expression
print('single quotes work too')
```
For multi-argument `print`: separate arguments with **commas**. `print` inserts a **single space** between each argument when it displays.

### 4. Behavior step-by-step
For `print("Result:", 2 + 3)`:
1. Parser sees `print(` → an argument list.
2. Argument 1: `"Result:"` → a string, kept as-is.
3. Comma separates.
4. Argument 2: `2 + 3` → an **expression**. Python evaluates it → `5`.
5. `print` receives two *values* (`"Result:"` and `5`). It displays them **separated by one space**: `Result: 5`.

For `print("2 + 3")`:
1. Parser sees one argument: `"2 + 3"` → a string. The `+` is **inside the fence**, so it's text, not an operator.
2. `print` displays it verbatim: `2 + 3`.

### 5. Line-by-line annotated code
```python
print("2 + 3")
print(2 + 3)
print("2 + 3 =", 2 + 3)
```
- **Line 1** — `"2 + 3"` is one string. Displays `2 + 3`.
- **Line 2** — `2 + 3` is an expression. Evaluates to `5`. Displays `5`.
- **Line 3** — two arguments: `"2 + 3 ="` (a string) and `2 + 3` (an expression → `5`). `print` displays them with one space between: `2 + 3 = 5`. **This is the pattern that makes the anchor project's `Result : 42` line possible.**

### 6. When to use / when NOT to use
**Use quoted strings** when the text itself is the point — labels, banners, messages.
**Use expressions** when you want the *value* — computations, totals, diagnostics.
**Use the multi-argument form** when you need both on one line — the label *and* the value, shown together.

**Do not** quote an expression hoping it will be evaluated — inside quotes it becomes literal text. **Do not** unquote a label hoping Python will guess it's text — outside quotes, letters become *names*, and names must exist, or you get `NameError`.

### 7. Sibling comparison
- **String vs. expression** — a string *is* a value (fixed text); an expression *produces* a value (via computation). `"2 + 3"` is a value whose content happens to look like math; `2 + 3` produces a *different* value.
- **Single argument `print(x)` vs. multi-argument `print(a, b)`** — the first displays one value; the second displays multiple values separated by a single space. The space between them is `print`'s default behavior, not part of either value.
- **Single vs. double quotes** — `"Hi"` and `'Hi'` produce identical string values. The *only* reason to prefer one is when your text contains the other: `'He said "hi"'` needs single quotes on the outside.

### 8. 🔓 Unlocks
- **R1 ticket: the "Check / Result" pair** — literally the `print("Result :", 6 * 7)` pattern from the anchor.
- **R3 variant: computed diagnostic line** — same job, different formula and label.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## §5 — Blank Lines

### 1. The problem this solves
Two unrelated blocks of statements sit side-by-side. Without visual separation, the file reads as one undifferentiated wall. Humans need *grouping*. Blank lines provide it — and the parser mostly ignores them, which is exactly what you want.

### 2. Mental model
A blank line is **invisible to the parser for indentation** but **visible to the reader**. It groups, it breathes, it doesn't break anything at parse time.

### 3. Full syntax & the rules
```python
# Startup card

print("===")
print("DataTool")
print("===")
```

1. **A blank line is ignored by the parser.** Between two statements, it changes nothing about execution.
2. **A blank line does not end a block.** Inside an `if` body (later), a blank line between two indented statements doesn't close anything. **Dedenting** closes blocks; blank lines don't.
3. **A whitespace-only line counts as blank.** `" "` (spaces-only) parses like `""`. Avoid creating them — most editors strip trailing whitespace on save.
4. **PEP 8 conventions** (style, not grammar — but every professional codebase enforces them):
   - Two blank lines between top-level function/class definitions (Phase 3+).
   - One blank line between methods (Phase 3+).
   - Use blank lines sparingly *inside* a function body, usually to separate logical sections.
   - End every file with **exactly one newline** — no trailing blank lines, no missing final newline.
5. **Blank lines do not error, ever.** You cannot cause `IndentationError` by *adding* blank lines. You can by *removing* required indentation, but that's §2 territory.

### 4. Behavior step-by-step
For the code block above:
1. Parser sees `#` → discards line 1.
2. Parser sees an empty line → skips.
3. Parser sees `print("===")` → statement, valid.
4. Repeats for remaining lines.
5. Executes: three lines displayed. **Identical output to the version without the blank line.**

### 5. Line-by-line annotated code
The blank line at line 2 is purely organizational. It groups the file as "title comment / code body." A reviewer's eye lands on the comment, then the code — without the blank line, the comment visually glues to the first print and both feel like noise.

### 6. When to use / when NOT to use
**Use blank lines** to separate logical sections: header comment vs. body, config vs. computations, before/after a multi-line block.

**Do not use** blank lines expecting them to close a block — that's what dedenting does. **Do not** leave multiple blank lines at end of file; one final newline is enough.

### 7. Sibling comparison
- **Blank line vs. comment** — a comment *records a reason*; a blank line *records separation*. One is text, one is absence of text. Both are invisible to the parser, so beginners sometimes use a blank line where they should use a comment (and vice versa).
- **Blank line at top level vs. blank line inside a block** — same parsing rule (ignored). But inside a block, a blank line can *look* like it's ending the block when it isn't. That visual trap is the entire reason rule #2 above is highlighted.

### 8. 🔓 Unlocks
- **Anchor project's visual grouping** — separating the banner section from the metric section from the footer section.
- **R4 variant: readability review** — a "same output, better readability" hardening project.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## §6 — Tabs vs. Spaces, and `TabError`

### 1. The problem this solves
A tab character and four spaces **look identical on screen** but are **different byte sequences**. If two lines use different ones at the same level, Python can't decide if they belong to the same block. Python 3 raises `TabError` (a subclass of `IndentationError`) to prevent silent "works on my machine" bugs.

### 2. Mental model
**Indentation is measured in characters, not in visible width.** A tab is one character. A space is one character. They are not interchangeable — even when they *look* the same.

### 3. Full syntax & rules
1. **Never mix tabs and spaces for indentation in the same file.** Python 3 raises `TabError` when it detects this in the same block.
2. **Convention: 4 spaces per indent level** (PEP 8). Any consistent width is *legal* (2, 3, 8), but 4 is universal.
3. **Set your editor to insert spaces when you press Tab.** Every editor (VS Code, PyCharm, vim, nano) has this setting. Turn it on once, forget it forever.
4. **`TabError` is a subclass of `IndentationError`** — same family, more specific diagnosis.

### 4. Behavior step-by-step
```python
def f():
	print("tab-indented")
    print("space-indented")
```
1. Line 2's indentation is one tab byte.
2. Line 3's indentation is four space bytes.
3. At top-level of the `def` body, both *render* at the same width — but the parser sees different bytes at what looks like the same level.
4. `TabError: inconsistent use of tabs and spaces in indentation` on line 3.

### 5. Line-by-line diagnostic
If you need to *prove* the bug exists, run:
```bash
python -c "print(open('file.py','rb').read())"
```
You'll see `\t` where tab was used, and ` ` (four spaces) where spaces were used. **Look at bytes, not at rendered indentation.**

### 6. When to use / when NOT to use
**Use spaces** (configured as 4 per level). Always. Universal convention.

**Do not use tabs** for indentation in Python. Some legacy codebases do — but you will inherit editor settings, not tap out tabs by hand.

### 7. Sibling comparison
- **`TabError` vs. `IndentationError`** — `TabError` is the specific "mixed characters" case. `IndentationError` is the broader "indentation is wrong in a single style" case.
- **Tab used as indentation vs. `\t` inside a string** — completely different. `"\t"` inside a string is intentional, safe, and displays as a tab character in output. A raw tab byte used *as indentation* is the problem. Don't conflate them.

### 8. 🔓 Unlocks
- **R4 variant: cross-editor compatibility** — copy-paste from the web, run on a teammate's machine. This is the exact class of bug that ship-breaking PRs fix.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## §7 — Escape Sequences and Raw Strings

### 1. The problem this solves
You need to put a **newline** or **tab** *inside* a string's value, or a **quote character** inside a quoted string. You also need to print a **literal backslash** — but `\` is normally an escape marker. All four cases need explicit syntax.

### 2. Mental model
Inside a string, `\` is a **prefix meaning "the next character is special."** It changes one character into something else. `\n` becomes newline, `\t` becomes tab, `\\` becomes one literal backslash, `\"` becomes a literal quote.

### 3. Full syntax — the essential escapes
| Escape | Produces | Typical use |
|---|---|---|
| `\n` | newline | multi-line display |
| `\t` | tab character | column-ish output (but see caution below) |
| `\\` | one literal `\` | Windows paths, literal backslashes |
| `\"` | `"` inside `"..."` | quoting without switching styles |
| `\'` | `'` inside `'...'` | same idea |
| `r"..."` | raw string | **no escape processing** — everything literal |

### 4. Behavior step-by-step
For `print("Hello\nWorld")`:
1. Parser enters string mode.
2. Reads `H`, `e`, `l`, `l`, `o` → literal.
3. Sees `\` → knows escape is next.
4. Reads `n` → translates to newline character (a single byte in the value).
5. Reads `W`, `o`, `r`, `l`, `d` → literal.
6. `print` displays. The embedded newline causes a line break.
7. `print` adds its own trailing newline (default behavior).

Output:
```
Hello
World
```

### 5. Line-by-line — the classic Windows path bug
```python
print("C:\temp\new_data")
```
**What you meant:** display `C:\temp\new_data`.

**What you get:** `C:` then `\t` becomes a tab, then `emp`, then `\n` becomes a newline, then `_data`. Result: `C:<TAB>emp` on line 1, `_data` on line 2.

Two fixes:
```python
print("C:\\temp\\new_data") # double every backslash
print(r"C:\temp\new_data")  # raw string --- backslashes are literal
```
The raw-string prefix `r"..."` is the cleaner fix for paths, regex patterns, and any text where you literally mean `\` to be a character.

### 6. When to use / when NOT to use
**Use `\n` and `\t`** when you genuinely want the *effect* (a line break, a tab).
**Use `r"..."`** when the backslash is meant literally — file paths, regex, escape-heavy text.
**Use `\"`** only when you can't switch quote styles (rare — usually `'He said "hi"'` is clearer).
**Do not use `\t` for column alignment** — tab widths vary by terminal, so alignment breaks across environments. Count spaces (as in the anchor project) or wait for Phase 2's alignment specifiers.

### 7. Sibling comparison
- **`\n` inside a string vs. literal newline in the source** — the first is a character in the *value*; the second usually breaks parsing (unless the string is triple-quoted, §10).
- **`"a\nb"` vs. `print("a"); print("b")`** — visually identical output, but `"a\nb"` is *one string of length 3* while two `print` calls are *two strings*. When we meet variables (§1.2), this distinction matters — the first string is a single value; the second is two values that happened to print adjacently.
- **`\"` vs. switching to `'...'`** — both display `"`. The escape form is only *required* when you need both quote styles in the same string.

### 8. 🔓 Unlocks
- **R3 variant: escaped path display** — the anchor prints a config file path like `Config : C:\app\config.yaml` without triggering a tab or newline. Real bug, real fix.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## §8 — Line Continuation

### 1. The problem this solves
Statements can get long. You want to break them across multiple physical lines **for readability** — but Python sees a newline as a statement boundary. Two ways to say "keep reading": **implicit** (inside brackets) and **explicit** (backslash at end of line).

### 2. Mental model
**Implicit:** "I'm inside `(` `[` `{` — the parser is patient until I close." **Explicit:** "I'm putting a `\` at end of line — a signal to continue."

### 3. Full syntax
```python
# Implicit --- inside brackets (PREFERRED)
print(
    "Hello world"
)

# Explicit --- backslash at end of line (RARE)
print("Hello " \
      "world")
```

### 4. Behavior step-by-step
For the explicit form:
1. Parser reads `print("Hello "` — incomplete (paren not closed).
2. It looks at the last non-whitespace character: `\` — "continue on next line."
3. It appends line 2: `print("Hello " "world")`.
4. **Adjacent string literals concatenate**: `"Hello " "world"` → `"Hello world"`.
5. `print` displays `Hello world`.

### 5. The two traps
```python
print("Hello" \ ← trailing space after \ --- SyntaxError
      "world")
```
1. **The `\` must be the last character on the line — even one trailing space breaks it.** → `SyntaxError: unexpected character after line continuation character`. Editors that auto-trim trailing whitespace save you here.
2. **Adjacent strings concatenate without a space.** `"Hello" "world"` → `"Helloworld"`. You need explicit spaces inside the strings.

### 6. When to use / when NOT to use
**Use implicit (brackets)** whenever possible — idiomatic, no invisible characters to trip on.
**Use explicit `\`** only when you can't wrap in brackets (rare in beginner code). Avoid.
**Do not use either to fake a multi-line string value** — that's triple quotes (§10), which is a *different* thing.

### 7. Sibling comparison
- **`\` continuation vs. `\n` in a string** — the first continues the *source statement*; the second embeds a *newline in the string value*. They look similar, do completely different things.
- **Implicit (brackets) vs. explicit (`\`)** — implicit is a parser feature of brackets; explicit is a parser feature of backslash. Prefer brackets.

### 8. 🔓 Unlocks
- **Anchor project: a long banner line** — a status line with multiple components can be written across lines for readability *if you wrap it in `print(` `)` correctly*. The project's reference solution won't *need* this, but the variant will.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## §9 — Semicolons

### 1. The problem this solves
One-line, two-statement Python. Legal, occasionally useful in shell one-liners, but **actively harmful in files** because it defeats line numbers in error tracebacks.

### 2. Mental model
`;` is a **statement separator** — same role a newline plays. Second-class citizen: allowed, discouraged, hides errors.

### 3. Full syntax
```python
print("a"); print("b")
```
Two statements on one line. Legal in both the REPL and scripts.

### 4. Behavior step-by-step
For `print("one"); print(unknown); print("three")`:
1. Parser splits into three statements.
2. Parses them — all three are grammatically valid.
3. Executes line 1 → displays `one`.
4. Executes line 2 → `NameError: name 'unknown' is not defined`.
5. Line 3 does not run.

The **traceback says "line 1"** — but line 1 contains *three* statements. You have no idea *which* one failed without reading the message carefully. Diagnostic pain.

### 5. Line-by-line comparison
```python
print("one"); print(unknown); print("three") # traceback: line 1
```
vs.
```python
print("one")
print(unknown) # traceback: line 2 --- instant locate
print("three")
```
Same failure. Vastly different debugging effort.

### 6. When to use / when NOT to use
**Use** for `python -c "stmt; stmt"` one-liners in a shell, or interactive pokes.
**Do not use** in a `.py` file you intend to keep, read, or debug. It defeats line numbers.

### 7. Sibling comparison
- **`;` vs. newline** — same role (statement separator). Newline is preferred.
- **`;` vs. `,`** — `,` separates *arguments to one function call*; `;` separates *statements*. Totally different. Beginners conflate them.
- **`;` vs. `:`** — `:` (Phase 2) opens a block; `;` is a separator. Different families.

### 8. 🔓 Unlocks
- **R4 hardening: the "why is the line number useless?" demo** — you'll see a real bug where a `;` line obscures the failure.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## §10 — Triple-Quoted Strings (and the "not a comment" trap)

### 1. The problem this solves
You need a string that **spans multiple lines** *literally* — where the newlines are part of the value, not just the source. You also need a way to include both `"` and `'` inside without escaping.

### 2. Mental model
`"""` or `'''` opens a string that **doesn't close until the matching triple appears**. Everything inside — including newlines — is literal.

### 3. Full syntax
```python
print("""Line one
Line two
Line three""")
```

### 4. Behavior step-by-step
1. Parser sees `"""` → enters multi-line string mode.
2. Every character up to the closing `"""` — **including actual newline bytes** — becomes part of the string value.
3. `print` displays them. Because `print` adds its own trailing newline, you often see one blank line after a triple-quoted print.

### 5. The "not a comment" trap
```python
"""
This looks like a comment.
"""
print("Still runs")
```
**What is actually happening:** the triple-quoted block is an **expression statement** — a valid statement whose value is a string that **gets constructed and then discarded** (nothing uses it). It is *not* a comment. Semantically different:

- **A comment** — invisible to Python. Never constructed. Cannot be inspected at runtime.
- **A triple-quoted string** — a real value. Python *constructs* the string object, then throws it away because nothing references it. (This is why it looks like a comment.)

At Phase 1, the visible effect looks the same — nothing prints. From Phase 3, this diverges: `"""..."""` at the top of a *function* or *module* becomes a **docstring**, retrievable via `help(...)`. That's the reason triple quotes exist.

**The rule for now:** *"I want it ignored"* → use `#`. *"I want multi-line text as a value"* → use `"""..."""`.

### 6. When to use / when NOT to use
**Use** for genuinely multi-line text — usage/help messages, SQL queries (Phase 4+), literal newline content in values.
**Do not use** as a "block comment." It isn't one. Use `#` on multiple lines instead.

### 7. Sibling comparison
- **`"""..."""` vs. `"..."`** — same escape rules, but multi-line and can contain the other quote style freely.
- **`"""..."""` vs. `#`** — comment is invisible; string has a value. At Phase 1 they look equivalent. From Phase 3 they diverge (docstrings).
- **`"""` vs. `'''`** — identical behavior. Pick one per project. PEP 8 uses `"""` for docstrings.

### 8. 🔓 Unlocks
- **R3 variant: multi-line help text** — the anchor gains a `--help`-style multi-line message. Real-world: every CLI tool has one.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## §11 — REPL vs. Script Execution

### 1. The problem this solves
You typed `python` and got a `>>>` prompt. Or you ran `python my_file.py`. These are **different execution models** with different parsing behavior — which is why "it worked in the tutorial, but not in my file" happens, and why "nothing printed" can be diagnosed instantly once you know the difference.

### 2. Mental model
**REPL = conversational.** Reads-evaluates-prints-loops, one chunk at a time, auto-displays values of expressions. **Script = compile-then-run.** Reads the entire file, parses it, then executes statements — but only if the *whole file* parses.

### 3. The three differences that matter
**Difference 1 — Auto-display of expression values.**
```
>>> 2 + 3
5
```
The REPL shows the value of any expression you type. In a script, `2 + 3` alone displays **nothing** — it computes `5` and discards it. **This is why bare expressions seem to "work" in the REPL but "do nothing" in a file.**

**Difference 2 — Error timing.**
```
>>> print("hi")
hi
>>> print("broken
... print("more")
```
You saw line 1's output **before** line 2's syntax error — because the REPL is incremental. In a script, a syntax error anywhere in the file means **no line runs**, including line 1. *This is the origin of every "nothing prints" mystery.*

**Difference 3 — Blank lines and blocks (preview, Phase 2).** In the REPL, a blank line inside an indented block **ends the block** — that's how you tell the REPL "I'm done typing this." In a script, a blank line inside a block is *ignored*. Same characters, opposite behavior.

### 4. Behavior step-by-step (script case)
For a file:
```python
print("a")
print("b"
print("c")
```
1. Parser reads the **whole file**. Line 2's paren is unclosed → `SyntaxError`.
2. Parse fails. Execution never starts.
3. **Nothing prints** — not even valid line 1.

In the REPL, pasting the same three lines one at a time: line 1 would run and print `a`. Line 2 would error. Line 3 would never be reached. **Partial output, different failure point.**

### 5. Line-by-line implication
Do **exercises in scripts**, not the REPL, unless the exercise explicitly says REPL. The anchor project assumes **script semantics** — all-or-nothing parse. Running it in the REPL will produce different error and output timing and confuse your diagnosis.

### 6. When to use / when NOT to use
**Use the REPL** for quick experiments, exploring a value, checking a syntax hunch. **Use scripts** for anything you'll keep, share, or debug precisely.

### 7. Sibling comparison
- **REPL vs. Jupyter notebook** — the notebook is closer to the REPL: incremental, auto-displays last expression, allows partial execution. Not a script.
- **`python my_file.py` vs. `python -c "..."`** — `-c` is closer to a script (parses whole string, then runs), but supports only one line — hence the `;` temptation from §9.
- **`python -i my_file.py`** — runs the script, then *drops into the REPL*. Hybrid. Useful for debugging later.

### 8. 🔓 Unlocks
- **All exercises in Part B and C** assume script semantics. This section is *why* the "nothing prints" diagnostic works.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## §12 — The Execution Model: Parse, Then Execute

### 1. The problem this solves
Beginners assume Python "runs line by line." It doesn't. Python first **parses the entire file** for syntax errors. **If any line has a syntax error, no line runs.** This one mental model eliminates half of Phase-1 confusion.

### 2. Mental model
**Two-phase.** **Phase 1 — Parse:** the whole file must be grammatically valid. **Phase 2 — Execute:** run statements top to bottom. Phase 2 only begins if Phase 1 finishes with zero errors.

### 3. Full syntax — the illustration
```python
print("first")
print("second"
print("third")
```

### 4. Behavior step-by-step
1. **Parse phase:** scan every line. Line 2 has an unclosed `(`. → `SyntaxError`. Parse **fails**.
2. **Execute phase:** never begins. **Nothing prints.**
3. If line 2 had been fixed, parse passes. Execute runs line 1 → `first`, line 2 → `second`, line 3 → `third`.

### 5. Line-by-line annotated code
```python
print("one")   # valid
print("two"    # ← SYNTAX ERROR: unclosed paren
print("three") # valid, but irrelevant
```
- Line 1: parse ✓
- Line 2: parse ✗ — **parse phase fails here**
- Line 3: parse ✓ — but never reached
- **Result:** zero output, `SyntaxError` on line 2. Not "one, then a crash." Nothing.

### 6. When to use / when NOT to use
Use this model whenever *"my program does nothing"* — it's nearly always a syntax or indentation error blocking Phase 1. Use it whenever *"my program ran partway then broke"* — that's a **runtime** error (name error, type error, division by zero), which is Phase-2 territory.

### 7. Sibling comparison
- **Parse-time vs. runtime errors** — `SyntaxError`, `IndentationError`, `TabError` are parse-time (nothing runs). `NameError`, `TypeError`, `ZeroDivisionError` are runtime (the program started). Knowing which category you're in cuts your debugging search in half.
- **Script parse-then-run vs. REPL incremental parse** — the script's parse phase is whole-file; the REPL parses one chunk at a time.

### 8. 🔓 Unlocks
- **Every debugging exercise in Part B.** This is *the* frame.
- **Part E interview question.** This is what a strong answer centers on.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## §13 — Error Categories: The Diagnostic Vocabulary

### 1. The problem this solves
Error messages are *information*, not punishment. Each category tells you **what phase you're in** and **what class of fix you're looking for**. Learning to *read* them is a skill; it starts here.

### 2. Mental model
An error message is a **doctor's note**: category (kind of problem), location (line + caret column), hint (what was expected). Read the category *first* — it determines your whole approach.

### 3. The categories you'll meet in Atom 1.1
| Category | Phase | Typical cause at Phase 1 |
|---|---|---|
| `SyntaxError` | **Parse** (nothing runs) | Missing `)`, missing `"`, mismatched quotes, `\` with trailing space, smart quotes |
| `IndentationError` | **Parse** (nothing runs) | Leading space at top level |
| `TabError` | **Parse** (nothing runs) | Tabs + spaces mixed |
| `NameError` | **Runtime** (program started) | Wrong case (`Print`), typos, use of undefined names |

### 4. Behavior — how to read a traceback
```
File "card.py", line 3
    print("Build: 2024-01-15)
          ^
SyntaxError: unterminated string literal (detected at line 3)
```
1. `File "card.py", line 3` — **where.**
2. `print("Build: 2024-01-15)` — the offending line, **echoed.**
3. `^` — **column** where Python gave up.
4. `SyntaxError:` — **category.** Parse phase → nothing ran.
5. `unterminated string literal` — **hint.** Fix: close the string.

**Workflow:** read category → read line → look at `^` column → fix exactly there.

### 5. Line-by-line — three examples
```python
 print("hi")
```
→ `IndentationError: unexpected indent`. Fix: remove leading space.

```python
Print("hi")
```
→ `NameError: name 'Print' is not defined`. **Program started; execution failed at this line.** Fix: lowercase.

```python
print("hi)
```
→ `SyntaxError: unterminated string literal`. Fix: close the quote.

### 6. When to use / when NOT to use
Use the category **first**, before touching code.

Do not "fix" by deleting lines or re-typing — that hides the lesson. Fix the exact location.

### 7. Sibling comparison
- **`SyntaxError` / `IndentationError` / `TabError`** — all parse-phase. Distinguish by *what* is wrong, but they all mean "nothing runs."
- **`NameError`** — runtime. Program started. Different fix category entirely (typo, wrong case, later: forgot to define).
- **Caret (`^`) vs. line number** — caret is precise; line is coarse. Read both.

### 8. 🔓 Unlocks
- **All of Part B and E** — this is the vocabulary they'll be graded against.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## §14 — File Encoding and Smart Quotes (LOW, mention only)

Not a major topic for Atom 1.1 — covered here for completeness so it doesn't bite you from a copy-paste:

- **Python 3 files default to UTF-8.** No special header needed (unlike Python 2's `# -*- coding: utf-8 -*-`).
- **Smart quotes** (`“ ” ‘ ’`) come from word processors. They look like `"` and `'` but are different Unicode characters. Copy-pasting into Python → `SyntaxError: invalid character '“'`. Fix: type straight quotes in a plain-text editor.
- **Shebang line** (`#!/usr/bin/env python3`) — `#` comment to Python, interpreter directive to Unix. Harmless, useful only if you make the file executable.
- **Line endings** (CRLF vs. LF) — Python 3 handles both. No action needed.

Skip unless you hit them. If you copy code from anywhere with a "smart" quote in it, this is the section to return to.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## Common Mistakes (5–8)

**M1 — Missing closing `)` or `"`**
```python
print("Hello
```
→ `SyntaxError: unterminated string literal`. Parse fails; **no output.** **Fix:** match every opening quote/paren. **Real-world consequence:** "the whole service fails to start" because one diagnostic line has a typo.

**M2 — Wrong case (`Print`)**
```python
Print("hi")
```
→ `NameError: name 'Print' is not defined`. **Program started; failed on this line.** **Fix:** lowercase. **Real-world consequence:** deployment succeeds, service crashes at the first log line.

**M3 — Unexpected leading space**
```python
 print("hi")
```
→ `IndentationError: unexpected indent`. **Fix:** remove leading space. **Real-world consequence:** copy-paste from a doc with an invisible leading space.

**M4 — `#` inside a string printed literally**
```python
print("audit: clean # verified by ops")
```
→ Prints the whole thing including `# verified by ops`. Not a comment — it's *inside the fence*. **Fix:** move `#` outside the quotes.

**M5 — Mismatched quote styles**
```python
print("Hello')
```
→ `SyntaxError: unterminated string literal`. **Fix:** `print("Hello")` or `print('Hello')` — match open and close.

**M6 — Smart quotes from a word processor**
```python
print(“Hello”)
```
→ `SyntaxError: invalid character '“'`. **Fix:** retype straight quotes in a code editor.

**M7 — Windows path with unescaped backslash**
```python
print("C:\temp\new_data")
```
→ No error, **but wrong output** (tab + newline). **Fix:** `print("C:\\temp\\new_data")` or `print(r"C:\temp\new_data")`. **Real-world consequence:** silent corruption of paths, the most insidious bug class because it doesn't error.

**M8 — Expecting earlier lines to have run before a later syntax error**
```python
print("one")
print("two"
```
→ **Nothing prints.** Parse failed. **Fix:** fix line 2. **Real-world consequence:** spending twenty minutes debugging valid code (line 1) when the real problem is elsewhere.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## Performance & Complexity

Honest and short:

- **Each `print` is effectively O(1)** in logic — a fixed amount of work per call. Cost grows only with the *length* of what you display, not with anything else.
- **A file with N statements runs in O(N)** — cost scales linearly with lines. Double the statements, double the runtime. Trivial at your scale.
- **Comments cost zero at runtime** — stripped before execution. They cost only file size and reading time for humans.
- **Parse-time cost:** Python parses the entire file once before executing. For a few hundred lines, imperceptible. The **consequence** of parse-time cost is *semantic*, not performance: a single parse error means nothing runs.
- **Memory:** a string occupies memory proportional to its length. `"a\nb"` (length 3) is three characters. Not a concern at your scale — just know that embedded newlines are real bytes, not free.

The real lesson at Phase 1: **cost scales with statement count; correctness scales with your model of parse-vs-execute.**

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## GATE 3 — GAP CHECK for Atom 1.1

```text
GAP CHECK --- Atom 1.1

Covered (Map A --- NAMED):
✓ syntax (§1)
✓ indentation (§2, §6)
✓ comments (§3)
✓ statements (§1, §5, §8, §9)
✓ expressions (§1, §4)

Covered (Map B --- ADJACENT MUST-COVER):
✓ whitespace asymmetry (§1, §2)
✓ case sensitivity (§1, §13)
✓ quotes / matching (§3, §4, §7, §13)
✓ literal vs. evaluated (§4)
✓ multi-arg print (§4)
✓ blank lines (§5)
✓ tabs vs. spaces / TabError (§6)
✓ escape sequences (§7)
✓ raw strings (§7)
✓ line continuation (§8)
✓ semicolons (§9)
✓ triple-quoted strings + not-a-comment trap (§10)
✓ REPL vs. script (§11)
✓ execution model / parse-vs-execute (§12)
✓ error categories (§13)
✓ file encoding basics (§14, mention only)

Deferred (Map C --- logged in deferrals.md):
→ variables / assignment ............ Atom 1.2
→ data types (int, float, str, bool, None) Atom 1.3
→ operators in depth ................. Atom 1.4
→ f-strings (interpolation, alignment) .... Phase 2
→ docstrings ......................... Phase 3
→ type hints ......................... later
→ regex / advanced escaping ......... Phase 4
→ shebang / file permission ......... LOW, mentioned only
→ CRLF vs. LF ........................ LOW, mentioned only

Discovered during teaching:
→ (add here as you encounter them; the Coverage Matrix in Part D will
   surface anything still unmapped)

Still missing if you apply Map D strictly (first-hour collisions)?
Each of the 14 first-hour collisions from the Atom Map is covered by at
least one of: §1--§13 (concept), Common Mistakes M1--M8, or Part B/C
exercises. Full mapping is closed out by Part D.

Recommend: proceed to Part B (Anchor Project).
```

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

## Mini Status: Where this puts you

You can now, using only §1–§14:
- Write a **multi-line** Python file that Python will **parse and run.**
- **Display** literal text and simple expressions.
- **Annotate** your file with comments a reviewer can read.
- **Diagnose** exactly why a file refuses to run (parse vs. runtime).

What you cannot yet do:
- **Store** values for later — that needs Variables (Atom 1.2).
- **Group** statements with conditional logic (if/else) — that's Phase 2.

That ordering is intentional. Every one of those missing pieces is a **prerequisite for a specific rung of the anchor project**, and every one will be unlocked before we ask you to build the rung that needs it.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

# Part B — Anchor Project: Service Status Card

The atom's centerpiece. Everything in Part A exists so you can build *this*. Read the spec carefully — **do not peek at the reference solution until you've attempted the build**.

## Why this is real

SREs, platform engineers, and ops on-call teams routinely keep small "status card" scripts as lightweight diagnostics — the ones that never quite made it into a monitoring system because they were faster to write than to alert on. Building one teaches you to write output a human can read *under pressure*.

## Realism Contract

```
STAKEHOLDER : On-call engineer for prod-eu-west-1.
              Needs a 2-second health snapshot to paste into a Slack
              incident channel while triaging an alert.
INPUT       : None — self-contained. Four metric values are hardcoded
              for now. (Phase 5 wires it to real data.)
OUTPUT      : Fixed-width text card, 40 chars wide, renders correctly
              in Slack's monospace block. Three sections: banner,
              metrics, notes. Multi-line footer.
FAILURE     : Card unreadable or wrong if —
              (a) Config path displays as C:<TAB>emp instead of the
                  literal Windows path (escape bug, §7)
              (b) Mem free prints "7 * 512 MB" instead of "3584 MB"
                  (literal-vs-evaluated bug, §4)
              (c) any line's alignment drifts (countable characters)
              (d) missing paren/quote/leading-space blocks the whole
                  file from parsing (parse-vs-execute, §12)
```

## The Spec — exact expected output

```
========================================
  Service Status  ·  prod-eu-west-1
  Generated by status_card.py
========================================

Uptime     : 14 days
Mem free   : 3584 MB
Disk free  : 128 GB
Latency p99: 250 ms

----------------------------------------
Notes:
  Config    : C:\srv\data\config.yaml
  Log path  : /var/log/svc
  Status    : healthy
----------------------------------------

Run status_card.py --help for usage.
Report issues to ops@example.com.
```

Read it carefully. Note:
- Top rule: **40** equals signs; second rule: **40** dashes.
- Middle dot `·` in the title (Unicode char — copy-paste from spec).
- **Metrics block** colons at column **12**.
- **Notes block** colons at column **13** (2-space indent + inner alignment).
- **Four** blank lines in output.
- Backslashes in the path must survive.

## Hard requirements

1. Exact output. Byte-for-byte. No trailing spaces. Exactly one final newline.
2. Only these features: `print(...)`, string literals (`"..."` / `'...'` / `r"..."` / `"""..."""`), integer arithmetic (`*`), `#` comments, blank lines. **No variables, f-strings, functions, loops, imports, `+` string concatenation.**
3. **Mem free must be computed.** Display `3584` as the *result* of an expression (`7 * 512`). Do **not** type `3584` as text.
4. **Uptime, Disk free, Latency must be literal strings.**
5. **Config path must survive as a Windows path.** Use `r"..."` or double every backslash.
6. **Footer must use one triple-quoted string** in one `print` call.
7. At least one full-line comment at top; at least one inline comment on the Mem free line. **Neither may appear in output.**
8. All top-level lines start at column 0.
9. No semicolons. No tabs. One statement per line.
10. File ends with exactly one newline.

## Milestones — build in this order

**M1 — Header only (5 output lines + trailing blank).** Top comment, top rule, title, subtitle, bottom rule, blank line. Verify 40 `=` chars per rule by counting.

**M2 — Metrics block.** Four lines below the blank line. Uptime / Disk free / Latency literal strings; Mem free computed with `print("Mem free   :", 7 * 512, "MB")`. Add inline comment. Verify all colons at column 12.

**M3 — Notes block.** 40-dash rule, `Notes:`, three entries (Config/Log/Status), closing 40-dash rule, blank line. Use `r"..."` for the Windows path. Verify colons at column 13.

**M4 — Footer.** Two-line footer via one `print("""...""")`. Save `python status_card.py > output.txt` and compare against the spec.

**M5 — Mandatory experiments.** Break, observe, restore — see below.

## Starter skeleton

```python
# <one-line purpose — WHY this file exists>
# <one-line note — WHEN it will stop being hardcoded>

print("========================================")
print("<title line, exact spec — count the · >")
print("<subtitle line, exact spec>")
print("========================================")

print("Uptime     : <value>")
print("Mem free   :", <expression to 3584>, "<unit>")  # <inline comment>
print("Disk free  : <value>")
print("Latency p99: <value>")

print("----------------------------------------")
print("Notes:")
print("  Config    :", <raw string path>)
print("  Log path  :", "<value>")
print("  Status    :", "<value>")
print("----------------------------------------")

print("""<multi-line footer, both lines, exact spec>""")
```

## Success Criteria

- [ ] Output byte-for-byte matches spec.
- [ ] 40 equals / 40 dashes per rule.
- [ ] Metrics colons at column 12.
- [ ] Notes colons at column 13.
- [ ] Mem free shows `3584 MB`, not `7 * 512 MB`.
- [ ] Config path one line, both backslashes.
- [ ] Footer 2 lines from one `print("""...""")`.
- [ ] 1 full-line + 1 inline comment, neither in output.
- [ ] All top-level lines column 0.
- [ ] No semicolons, no tabs, one trailing newline.
- [ ] All 5 experiments run and code restored.

## Mandatory Experiments

Run each; paste the exact output or error; restore; confirm restore worked.

**X1 — Literal vs. evaluated.** Change `print("Mem free   :", 7 * 512, "MB")` → `print("Mem free   : 7 * 512 MB")`. Observe: output shows `7 * 512 MB` (text), not `3584`. Proves quote presence decides mode.

**X2 — Windows path escape.** Drop the `r` prefix from the Config path. Observe: `\s \d \c` are accidentally safe in this path, but the bug pattern is real. (To *prove* the class, temporarily change the path to `C:\temp\new_data` and observe the tab+newline bug — then restore.)

**X3 — Parse-error silence.** Delete one closing `)` from a mid-file `print`. Observe: **nothing prints**, error is `SyntaxError`. Proves parse-before-execute.

**X4 — Indentation error.** Add one leading space to any top-level line. Observe: `IndentationError: unexpected indent`. Remove the space.

**X5 — Comment identity.** Delete the `#` from the inline comment. Observe: `SyntaxError` (the text becomes code). Restore the `#`. Proves the `#` *makes* the comment — it's not a decoration on already-comment text.

## Reference Solution

```python
# Service status card for on-call triage.
# Values hardcoded for now; Phase 5 will wire this to real metrics.

print("========================================")
print("  Service Status  ·  prod-eu-west-1")
print("  Generated by status_card.py")
print("========================================")

print("Uptime     : 14 days")
print("Mem free   :", 7 * 512, "MB")  # computed, not literal — audit trails show the result
print("Disk free  : 128 GB")
print("Latency p99: 250 ms")

print("----------------------------------------")
print("Notes:")
print("  Config    :", r"C:\srv\data\config.yaml")
print("  Log path  :", "/var/log/svc")
print("  Status    :", "healthy")
print("----------------------------------------")

print("""Run status_card.py --help for usage.
Report issues to ops@example.com.""")
```

### Line-by-line reasoning

- **Lines 1–2:** two full-line comments — the parser discards both entirely. The second records "this is temporary" — one of the most valuable comments you can leave.
- **Line 3:** 40 `=` characters inside a string. Literal — no computation. If the count is off, alignment breaks.
- **Lines 4–5:** two leading spaces **inside the string** — kept in output. Not before `print`. The `·` is a plain Unicode character inside the string; no special meaning. `v0.1` in the anchor's sibling would be text, not a number — a `v0.1` outside quotes would be a NameError.
- **Line 6:** repeat top rule.
- **Line 7:** blank line — parser ignores, reader groups.
- **Lines 8–11 — metrics block:**
  - `Uptime` = 6 chars + 5 spaces = 11, colon at 12. Literal.
  - `Mem free` = 8 + 3 = 11, colon at 12. **Two arguments** to `print`: `"Mem free   :"` (string) and `7 * 512` (expression → `3584`), and `"MB"` (string). `print` joins with one space each → `Mem free   : 3584 MB`. The space after `:` comes from `print`, not the string.
  - `Disk free` = 9 + 2 = 11, colon at 12.
  - `Latency p99` = 11 + 0 = 11, colon at 12.
- **Line 12:** blank line.
- **Line 13:** 40 dashes.
- **Line 14:** `Notes:` — literal, colon is inside the fence.
- **Lines 15–17:**
  - `  Config    :` — 2 + 6 + 4 = 12, colon at 13. Second arg `r"C:\srv\data\config.yaml"` — raw string preserves backslashes.
  - `  Log path  :` — 2 + 8 + 2 = 12, colon at 13.
  - `  Status    :` — 2 + 6 + 4 = 12, colon at 13.
- **Line 18:** closing 40 dashes.
- **Line 19:** blank line.
- **Lines 20–21:** `print("""...""")` — one triple-quoted string spanning two source lines. The newline between them is part of the *value*. `print` adds its own trailing newline.

### Things to verify in your build

1. All four metrics colons at column 12 — finger-slide test.
2. All three notes colons at column 13 — finger-slide test.
3. `Mem free` output shows `3584`, not `7 * 512`.
4. `Config` output is one line, both backslashes intact.

If your build differs, that's the lesson — post it and we walk through the difference.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

# Part C — Progressive Project Bank

Labeled by rung (R0 = nano-drill, R1 = junior ticket, R3 = professional variant, R4 = hardening, R4+ = integration). Each project lists realism contract, task, full solution, why-correct reasoning, mastery trained.

## C.1 — Nano-drills (R0 — Recognize / Write on single rules)

### C.1.1 — Three quote styles + raw strings

**Task:** Display `Hello` using `"..."`, `'...'`, and `r"..."`. Then display `\n` in a normal string (becomes newline) vs. a raw string (stays literal).

**Solution:**
```python
print("Hello")
print('Hello')
print(r"Hello")
print("---")
print("This is escaped: \n")
print(r"This is raw: \n")
```

**Why:** first three produce identical output (no special characters). The last two diverge — `\n` in a normal string translates to a newline; in a raw string it stays two visible characters `\n`.

**Mastery:** Recognize + Write. **Mirror:** regex patterns, Windows paths.

### C.1.2 — Blank lines change nothing

**Task:** Print `A` then `B` with consecutive lines, then with three blank lines between. Confirm identical output.

**Solution:** (two files — one compact, one with extra blank lines)

**Why:** parser ignores blank lines between statements. Readability only.

**Mastery:** Recognize. **Mirror:** code review "why this grouping?"

### C.1.3 — Multi-arg `print` inserts exactly one space

**Task:** Show output for 1, 2, 3, 4 arguments.

**Solution:**
```python
print("a")
print("a", "b")
print("a", "b", "c")
print("a", "b", "c", "d")
```

**Why:** `print` inserts exactly one space between adjacent arguments — not before the first, not after the last. This is the "space tax" that makes `print("Mem free :", 3584)` produce `Mem free : 3584`.

**Mastery:** Write. **Mirror:** every multi-column CLI.

### C.1.4 — `print()` with no arguments

**Task:** Emit intentional blank lines with `print()`.

**Solution:**
```python
print("hi")
print()
print("hi again")
print()
print()
print("done")
```

**Why:** `print()` emits just its trailing newline — one blank line per call. Cleaner intent than a blank line in source.

**Mastery:** Write. **Mirror:** spacing between report sections.

### C.1.5 — Reproduce `IndentationError` (TabError proper deferred)

**Task:** Write a script with one leading space on a top-level `print`.

**Solution:**
```python
print("first")
 print("second")
```

**Output:** `IndentationError: unexpected indent` on line 2.

**Deferral:** real `TabError` requires a block → Phase 2. Phase-1 lesson: **any leading whitespace at top level is unexpected** regardless of tab or space.

**Mastery:** Debug + Recognize (deferral boundary).

### C.1.6 — The "not a comment" triple-quote trap

**Task:** Write script A with `#` hiding a `print`, and script B with the same print inside `"""..."""`. Confirm identical output; explain the semantic difference.

**Solution:**
```python
# Script A
# print("hidden")
print("visible")
```
```python
# Script B
"""
print("hidden")
"""
print("visible")
```

**Why:** A is a real comment — parser never sees it. B is an **expression statement** — Python constructs the string and discards it. Same visible effect, different mechanism. Phase 3 makes them diverge (docstrings).

**Mastery:** Recognize + Explain. **Mirror:** code review "that's a docstring, not a comment."

## C.2 — Junior tickets (R1 — Write / Debug on single-file tasks)

### C.2.1 — CLI startup banner

```
STAKEHOLDER: Developer releasing `logpeek`.
OUTPUT:     3-line banner.
FAILURE:    Must render identically in terminal and CI log — no colors, no tabs.
```

**Task:**
```
logpeek v0.1.2 — ready
Type `logpeek --help` for usage.
Source: https://example.com/logpeek
```

**Solution:**
```python
print("logpeek v0.1.2 — ready")
print("Type `logpeek --help` for usage.")
print("Source: https://example.com/logpeek")
```

**Why:** all literal text. Em dash and backticks are Unicode chars inside strings. Static banner is correctly literal — display, not computation.

### C.2.2 — Greeting with apostrophe

```
STAKEHOLDER: Onboarding script greeting a new hire.
FAILURE:    Name capitalization must match exactly.
```

**Task:**
```
Welcome aboard, Ada Lovelace.
We're glad you're here.
```

**Solution:**
```python
print("Welcome aboard, Ada Lovelace.")
print("We're glad you're here.")
```

**Why:** line 2 contains an apostrophe. **Outer quotes must differ from inner** — use `"..."` when the content has `'`. If you wrote `print('We're glad...')`, Python would parse `'We'` as a complete string, then `re` as a name → `SyntaxError`. Classic quote-style-by-content choice.

### C.2.3 — Version card with computed build

```
STAKEHOLDER: Release engineer — marketing version literal, build ID computed.
FAILURE:     Build must be computed (auditable). Version must be literal.
```

**Task:**
```
Version: v0.1.2
Build  : 4096
```

**Solution:**
```python
print("Version: v0.1.2")
print("Build  :", 64 * 64)
```

**Why:** line 1 literal (`v0.1.2` isn't a number — it's a label). Line 2 computed via multi-arg `print`. Colons align: `Version:` and `Build  :` both 8 chars. If you wrote `"Build :"` (one space) it'd drift by 1.

### C.2.4 — Log line with embedded quoted message

```
STAKEHOLDER: On-call engineer formatting one log line.
FAILURE:     Message must display with quotes; if they break the script, unusable.
```

**Task:**
```
[ERROR] user 42 said "unexpected token"
```

**Solution:**
```python
print('[ERROR] user 42 said "unexpected token"')
```

**Why:** inner `"` — switch outer to `'`. Alternative: `"[ERROR] user 42 said \"unexpected token\""` (escaped form). Both work; outer-switch is cleaner when the inner quote appears once.

### C.2.5 — Windows path in an error message

```
STAKEHOLDER: Setup script showing the missing config path.
FAILURE:     Path must survive intact as one line with backslashes.
```

**Task:**
```
Missing config: C:\app\config.yaml
```

**Solution:**
```python
print(r"Missing config: C:\app\config.yaml")
```

**Why:** `\a` in `\app` is the BELL character in a non-raw string — silent beep, corrupted path. Raw string is the correct fix by construction.

### C.2.6 — Receipt total (integer cents)

```
STAKEHOLDER: Café POS receipt.
FAILURE:     Total must be computed; item price literal.
```

**Task:**
```
Coffee x2 : 350 cents
TOTAL     : 700 cents
```

**Solution:**
```python
print("Coffee x2 : 350 cents")
print("TOTAL     :", 350 * 2, "cents")
```

**Why:** line 1 literal. Line 2 computed via multi-arg `print`. Alignment: `Coffee x2 :` and `TOTAL     :` are both 11 chars — colon aligned. Deferral: `$7.00` formatting → Phase 2 (f-strings), Atom 1.3 (types), Atom 1.4 (operators). **Integer cents is *not* a workaround — professional financial systems use cents to avoid float errors.**

### C.2.7 — Three-row column-aligned mini-table

**Task:**
```
auth    : PASS
billing : FAIL
search  : PASS
```

**Solution:**
```python
print("auth    : PASS")
print("billing : FAIL")
print("search  : PASS")
```

**Why:** alignment by counting. `auth` = 4 chars, 4 spaces → colon at 9. `billing` = 7 chars, 1 space → colon at 9. `search` = 6 chars, 2 spaces → colon at 9. All three colons aligned at column 9 — finger-slide verify.

## C.3 — Professional variants (R3 — Extend / Transfer)

### C.3.1 — Multi-line `--help` block

**Task:**
```
Usage: logpeek [options] <file>

Options:
  --help     Show this help and exit
  --version  Print version and exit
  --lines N  Show only the last N lines
```

**Solution:**
```python
print("""Usage: logpeek [options] <file>

Options:
  --help     Show this help and exit
  --version  Print version and exit
  --lines N  Show only the last N lines""")
```

**Why:** single `print` call, one triple-quoted string. Leading 2-space indents on options are *inside the string* — not Python indentation. Option column alignment: 2 + 6 + 5 = 13 before `Show`; 2 + 9 + 2 = 13 before `Print`. All three align.

### C.3.2 — Config snippet with `\a` path

**Task:**
```
service  : prod-eu-west-1
uptime   : 14 days
mem_mb   : 3584
retries  : 3
cfg_path : C:\srv\data\app.conf
```

**Solution:**
```python
print("service  : prod-eu-west-1")
print("uptime   : 14 days")
print("mem_mb   :", 7 * 512)
print("retries  : 3")
print("cfg_path :", r"C:\srv\data\app.conf")
```

**Why:** `mem_mb` computed. `cfg_path` **must** be raw string — `\a` in `\app` is a real escape (BELL char). Unlike the anchor's path (`\s \d \c` happen to be non-escapes), this path *breaks* without `r`. This is the exercise that proves raw strings are more than good habit. Colons all at column 10.

### C.3.3 — Two computed values on one line

**Task:**
```
Latency : p50= 120 ms  |  p99= 250 ms
```
Both `120` and `250` must be integer expressions.

**Solution:**
```python
print("Latency : p50=", 100 + 20, " ms  |  p99=", 200 + 50, " ms")
```

**Why:** five arguments → `print` inserts four spaces. The space after `p50=` comes from `print`, not the string. **Space tax** — accepted by design; f-strings in Phase 2 remove it.

### C.3.4 — Audit-hidden comments

**Task:** Print `status : clean` and `audit  : passed`. Source must contain ≥3 comments; none may appear in output.

**Solution:**
```python
# AUDIT-2026-01-15: reviewed by ops-team.
# Rationale: PII suppressed per policy §4.2.
print("status : clean")  # verified in runbook RB-017
print("audit  : passed")  # countersigned by on-call lead
```

**Why:** all four comments vanish because `#` sits outside any string. Verify: delete the `#` from line 3 — text becomes code → `SyntaxError` → nothing prints → restore. This proves the `#` *makes* the comment.

### C.3.5 — Three-section card with varied separators

**Task:**
```
===== HEADER =====
status : ok

----- METRICS -----
mem_mb : 3584

..... NOTES .....
note   : all clear
```

**Solution:**
```python
print("===== HEADER =====")
print("status : ok")
print()

print("----- METRICS -----")
print("mem_mb :", 7 * 512)
print()

print("..... NOTES .....")
print("note   : all clear")
```

**Why:** three separator characters (=, -, .) are a design choice — literal strings. `print()` intentionally emits blank lines. `mem_mb` reuses computed form. All three colons at column 8.

## C.4 — Hardening (R4 — Debug)

### C.4.1 — Mismatched quote from copy-paste

**Broken:**
```python
print("Service starting")
print('Config loaded")
print("Ready")
```

**Fails:** `SyntaxError: unterminated string literal` on line 2. **Nothing prints.**

**Fix:** match quote styles.

**Real-world:** the "my service is silent" bug class — a broken line at the top makes every preceding line vanish. Read traceback *category* first.

### C.4.2 — Smart quotes from a word processor

**Broken (curly quotes):**
```python
print(“Hello, world”)
```

**Fails:** `SyntaxError: invalid character '“' (U+201C)`.

**Fix:** retype with straight ASCII `"`.

**Real-world:** #1 copy-paste bug in Python teams. When you see `invalid character` with a Unicode code point, check quotes first.

### C.4.3 — Trailing space after `\` continuation

**Broken** (space between `\` and newline, invisible):
```python
print("Hello " \ 
      "world")
```

**Fails:** `SyntaxError: unexpected character after line continuation character`.

**Fix:** prefer implicit continuation inside brackets — immune to invisible chars. Or turn on "trim trailing whitespace on save."

**Real-world:** copy-paste across editors silently breaks continuation. Correct response is *process*, not "be careful."

### C.4.4 — Missing paren (traceback reading)

**Broken:**
```python
print("start")
print("middle"
print("end")
```

**Fails:** `SyntaxError: '(' was never closed (detected at line 2)`. **Nothing prints.**

**Fix:** `print("middle")`.

**Professional debugging move:**
1. Read category first — `SyntaxError` → parse phase → nothing ran.
2. Read `detected at line N` — that's where Python *gave up*, not always where the fix belongs. Fix is usually 1–3 lines earlier.
3. Count parens on N-1 and N.
4. Don't delete lines — add the missing character.

**Real-world:** most common production "my service won't start" is a `SyntaxError` at the top of a module.

### C.4.5 — Mixed indentation from copy-paste (TabError deferred)

**Broken:**
```python
print("first")
	print("second")
print("third")
```

**Fails:** `IndentationError: unexpected indent` on line 2. **Nothing prints.**

**Fix:** remove the tab.

**Deferral:** real `TabError` (mixed tabs/spaces *within a block*) needs `if`/`for` → Phase 2. Phase-1 lesson: any leading whitespace at top level is unexpected.

**Real-world:** copy-pasting from the web is #1 source of indentation errors. Correct response: **select all → convert indentation to spaces → save → rerun.**

## C.5 — Integration capstones (R4+)

*Note: at Atom 1.1 there are no previous atoms to integrate with, so C.5 is a within-atom composite.*

### C.5.1 — Status Card v2 (full recombine)

**Task:**
```
================================
  Status Card v2  ·  prod-eu-west-1
================================

Uptime : 14 days
Mem MB : 3584
CPU    : 42

-------------------
Config : C:\srv\data\config.yaml
Log    : /var/log/svc

Usage: status_card_v2 [--verbose]
  --verbose  Show per-service breakdown
```

**Solution:**
```python
# Status Card v2 — composite atom-1.1 card.
# Values hardcoded; Phase 5 wires to real data.

print("================================")
print("  Status Card v2  ·  prod-eu-west-1")
print("================================")
print()

print("Uptime : 14 days")
print("Mem MB :", 7 * 512)
print("CPU    : 42")
print()

print("-------------------")
print("Config :", r"C:\srv\data\config.yaml")
print("Log    :", "/var/log/svc")
print()

print("""Usage: status_card_v2 [--verbose]
  --verbose  Show per-service breakdown""")
```

**Self-audit table:**

| Mode | Where | Break test |
|---|---|---|
| Literal vs. evaluated | `Mem MB` computed | `"7 * 512"` shows text |
| Multi-arg `print` | Mem MB, Config, Log | Drop commas → no computed value |
| Raw string | Config path | (this path accidentally safe; use C.3.2's path to prove) |
| Triple quote | 2-line footer | Split into two `print`s → pattern hidden |
| `print()` blank lines | Three calls | Remove → sections lose grouping |
| Comments | Top 2-line | Remove `#` → SyntaxError |
| Alignment | All 5 colons at column 8 | Add a space → colon drifts |

### C.5.2 — Receipt printer (composite)

**Task:** See full spec in the previous chunk. Key moves: item/qty/price columns right-aligned, `TOTAL` line computed with `350 * 2 + 200`, footer using `r"""..."""` (raw + triple combo — first time in the atom), which protects the `\f` in `\front-desk` from becoming a form-feed byte.

**Solution** (compact — item rows + computed total + raw-triple footer):
```python
# Receipt printer — demo café receipt.
# Total computed; printer path uses raw triple-quoted string.

print("           ACME CAFE")
print("    42 Main St, Springfield")
print("================================")
print("Item             Qty  Price")
print("--------------------------------")
print("Coffee             2    350")
print("Muffin             1    200")
print("--------------------------------")
print("TOTAL                  ", 350 * 2 + 200)  # 18 spaces after TOTAL
print("================================")
print()

print(r"""Printer : \\printers\front-desk
Thanks for visiting!""")
```

**Why:** `350`, `200`, `900` all end at the same column — counted, not eyeballed. `r"""..."""` handles both the escape-sensitive UNC path (`\f` → form feed without the `r`) and the real newline in the footer. First composite of raw + triple in the atom.

**Mastery:** Integration + Transfer (different domain, all modes, one new composite move).

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

# Part D — Domain Coverage Matrix

The audit that closes the loop on the Gate 1 atom map. If any row is unmapped, the atom is incomplete.

## D.1 — Real-world uses → projects

| # | Real-world use | Covered by | Status |
|---|---|---|---|
| 1 | CLI startup banner | Anchor, C.2.1, C.3.1, C.5.1 | ✅ |
| 2 | Multi-line help / usage text | C.3.1 | ✅ |
| 3 | Diagnostic / status messages | Anchor, C.2.3, C.3.5, C.5.1 | ✅ |
| 4 | Log lines with quoted messages | C.2.4 | ✅ |
| 5 | Timestamped log line / audit comments | C.2.4, C.3.4 | ✅ |
| 6 | Receipt / invoice (aligned columns + total) | C.2.6, C.5.2 | ✅ |
| 7 | Config snippet generation | C.3.2 | ✅ |
| 8 | Column-aligned terminal report | C.2.7, C.3.5, C.5.1 | ✅ |
| 9 | Comment discipline for audit / compliance | C.3.4 | ✅ |
| 10 | Escaping pathnames | Anchor, C.2.5, C.3.2, C.4.2, C.5.1, C.5.2 | ✅ |
| 11 | Computed value next to a label | Anchor, C.2.3, C.2.6, C.3.2, C.3.3, C.3.5, C.5.1, C.5.2 | ✅ |
| 12 | Two computed values on one line | C.3.3 | ✅ |

**No unmapped rows.**

## D.2 — Coverage by concept (from Part A)

| Concept | Exercised by |
|---|---|
| Literal vs. evaluated | Anchor, C.1.3, C.2.3, C.2.6, C.3.2, C.3.3, C.5.1, C.5.2 |
| Multi-arg `print` + space behavior | Anchor, C.1.3, C.2.3, C.2.6, C.3.2, C.3.3, C.5.1 |
| Quote-style choice by content | C.2.2, C.2.4, C.4.1 |
| Raw strings | C.1.1, C.2.5, C.3.2, C.4.2, C.5.1, C.5.2 |
| Triple-quoted strings as values | Anchor, C.1.6, C.3.1, C.5.1, C.5.2 |
| Comments verified invisible by deletion | C.1.6, C.3.4, C.4.4, C.5.1 |
| Blank lines as grouping | C.1.2, C.1.4, C.3.5, C.5.1 |
| Alignment by counting | Anchor, C.2.7, C.3.1, C.3.5, C.5.1, C.5.2 |
| Parse phase vs. execute phase | C.4.1, C.4.4, C.4.5, X3 |
| Traceback reading | C.4.4 |
| Leading whitespace at top level | C.4.5, X4 |
| Escapes / invisible characters | C.4.2, C.4.3, C.5.2 |
| Comment vs. triple-string semantics | C.1.6, C.3.4 |

**Every concept has ≥2 projects exercising it.**

## D.3 — Deferred uses (tracked in `deferrals.md`)

| Deferred use | Needs | Phase |
|---|---|---|
| Interpolating a variable into a banner (`f"Version {v}"`) | Variables (1.2) + f-strings (P2) | Phase 2 |
| Reading banner text from config file | File I/O (P6) | Phase 6 |
| Timestamp generation (`datetime.now()`) | `import` + datetime | Phase 4 |
| ANSI colored output | ANSI codes | Phase 6+ |
| Column formatting via f-string (`f"{x:<8}"`) | f-string alignment | Phase 2 |
| Dynamic width from `len(longest_label)` | `len()` + loops | Phase 2 |
| Tested CLI banner (regression) | Testing frameworks | Phase 6 |
| Docstring-attached documentation | Functions (P3) | Phase 3 |
| Card as a reusable function | Functions (P3) | Phase 3 |

## D.4 — Honest gaps (what this audit cannot prove)

1. **Error recovery** — parsing halts on first error; the "partial banner succeeded" story needs try/except (Phase 5).
2. **Long-output pagination** — one-screen banners by definition; scroll handling is a UI concern (deferred).
3. **Internationalization** — smart quotes (adversarial case) tested; RTL, combining chars are not (Phase 6).
4. **Concurrency** — interleaved output from two processes; out of scope for a single-file atom.

These are honest boundaries — not holes in this atom's job.

## D.5 — Verdict

**Atom 1.1 coverage: complete and audited.**
- 12/12 real-world uses mapped ✅
- 13/13 concepts exercised by ≥1 project (most by 4+) ✅
- 9 deferred uses logged with phase targets ✅
- 4 gaps named honestly, out of scope ✅

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

# Part E — Interview-Style Problems

## E.1 — Level 1: "Walk me through this file" (phone screen)

**Prompt:**
> Here's a file with two lines:
> ```python
> print("hello")
> print("world"
> ```
> Walk me through exactly what happens when I run `python this_file.py`. What prints, what error appears, why? Then: what changes — output, error category — if I fix the second line to `Print("world")` (capital P, properly closed)?

**Strong answer:**
1. States two-phase model first.
2. Case 1: unterminated string + unclosed paren → parse fails on line 2 → **nothing runs, no output**.
3. Case 2: `Print(...)` parses cleanly. Python runs line 1 → prints `hello`. Line 2 → `NameError: name 'Print' is not defined`. **The program started.**
4. Concludes: two files both fail, but one prints nothing (parse-time), the other printed `hello` then failed (runtime). **The category tells you which phase — and whether earlier lines executed.**

**Weak answers:**
- "Both fail" — no distinction.
- "Line 1 prints, then line 2 fails" — classic misconception (parse precedes execute). Ships "my service is silent" to prod.
- "Just fix the syntax" — no reasoning about *what the parser does with it*.

**Rubric:** L1 identifies fix; L2 adds "nothing prints" + parse-phase reasoning + NameError correction; L3 uses exact terms *parse-time* vs. *runtime* and states the practical debugging consequence.

## E.2 — Level 2: "Read this output and diagnose the bug" (technical screen)

**Prompt:**
> Service log shows:
> ```
> log dir : C:	    emp\sync-logs
> ```
> Source line:
> ```python
> print("log dir : C:\temp\sync-logs")
> ```
> The developer says: *'The code looks fine — the path shows `C:` then a big gap then `emp`. I don't understand.'*
> Diagnose. Explain why. Give the fix. Then: could the same bug appear in `C:\srv\data-sync\config.yaml`, and why or why not?

**Strong answer:**
1. **Identifies the character.** The gap is a tab (`0x09`). `\t` in `\temp` translates to a tab byte.
2. **Explains the mechanism.** Inside a string, `\` signals an escape. `\t` is a real escape. The tab is hidden in the string value — printing reveals it as a gap.
3. **Fixes both ways.** `r"..."` (raw — no escape processing) or `"C:\\temp\\..."` (double the backslash). Raw is safer because it rules out the whole escape class without needing to remember which `\x` are real.
4. **Handles counterfactual.** `\s`, `\d`, `\c` are **not** valid Python escapes — Python leaves them as-is (with a DeprecationWarning on 3.12+). So `C:\srv\data-sync\config.yaml` *happens* to survive. **But that's accident, not correctness.** The safety is content-dependent — swap `srv` for `temp` and it silently corrupts. **The right engineering discipline is `r"..."` for every path — because content will change in a future commit, and the raw string guarantees safety under evolution.**

**Weak answers:**
- "Just add `\\`" — right fix, no reasoning about the class of bug. Fails the counterfactual.
- "Backslashes are bad in Python" — over-simplified.
- "It works — I ran it and nothing broke" — silent-bug trap.
- Doesn't address the counterfactual — Level 2 answer, not Level 3.

**Rubric:** L1 sees the tab, says "add another backslash"; L2 explains the escape mechanism + fix; L3 names which escapes are real (`\t` yes, `\s` no), explains content-dependence, and states `r"..."` is *correct discipline* because safety of `\s` is accidental — reasoning about safety under change.

## E.3 — Level 3: "Review this PR before we merge" (on-site)

**Prompt:**
> PR adds a startup banner to a data-sync service. Author says: *'Works on my Mac but on the Windows CI runner the output looks wrong — no error, so I think it's the terminal.'*
> Review it. Tell me what's wrong, in order — **including anything the CI runner isn't showing yet.** Give the corrected version.
> ```python
> # startup banner for the data-sync service
> print("== data-sync starting ==")
> print("version : 2.4.1)
> print("log dir : C:\temp\sync-logs")
> print("mem MB  : 7 * 512")
> ```

**Strong answer:**
1. **Counts bugs first.** Three bugs, three categories — one parse-time, two silent. The author's report is *misleading* because the parse bug masks the other two.
2. **Walks top-to-bottom with parse-then-execute active.** Line 4 (third `print`) — `print("version : 2.4.1)` — `"` opens and never closes; the `)` is inside the unterminated string. **`SyntaxError` on parse. Nothing runs. The "Mac works, Windows doesn't" claim is impossible** — either they tested a different file, fixed it locally then reverted before commit, or mis-remembered.
3. **Names categories explicitly.** Bug 1 (line 4): `SyntaxError` — unterminated string. Fix: `print("version : 2.4.1")`.
4. **Then the silent bugs.** Bug 2 (line 5): **silent escape bug** — `\t` in `\temp` → tab. Fix: `r"C:\temp\sync-logs"`. Bug 3 (line 6): **silent literal-vs-evaluated bug** — expression in string → displays `7 * 512` instead of `3584`. Fix: `print("mem MB  :", 7 * 512)`.
5. **Explains the trap.** Author saw *something* on Mac (earlier version) and nothing on Windows CI. But the silent bugs produce **no error on either OS — only wrong output.** "It's the terminal" diagnosis is wrong — the output isn't a terminal issue, it's string content. **A reviewer who fixes only line 4 ships a broken banner that runs fine in production — the class of bug that ships for a month before someone notices.**
6. **Gives the fixed file:**
   ```python
   # startup banner for the data-sync service
   print("== data-sync starting ==")
   print("version : 2.4.1")
   print("log dir :", r"C:\temp\sync-logs")
   print("mem MB  :", 7 * 512)
   ```
7. **Gives the process fix.** In review I'd ask the author to (a) always run end-to-end before claiming "works here but not there" — a parse error kills *all* platforms — and (b) review own output, not own code. **Verify output, don't eyeball code.**

**Weak answers:**
- **Only fixes line 4.** Ships two silent bugs into prod. Most consequential failure of this interview.
- Fixes 4+5 but not 6 — underscores that silent bugs need *output* reading.
- Fixes all but doesn't call out the author's impossible claim.
- Misses the process fix — code review is not just "fix the line."

**Rubric:** L1 finds missing quote; L2 finds all three bugs and fixes correctly; L3 adds (a) categories named in order (parse then silent), (b) masked-bug explanation, (c) impossible-claim callout, (d) process fix — "verify output, don't eyeball code."

**Level 3 is the ask.** L2 proves you understand individual modes; L3 proves you compose them under review pressure.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

# Part F — Quick-fire Q&A

### F.1 — Parse vs. execute — why does this distinction matter practically?
**Parse phase** = whole file checked for grammar; any error = nothing runs. **Execute phase** = statements run top-to-bottom; errors here (NameError etc.) happen after program started, so earlier output may have printed. **Practical consequence:** "nothing printed" → parse bug; "printed then crashed" → runtime bug. This one distinction cuts debugging search in half in three seconds.

### F.2 — Literal vs. evaluated — the single test
**Q: How do you know if `X` in `print(X)` is evaluated?** **A:** **"Is X inside quotes?"** Yes → literal string, kept verbatim. No → Python evaluates as expression. `print("2 + 3")` → `2 + 3`; `print(2 + 3)` → `5`. Quote presence, **not intent**, decides. This is the atom's most important distinction because it silently produces wrong output with no error.

### F.3 — When do you use `r"..."` and what bug class does it prevent?
**Rule:** use raw strings whenever the backslash is meant literally — Windows/UNC paths, regex. **Bug class:** *silent escape sequences*. `"C:\temp"` has hidden `\t` → real tab → corrupted output, no error. `r"C:\temp"` → correct. Bug is *content-dependent*: `"C:\srv"` happens to survive (`\s` isn't a real escape), but `"C:\temp"` breaks — and if a path is edited later, the bug appears retroactively. **Raw is safe under change; double-backslash is only safe for current content.** Prefer raw.

### F.4 — `#` vs. `"""..."""`
**`#` makes a comment** — parser discards; nothing constructed. **`"""..."""` makes a multi-line string value** — Python constructs the string, discards it (nothing uses it). Visible effect identical at Phase 1 — run works, nothing from block appears. **But:** from Phase 3 onwards, `"""..."""` at top of function/module becomes a **docstring**, retrievable via `help(...)` — a comment never will be. **Rule now:** "ignore this" → `#`; "multi-line text as value" → `"""..."""`. **Rule after Phase 3:** "documentation attached to a function" → `"""..."""`.

### F.5 — The "space tax" of multi-arg `print`
**Q: `print("Mem free :", 3584, "MB")` shows `Mem free : 3584 MB` — you didn't type those spaces after `:` or after `3584`. Where did they come from?** **A:** `print` inserts exactly one space between adjacent arguments. `print(a, b, c)` → `a b c`. Spaces after `:` and after `3584` come from `print`'s inter-arg separator. **Consequence:** if you want *no* space in a specific spot, you can't via multi-arg `print`. Either design strings around the tax (accept, align elsewhere) or wait for Phase 2 f-strings (interpolate inside one string, no auto space). Today's rule: **design strings around the space tax.**

### F.6 — Why is indentation grammar in Python?
Python chose leading whitespace as block syntax. Consequences: (1) top level — *any* leading space is error (§2); (2) inside block — indentation *required* and *consistent* (Phase 2); (3) mixing tabs/spaces → `TabError` (§6). **Bigger consequence:** between tokens = cosmetic (`print ( "Hi" )` works); before a line = grammar (` print("Hi")` fails). **This asymmetry — between=ignored, before=grammar — is the single most important thing to internalize.**

### F.7 — Alignment by counting — why bother in Phase 1?
**Q: Why count characters by hand when Phase 2's f-string alignment will do it automatically?** **A:** Because **alignment is arithmetic, not magic — and you can't debug what you can't do by hand.** When `f"{label:<8}"` produces a misaligned column in Phase 5, the fix requires knowing *what column the colon should be at* — which requires knowing alignment is *counting*, not eyeballing. Every "columns drifted" bug got there because someone trusted their eye. **Phase 1 trains the mental model; Phase 2 gives you a tool built on it.**

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

# Part G — What To Do Now

This is the whole atom in one action list. No jargon. Just what you do, in order, before we open Atom 1.2.

### Step 1 — Build the anchor (`status_card.py`)
Create the file and make it produce exactly the spec output from Part B. Use the notes-block alignment (colons at column 13 — `Config` and `Status` get 4 spaces, `Log path` gets 2). Type your own strings; do not paste the reference solution.

### Step 2 — Run the five experiments
From Part B, X1 through X5. For each: break it, run it, paste the exact output/error, restore, confirm restore. (X1: literal bug. X2: raw string bug. X3: missing paren. X4: leading space. X5: remove `#`.)

### Step 3 — Do the recommended 14 project exercises
From Part C. This minimum covers every mode and every real-world domain:
- **C.1:** C.1.1, C.1.3, C.1.4, C.1.6
- **C.2:** C.2.2, C.2.4, C.2.5, C.2.6, C.2.7
- **C.3:** C.3.2, C.3.3
- **C.4:** C.4.2, C.4.4
- **C.5:** C.5.2

### Step 4 — Write four short files in your repo
Create these in `phase-01-foundations/atom-1.1-syntax/`:
1. `status_card.py` — the working anchor.
2. `output.txt` — the anchor's actual run.
3. `experiments.md` — X1–X5 with real pasted traces.
4. `coverage.md` — the concept → project mapping from Part D.
5. `deferrals.md` (repo root) — the running list from Part D.3.
6. `reflection.md` — one paragraph on the experiment that surprised you most.

### Step 5 — Do the challenge
Write a 200–300 word document titled "How to debug a Python file that prints nothing." Include: (1) why "nothing prints" is a parse error, (2) the traceback categories that mean parse vs. runtime, (3) the exact steps to read a traceback, (4) one code example with `SyntaxError` vs. `NameError`. Save in `challenge.md` and paste it back to me.

### Step 6 — Commit and tag
```bash
git add .
git commit -m "atom(1.1): syntax, indentation, comments, statements, expressions

- status_card.py: anchor, computed Mem free line, raw-string Config path
- experiments.md: X1–X5 with real traces
- coverage.md: concept → project audit
- deferrals.md: running ledger started
- reflection.md: what changed in how I debug"
git push
git tag atom-1.1-complete
git push --tags
```

### Step 7 — Paste back these five things to me
1. The full text of `status_card.py`.
2. The exact terminal output of `python status_card.py` (byte-for-byte).
3. The five experiment results from Step 2, each with its pasted traceback.
4. Your `coverage.md` table — the concept → project mapping.
5. Your `challenge.md` — the 200–300 word document.

Do not skip Step 3 and paste only the anchor. Both are required.

### Step 8 — Then say `ready for 1.2`
Or `go deeper on ___` if anything still feels shaky. A shaky 1.1 makes 1.2 harder; a clean 1.1 makes everything downstream easier.

### Done Checklist
- [ ] `status_card.py` produces byte-for-byte matching output
- [ ] All colons in the metrics block are at column 12
- [ ] All colons in the notes block are at column 13 (`Config` and `Status` get 4 spaces, `Log path` gets 2)
- [ ] `Mem free` line shows `3584`, not `7 * 512`
- [ ] `Config` line shows `C:\srv\data\config.yaml` as one line, both backslashes intact
- [ ] Footer is 2 lines from a single `print(...)` using `"""..."""`
- [ ] At least one full-line comment + one inline comment; neither appears in output
- [ ] All top-level lines start at column 0
- [ ] No semicolons, no tabs, exactly one final newline
- [ ] X1–X5 all run, results pasted, code restored to working state
- [ ] The 14 recommended project exercises are done and saved
- [ ] `coverage.md`, `deferrals.md`, `reflection.md` exist and are in your own words
- [ ] `challenge.md` is written and pasted back
- [ ] Committed with the `atom(1.1):` prefix and tagged `atom-1.1-complete`
- [ ] You can explain parse-vs-execute to a friend without looking at notes

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---

# Part H — Where We Go Next

Three atoms ahead in Phase 1:

### Atom 1.2 — Variables, Assignment, and Names
**Scope:** giving a value a **name** (`x = 5`), what a name *is* (a label pointing at a value — **not** a container that "holds" it), reassignment, and the first look at why Python doesn't need C-style type declarations. **Why now:** every future atom — arithmetic, strings, lists, functions — is built on the idea that values can be *named* and *retrieved*. This is where "the reader's finger on the page" gets memory.

### Atom 1.3 — Primitive Data Types: `int`, `float`, `str`, `bool`, `None`
**Scope:** the five shapes of value you'll use constantly. How Python classifies them, what `type()` reveals, and the crucial distinction between `"42"` (text) and `42` (integer). **Why now:** the literal-vs-evaluated distinction from Atom 1.1 becomes *semantically richer* — a string `"42"` is now a *different type* from an integer `42`, and arithmetic on one doesn't work on the other.

### Atom 1.4 — Operators and Expressions in Depth
**Scope:** `+ - * / // % **`, comparison operators (`==`, `<`, etc.), boolean operators (`and`, `or`, `not`), operator precedence. **Why now:** "expression" from Atom 1.1 becomes a genuine tool. The multi-arg `print("Mem free :", 7 * 512, "MB")` pattern gets a dozen new expression shapes to fill in.

---

### The challenge before you proceed

**Atom 1.1 is small on purpose.** It's five words in a title. But every atom after it — 18 phases of atoms — assumes you can look at a file and say *"here's what parses, here's what runs, here's what prints."* If that sentence is shaky today, it will be shaky for Phase 2, Phase 3, Phase 4 — and by Phase 7 you'll be paying back with interest.

So do the challenge (Step 5 above), do it honestly in your own words, and **paste it back before you say `ready for 1.2`.**

The temptation is to race through Phase 1 because the atoms feel *easy*. **Resist it.** The atoms feel easy because they're load-bearing — they're *supposed* to feel easy. The mistake isn't doing them slowly; the mistake is doing them fast and finding out in Phase 5 that you never actually built the foundation.

When the challenge is pasted and the checklist is ticked, say **`ready for 1.2`**. I'll open Atom 1.2 under the same protocol — Gate 1 Atom Map first, no teaching until you approve it.

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)

---
**Navigation:**
[⬅️ Previous: 0.8 Build-in-public](../../CURRICULUM.md#phase-0--setup--professional-baseline) | [Next: 1.2 Variables & Types ➡️](01.2-variables-types.md)

[⬆️ Back to Top](#11-syntax-indentation-comments-statements)