# Chapter 1: MASTERING PYTHON, ETHICS & INTERACTIVITY

> **Review Teacher's Note — read this first.**
> This is a **self-study practice worksheet** built to get you comfortably ahead of the
> COMP 1000 schedule. Today is Week 0; your class covers this material in Week 1, and
> **Quiz 1** lands at the start of Week 2 (Monday, Sept 14), drawn straight from
> Runestone Chapter 1. Quiz 1 is worth 1%, your lowest quiz is dropped, and it exists to
> *help* you — not to scare you. Work through this once and the quiz becomes a formality.
>
> This document is study material, consistent with the course academic-integrity policy
> (AI tools are allowed "when practicing coding and when reading through the textbook").
>
> **Estimated completion time:** 60–90 minutes (plus ~15 for the Section 3 warm-ups).
> Have a Python 3 environment open
> (IDLE, the Runestone activecode boxes, or `python3` in a terminal) and actually run
> every snippet. Reading is not the same as knowing.

---

## ▶ Before You Start: Watch This First

**Course:** *Python for Non-Programmers* (LinkedIn Learning) —
<https://www.linkedin.com/learning/python-for-non-programmers/>

Watch these videos in **this order** (~32 min total). Videos 1–6 run back-to-back;
videos 7–8 are further down the course under "Functions and More" — jump ahead to them,
then come back here.

| # | Section → Video | Length |
|---|---|---|
| 1 | Introduction → *Python from zero* | 1 min |
| 2 | Introduction → *Your first line of code* | 3 min |
| 3 | Python Basics → *Variables* | 5 min |
| 4 | Python Basics → *Numbers: Ints and floats* | 4 min |
| 5 | Python Basics → *Strings* | 5 min |
| 6 | Python Basics → *Using variables in strings* | 5 min |
| 7 | Functions and More → *Comments* | 4 min |
| 8 | Functions and More → *Input* | 5 min |

**Stop there.** The video after "Using variables in strings" is *Booleans and if
statements* — that's COMP 1000 **Chapter 6 (Conditionals)**, weeks away. Lists, loops,
dictionaries and functions are all later chapters too. Watching ahead won't hurt, but
none of it is needed for Quiz 1, and the exercises below deliberately don't use any of it.

> **Two notes.**
> 1. The *Using variables in strings* video may show **f-strings** (`f"Hi {name}"`).
>    Good to recognise, but the exercises here stick to commas in `print(...)` and `+`
>    for joining strings — that's all Runestone Chapter 1 uses.
> 2. The **programmer / program / end-user roles and the ethics thread** in Section 2 are
>    COMP 1000-specific. They are *not* in this course — read them in the worksheet and
>    the Runestone chapter.

### Concepts to understand before attempting the questions

Tick each one off. If any is shaky, re-watch that video before starting the practice
questions (Sections 3–4).

- [ ] I can run a Python file (or a single line) and see its output.
- [ ] **`print(...)`** displays text; separating items with commas puts one space between them.
- [ ] A **variable** is a named box: `visitor_name = "Ada"` stores a value under a name.
- [ ] **`int` vs `float`** — whole numbers vs numbers with a decimal part.
- [ ] A **string** is text in quotes; `"5"` (text) is not the same as `5` (number).
- [ ] **`input(prompt)`** shows the prompt, waits for Enter, and returns what the user typed **as a string** — always.
- [ ] To do arithmetic on an `input()` result I must convert it first with **`int(...)`** or **`float(...)`**.
- [ ] **`#`** starts a comment: ignored by Python, written for humans.
- [ ] (From the worksheet, not the video) the **programmer** decides what a program asks for, how each prompt is worded, and what happens to the answer.

---

## Setup for this worksheet (do this before Sections 3–4)

You'll do the coding parts in your IDE (IDLE, VS Code, Thonny — whatever you use for
labs), one small script per exercise.

1. **Make a folder** for this chapter's practice work:

   ```
   comp1000/
     chapter_01/
   ```

2. **As you reach each coding exercise**, create the file named in its
   `# filename:` line and paste the block that's provided. This chapter hands you
   ready-to-paste code — from later chapters you'll set more of it up yourself.

   | Exercise | File to create |
   |---|---|
   | A1 | `chapter_01/a1_greeting_bot.py` |
   | A2 | `chapter_01/a2_adder.py` |
   | A3 | `chapter_01/a3_tip_calculator.py` |
   | B  | `chapter_01/b_membership_card.py` |
   | C  | `chapter_01/c_kiosk.py` |

3. **Run** a script with the Run button, or `python3 chapter_01/a2_adder.py` in a
   terminal. When it asks a question, type your answer and press Enter.

> **✍️ ON THE SIDE** — Some prompts are marked like this. They are *thinking* answers
> (explanations, hand-traces, reflections), **not** code to run. Write them wherever
> suits you — on paper, or in a plain typed notes file beside you. Nothing to submit,
> no filename required. The point is that you actually write them out in words.

