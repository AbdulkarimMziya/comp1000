# Chapter 2: MASTERING DATA & INSTRUCTIONS

> **Review Teacher's Note — read this first.**
> This is a **self-study practice worksheet** built to keep you ahead of the COMP 1000
> schedule. Your class covers this material in **Week 2** (Sept 14, 16), from Runestone
> Chapter 2.
>
> There is **no quiz dedicated to Chapter 2** — Quiz 1 (Week 2) is on Chapter 1, and the
> Week 3 slot is **Test 1**. So this worksheet targets **Test 1: Wednesday, Sept 23**,
> which is *cumulative over Chapters 1–2* (plus the first bits of Ch3 debugging). Test 1
> is worth 6% and is made of multiple-choice, short-answer, and coding questions. It's
> the first graded test — get comfortable now and it's just another Wednesday.
>
> This document is study material, consistent with the course academic-integrity policy
> (AI tools are allowed "when practicing coding and when reading through the textbook").
>
> **Estimated completion time:** 75–100 minutes (plus ~15 for the Section 3 warm-ups).
> Have a Python 3 environment open (IDLE, the Runestone activecode boxes, or `python3` in
> a terminal) and actually run every snippet. Reading is not the same as knowing.

---

## ▶ Before You Start: Watch This First

**Course:** *Python for Non-Programmers* (LinkedIn Learning) —
<https://www.linkedin.com/learning/python-for-non-programmers/>

This course front-loads all of its data-and-operators material into two dense early
videos, so the watch list for this chapter is short — but **re-watch them slowly**, pausing
on every operator. The real depth for Chapter 2 is the **Runestone Chapter 2 reading**;
do every section there.

| # | Section → Video | Length | Watch for |
|---|---|---|---|
| 1 | Python Basics → *Numbers: Ints and floats* (re-watch) | 4 min | every operator: `+ - * / // % **` |
| 2 | Python Basics → *Strings* (re-watch) | 5 min | `+` (join), `*` (repeat), `len()` |
| 3 | Functions and More → *Solution: Is there a remainder?* | 3 min | `%` used in a real problem |
| 4 | Python Basics → *Solution: Odd or even* | 2 min | the `%` idea — **ignore the `if` part**, that's Chapter 6 |

**Stop there.** *Booleans and if statements* and *Comparison and else* are COMP 1000
**Chapter 6 (Conditionals)**. For now you only need to know that `True` and `False` are a
data type (`bool`) — you'll compute *with* them in Chapter 6.

> **Two notes.**
> 1. If a video shows `round(number, 2)` — good to recognise. The exercises here don't
>    require it; they'll show you the raw float so you *see* the imprecision.
> 2. The **ethics thread** in Section 2 (honesty in how numbers are stored and shown) is
>    COMP 1000-specific — read it in the worksheet and the Runestone chapter.

### Concepts to understand before attempting the questions

Tick each one off. If any is shaky, re-watch that video or re-read the Runestone section
before starting the practice questions (Sections 3–4).

- [ ] I can name the four basic types — **`int`, `float`, `str`, `bool`** — and use
      **`type(x)`** to check one.
- [ ] **`/`** always gives a `float`; **`//`** gives the whole-number part (rounds down);
      **`%`** gives the remainder.
- [ ] **`**`** means "to the power of" (`2 ** 10` is `1024`).
- [ ] **Precedence:** `( )` → `**` → `*  /  //  %` → `+  -`; operators on the same tier
      run left to right.
- [ ] An **expression** works out to a single value; a **statement** *does* something
      (an assignment, a `print`).
- [ ] **`=` means "gets":** the right-hand side is worked out first (using the current
      values), then the result is stored in the left-hand box.
- [ ] **`count = count + 1`** only works if `count` already holds a value.
- [ ] On strings: **`+`** joins, **`*`** repeats, **`len(text)`** counts the characters.
- [ ] **`input()`** still returns a `str` — convert with `int()` / `float()` before doing
      arithmetic.

---

## Setup for this worksheet (do this before Sections 3–4)

You'll do the coding parts in your IDE (IDLE, VS Code, Thonny — whatever you use for
labs), one small script per exercise.

1. **Make a folder** for this chapter's practice work:

   ```
   comp1000/
     chapter_02/
   ```

2. **As you reach each coding exercise**, create the file named in its `# filename:` line
   and paste the block that's provided.

   | Exercise | File to create |
   |---|---|
   | A1 | `chapter_02/a1_price_split.py` |
   | A2 | `chapter_02/a2_cart_total.py` |
   | A3 | `chapter_02/a3_growth.py` |
   | B  | `chapter_02/b_time_formatter.py` |
   | C  | `chapter_02/c_print_shop.py` |

