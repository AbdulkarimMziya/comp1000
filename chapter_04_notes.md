# Chapter 4 Notes: Iteration & Strings

> **How to use these notes:** read one lesson, then go do the matching tasks in
> [`chapter_04_practice.md`](chapter_04_practice.md). Come back here when you get stuck. The
> notes are short on purpose. You learn this by writing loops, not by reading about them.
>
> *Practice material only. Don't use AI tools or these notes on labs, assignments, or
> tests (course rules).*

---

## Recap Card: Ch 1–3 in one screen

| Idea | Remember |
|---|---|
| `input("prompt")` | Always returns a **`str`**. Convert it: `int(...)` or `float(...)`. |
| Types | `int` `7`, `float` `7.0`, `str` `"7"`, `bool` `True`. Check with `type()`. |
| Maths | `/` always gives a float. `//` = whole part. `%` = remainder. `**` = power. |
| Order | `( )` → `**` → `* / // %` → `+ -`. Ties go left to right. |
| `=` | Right side runs **first**, then the result is stored on the left. |
| Accumulator | `total = total + price`: the new value is built from the old one. |
| Syntax error | Python can't read the code (missing `:`, `)` or quote). Nothing runs. |
| Runtime error | Crashes partway through: `NameError`, `TypeError`, `ValueError`, `ZeroDivisionError`. |
| Logic error | No crash, but the answer is **wrong**. These are the hardest to find. |
| Tracebacks | Read the **last line** first (the error type), then the line number above it. |
| Modules | `import math` → `math.sqrt(16)` is `4.0`. `import random` → `random.randint(1, 6)` includes **both** ends. |

---

## 4.1 What a loop is

A loop **repeats a block of code**. Instead of writing `print` 100 times, you write it once
and tell Python how many times to run it.

```python
for count in range(3):
    print("Hello")
print("Done")
```
```
Hello
Hello
Hello
Done
```

Anatomy: `for` + **loop variable** + `in` + **what to loop over** + `:`. The **indented**
lines are the *body*, and they repeat. The first line that isn't indented runs once, after
the loop finishes.

> ⚠ **Trap:** forget the `:` and you get a SyntaxError. Forget to indent and you get an IndentationError.
> Indent a line by mistake and it repeats when it should only run once.

---

## 4.2 `range()`: the number generator

| Call | Produces | Rule |
|---|---|---|
| `range(5)` | `0 1 2 3 4` | starts at 0, **stops before** 5 |
| `range(2, 6)` | `2 3 4 5` | start, stop |
| `range(0, 10, 2)` | `0 2 4 6 8` | start, stop, step |
| `range(10, 0, -3)` | `10 7 4 1` | a negative step counts down |
| `range(5, 1)` | *(nothing)* | you can't count up from 5 to 1, so the body never runs |

`range(n)` runs the body **exactly n times**. To include the last number, use `stop + 1`:
`range(1, 11)` gives 1 to 10.

> ⚠ **Trap:** the stop number is **never** included. This off-by-one mistake is the most
> common loop bug.

---

## 4.3 Trace it like the computer

The course is about *simulating* the computer, so trace loops with a table. Add **one row
per time through the loop**.

```python
total = 0
for number in range(1, 4):
    total = total + number
print(total)
```

| Pass | `number` | `total` after the line runs |
|---|---|---|
| start | – | 0 |
| 1 | 1 | 1 |
| 2 | 2 | 3 |
| 3 | 3 | 6 |

Output: `6`. The `print` isn't indented, so it runs **once**, after the loop.

> ⚠ **Trap:** move `print(total)` inside the loop and the output becomes `1`, `3`, `6` on
> three lines. On a quiz, always check the indentation of the `print`.

---

## 4.4 Loop patterns you'll use forever

**Sum.** Start at `0` and add each time:
```python
total = 0
for number in range(1, 101):
    total = total + number
```

**Product.** Start at `1`, because starting at 0 makes everything 0:
```python
product = 1
for number in range(1, 6):
    product = product * number     # ends as 120
```

**Build a string.** Start at `""` (empty) and join onto it each time:
```python
stars = ""
for step in range(4):
    stars = stars + "*"
    print(stars)
```
```
*
**
***
****
```

> ⚠ **Trap:** create the accumulator **before** the loop. If you put `total = 0` inside
> the loop, it resets to 0 on every pass.

---

## 4.5 Looping over a string

A string is a sequence of characters, and `for` can walk through it one character at a
time.

```python
for letter in "cat":
    print(letter)
```
```
c
a
t
```

The loop variable (`letter`) holds a **different character** on each pass. You pick its
name, so choose a clear one.

---

## 4.6 Indexing: grab one character

```
 word  =   p   y   t   h   o   n
 index     0   1   2   3   4   5
 negative -6  -5  -4  -3  -2  -1
```

| Code | Result |
|---|---|
| `word[0]` | `'p'`: the first character is index **0** |
| `word[-1]` | `'n'`: `-1` always means the last character |
| `len(word)` | `6` |
| `word[6]` | **IndexError**, because the last index is `len(word) - 1` |

Looping **by index** gives you the position *and* the character:
```python
for index in range(len(word)):
    print(index, word[index])
```

> ⚠ **Trap:** `len(word)` is the count, **not** the last index. The last index is one less.

---

## 4.7 Slicing: grab a piece

`word[start:stop]` works like `range`: start is included and **stop is not**.

| Code | Result | Why |
|---|---|---|
| `word[0:3]` | `'pyt'` | indexes 0, 1, 2 |
| `word[2:]` | `'thon'` | leaving out stop means "to the end" |
| `word[:2]` | `'py'` | leaving out start means "from the beginning" |
| `word[::-1]` | `'nohtyp'` | a step of −1 reverses the string |

Strings are **immutable**, which means you can't change them in place.
`word[0] = "P"` → `TypeError: 'str' object does not support item assignment`.
To "change" a string, **build a new one**: `new_word = "P" + word[1:]`.

---

## 4.8 String methods

> Only use the methods your Runestone chapter has shown you.

| Method | Example | Result |
|---|---|---|
| `.upper()` / `.lower()` | `"Hello".upper()` | `'HELLO'` |
| `.count(x)` | `"banana".count("a")` | `3` |
| `.find(x)` | `"banana".find("n")` | `2`, the **first** index where it appears (`-1` if it isn't there) |
| `.replace(old, new)` | `"banana".replace("a", "o")` | `'bonono'` |

Methods **return a new string**. The original doesn't change, so store the result:
`shout = name.upper()`.

---

## 60-Second Self-Check

Before Quiz 3, can you do all of these without looking?

- [ ] Say what `range(3, 12, 3)` produces, and how many times the body runs.
- [ ] Trace a sum loop in a table, pass by pass.
- [ ] Explain why a product starts at `1` and a string starts at `""`.
- [ ] Say what `word[-1]`, `word[1:4]` and `word[::-1]` give for `word = "loops"`.
- [ ] Explain why `word[len(word)]` crashes.
- [ ] Tell whether a `print` runs once or every pass, just by its indentation.

If you can't do one of these, reread that lesson and redo two tasks from the practice file.
