# Chapter 1 — Warm-Up Drills: Answer Key

> Companion to **Section 3** of `chapter_01_python_ethics_interactivity.md`.
> Try all nine drills first. For anything you missed, don't just read the answer — retype
> the snippet, run it, and watch it behave.

---

## Predict the output

### W1

```python
print("2" + "3")
```

**Output:** `23`

Both `"2"` and `"3"` are **strings** (they're in quotes). For strings, `+` means
*concatenate* — stick them end to end. It is **not** `5`. If you wanted `5` you'd need
numbers with no quotes: `print(2 + 3)`.

### W2

```python
age = "17"
print("You are", age, "years old")
```

**Output:** `You are 17 years old`

`print(...)` with items separated by **commas** prints each item with a single space
between them. It doesn't matter that `age` holds a string — the comma form accepts any
mix of strings and numbers. (Notice you get `You are 17 years old`, not
`You are17years old` — the spaces come from the commas, not from the text.)

### W3

```python
apples = 4
baskets = 2
print(apples / baskets)
```

**Output:** `2.0`

The `/` (divide) operator in Python **always produces a `float`** — a number with a
decimal part — even when the division comes out even. So `4 / 2` is `2.0`, not `2`.
(If you ever need the whole-number result, that's a different operator you'll meet
later. For now, just remember: `/` gives you a `.0` on the end.)

---

## Fill in the blank

### W4

```python
first_name = "Sam"
print("Hello, " + first_name + "!")
```

- `_____[1]_____` → `+`
- `_____[2]_____` → `+`

**Output:** `Hello, Sam!`

All three pieces — `"Hello, "`, `first_name` (which holds `"Sam"`), and `"!"` — are
strings, so `+` glues them into one string. Note the space inside `"Hello, "` is
deliberate; that's what separates the words.

### W5

```python
first_value  = input("First number: ")
second_value = input("Second number: ")
print(int(first_value) + int(second_value))
```

- `_____[1]_____` → `int`
- `_____[2]_____` → `int`

**Output for inputs `8` and `9`:** `17`

`input()` hands back a **string**. Without the `int(...)` conversions you'd be computing
`"8" + "9"`, which concatenates to `"89"`. Wrapping each one in `int(...)` turns the text
into a real number first, so `+` does arithmetic: `8 + 9` → `17`.

*(`float` would also run, but give `17.0`. The question says "numbers the user types" as
whole numbers, so `int` is the right pick.)*

### W6

```python
print("keep this")
# print("hide this line from Python")
```

- `_____[1]_____` → `#`

**Output:** `keep this`

A `#` turns the rest of that line into a **comment** — Python skips it entirely. The line
is still there for a human to read, but it no longer runs. This is how you "switch off" a
line without deleting it.

---

## Write one line

### W7

```python
user_name = input("What's your name? ")
```

`input("What's your name? ")` shows the prompt, waits for the user to type and press
Enter, and *becomes* whatever they typed. The `=` stores that text in `user_name`.
Keep the space after the `?` inside the quotes so the cursor isn't jammed against the
question mark.

### W8

```python
print("$" + str(total_price))
```

**Output:** `$19.99`

You need `$` with **no space** before the number, so the comma form
(`print("$", total_price)` → `$ 19.99`) won't do. `+` joins strings, but `total_price` is
a number — so convert it with `str(...)` first. `"$" + "19.99"` → `"$19.99"`.

---

## Spot the bug

### W9

```python
quantity = input("How many? ")
print("Double that is", quantity * 2)
```

**What actually happens:** for input `5`, it prints `Double that is 55`.

`input()` returns the **string** `"5"`. Multiplying a string by an integer *repeats the
string*, so `"5" * 2` is `"55"` — not `10`.

**One-word fix:** `int`

```python
quantity = input("How many? ")
print("Double that is", int(quantity) * 2)   # -> Double that is 10
```

Converting `quantity` to an `int` before the `* 2` makes it real multiplication.

---

## The one lesson under all nine

`input()` always gives you a **string**. Quoted things are strings. `+` on strings
*joins*; `+` on numbers *adds*; `*` on a string *repeats* it. Before you do arithmetic on
anything that came from `input()` — or anything in quotes — convert it with `int(...)` or
`float(...)` first.