3. **Run** a script with the Run button, or `python3 chapter_02/a1_price_split.py` in a
   terminal. When it asks a question, type your answer and press Enter.

> **✍️ ON THE SIDE** — Some prompts are marked like this. They are *thinking* answers
> (explanations, hand-traces, reflections), **not** code to run. Write them wherever suits
> you — on paper, or in a plain typed notes file beside you. Nothing to submit, no
> filename required. The point is that you actually write them out in words.

---

## 1. The Bridge: Connecting the Dots (Review & Linkage)

### The Review — *Teacher Review Notes: Chapter 1*

Chapter 1 gave you four tools and one mental model:

- **`print(...)`** shows things to the user; commas put one space between items.
- **`input(prompt)`** shows a prompt, waits, and hands back **whatever was typed, as a
  `str`** — always.
- **`int(...)` / `float(...)` / `str(...)`** convert a value from one kind to another.
- **`#`** starts a human-only comment.
- The **mental model:** a program is statements run top to bottom; each variable is a
  **labelled box** holding a value; to predict output you keep a trace table of the boxes
  and walk down the code.

You also met the **programmer / program / end-user** roles and the idea that the
programmer carries responsibility for what a program asks for and does.

### The Evolution — *why Chapter 1's toolkit gets cramped*

In Chapter 1 you mostly *stored* values and did **one** operation at a time (`price *
count`, `a + b`). Three things start to hurt as programs grow:

1. **Real formulas chain many operators.** `base + rate * years ** 2 - fee` — Python has
   to decide what happens first. Guess wrong and your total is silently wrong.
2. **`+` and `*` mean different things depending on type.** `"5" + "5"` is `"55"`;
   `5 + 5` is `10`. You need to *know*, at every step, what kind of data is in each box —
   and be able to ask Python with `type(...)`.
3. **You often need to update a box from its own current value** — a running total, a
   score, a counter: `total = total + item_price`. Chapter 1 never did this.

And Chapter 1's `/` always handed back a `.0` — it had no way to say "just the whole
part" or "the remainder".

Chapter 2 fixes all of it: the **full operator set** (`+ - * / // % **`), the
**precedence rules** that order them, **`type()`**, and **reassignment / the accumulator
pattern**.

### The Connection — *the trace table grows one column*

Your Week 0 / Chapter 1 trace table listed each box and its value. In Chapter 2 it gets a
**type** column, because the type decides what every operator does:

| Chapter 1 idea | Chapter 2 form |
|---|---|
| A box holds a value | A box holds a value **and a type** (`int` / `float` / `str` / `bool`); `type(box)` tells you which |
| `+` joins strings; `+` adds numbers | The full set `+ - * / // % **`, each behaving **by type**, ordered by **precedence** |
| `total = price * count` (one step) | `total = total + price` — a box updated **from its own current value** |
| `/` always gave a `.0` | `//` gives the whole-number part, `%` gives the remainder |
| Convert once with `int()` / `float()` | The same conversions, now used fluently mid-expression |

`input()` still returns a `str`. Chapter 2 just makes you fast and sure about the
conversions and the arithmetic that comes after.

---

## 2. Concept Blueprint & Visual Blueprint (Theory & Application)

### The Core Theory (metaphors first, syntax second)

**Data types = what *kind* of thing is in the jar.** Flour, water, a printed label, a
light switch. You can triple the flour. You can "triple" a printed label too — you just
get the same label three times in a row (`"ha" * 3` → `"hahaha"`). That difference is the
source of half the Chapter 2 traps.

| Type | What it is | Literal examples | `type(value)` shows |
|---|---|---|---|
| `int` | a whole number | `0`, `42`, `-7` | `<class 'int'>` |
| `float` | a number with a decimal point | `3.0`, `-0.5`, `2.5` | `<class 'float'>` |
| `str` | text in quotes | `"hi"`, `'42'`, `""` | `<class 'str'>` |
| `bool` | a yes/no value — only two exist | `True`, `False` | `<class 'bool'>` |

**Expression vs statement.** An **expression** is a question Python works out to *one
value*: `2 + 3 * 4` → `14`. A **statement** is an instruction that *does* something: an
assignment, a `print(...)`. The assignment statement `box = expression` means: *work out
the right side to a single value, then put that value in the box named on the left.*

**`=` is "gets", not "equals".** `score = score + 10` is not a claim that `score` equals
`score + 10` (impossible in maths). It's an instruction: *take the current contents of
`score`, add 10, put the result back into `score`.* This is the **accumulator pattern**,
and it needs `score` to already hold a value.

**Operators and what they do to two numbers** (using `7` and `2`):