---

## 1. The Bridge: Connecting the Dots (Review & Linkage)

### The Review — *Teacher Review Notes: "Thinking Like a Computer"*

Week 0 gave you the single most important skill in this course: **mentally simulating
how a computer executes a program.** The whole idea rests on three rules:

1. **A program is a list of instructions (statements), run one at a time, top to bottom.**
   The computer never skips ahead, never gets bored, never guesses what you meant. It
   does exactly what the current line says, then moves to the next line.
2. **The computer keeps a "state" — a set of named boxes holding values.** Every time a
   program stores something, picture a labelled box on a shelf. The label is the
   **variable name**; the thing inside is the **value**. Later lines can look inside those
   boxes or replace what's in them.
3. **To predict a program's output, you trace it.** You keep a little table of every box
   and its current value, walk down the code line by line, update the table when a line
   changes a box, and write down anything the program is told to display.

That trace table — done by hand, on paper — is your "computer on paper."

### The Evolution — *why paper tracing alone runs out of road*

Hand-tracing is precise and it builds real understanding, but it has two hard limits:

- **It's slow and it doesn't scale.** Tracing 8 lines is fine. Tracing 80 lines, or the
  same 8 lines for 500 different inputs, is a full day of pencil work and a guaranteed
  arithmetic slip somewhere.
- **It's a closed world.** When *you* do the trace, *you* also invent every value that
  goes in. The "program" only ever knows what the programmer decided in advance. Nothing
  outside the code can influence what happens.

Chapter 1 removes both limits at once:

- You hand the list of instructions to the **Python interpreter**, and *it* does the
  trace — perfectly, instantly, every time, at any scale.
- You add one new kind of instruction, **`input()`**, that pauses the program and lets a
  real person — the **end user** — put a value into one of the boxes *while the program
  is running*. The program stops being a fixed script and becomes **interactive**.

### The Connection — *the old skill nests inside the new one*

You are not throwing away hand-tracing — you are **plugging it into** real code:

| Week 0 idea | Chapter 1 form |
|---|---|
| "Run statements top to bottom, one at a time" | Exactly how Python runs your `.py` file |
| "A labelled box holding a value" | A Python **variable**: `visitor_name = "Ada"` |
| "Write down what the program displays" | The **`print()`** function does the displaying |
| "*You* supply the values while tracing" | **`input()`** lets the *end user* supply them at runtime |
| "Keep a trace table to predict output" | Still exactly how you'll answer Quiz 1 code-tracing questions — now some box values are labelled *"whatever the user typed"* |

So the plan for this worksheet: keep tracing like you learned in Week 0, and learn the
four Chapter 1 tools that let a program store data, talk to a user, listen to a user, and
do arithmetic on what it hears.

---

## 2. Concept Blueprint & Visual Blueprint (Theory & Application)

### The Core Theory (metaphors first, syntax second)

Think of a small restaurant kitchen:

| Metaphor | Programming reality | Syntax you'll use |
|---|---|---|
| The **recipe card** you wrote | Your **source code** — the `.py` file | plain text you type |
| The **cook** who follows the card exactly, step by step | The **Python interpreter** | `python3 my_program.py` |
| **Plating a dish and sending it out** to the diner | Showing information to the user | `print(something)` |
| The cook **pausing to ask the diner** "how spicy?" and waiting for the answer | Asking the user for information and waiting | `answer = input("How spicy? ")` |
| A **labelled jar** on the shelf holding one ingredient | A **variable** holding one value | `spice_level = "hot"` |
| Reading "3" off an order ticket — it's **ink on paper**, not the number 3 | `input()` always hands back **text (`str`)**, even if it looks like a number | `int("3")` turns text into a number |

Four facts to carry into the quiz:

1. **`print(...)`** displays its contents to the user, then moves to a new line. You can
   give it several items separated by commas — `print("Hi", name)` — and it puts a single
   space between them.
2. **`input(prompt)`** displays `prompt`, waits for the user to type something and press
   Enter, and then **evaluates to the text they typed** (a `str`). You almost always
   store that result in a variable: `city = input("Your city: ")`.
3. **`input()` gives you a string — full stop.** If the user types `25`, you get the
   two-character string `"25"`, not the number `25`. `"25" + "10"` is `"2510"`. To do
   math you must convert: `int("25")` → `25`, or `float("3.5")` → `3.5`.
4. **A comment starts with `#`.** Everything after `#` on that line is ignored by Python
   and is there for humans. Lab grading gives you a mark for style/commenting, so this is
   free points — get in the habit now.

### Real-World Context (where this exact pattern ships in production)

The `prompt → read → convert → compute → display` cycle you're learning **is** the
skeleton of an enormous amount of real software:

- **Command-line tools** (`git`, `pip`, database shells): print a prompt, read what you
  type, act on it.
