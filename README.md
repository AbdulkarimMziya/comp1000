# COMP 1000 — Review Worksheets

Self-study Python worksheets for **COMP 1000: Introductory Programming — Think Like a
Computer** (ICM, Fall 2026). Each worksheet stays one step ahead of the class schedule:
lock in the current chapter's fundamentals and learn the next chapter early, tuned to the
next quiz or test.

> **Academic integrity.** These are practice material only. The course allows AI help
> "when practicing coding and when reading through the textbook" — it does **not** allow
> it on assignments, labs, or tests. Nothing here is to be copied into graded work.

---

## Chapters

| # | Worksheet | Class week | Targets |
|---|-----------|-----------|---------|
| 1 | [`chapter_01_python_ethics_interactivity.md`](chapter_01_python_ethics_interactivity.md) | Week 1 (Sept 9, 13) | **Quiz 1** (Mon Sept 14) |
| 2 | [`chapter_02_data_and_instructions.md`](chapter_02_data_and_instructions.md) | Week 2 (Sept 14, 16) | **Test 1** (Wed Sept 23, cumulative Ch 1–2) |

### Chapter 1 — Python, Ethics & Interactivity

- Running a Python program; `print()` and output (commas insert one space).
- `input(prompt)` — always returns a **`str`**, even when it looks like a number.
- Converting values: `int()`, `float()`, `str()`.
- `#` comments.
- String `+` (join) vs. comma in `print()`.
- The **programmer / program / end-user** roles, and the ethics thread: the programmer
  decides what a program asks for, how prompts are worded, and what happens to the answer.

### Chapter 2 — Data & Instructions

- The four basic data types — `int`, `float`, `str`, `bool` — and `type()`.
- The full operator set: `+  -  *  /  //  %  **`.
  - `/` always gives a `float`; `//` is the whole-number part; `%` is the remainder.
- Operator **precedence**: `( )` → `**` → `* / // %` → `+ -`; ties go left to right.
- **Expressions vs. statements**; `=` means "gets" (right side computed first, then stored).
- **Reassignment / the accumulator pattern** — `total = total + x`.
- Strings: `*` (repeat), `len()`.
- Ethics angle: honesty in how numbers are stored and shown (types, rounding, float display).

---

## Repository layout

```
comp1000/
  chapter_01_python_ethics_interactivity.md   worksheet
  chapter_02_data_and_instructions.md         worksheet
  answers/
    chapter_01_warmup_answers.md              Section 3 warm-up answer key
    chapter_02_warmup_answers.md
  images/
    chapter_01_diagram_1_execution_flow.png   rendered diagrams
    chapter_01_diagram_2_three_roles.png
```

When you work a chapter, make a `chapter_NN/` folder for your `.py` practice scripts (the
worksheet's Setup section lists the exact filenames).

---

## How each worksheet is built

1. **▶ Before You Start** — an ordered *Python for Non-Programmers* (LinkedIn Learning)
   watch list mapped to the chapter, plus a "concepts to understand before the questions"
   checklist.
2. **Setup** — the `chapter_NN/` folder and one `.py` file per coding exercise.
3. **The Bridge** — how the previous chapter connects into this one.
4. **Concept Blueprint** — theory in plain metaphors, real-world context, the ethics
   thread, and a `[DIAGRAM DESIGN & ANNOTATION SPECIFICATION]` block (rendered images in
   `images/` where available).
5. **Warm-Up Drills** — ~9 quick questions (predict the output / fill in the blank / write
   one line / spot the bug). Answers in `answers/`.
6. **Quiz-Prep Practice Engine** — Exercise A (fill-in-the-blank scripts), Exercise B
   (explain the algorithm), Exercise C (code from scratch). Coding blocks are paste-ready,
   each headed with a `# filename:` line.
7. **Solution Manual** — worked solutions with **QUIZ TRAP** callouts.
8. **Quiz-Day Checklist** — the 60-second review.

Prompts marked **✍️ ON THE SIDE** are thinking answers — write them on paper or in a notes
file; they're not code to run and nothing is submitted.

---

## Source

- Course textbook: Runestone Academy (linked from Moodle), one chapter per week.
- Video course: [*Python for Non-Programmers*](https://www.linkedin.com/learning/python-for-non-programmers/)
  (LinkedIn Learning) — note its ordering differs from COMP 1000's.