| Operator | Name | `7 op 2` | Also note |
|---|---|---|---|
| `+` | add | `9` | on `str`: **join** — `"a" + "b"` → `"ab"` |
| `-` | subtract | `5` | |
| `*` | multiply | `14` | `str * int`: **repeat** — `"ab" * 3` → `"ababab"` |
| `/` | true divide | `3.5` | **always** a `float` — even `4 / 2` → `2.0` |
| `//` | floor divide | `3` | the whole-number part; rounds **down** |
| `%` | modulo | `1` | the remainder left after `//` |
| `**` | power | `49` | `7 ** 2` = 7 squared |

**Precedence — the order Python does the steps** (high to low):

```
1.  ( )         brackets first
2.  **          powers
3.  *  /  //  % left to right
4.  +  -        left to right
```

It's the "BEDMAS / PEMDAS" from maths class, with `//` and `%` sitting alongside `*` and
`/`. When two operators are on the same tier, Python works **left to right**.

**`%` (modulo) is worth its own paragraph.** It's "what's left over after fair sharing".
`17 % 5` → `2`. It answers a surprising number of real questions:

- **Is a number even?** `number % 2` is `0` for even, `1` for odd.
- **Last digit of a number?** `number % 10`.
- **Wrap around a clock?** `(hour + 5) % 12`.

### Real-World Context (where this ships in production)

- **Every spreadsheet formula** is an expression evaluated by precedence rules — get the
  rules wrong in a finance model and the numbers are wrong with no error message.
- **`%` is everywhere:** paginating results (item 47, 10 per page → page `47 // 10`, slot
  `47 % 10`), striping alternate table rows (`row_number % 2`), spreading work across
  servers (`user_id % number_of_servers`), calendar and clock math, wrapping colour
  values.
- **The accumulator pattern** (`total = total + x`) is the engine of every running total,
  shopping cart, game score, download progress bar, and analytics sum ever written.
- **Type awareness:** data from a web API or a form arrives as **strings**. Every backend
  converts and *validates* each field's type before doing arithmetic — the same
  `int(...)` / `float(...)` you're learning, at scale.

**The ethics thread — honesty in how numbers are stored and shown.** A "small" type or
rounding choice becomes an ethical choice the moment the number is someone's money, grade,
or medication dose:

- Storing a price as `int` when it needs cents silently drops money.
- Using `//` where the customer expects normal rounding changes what they're charged.
- Showing `45.449999999999996` on a receipt instead of `$45.45` is technically the
  computer's honest answer, but it's not an honest *presentation* — and choosing the
  presentation is the programmer's job. (You'll produce exactly that number in
  Exercise C.)

The end user trusts that the arithmetic behind a total is done right **and shown fairly**.
Both halves are on you.

### Visual Diagram Blueprint Box

You can't get an image from a worksheet, so here are two precise build specs. Draw them by
hand (or in any diagram tool) — the act of drawing is the point.

