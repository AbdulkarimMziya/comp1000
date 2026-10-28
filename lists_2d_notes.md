# Strings, Lists & 2D Lists: Notes (Ch9 Sequences, ahead of Test 3)

> **How to use these notes:** learn the **Key Words** and the **Big Picture** steps first.
> Then read one lesson and do the matching tasks in [`lists_2d_practice.md`](lists_2d_practice.md).
> Every output shown here is real: the code was run.
>
> Ch9 is taught the week of Nov 2, and **Test 3 is Nov 4**. This gets you ahead.
>
> *Practice material only. Don't use AI tools or these notes on labs, assignments, or
> tests (course rules). The examples are deliberately different from A2.*

---

## Key Words (learn these first)

| Word | What it means | Tiny example |
|---|---|---|
| **sequence** | Anything with items in order that you can number. Strings and lists are both sequences. | `"cat"`, `[1, 2, 3]` |
| **string** | A sequence of **characters**. | `"python"` |
| **list** | A sequence of **values** in square brackets, separated by commas. | `["Ana", "Ben"]` |
| **item / element** | One thing inside a list (or one character inside a string). | `"Ben"` |
| **index** | The **position number** of an item. Counting **starts at 0**. | `fruits[0]` is the 1st item |
| **negative index** | Counts from the end. `-1` is the last item. | `fruits[-1]` |
| **`len()`** | How many items. The last index is always `len(...) - 1`. | `len("cat")` → `3` |
| **slice** | A piece of a sequence: `[start:stop]`. It stops **before** `stop`. | `"python"[0:3]` → `'pyt'` |
| **`IndexError`** | You asked for a position that doesn't exist. | `"cat"[3]` |
| **mutable** | Can be changed in place. **Lists** are mutable. | `fruits[0] = "kiwi"` ✅ |
| **immutable** | Can't be changed in place. **Strings** are immutable. | `word[0] = "P"` ❌ `TypeError` |
| **`.append()`** | Adds one item to the end of a list. | `fruits.append("date")` |
| **`in`** | Checks whether something is inside. Gives `True` or `False`. | `"Ben" in names` |
| **traverse** | Visit every item with a loop. | `for name in names:` |
| **search** | Traverse while looking for something, and remember what you find. | see S.7 |
| **flag** | A `True`/`False` variable that remembers whether something happened. | `found = False` |
| **2D list** | A **list of lists**. Think of a table: each inner list is a **row**. | `[[1, 2, 3], [4, 5, 6]]` |
| **row** | One inner list, going across. | `grid[0]` → `[1, 2, 3]` |
| **column** | The same position in every row, going down. | `grid[0][1]`, `grid[1][1]` |
| **`grid[row][col]`** | Get one item: **row first, then column**. | `grid[1][2]` → `6` |
| **nested loop** | A loop inside a loop. The outer loop picks a row, the inner loop goes along it. | see S.10 |

---

## The Big Picture: 3 sets of steps

### A. To get ONE item from a string or list
1. **Draw it.** Write the items in a row with their index under each one, starting at **0**.
2. **Find the position.** Which index do you want? (The last one is `len - 1`, or just `-1`.)
3. **Write `name[index]`.**

### B. To get ONE item from a 2D list
1. **Draw it as a table.** Rows go down the side (0, 1, 2…) and columns go across the top (0, 1, 2…).
2. **Find the ROW** first. That's which inner list it's in.
3. **Find the COLUMN.** That's its position inside that row.
4. **Write `grid[row][col]`.** Row first, every time. Say "row, then column".

### C. To SEARCH for something (1D or 2D)
1. **Decide** what you're looking for (the **target**).
2. **Set up** your "remember" variables **before** the loop: `found = False`, `position = -1`.
3. **Loop over every index** (a nested loop for 2D).
4. **If it matches**, set `found = True` and record where it is.
5. **After the loop**, check `found` and print or return the result.

> ⚠ **Trap:** never put `found = False` inside the loop's `else`. You'd forget what you
> found earlier (see Practice bug 2.6). And don't use `break`. The course doesn't allow it
> on assignments, and you don't need it.

---

## S.1 Strings: indexing *(Steps A)*

```
 index:   0   1   2   3   4   5
 word:   "p" "y" "t" "h" "o" "n"
 negative:-6  -5  -4  -3  -2  -1
```
```python
word = "python"
print(word[0], word[2], word[-1], word[len(word) - 1], len(word))
```
```
p t n n 6
```
> ⚠ **Trap:** `word[6]` → `IndexError: string index out of range`. 6 letters means the
> indexes are 0–5. The last index is `len - 1`.

---

## S.2 Slices: a piece of the sequence

```python
print(word[0:3], word[2:], word[:2])
```
```
pyt thon py
```
`[start:stop]` **includes** start and **stops before** stop. Leave out start and it begins
at 0. Leave out stop and it goes to the end. Slices work on **lists** too.

---

## S.3 Strings can't be changed (immutable)

```python
word[0] = "P"
```
```
TypeError: 'str' object does not support item assignment
```
Build a **new** string instead:
```python
new_word = "P" + word[1:]
print(new_word)
```
```
Python
```

---

## S.4 Lists: make, read, change, add *(Steps A)*

```python
fruits = ["apple", "banana", "cherry"]
print(fruits[0], fruits[-1], len(fruits))

fruits[1] = "blueberry"          # lists CAN be changed
print(fruits)

fruits.append("date")            # add to the end
print(fruits)
```
```
apple cherry 3
['apple', 'blueberry', 'cherry']
['apple', 'blueberry', 'cherry', 'date']
```
> ⚠ **Trap:** `fruits[4]` on a 4-item list → `IndexError: list index out of range`.

---

