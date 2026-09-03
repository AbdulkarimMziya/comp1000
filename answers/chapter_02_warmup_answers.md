# Chapter 2 — Warm-Up Drills: Answer Key

> Companion to **Section 3** of `../chapter_02_data_and_instructions.md`.
> Try all nine drills first. For anything you missed, retype the snippet, run it, and
> watch it behave.

---

## Predict the output

### W1

```python
print(7 / 2, 7 // 2, 7 % 2)
```

**Output:** `3.5 3 1`

Three different division operators on the same pair of numbers:

- `7 / 2` → `3.5` — **true divide**, always a `float` (note the `.5`, and it would still
  be `2.0` for `4 / 2`).
- `7 // 2` → `3` — **floor divide**, the whole-number part only (rounds down).
- `7 % 2` → `1` — **modulo**, the remainder after taking out those 3 whole twos.

The commas in `print(...)` put one space between the three results.

### W2

```python
print(2 ** 3 + 1)
```

**Output:** `9`

Precedence: `**` (power) runs before `+`. So `2 ** 3` → `8` first, then `8 + 1` → `9`.
It is **not** `2 ** 4` → `16`.

### W3

```python
score = 10
score = score + 5
score = score * 2
print(score)
```

**Output:** `30`

The accumulator pattern, three frames:

1. `score` gets `10`.
2. `score` gets `10 + 5` → `15` (right side uses the *old* value, then overwrites).
3. `score` gets `15 * 2` → `30`.

---

## Fill in the blank

### W4

```python
number = 18
print("Remainder when divided by 2:", number % 2)
```

- `_____[1]_____` → `%`

**Output:** `Remainder when divided by 2: 0`

`18 % 2` is `0` because 18 divides evenly by 2 (18 is even). For an odd number like `19`,
`19 % 2` would be `1`. That `% 2` test — `0` means even, `1` means odd — is one of the
most common uses of modulo.

### W5

```python
divider = "-" * 20
print(divider)
```

- `_____[1]_____` → `"-" * 20`

**Output:** `--------------------` (exactly 20 dashes)

`*` between a **string** and an **int** *repeats* the string that many times. Handy for
drawing separator lines without typing 20 dashes by hand. `"-" * 20` builds the string
first; `print` then shows it.

### W6

```python
cart_total = 0.0
cart_total = cart_total + 4.50
cart_total = cart_total + 2.25
print(cart_total)
```

- `_____[1]_____` → `cart_total`
- `_____[2]_____` → `cart_total`

**Output:** `6.75`

Each line reads the current `cart_total`, adds the new amount, and stores the result
back. `0.0` → `4.5` → `6.75`. The blank has to be `cart_total` itself — that's what makes
it a *running* total rather than three unrelated assignments.

---

## Write one line

### W7

```python
print(total_seconds // 60)
```

(`print(200 // 60)` also works.)

**Output:** `3`

`200 // 60` is `3` — three whole minutes fit in 200 seconds (with 20 seconds left over,
which `// ` throws away). Using `/` here would print `3.3333333333333335`, which isn't
"whole minutes".

### W8

```python
print(len(password))
```

**Output:** `8`

`len(...)` counts the characters in a string. `"sunshine"` has 8 letters. `len` works on
the value *in* the box, so you write `len(password)`, not `len("password")` (that would
count the word "password", which is also 8 — coincidence; try it with a different
variable name to see the difference).

---

## Spot the bug

### W9

```python
total = total + 10
print(total)
```

**What actually happens:** it crashes on the first line with

```
NameError: name 'total' is not defined
```

The right-hand side `total + 10` tries to **read** `total` before it has ever been given
a value. You can't read an empty shelf.

**The one line that fixes it** — give `total` a starting value first:

```python
total = 0
total = total + 10
print(total)        # -> 10
```

---

## The one lesson under all nine

Three division operators, three answers: `/` → float, `//` → whole part (down), `%` →
remainder. Precedence orders everything: `**` before `* / // %` before `+ -`. And `=`
means **gets** — the right side is worked out with the current values, *then* stored, so
`x = x + n` needs `x` to already exist.