```
[DIAGRAM DESIGN & ANNOTATION SPECIFICATION]
==========================================================================
DIAGRAM 1 OF 2 — "EXPRESSION EVALUATION: HOW PRECEDENCE COLLAPSES AN
                  EXPRESSION TO ONE VALUE"
==========================================================================

REFERENCE STATEMENT (the exact line the diagram must map):

    answer = 2 ** 3 + 12 // 5 * 3 - 4 % 3

LAYOUT
------
- Draw it as a LADDER of rewrites, top to bottom. Each rung is the whole
  expression with exactly ONE operator resolved, the resolved part boxed.
- To the RIGHT of each rung, a callout says WHICH precedence rule fired
  and WHY that operator went next.
- At the bottom, a single box: "answer  <-  13   [int]".

THE RUNGS (fill these in exactly):

  2 ** 3 + 12 // 5 * 3 - 4 % 3
      |_____|  <- (1) ** is tier 2, the highest here -> 2 ** 3 = 8

  8 + 12 // 5 * 3 - 4 % 3
      |______|  <- (2) tier 3 (* / // %), LEFT-MOST first -> 12 // 5 = 2

  8 + 2 * 3 - 4 % 3
      |___|  <- (3) still tier 3, next one left -> 2 * 3 = 6

  8 + 6 - 4 % 3
          |____|  <- (4) still tier 3, the % -> 4 % 3 = 1

  8 + 6 - 1
  |___|  <- (5) tier 4 (+ -), LEFT-MOST first -> 8 + 6 = 14

  14 - 1
  |____|  <- (6) tier 4, last one -> 14 - 1 = 13

  answer <- 13   [int]

ANNOTATION CALLOUTS (add as speech bubbles):
  - Big arrow on rung (2)->(3)->(4): "Same tier => there is NO 'do
    multiplication before modulo'. It is purely LEFT TO RIGHT."
  - On the final box: "Only NOW does the assignment happen. '=' waited for
    the whole right side to become one value."
  - TRAP FLAG near the top: "2 ** 3 ** 2 is NOT (2**3)**2. '**' is the one
    operator that goes RIGHT to left: 2 ** (3 ** 2) = 2 ** 9 = 512."

==========================================================================
DIAGRAM 2 OF 2 — "REASSIGNMENT: ONE BOX, PHOTOGRAPHED OVER TIME"
==========================================================================

REFERENCE PROGRAM:

    L1  running_total = 0
    L2  running_total = running_total + 5
    L3  running_total = running_total + 3
    L4  running_total = running_total * 2

LAYOUT
------
- ONE box labelled 'running_total', drawn as a filmstrip of 4 frames
  (after L1, after L2, after L3, after L4).
- Under each frame (except the first) show a 3-part strip:
      READ old value  ->  EVALUATE right-hand side  ->  WRITE back
- Arrows loop from the box, down through READ/EVALUATE, back UP into the
  box for WRITE. The loop-back arrow is the whole point.

FRAME CONTENTS:
  after L1:  running_total = 0
  after L2:  READ 0   -> 0 + 5  = 5   -> WRITE 5     (box now 5)
  after L3:  READ 5   -> 5 + 3  = 8   -> WRITE 8     (box now 8)
  after L4:  READ 8   -> 8 * 2  = 16  -> WRITE 16    (box now 16)

ANNOTATION CALLOUTS:
  (1) On the L2 strip: "The right side uses the OLD value (0). The box is
      not overwritten until the right side is fully worked out."
  (2) Between frames: "'=' here means GETS, not 'is equal to'. Read it as
      'running_total GETS running_total + 5'."
  (3) TRAP FLAG before L1: "Delete line L1 and L2 crashes:
      NameError: name 'running_total' is not defined. You cannot READ a
      box that was never filled."
  (4) End note: "This read -> change -> write-back loop is the accumulator
      pattern. Every running total in every program is this."
```

---

## 3. Warm-Up Drills (start here)

Nine quick questions to loosen up before the bigger exercises. Each is 30 seconds to 2
minutes. Do them **in your head or on paper**, or type them into a Python shell (the
`>>>` prompt) or a scratch file `chapter_02/warmup.py` — whatever is fastest.

**Answers are in `answers/chapter_02_warmup_answers.md`.** Do all nine before
you open it.

### Predict the output

**W1.** What does this print?

```python
print(7 / 2, 7 // 2, 7 % 2)
```

**W2.** What does this print?

```python
print(2 ** 3 + 1)
```

**W3.** What does this print?

```python
score = 10
score = score + 5
score = score * 2
print(score)
```

### Fill in the blank

**W4.** Make this print `Remainder when divided by 2: 0`

```python
number = 18
print("Remainder when divided by 2:", number _____[1]_____ 2)
```

**W5.** Make `divider` hold a line of exactly **20 dashes**, then print it.

```python
divider = _____[1]_____
print(divider)          # must print:  --------------------
```

**W6.** Make this print `6.75` (a running total built up item by item).

```python
cart_total = 0.0
cart_total = _____[1]_____ + 4.50
cart_total = _____[2]_____ + 2.25
print(cart_total)
```

### Write one line

**W7.** `total_seconds` holds `200`. Write one line that prints how many **whole minutes**
that is (the answer should be `3`).

**W8.** `password` holds `"sunshine"`. Write one line that prints how many characters it
has.

### Spot the bug

**W9.** The programmer expects this to print `10`. What actually happens when you run it,
and what one line fixes it?

```python
total = total + 10
print(total)
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
the `# sample run` comment at the bottom.

---

**A1 — Price splitter**
Behaviour: takes a whole price in **cents** and prints it as dollars and cents
(so `1234` prints `That's 12 dollars and 34 cents`).

```python
# filename: chapter_02/a1_price_split.py
# COMP 1000 - Chapter 2 practice - Exercise A1
# Purpose: split a price given in cents into whole dollars + leftover cents.

total_cents_text = input("Total price in cents: ")
total_cents = int(total_cents_text)

dollars = total_cents _____[1]_____ 100      # whole dollars
cents   = total_cents _____[2]_____ 100      # leftover cents

print("That's", dollars, "dollars and", cents, "cents")

# ▶ paste into the file above, fill blanks [1]-[2], then Run.
# sample run:  type  1234
#   Total price in cents: 1234
#   That's 12 dollars and 34 cents
```

- `_____[1]_____` — the operator that keeps only the whole-number part of a division.
- `_____[2]_____` — the operator that gives the remainder.

> **✍️ ON THE SIDE** — What would `dollars` be if you used `/` instead of `//`, and why
> would the sentence then read wrong?

---