## S.5 Two ways to loop over a list

```python
marks = [72, 85, 90, 64]

for mark in marks:                       # way 1: you get the ITEMS
    print(mark)

for index in range(len(marks)):          # way 2: you get the POSITIONS
    print("Position", index, "has", marks[index])
```
```
72
85
90
64
Position 0 has 72
Position 1 has 85
Position 2 has 90
Position 3 has 64
```
**Which one?** If you only need the values, use way 1. If you need **where** something is,
or two lists at the same position, use way 2.

---

## S.6 `in`: is it there?

```python
print("banana" in ["apple", "banana"], "kiwi" in ["apple", "banana"], "an" in "banana")
```
```
True False True
```
`in` tells you **whether** something is there, but not **where**. To find out where, search (S.7).

---

## S.7 Searching a list *(Steps C)*

```python
names = ["Ana", "Ben", "Chloe", "Ben"]
target = "Ben"

found = False                    # STEP 2: set up BEFORE the loop
position = -1

for index in range(len(names)):  # STEP 3: visit every index
    if names[index] == target and found == False:   # STEP 4: first match only
        found = True
        position = index

if found:                        # STEP 5: check AFTER the loop
    print(target, "found at index", position)
else:
    print(target, "not found")
```
```
Ben found at index 1
```
**Counting** is a search that adds 1 each time it finds a match:
```python
count = 0
for name in names:
    if name == "Ben":
        count = count + 1
print("Ben appears", count, "times")
```
```
Ben appears 2 times
```

---

## S.7b A list of strings has 2 levels already

```python
print(names[2][0], names[2][-1], len(names[2]))
```
```
C e 5
```
`names[2]` is `"Chloe"`, and then `[0]` takes its first letter. **Two brackets mean two
steps:** first pick the item, then pick inside it. 2D lists work exactly the same way.

---

## S.8 2D lists: a list of lists *(Steps B)*

```python
seats = [["Ana", "Ben",  "Chloe"],
         ["Dev", "Eli",  "Fay"],
         ["Gus", "Hana", "Ivan"]]
```
Draw it as a table:
```
           col 0    col 1    col 2
 row 0     Ana      Ben      Chloe
 row 1     Dev      Eli      Fay
 row 2     Gus      Hana     Ivan
```
```python
print(seats[1])         # a whole ROW (one inner list)
print(seats[1][2])      # row 1, then column 2
print(seats[0][0], seats[2][1])
row = seats[2]          # two steps, done one at a time
print(row[0])
```
```
['Dev', 'Eli', 'Fay']
Fay
Ana Hana
Gus
```
**Read `seats[1][2]` as:** "go to row 1, then go to column 2 inside that row".

---

## S.9 How big is it?

```python
grid = [[1, 2, 3],
        [4, 5, 6]]
print(len(grid), len(grid[0]))
```
```
2 3
```
- `len(grid)` = how many **rows** (inner lists)
- `len(grid[0])` = how many **columns** (items in one row)

---

## S.10 Looping over the whole grid (nested loops)

```python
for row in range(len(grid)):                 # outer: pick a row
    line = ""
    for col in range(len(grid[row])):        # inner: walk along that row
        line = line + str(grid[row][col]) + " "
    print(line)
```
```
1 2 3 
4 5 6 
```
**Row totals:** reset the total for **each** row, inside the outer loop:
```python
for row in range(len(grid)):
    row_total = 0
    for col in range(len(grid[row])):
        row_total = row_total + grid[row][col]
    print("Row", row, "total:", row_total)
```
```
Row 0 total: 6
Row 1 total: 15
```

---

## S.11 One column: keep `col` fixed, loop the rows

```python
col = 1
col_total = 0
for row in range(len(grid)):
    col_total = col_total + grid[row][col]
print("Column", col, "total:", col_total)
```
```
Column 1 total: 7
```
(2 + 5 = 7.) For a **row** you loop the columns. For a **column** you loop the rows.

---

## S.12 Searching a 2D list *(Steps C, nested)*

```python
target = "Fay"
found = False
found_row = -1
found_col = -1

for row in range(len(seats)):
    for col in range(len(seats[row])):
        if seats[row][col] == target:
            found = True
            found_row = row
            found_col = col

if found:
    print(target, "is in row", found_row, "seat", found_col)
else:
    print(target, "is not here")
```
```
Fay is in row 1 seat 2
```

---

## S.13 Changing one cell

```python
seats[0][1] = "Bea"
print(seats[0])
```
```
['Ana', 'Bea', 'Chloe']
```

---

## S.14 Traps to remember

| You wrote | What happens | Why |
|---|---|---|
| `grid[2][0]` on a 2-row grid | `IndexError: list index out of range` | rows are 0 and 1 only |
| `grid[1][0]` vs `grid[0][1]` | `4` vs `2` | **row first**, so swapping them gives a different item |
| `seats[1][0][0]` | `D` | 3 steps: row 1 → `"Dev"` → first letter |
| `"Eli" in seats` | `False` | `seats` holds **rows**, not names. Use `"Eli" in seats[1]`, or search every row |
| `for col in range(len(grid))` | wrong number of columns | `len(grid)` counts **rows**. For columns use `len(grid[row])` |

---

## 60-second self-check

1. What index is the **first** item? How do you get the **last** one, in two different ways?
2. What's the difference between `"cat"[1]` and `"cat"[1:]`?
3. Why can you change `fruits[0]` but not `word[0]`?
4. In `grid[r][c]`, which comes first, row or column?
5. What do `len(grid)` and `len(grid[0])` each tell you?
6. Name the 5 search steps in order. Why is `found = False` set **before** the loop?
7. To total one **column**, which index stays the same and which one changes?