- **Installers and setup wizards**: "Install location?", "Accept the licence? (y/n)" —
  each is an `input()` whose answer decides what happens next.
- **Chatbots and assistants**: at the lowest level it's a loop of *read the user's
  message → process → print a reply*.
- **Web form handlers**: a signup form is the browser version of a stack of `input()`
  calls; the server converts and validates each field before storing it.

**The ethics thread (this is examinable and it's a graded theme all term).** The
programmer decides three things the end user never sees:

- **What the program asks for.** Every field you prompt for is data someone now has to
  trust you with. Asking for a birth date "to personalise your experience" when you only
  need it to check an age limit is a small dishonesty with real consequences.
- **What the wording says.** Prompts should be clear, plain, and accessible — not
  jargon, not manipulative ("Are you *sure* you want to miss out?").
- **What happens to the answer.** Storing it, sending it somewhere, showing it back to
  the user, logging it — the user consented to *answering a question*, not necessarily to
  all of that.

The three roles — **programmer**, **program**, **end user** — have different knowledge
and different power, and the programmer holds the most of both. That asymmetry is the
reason "just following the spec" is not a complete ethical answer.

### Visual Diagram Blueprint Box

**Both diagrams are drawn for you below.** The full annotation spec follows them — read it
alongside the pictures; its callouts explain *why* each step happens, and it's still worth
re-drawing Diagram 1 yourself from memory as a check.

![Chapter 1, Diagram 1 — execution flow and memory state for the ticket-price script: a START-to-END flowchart of lines L1-L6 down the left, memory-state snapshots after L1/L3/L5/L6 in the middle, seven numbered callouts explaining each step, a colour key for str/float/int, and a SCREEN box showing the printed output "Ticket price check / Total: 50.0".](images/chapter_01_diagram_1_execution_flow.png)

![Chapter 1, Diagram 2 — the three roles: PROGRAMMER --writes--> PROGRAM --serves--> END USER, with a "feedback / consequences" arrow looping back from the end user to the programmer. Under each box: what that role controls, is responsible for, and knows. A cloud callout reads "The programmer has the most knowledge AND the most power. That asymmetry is why 'the spec told me to' is not a full answer to an ethical question."](images/chapter_01_diagram_2_three_roles.png)

The full annotation spec for both diagrams follows — use it to check details and read the
callouts.

```
[DIAGRAM DESIGN & ANNOTATION SPECIFICATION]
==========================================================================
DIAGRAM 1 OF 2 — "EXECUTION FLOW + MEMORY STATE FOR AN INTERACTIVE SCRIPT"
==========================================================================

REFERENCE PROGRAM (the exact 6 logical lines the diagram must map):

    L1  print("Ticket price check")
    L2  ticket_price_text = input("Price per ticket in dollars: ")
    L3  ticket_count_text  = input("How many tickets? ")
    L4  ticket_price_dollars = float(ticket_price_text)
    L5  ticket_count         = int(ticket_count_text)
    L6  print("Total:", ticket_price_dollars * ticket_count)

LAYOUT
------
- LEFT COLUMN: a vertical flowchart. One rounded rectangle per line L1..L6,
  connected top-to-bottom by DOWN arrows. At the very top add a "START"
  pill; at the very bottom add an "END" pill.
- RIGHT COLUMN: a "MEMORY / STATE" panel drawn as a stack of labelled
  boxes. The box list GROWS as you move down the flowchart — show the
  panel four times (a snapshot after L1, after L3, after L5, after L6).
- Draw a dashed horizontal "you are here" line linking the current
  flowchart box to the matching memory snapshot.

ANNOTATION CALLOUTS (add each as a numbered speech bubble):

  (1) On L1  -> "Output only. No box is created. The interpreter is on
                line 1; state is still empty."
  (2) On L2  -> "input() PAUSES the whole program here and waits for Enter.
                The value that comes back is TEXT. New box created:
                ticket_price_text = '12.50'  (note the quotes — it's a str)."
      >> TRAP FLAG: draw a small warning triangle: "Even though it looks
         like a number, it is a string. '12.50' + '3' would be '12.503'."
  (3) On L3  -> "Second pause. Second box: ticket_count_text = '4'
                (still a string)."
  (4) On L4  -> "float(...) reads the text in ticket_price_text and
                produces a NEW value 12.5 of type float. New box:
                ticket_price_dollars = 12.5. The old text box still exists,
                unchanged."
  (5) On L5  -> "int(...) does the same for the count. New box:
                ticket_count = 4 (an int). Conversion never edits the
                original box — it makes a new value."
  (6) On L6  -> "Expression evaluated FIRST: 12.5 * 4 -> 50.0. THEN print
                shows: Total: 50.0  (comma in print() inserts one space)."
  (7) On END -> "No more lines. The interpreter stops. All boxes are
                discarded when the program exits."

MEMORY SNAPSHOT CONTENTS (what each right-column panel must show)
  after L1:  (empty)
  after L3:  ticket_price_text = '12.50'   [str]
             ticket_count_text  = '4'       [str]
  after L5:  ticket_price_text     = '12.50'  [str]
             ticket_count_text     = '4'      [str]
             ticket_price_dollars  = 12.5     [float]
             ticket_count          = 4        [int]
  after L6:  (same four boxes; nothing new — print() creates no box)

COLOUR / STYLE HINTS
  - Tint str boxes one colour, number boxes another. Seeing "text vs
    number" as two visibly different things is the whole lesson.
  - Put the printed console output in a separate "SCREEN" box at the
    bottom right, containing the two lines the user actually sees:
        Ticket price check
        Total: 50.0

==========================================================================
DIAGRAM 2 OF 2 — "THE THREE ROLES"
==========================================================================

Three boxes left-to-right, connected by arrows:

   [ PROGRAMMER ] --writes--> [ PROGRAM ] --serves--> [ END USER ]
        ^                                                   |
        |------------------ feedback / consequences --------|

Under each box list what that role CONTROLS and is RESPONSIBLE FOR:

  PROGRAMMER
    controls: what data is requested, the wording of every prompt,
              what the code does with each answer, what is stored/sent
    responsible for: honesty, clarity, accessibility, not over-asking,
              consequences they could reasonably foresee
    knows: how the whole system works

  PROGRAM
    controls: nothing of its own — it only does what the code says
    responsible for: nothing morally; it is an instrument
    knows: only the values currently in its boxes

  END USER
    controls: the values they choose to type in
    responsible for: giving truthful input if they want correct output
    knows: only what the prompts and printed output tell them

CALLOUT: "The programmer has the most knowledge AND the most power.
That asymmetry is why 'the spec told me to' is not a full answer to an
ethical question."
```

---

## 3. Warm-Up Drills (start here)

Nine quick questions to loosen up before the bigger exercises. Each one is 30 seconds to
2 minutes. Do them **in your head or on paper**, or type them into a Python shell (the
`>>>` prompt) or a scratch file `chapter_01/warmup.py` — whatever is fastest.

**Answers are in `answers/chapter_01_warmup_answers.md`.** Do all nine before
you open it. Getting one wrong and then seeing why is the point.

### Predict the output

**W1.** What does this print?

```python
print("2" + "3")
```

**W2.** What does this print?

```python
age = "17"
print("You are", age, "years old")
```

**W3.** What does this print, and why is there a `.0`?

```python
apples = 4
baskets = 2
print(apples / baskets)
```

### Fill in the blank

**W4.** Make this print exactly `Hello, Sam!`

```python
first_name = "Sam"
print("Hello, " _____[1]_____ first_name _____[2]_____ "!")
```

**W5.** Make this print the **sum** of the two numbers the user types (inputs `8` and `9`
must give `17`, not `89`).

```python
first_value  = input("First number: ")
second_value = input("Second number: ")
print(_____[1]_____(first_value) + _____[2]_____(second_value))
```

**W6.** Make Python ignore the second line without deleting it.

```python
print("keep this")
_____[1]_____ print("hide this line from Python")
```

### Write one line

**W7.** Write one line that asks `What's your name? ` and stores the reply in a variable
called `user_name`.

**W8.** `total_price` holds the number `19.99`. Write one line that prints it right after
a dollar sign with **no space**, like `$19.99`.

### Spot the bug

**W9.** The programmer wants `Double that is 10` when the user types `5`. What actually
happens, and what's the one-word fix?

```python
quantity = input("How many? ")
print("Double that is", quantity * 2)
```

---

## 4. Quiz-Prep Practice Engine (The Exercises)

Do these **in order**. A first, then B, then C. Try each one fully before looking at
Section 5 — a wrong attempt you then correct teaches far more than a right answer you
read.

### Exercise A: Missing Code (Fill-in-the-Blanks)

**How to work each one:** create the file named in its `# filename:` line, paste the whole
block, then replace every `_____[n]_____` with the exact code that makes it run correctly.
The block will **not** run until every blank is filled. When it does run, check it against
the `# sample run` comment at the bottom. Watch the string-vs-number trap.

---

**A1 — Greeting bot**
Behaviour: prints a title, asks for the user's first name, then prints
`Welcome aboard, <name>!` on its own line.

```python
# filename: chapter_01/a1_greeting_bot.py
# COMP 1000 - Chapter 1 practice - Exercise A1
# Purpose: greet the visitor by the name they type in.

_____[1]_____("=== Visitor Check-In ===")

visitor_name = _____[2]_____("Please type your first name: ")

print("Welcome aboard,", _____[3]_____ + "!")

# ▶ paste into the file above, fill blanks [1]-[3], then Run.
# sample run:  type  Ada
#   === Visitor Check-In ===
#   Please type your first name: Ada
#   Welcome aboard, Ada!
```

- `_____[1]_____` — the function that displays a line of output.
- `_____[2]_____` — the function that shows a prompt and returns what the user types.
- `_____[3]_____` — the variable holding the name the user entered.

> **✍️ ON THE SIDE** — In one sentence each, say *why* `[2]` must be `input` (not
> `print`) and why `[3]` is the variable rather than the text `"visitor_name"` in quotes.

---

**A2 — Two-number adder**
Behaviour: asks for two whole numbers and prints their arithmetic sum
(so inputs `20` and `22` must print `The sum is 42`, **not** `2022`).

```python
# filename: chapter_01/a2_adder.py
# COMP 1000 - Chapter 1 practice - Exercise A2
# Purpose: add two whole numbers the user types in.

first_number_text  = input("Enter the first whole number: ")
second_number_text = input("Enter the second whole number: ")

first_number  = _____[1]_____(first_number_text)
second_number = _____[2]_____(second_number_text)

total = first_number _____[3]_____ second_number

print("The sum is", _____[4]_____)

# ▶ paste into the file above, fill blanks [1]-[4], then Run.
# sample run:  type  20  then  22
#   Enter the first whole number: 20
#   Enter the second whole number: 22
#   The sum is 42
```

- `_____[1]_____`, `_____[2]_____` — convert the entered text into whole numbers.
- `_____[3]_____` — the operator that adds two numbers.
- `_____[4]_____` — the variable holding the result to display.

> **✍️ ON THE SIDE** — What exactly would print if you deleted lines `[1]` and `[2]` and
> just wrote `total = first_number_text + second_number_text`? Say why.

---

**A3 — Tip calculator**
Behaviour: asks for a bill amount (may have cents, e.g. `54.80`) and a tip percentage
(e.g. `15`), then prints the tip amount in dollars. Formula: `tip = bill * percent / 100`.

```python
# filename: chapter_01/a3_tip_calculator.py
# COMP 1000 - Chapter 1 practice - Exercise A3
# Purpose: work out the tip in dollars from a bill amount and a percentage.

_____[1]_____ Tip calculator: works out the tip in dollars

bill_amount_text     = input("Bill amount in dollars: ")
tip_percentage_text  = input("Tip percentage (just the number): ")

bill_amount    = _____[2]_____(bill_amount_text)
tip_percentage = float(tip_percentage_text)

tip_amount_dollars = bill_amount _____[3]_____ tip_percentage / 100

print("Tip to leave: $", tip_amount_dollars)

# ▶ paste into the file above, fill blanks [1]-[3], then Run.
# sample run:  type  54.80  then  15
#   Bill amount in dollars: 54.80
#   Tip percentage (just the number): 15
#   Tip to leave: $ 8.22
```

- `_____[1]_____` — begins a human-only comment line.
- `_____[2]_____` — converts text like `"54.80"` into a number with a decimal part.
- `_____[3]_____` — the multiplication operator.

> **✍️ ON THE SIDE** — Why is `[2]` `float` and not `int` here? What happens if the user
> types `54.80` and the code uses `int(...)`?

---

### Exercise B: Explain the Algorithm (Code Comprehension)

Create `chapter_01/b_membership_card.py`, paste the program below, and **run it once**
with the inputs `Ada` then `2001` so you can see its behaviour. **Do not rewrite the
code.** Your task is a written explanation (see the ✍️ prompt after it).

```python
# filename: chapter_01/b_membership_card.py
# COMP 1000 - Chapter 1 practice - Exercise B (read + explain, do not edit)
# ---------------------------------------------------------------
# Membership card summary
# Asks the visitor for their name and birth year, then prints a
# small formatted report.
# ---------------------------------------------------------------

CURRENT_YEAR = 2026

print("=== Membership Card Summary ===")

member_name       = input("Full name: ")
birth_year_text   = input("Year you were born (e.g. 1998): ")

birth_year = int(birth_year_text)
age_in_years = CURRENT_YEAR - birth_year

print("--------------------------------")
print("Member:", member_name)
print("Born:", birth_year)
print("Age this year:", age_in_years)
print("Card ID:", member_name + "-" + birth_year_text)
print("--------------------------------")
print("Thank you,", member_name)

# ▶ Run it once with inputs:  Ada   then   2001
```

> **✍️ ON THE SIDE** — Write a step-by-step technical paragraph (aim for 8–12 sentences)
> explaining the algorithm: what data enters, in what order the lines execute, how each
> variable box is created and what type it holds, how the final values are computed, and
> exactly how the printed report is assembled. Assume the user answers `Ada` then `2001`
> and that "this year" is 2026.

Make sure your paragraph answers:

1. Which lines produce output *before* the user has typed anything?
2. After both `input()` calls, name every variable that exists and its type
   (`str` / `int`). Why is `birth_year_text` still a string?
3. `CURRENT_YEAR - birth_year` — why does this arithmetic work, when
   `CURRENT_YEAR - birth_year_text` would crash?
4. On the `Card ID` line, `+` is used with strings. What does `+` do there, and why is
   `birth_year_text` used instead of `birth_year`?
5. Write out, line for line, the exact text the user sees on screen.

### Exercise C: Code from Scratch (Real-World Application Challenge)

**The story.** The Riverside Community Centre runs a small front-desk kiosk. When a
visitor arrives for a paid event, a volunteer needs the kiosk to:

1. Print a friendly title line for the event check-in.
2. Ask the visitor for their **name**.
3. Ask **how many people** are in their group.
4. Ask the **price per ticket** in dollars (this can have cents, e.g. `7.50`).
5. Work out the **total cost** (`people × price per ticket`).
6. Print a tidy multi-line receipt showing the visitor's name, the group size, the price
   per ticket, and the total cost.

**Constraints — you must use both the old skill and the new tools:**

- The program must use: at least two `# comments`, descriptive variable names (no `x`,
  `n`, `tmp`), `input()` for all three questions, `int()` and/or `float()` conversion so
  the arithmetic is numeric (not string-joining), a computed `total_cost` variable, and
  `print()` with comma-separated items for the receipt.
- **Stay in scope:** use only Chapter 1 features — no `if`, no loops, no functions of
  your own, no `import`, no lists. If you find yourself reaching for those, you've
  over-engineered it.

> **✍️ ON THE SIDE (do this first, before you write any code)** — Hand-trace the program
> you're about to write (Week 0 skill): list the variable boxes it will create, in order,
> and mark which hold text straight from `input()` and which hold numbers after
> conversion. Then predict the exact screen output for the inputs `Sam`, `3`, `7.50`.

Now create `chapter_01/c_kiosk.py`, paste this starter stub, and replace each `# TODO`
with real code:

```python
# filename: chapter_01/c_kiosk.py
# COMP 1000 - Chapter 1 practice - Exercise C
# Purpose: front-desk kiosk - greet a visitor and print a ticket receipt.

# TODO 1: print a friendly title line for the event check-in

# TODO 2: ask the visitor for their name            -> visitor_name
# TODO 3: ask how many people are in their group    -> group_size_text
# TODO 4: ask the price per ticket in dollars       -> price_per_ticket_text

# TODO 5: convert the group size to a whole number  -> group_size
# TODO 6: convert the ticket price to a decimal     -> price_per_ticket

# TODO 7: work out total_cost  =  group_size * price_per_ticket

# TODO 8: print a tidy multi-line receipt:
#         name, group size, price per ticket, total cost
#         (use print() with comma-separated items)

# ▶ Run it and check your output against your hand-trace prediction above.
```

> **✍️ ON THE SIDE (after coding)** — Ethics reflection, 2–4 sentences. The kiosk asks
> for the visitor's name. Does this task actually need it? Name one responsible choice
> the *programmer* could make about that name — how the prompt is worded, whether the
> name is stored anywhere after the receipt prints, or who can see the screen while it's
> displayed.

---

---

## 5. The Comprehensive Solution Manual (Teacher's Desk)

> Check your work against these. If you got something wrong, don't just read the fix —
> re-run *your* version, watch it fail, apply the fix, watch it pass. That loop is what
> sticks for the quiz.

### Exercise A — Answers

**A1 — Greeting bot**

```python
# filename: chapter_01/a1_greeting_bot.py
# COMP 1000 - Chapter 1 practice - Exercise A1
print("=== Visitor Check-In ===")          # [1] print  -> displays a line of output

visitor_name = input("Please type your first name: ")   # [2] input -> returns the typed text (a str)

print("Welcome aboard,", visitor_name + "!")            # [3] visitor_name -> the box holding the name
```

- `[1] print`
- `[2] input`
- `[3] visitor_name`

Why it works: `print` shows the title. `input` shows its prompt, waits for Enter, and
the whole `input(...)` call *becomes* the text the user typed, which we store in
`visitor_name`. In the final line, `print` gets two items separated by a comma
(`"Welcome aboard,"` and `visitor_name + "!"`), so it prints them with one space between.
`visitor_name + "!"` glues the exclamation mark onto the name because **both sides are
strings** — that's what `+` does for strings.

> **QUIZ TRAP — comma vs. `+` inside `print`.**
> `print("Welcome aboard,", visitor_name)` → `Welcome aboard, Ada` (space from the comma).
> `print("Welcome aboard," + visitor_name)` → `Welcome aboard,Ada` (no space — `+` glues
> strings with nothing between). Both are legal; they produce different output. Read
> these carefully on the quiz.

---

**A2 — Two-number adder**

```python
# filename: chapter_01/a2_adder.py
# COMP 1000 - Chapter 1 practice - Exercise A2
first_number_text  = input("Enter the first whole number: ")
second_number_text = input("Enter the second whole number: ")

first_number  = int(first_number_text)     # [1] int -> "20" becomes the number 20
second_number = int(second_number_text)    # [2] int -> "22" becomes the number 22

total = first_number + second_number       # [3] +  -> numeric addition: 20 + 22 == 42

print("The sum is", total)                 # [4] total -> holds 42
```

- `[1] int`
- `[2] int`
- `[3] +`
- `[4] total`

> **QUIZ TRAP — this is *the* Chapter 1 trap.**
> `input()` returns a **string**. If you skip the `int(...)` conversions, then
> `first_number_text + second_number_text` is `"20" + "22"` which is `"2022"` — string
> **concatenation**, not addition. The program still runs (no error!), it just gives the
> wrong answer. Whenever a quiz snippet does math on something from `input()`, check for
> the conversion first.

---

**A3 — Tip calculator**

```python
# filename: chapter_01/a3_tip_calculator.py
# COMP 1000 - Chapter 1 practice - Exercise A3
# Tip calculator: works out the tip in dollars       # [1] #  -> starts a comment line

bill_amount_text     = input("Bill amount in dollars: ")
tip_percentage_text  = input("Tip percentage (just the number): ")

bill_amount    = float(bill_amount_text)              # [2] float -> "54.80" becomes 54.8
tip_percentage = float(tip_percentage_text)

tip_amount_dollars = bill_amount * tip_percentage / 100   # [3] *  -> multiplication

print("Tip to leave: $", tip_amount_dollars)
```

- `[1] #`
- `[2] float`
- `[3] *`

Why `float` and not `int` for the bill: `int("54.80")` would **crash** with a
`ValueError` because `"54.80"` is not a whole number. `float("54.80")` handles the
decimal part. For inputs `54.80` and `15`, the result is
`54.8 * 15 / 100` → `8.22`.

> **QUIZ TRAP — evaluation order.** `bill_amount * tip_percentage / 100` runs left to
> right for `*` and `/` (same precedence): first `54.8 * 15` = `822.0`, then `/ 100` =
> `8.22`. You don't need brackets here, but adding them —
> `(bill_amount * tip_percentage) / 100` — makes the intent obvious and costs nothing.
> Also note `print("... $", tip_amount_dollars)` prints `Tip to leave: $ 8.22` with a
> space after the `$` (from the comma). To kill that space you'd write
> `print("Tip to leave: $" + str(tip_amount_dollars))` — `str(...)` converts the number
> back to text so `+` can glue it.

---

### Exercise B — Model Answer

**A correct explanatory paragraph looks like this:**

> Execution begins at the top. `CURRENT_YEAR = 2026` creates the first box, an `int`
> holding `2026`. The next line, `print("=== Membership Card Summary ===")`, runs before
> any user interaction and displays that title line. The program then reaches
> `member_name = input("Full name: ")`: it shows the prompt `Full name: `, pauses until
> the user types `Ada` and presses Enter, and stores the resulting **string** `"Ada"` in
> a new box called `member_name`. It does the same for
> `birth_year_text = input("Year you were born (e.g. 1998): ")`, storing the **string**
> `"2001"` — a string, because `input()` always returns text, regardless of whether the
> characters look like a number. Next, `birth_year = int(birth_year_text)` reads the text
> `"2001"`, produces the `int` value `2001`, and stores it in a new box `birth_year`;
> `birth_year_text` still exists and still holds `"2001"` unchanged, because conversion
> creates a new value rather than editing the original. Then
> `age_in_years = CURRENT_YEAR - birth_year` evaluates `2026 - 2001` — this works because
> both operands are `int`s — giving `25`, stored in `age_in_years`. Writing
> `CURRENT_YEAR - birth_year_text` instead would raise a `TypeError`, because you cannot
> subtract a string from an integer. The program then runs seven `print` calls in order:
> a divider line; `Member: Ada` (comma puts one space after the colon-space in the
> literal); `Born: 2001`; `Age this year: 25`; then `Card ID: Ada-2001`, where `+` is
> used to **concatenate** three strings — `member_name`, the literal `"-"`, and
> `birth_year_text`; `birth_year_text` is used here (not `birth_year`) precisely because
> `+` needs strings on both sides, and `"Ada" + "-" + 2001` would crash. A final divider
> and `Thank you, Ada` complete the output, and the program ends.

**Exact screen output** (inputs `Ada`, `2001`):

```
=== Membership Card Summary ===
Full name: Ada
Year you were born (e.g. 1998): 2001
--------------------------------
Member: Ada
Born: 2001
Age this year: 25
Card ID: Ada-2001
--------------------------------
Thank you, Ada
```

(The lines `Full name: Ada` and `Year you were born (e.g. 1998): 2001` appear because the
prompt text and the user's typed reply share the same line on screen.)

> **QUIZ TRAP — mixing `str` and `int` with `+`.** `member_name + "-" + birth_year_text`
> is fine (all strings). `member_name + "-" + birth_year` would raise
> `TypeError: can only concatenate str (not "int") to str`. If you ever need a number
> inside a `+` string join, wrap it: `member_name + "-" + str(birth_year)`.

---

### Exercise C — Model Solution

**Hand trace (written before the code):**

Boxes created, in order:
1. `visitor_name` — text straight from `input()` → `"Sam"`
2. `group_size_text` — text straight from `input()` → `"3"`
3. `price_per_ticket_text` — text straight from `input()` → `"7.50"`
4. `group_size` — number after `int()` conversion → `3`
5. `price_per_ticket` — number after `float()` conversion → `7.5`
6. `total_cost` — number, computed `3 * 7.5` → `22.5`

Predicted screen output for `Sam`, `3`, `7.50`:

```
=== Riverside Community Centre — Event Check-In ===
Your name: Sam
How many people are in your group? 3
Price per ticket in dollars: 7.50
------------- RECEIPT -------------
Name: Sam
Group size: 3
Price per ticket: $ 7.5
Total cost: $ 22.5
----------------------------------
```

**Program:**

```python
# filename: chapter_01/c_kiosk.py
# COMP 1000 - Chapter 1 practice - Exercise C
# Riverside Community Centre front-desk kiosk
# Chapter 1 only: input(), int()/float() conversion, print(), comments.

# --- Greeting ---------------------------------------------------------
print("=== Riverside Community Centre — Event Check-In ===")

# --- Collect information from the visitor (all input() results are text)
visitor_name          = input("Your name: ")
group_size_text       = input("How many people are in your group? ")
price_per_ticket_text = input("Price per ticket in dollars: ")

# --- Convert the text answers into numbers so we can do arithmetic ---
group_size       = int(group_size_text)          # "3"    -> 3     (whole people)
price_per_ticket = float(price_per_ticket_text)   # "7.50" -> 7.5   (dollars + cents)

# --- Do the calculation --------------------------------------------------
total_cost = group_size * price_per_ticket        # 3 * 7.5 -> 22.5

# --- Print the receipt -------------------------------------------------
print("------------- RECEIPT -------------")
print("Name:", visitor_name)
print("Group size:", group_size)
print("Price per ticket: $", price_per_ticket)
print("Total cost: $", total_cost)
print("----------------------------------")
```

Notes on the design:

- **`int` for people, `float` for money.** You can't have 2.5 visitors, so `group_size`
  is a whole number. Ticket prices have cents, so `price_per_ticket` must be `float` —
  `int("7.50")` would crash.
- **Why keep the `_text` variables at all?** Clarity. Naming the raw string
  `group_size_text` and the converted number `group_size` makes it obvious at a glance
  which boxes hold text and which hold numbers — the exact distinction the quiz tests.
- **Comma, not `+`, in every `print`.** `print("Group size:", group_size)` works even
  though `group_size` is a number, because the comma form doesn't require both sides to
  be strings. `print("Group size:" + group_size)` would raise a `TypeError`.

> **QUIZ TRAP — forgetting the conversion.** If you wrote
> `total_cost = group_size_text * price_per_ticket_text` you'd get an error
> (`can't multiply sequence by non-int of type 'str'`). And
> `group_size_text * 3` would actually *succeed* and give `"333"` — Python repeats a
> string when you multiply it by an int. Neither is what you want. Convert first, always.

> **QUIZ TRAP — the space after `$`.** `print("Total cost: $", total_cost)` prints
> `Total cost: $ 22.5` (space from the comma). That's acceptable here. If a question
> demands `$22.5` with no gap, the Chapter 1 way is
> `print("Total cost: $" + str(total_cost))`.

**Ethics reflection (model answer):**

> Strictly, the kiosk does not *need* the visitor's name to compute a total — the
> arithmetic only uses the group size and ticket price. The name is collected for the
> receipt and for a friendlier interaction, which is a reasonable purpose, but it should
> be treated with care. One responsible programmer choice: do **not** store or log the
> name anywhere after the receipt is printed — hold it only in the `visitor_name`
> variable for the length of one check-in, so the kiosk never accumulates a list of who
> attended. A second choice: word the prompt as "Your name (optional, for your receipt):"
> so the visitor knows why it's asked and that they can skip it.

---

## Quiz-Day Checklist (the 60-second review)

- [ ] `input()` **always** returns a `str`. Look for `int()` / `float()` before any math.
- [ ] `int("3.5")` **crashes**; `float("3.5")` is fine. `int("3")` and `float("3")` both fine.
- [ ] `print(a, b)` → one space between. `print(a + b)` → strings glued, no space, and both must be strings.
- [ ] `"5" + "5"` → `"55"`.  `5 + 5` → `10`.  `"5" * 3` → `"555"`.
- [ ] A `#` comment runs to the end of its line and is ignored by Python.
- [ ] To predict output: trace top to bottom, keep a box table, write down every `print`.
- [ ] Roles: the **programmer** chooses what's asked, how it's worded, and what's done with the answer — and carries the responsibility for all three.