**A2 — Cart running total**
Behaviour: asks for three item prices and prints the total, building it up one item at a
time with the accumulator pattern.

```python
# filename: chapter_02/a2_cart_total.py
# COMP 1000 - Chapter 2 practice - Exercise A2
# Purpose: add three prices into one running total.

cart_total = 0.0                       # start empty

price_one_text = input("Price of item 1: ")
cart_total = cart_total _____[1]_____ float(price_one_text)

price_two_text = input("Price of item 2: ")
cart_total = cart_total + _____[2]_____(price_two_text)

price_three_text = input("Price of item 3: ")
cart_total = _____[3]_____ + float(price_three_text)

print("Cart total: $", cart_total)

# ▶ paste into the file above, fill blanks [1]-[3], then Run.
# sample run:  type  3.50  then  1.25  then  10.00
#   Cart total: $ 14.75
```

- `_____[1]_____` — the operator that adds a number onto the running total.
- `_____[2]_____` — the function that turns `"1.25"` into the number `1.25`.
- `_____[3]_____` — the box whose **current value** must be read before the new price is
  added on.

> **✍️ ON THE SIDE** — Line 3 blank must be `cart_total`. In one sentence, explain why the
> line `cart_total = cart_total + float(price_three_text)` is not circular / not a
> contradiction.

---

**A3 — Two-year growth**
Behaviour: a deposit grows by a fixed rate **each year for two years**. Formula:
`final = starting * rate ** 2`.

```python
# filename: chapter_02/a3_growth.py
# COMP 1000 - Chapter 2 practice - Exercise A3
# Purpose: compound a starting amount by a yearly rate, twice.

starting_amount_text = input("Starting amount in dollars: ")
starting_amount = float(starting_amount_text)

growth_rate = 1.1                      # 10% growth per year

final_amount = starting_amount _____[1]_____ growth_rate _____[2]_____ 2

print("After 2 years: $", final_amount)

# ▶ paste into the file above, fill blanks [1]-[2], then Run.
# sample run:  type  100
#   Starting amount in dollars: 100
#   After 2 years: $ 121.00000000000001
```

- `_____[1]_____` — the multiplication operator.
- `_____[2]_____` — the "to the power of" operator.

> **✍️ ON THE SIDE** — Because of precedence, `starting_amount * growth_rate ** 2` does
> the `** 2` **first**. Work out by hand what the answer would instead be if it ran as
> `(starting_amount * growth_rate) ** 2`. (For `100` that's `110 ** 2` = `12100` — wildly
> different. That's why precedence matters.)

---

### Exercise B: Explain the Algorithm (Code Comprehension)

Create `chapter_02/b_time_formatter.py`, paste the program below, and **run it once** with
the input `7384` so you can see its behaviour. **Do not rewrite the code.** Your task is a
written explanation (see the ✍️ prompt after it).

```python
# filename: chapter_02/b_time_formatter.py
# COMP 1000 - Chapter 2 practice - Exercise B (read + explain, do not edit)
# -------------------------------------------------------------
# Turns a number of seconds into hours, minutes, and seconds.
# -------------------------------------------------------------

total_seconds_text = input("Enter a number of seconds: ")
total_seconds = int(total_seconds_text)

hours = total_seconds // 3600
remaining_seconds = total_seconds % 3600

minutes = remaining_seconds // 60
seconds = remaining_seconds % 60

print("----------------------")
print("Total seconds:", total_seconds)
print("Hours:", hours)
print("Minutes:", minutes)
print("Seconds:", seconds)
print(hours, "h", minutes, "m", seconds, "s")

# ▶ Run it once with input:  7384
```

> **✍️ ON THE SIDE** — Write a step-by-step technical paragraph (aim for 8–12 sentences)
> explaining the algorithm: what data enters, how it is converted, and how each `//` and
> `%` step peels off one unit of time. Assume the user enters `7384`.

Make sure your paragraph answers:

1. What is the **type** of `total_seconds_text`, and the type of `total_seconds`? Why do
   they differ?
2. Trace the arithmetic for input `7384`: give the value of `hours`, `remaining_seconds`,
   `minutes`, and `seconds`, in the order they are computed.
3. Why does the code compute `remaining_seconds` at all, instead of going straight to
   `minutes = total_seconds // 60`?
4. `3600` and `60` are written directly in the code ("magic numbers"). Where do they come
   from?
5. Write out, line for line, the exact text printed for input `7384`.

### Exercise C: Code from Scratch (Real-World Application Challenge)

**The story.** The campus print shop needs a quick estimator. A print job has a **page
count**. Pages are printed **double-sided — 2 pages per sheet**. Paper is stocked in
**packs of 500 sheets**. Given the page count, the clerk needs to see:

1. A title line for the estimate.
2. **Sheets needed** — pages ÷ 2, rounded **up** (an odd last page still needs a whole
   sheet). The rounding-up trick with only Chapter 2 tools: `(page_count + 1) // 2`.
3. **Whole packs** that many sheets uses up (`sheets_needed // 500`).
4. **Loose sheets** left over beyond the whole packs (`sheets_needed % 500`).
5. **Cost** at **$0.09 per sheet** (`sheets_needed * 0.09`).
6. A tidy multi-line estimate showing page count, sheets needed, packs, loose sheets, and
   cost.

**Constraints:**

- Use only Chapter 1–2 features: variables, `input()`, `print()` with commas,
  `int()` / `float()` / `str()`, and the operators `+ - * / // % **`, plus `#` comments.
- Descriptive variable names (no `x`, `n`, `tmp`). At least two comments.
- **No** `if`, loops, functions of your own, `import`, or lists.

> **✍️ ON THE SIDE (do this first, before you write any code)** — Hand-trace your planned
> program for `page_count = 1010`: list every box in the order it's created, with its
> value and type, then predict the exact screen output.

Now create `chapter_02/c_print_shop.py`, paste this starter stub, and replace each
`# TODO` with real code:

```python
# filename: chapter_02/c_print_shop.py
# COMP 1000 - Chapter 2 practice - Exercise C
# Purpose: print-shop estimator - sheets, packs, loose sheets, and cost.

# TODO 1: print a title line for the estimate

# TODO 2: ask for the page count (text)             -> page_count_text
# TODO 3: convert it to a whole number              -> page_count

# TODO 4: sheets_needed = (page_count + 1) // 2      (2 pages per sheet, round UP)
# TODO 5: whole_packs   = sheets_needed // 500
# TODO 6: loose_sheets  = sheets_needed  % 500
# TODO 7: cost_dollars  = sheets_needed  * 0.09

# TODO 8: print a tidy multi-line estimate:
#         page count, sheets needed, whole packs, loose sheets, cost
#         (use print() with comma-separated items)

# ▶ Run it and check your output against your hand-trace prediction above.
```

> **✍️ ON THE SIDE (after coding)** — Run it with `page_count = 1010`. The cost line will
> print `45.449999999999996`. In 2–4 sentences: is it honest to show that to a customer?
> What should the programmer do instead — and how could you compute the cost in whole
> **cents** (an `int`) so the imprecision never appears?

---

---

## 5. The Comprehensive Solution Manual (Teacher's Desk)

> Check your work against these. If you got something wrong, don't just read the fix —
> re-run *your* version, watch it fail, apply the fix, watch it pass.

### Exercise A — Answers

**A1 — Price splitter**

```python
# filename: chapter_02/a1_price_split.py
# COMP 1000 - Chapter 2 practice - Exercise A1
total_cents_text = input("Total price in cents: ")
total_cents = int(total_cents_text)

dollars = total_cents // 100     # [1] //  -> 1234 // 100 = 12   (whole dollars)
cents   = total_cents % 100      # [2] %   -> 1234 % 100  = 34   (leftover cents)

print("That's", dollars, "dollars and", cents, "cents")
```

- `[1] //`
- `[2] %`

`//` and `%` are a pair: `total_cents // 100` is "how many whole hundreds", and
`total_cents % 100` is "what's left after taking those hundreds out". Together they
always satisfy `1234 == (1234 // 100) * 100 + (1234 % 100)` → `1200 + 34`.

> **QUIZ TRAP — `/` vs `//`.** With `/`, `dollars` would be `12.34` (a single `float`),
> so the sentence would read `That's 12.34 dollars and 34 cents` — nonsense. `/` never
> gives you "just the whole part"; that's what `//` is for.

---

**A2 — Cart running total**

```python
# filename: chapter_02/a2_cart_total.py
# COMP 1000 - Chapter 2 practice - Exercise A2
cart_total = 0.0

price_one_text = input("Price of item 1: ")
cart_total = cart_total + float(price_one_text)     # [1] +      -> 0.0 + 3.5  = 3.5

price_two_text = input("Price of item 2: ")
cart_total = cart_total + float(price_two_text)     # [2] float  -> "1.25" -> 1.25 ; 3.5 + 1.25 = 4.75

price_three_text = input("Price of item 3: ")
cart_total = cart_total + float(price_three_text)   # [3] cart_total -> 4.75 + 10.0 = 14.75

print("Cart total: $", cart_total)
```

- `[1] +`
- `[2] float`
- `[3] cart_total`

Each line is the **accumulator pattern**: read `cart_total`'s current value, add the new
price, store the result back in `cart_total`. It isn't circular because `=` means
"gets" — the right side is fully worked out (using the *old* `cart_total`) before the box
is overwritten.

> **QUIZ TRAP — the box must already exist.** `cart_total = 0.0` on the first line is not
> decoration. Delete it and the very next line throws
> `NameError: name 'cart_total' is not defined`, because you can't read a box that was
> never filled.

> **QUIZ TRAP — convert before you add.** Without `float(...)`, `cart_total + price_one_text`
> is `float + str`, which raises `TypeError`. (Unlike `int + str`, there's no "accidental
> success" here — it just stops.)

---

**A3 — Two-year growth**

```python
# filename: chapter_02/a3_growth.py
# COMP 1000 - Chapter 2 practice - Exercise A3
starting_amount_text = input("Starting amount in dollars: ")
starting_amount = float(starting_amount_text)

growth_rate = 1.1

final_amount = starting_amount * growth_rate ** 2   # [1] *   [2] **

print("After 2 years: $", final_amount)
```

- `[1] *`
- `[2] **`

**Precedence does the `** 2` first.** So `100.0 * 1.1 ** 2` is `100.0 * (1.1 ** 2)` =
`100.0 * 1.21` = `121.00000000000001`.

> **QUIZ TRAP — `**` binds tighter than `*`.**
> `starting_amount * growth_rate ** 2`  → `100.0 * 1.21`  → `121.0…`
> `(starting_amount * growth_rate) ** 2` → `110.0 ** 2`    → `12100.0`
> Same symbols, wildly different answers. On a test, resolve `**` before `*` and `/`.

> **QUIZ TRAP — float display.** The printout is `121.00000000000001`, not `121.0`.
> `1.1` can't be stored exactly in binary, so a tiny error surfaces after the arithmetic.
> The *value* is essentially right; the *presentation* isn't receipt-ready. Fixing how a
> number is shown is the programmer's responsibility — see the ethics note in Section 2.
> (You'll meet `round(value, 2)` and cleaner formatting soon.)

---

### Exercise B — Model Answer

**A correct explanatory paragraph looks like this:**

> The program first runs `total_seconds_text = input("Enter a number of seconds: ")`,
> which shows the prompt, waits, and stores what the user types as a **string** — for the
> sample that box holds `"7384"`, type `str`. The next line
> `total_seconds = int(total_seconds_text)` converts that text into the whole number
> `7384` and stores it in a new box `total_seconds` of type `int`; the two boxes differ
> because `input()` always yields text and arithmetic needs a number. Then
> `hours = total_seconds // 3600` uses floor division to ask "how many whole hours fit in
> 7384 seconds": `7384 // 3600` is `2`, stored in `hours`. `remaining_seconds =
> total_seconds % 3600` takes the remainder after removing those two whole hours:
> `7384 % 3600` is `184`, stored in `remaining_seconds`. Now the same two-operator move is
> repeated on what's left: `minutes = remaining_seconds // 60` is `184 // 60` → `3`, and
> `seconds = remaining_seconds % 60` is `184 % 60` → `4`. The `3600` is the number of
> seconds in an hour (60 × 60) and `60` is the number of seconds in a minute. Finally six
> `print` calls run in order: a divider line, then `Total seconds: 7384`, `Hours: 2`,
> `Minutes: 3`, `Seconds: 4` (each comma inserting one space), and a summary line
> `2 h 3 m 4 s` built from the four values with literal strings between them. The program
> then ends. `remaining_seconds` exists so the minutes step works on *only the leftover
> part of the hour*; without it you'd first need `total_seconds // 60` (which is `123`,
> total minutes) and then a second `% 60` to trim it back — the intermediate box just
> makes that two-step obvious.

**Trace table for input `7384`:**

| Step | Box | Computed as | Value | Type |
|---|---|---|---|---|
| 1 | `total_seconds_text` | `input(...)` | `"7384"` | `str` |
| 2 | `total_seconds` | `int("7384")` | `7384` | `int` |
| 3 | `hours` | `7384 // 3600` | `2` | `int` |
| 4 | `remaining_seconds` | `7384 % 3600` | `184` | `int` |
| 5 | `minutes` | `184 // 60` | `3` | `int` |
| 6 | `seconds` | `184 % 60` | `4` | `int` |

**Exact screen output** (input `7384`):

```
Enter a number of seconds: 7384
----------------------
Total seconds: 7384
Hours: 2
Minutes: 3
Seconds: 4
2 h 3 m 4 s
```

> **QUIZ TRAP — check your `//` and `%` agree.** A quick sanity check:
> `2 * 3600 + 3 * 60 + 4` = `7200 + 180 + 4` = `7384`. If rebuilding the original number
> from your pieces doesn't match, one of your `//` / `%` steps is wrong.

---

### Exercise C — Model Solution

**Hand trace (written before the code), for `page_count = 1010`:**

| Order | Box | Value | Type |
|---|---|---|---|
| 1 | `page_count_text` | `"1010"` | `str` |
| 2 | `page_count` | `1010` | `int` |
| 3 | `sheets_needed` | `(1010 + 1) // 2` → `1011 // 2` → `505` | `int` |
| 4 | `whole_packs` | `505 // 500` → `1` | `int` |
| 5 | `loose_sheets` | `505 % 500` → `5` | `int` |
| 6 | `cost_dollars` | `505 * 0.09` → `45.449999999999996` | `float` |

**Predicted screen output:**

```
=== Print Shop Estimate ===
Page count: 1010
Sheets needed: 505
Whole packs (500): 1
Loose sheets: 5
Cost at $0.09/sheet: $ 45.449999999999996
```

**Program:**

```python
# filename: chapter_02/c_print_shop.py
# COMP 1000 - Chapter 2 practice - Exercise C
# Print-shop estimator: sheets, packs, loose sheets, and cost.
# Chapter 1-2 only: input(), int()/float(), print(), + - * / // % ** , comments.

# --- Title ----------------------------------------------------------
print("=== Print Shop Estimate ===")

# --- Get the job size ---------------------------------------------------
page_count_text = input("How many pages? ")
page_count = int(page_count_text)

# --- Do the paper math ------------------------------------------------
# 2 pages per sheet, rounded UP: adding 1 before // 2 bumps an odd
# page count up to the next whole sheet.
sheets_needed = (page_count + 1) // 2
whole_packs   = sheets_needed // 500      # full 500-sheet packs used
loose_sheets  = sheets_needed % 500       # sheets beyond the whole packs
cost_dollars  = sheets_needed * 0.09      # $0.09 per sheet

# --- Print the estimate ---------------------------------------------
print("Page count:", page_count)
print("Sheets needed:", sheets_needed)
print("Whole packs (500):", whole_packs)
print("Loose sheets:", loose_sheets)
print("Cost at $0.09/sheet: $", cost_dollars)
```

Notes on the design:

- **`(page_count + 1) // 2` is the round-up trick.** Plain `page_count // 2` rounds
  *down*, so 1011 pages would report 505 sheets when it really needs 506. Adding 1 before
  the `// 2` pushes any odd count up to the next whole sheet, and leaves even counts
  unchanged (`1010 + 1` → `1011 // 2` → `505`, same as `1010 // 2`).
- **`//` and `%` as a pair again:** `sheets_needed // 500` is whole packs,
  `sheets_needed % 500` is the remainder.
- **Comma, not `+`, in every `print`** — the values are numbers, and the comma form
  doesn't require strings on both sides.

> **QUIZ TRAP — rounding direction.** "Round up" is not `//`. `//` always rounds *down*
> (toward negative infinity). The `(n + 1) // 2` pattern is how you round *up* for a
> divide-by-2 with only Chapter 2 tools.

**Ethics reflection (model answer):**

> Showing `45.449999999999996` on a customer-facing estimate is technically the
> computer's exact answer, but it's not an honest *presentation* — no price is quoted to
> fifteen decimal places, and it makes the shop look careless or the total look untrustworthy.
> The responsible move is to decide, deliberately, how money is displayed: round to two
> decimals for the printout, or better, do the whole calculation in **whole cents** as an
> `int` and never touch a float. Since each sheet costs 9 cents, `cost_cents =
> sheets_needed * 9` gives `4545` exactly; you can then show dollars with
> `cost_cents // 100` and cents with `cost_cents % 100` (the A1 pattern), so the receipt
> reads `$45.45` with no imprecision possible.

---

## Quiz-Day Checklist (the 60-second review)

- [ ] `/` **always** gives a `float` (`4 / 2` → `2.0`). `//` rounds **down**. `%` is the remainder.
- [ ] Sanity check: `a == (a // b) * b + (a % b)`.
- [ ] Precedence: `( )` → `**` → `* / // %` → `+ -`. Same tier ⇒ **left to right**.
- [ ] `**` is the exception — it groups **right to left**: `2 ** 3 ** 2` = `2 ** 9` = `512`.
- [ ] `=` means **gets**: right side computed with current values, *then* stored. `x = x + 1` needs `x` to already exist.
- [ ] `type(v)` names the kind. `int + float` → `float`. `"ab" + "ab"` → `"abab"`; `"ab" * 3` → `"ababab"`.
- [ ] `len("hello")` → `5`.
- [ ] `input()` still returns a `str` — convert before arithmetic.
- [ ] Ethics: choosing a type or a rounding rule is an ethical choice when the number is money, a grade, or a dose — get the value right **and** show it fairly.
