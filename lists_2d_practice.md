# Strings, Lists & 2D Lists: Practice

> **Rules of the gym**
> 1. **Start at Level 0** (on paper). Then do the levels **in order**.
> 2. **Try first, look second.** Only open [`lists_2d_notes.md`](lists_2d_notes.md) after an
>    honest attempt. For any 2D question, **draw the table first**.
> 3. There's **no answer key**. Run your code and compare it with the sample run.
> 4. **Retention rep:** 3–4 days later, delete your Level 3 files and write them again.
>
> Only use course tools: indexing, slicing, `len`, `in`, `for` + `range`, `if`, `def`,
> `return`, `.append()`. **No `break`, no `while`** (Ch11), and no `max()` / `sum()`.
>
> *Practice material only. Not for labs, assignments or tests.*

**Setup:** make a folder called `lists_2d/`. Every code block starts with a
`# filename:` line. Make a new file with that name, paste the whole block in, and run it.

Grids used below. You don't need to type them: they're already inside each code block.
```
seats                               marks
         col0   col1   col2                  col0  col1  col2
 row 0   Ana    Ben    Chloe         row 0    72    85    90
 row 1   Dev    Eli    Fay           row 1    64    70    88
 row 2   Gus    Hana   Ivan          row 2    95    80    77
```

---

## Level 0: Words & Steps ✍️ (paper only)

**0.1 Match each word to its meaning.**

| Word | | Meaning |
|---|---|---|
| 1. index | | A. A list of lists, like a table |
| 2. `len()` | | B. Can't be changed in place |
| 3. immutable | | C. The position number, starting at 0 |
| 4. 2D list | | D. A `True`/`False` variable that remembers if something happened |
| 5. row | | E. How many items there are |
| 6. flag | | F. One inner list of a 2D list |
| 7. `IndexError` | | G. Asking for a position that doesn't exist |

**0.2 Draw it.** For `word = "planet"`, write each letter with its index underneath (0–5)
and its negative index too (-6 to -1). Then write the index for: the `p`, the `t`, and the `n`.

**0.3 Point to it.** Using the `seats` table above, write the name for each:
`seats[0][2]` · `seats[2][0]` · `seats[1][1]` · `seats[2][2]`.
Then write the `seats[?][?]` for: Ben · Gus · Fay.

**0.4 Put the 5 search steps in order:** Check `found` after the loop · Set up `found = False`
before the loop · Decide on the target · If it matches, record it · Loop over every index

**0.5 True or false?** If it's false, write the true version.
1. The first item in a list is at index 1.
2. `len("cat")` is 3, so the last index is 3.
3. You can change one letter of a string with `word[0] = "X"`.
4. In `grid[r][c]`, `r` is the row.
5. `len(grid)` gives the number of columns.
6. `"Eli" in seats` is `True`.

---

## Level 1: Predict the Output ✍️

Write your prediction on paper (draw the table for 2D ones), **then** run it.

**1.1**
```python
# filename: lists_2d/p1.py
word = "planet"
print(word[0], word[3], word[-1], len(word))
```

**1.2**
```python
# filename: lists_2d/p2.py
word = "planet"
print(word[1:4])
print(word[:3] + word[3:])
```

**1.3**
```python
# filename: lists_2d/p3.py
colours = ["red", "green", "blue"]
colours[0] = "pink"
colours.append("gold")
print(colours)
print(len(colours), colours[-1])
```

**1.4**
```python
# filename: lists_2d/p4.py
colours = ["red", "green", "blue"]
for index in range(len(colours)):
    print(index, colours[index], colours[index][0])
```

**1.5**
```python
# filename: lists_2d/p5.py
seats = [["Ana", "Ben", "Chloe"],
         ["Dev", "Eli", "Fay"],
         ["Gus", "Hana", "Ivan"]]
print(seats[2])
print(seats[2][1])
print(seats[0][2][0])
```

**1.6**
```python
# filename: lists_2d/p6.py
grid = [[1, 2, 3],
        [4, 5, 6]]
print(len(grid), len(grid[0]))
print(grid[1][0] + grid[0][2])
```

**1.7**
```python
# filename: lists_2d/p7.py
seats = [["Ana", "Ben", "Chloe"],
         ["Dev", "Eli", "Fay"],
         ["Gus", "Hana", "Ivan"]]
print("Eli" in seats)
print("Eli" in seats[1])
```

**1.8** Trace the nested loop on paper first.
```python
# filename: lists_2d/p8.py
grid = [[1, 2, 3],
        [4, 5, 6]]
total = 0
for row in range(len(grid)):
    for col in range(len(grid[row])):
        total = total + grid[row][col]
print(total)
```

---

## Level 2: Fix the Bug 🔧

Predict what goes wrong, run it, then fix it with the smallest change you can.

**2.1** Should print the last letter, `n`.
```python
# filename: lists_2d/bug1.py
word = "python"
print(word[len(word)])
```

**2.2** Should print `Jython`.
```python
# filename: lists_2d/bug2.py
word = "python"
word[0] = "J"
print(word)
```

**2.3** Prints all 4 marks, then crashes.
```python
# filename: lists_2d/bug3.py
marks = [72, 85, 90, 64]
for index in range(len(marks) + 1):
    print(marks[index])
```

**2.4** Should print `Fay` (row 1, seat 2), but prints `Hana`.
```python
# filename: lists_2d/bug4.py
seats = [["Ana", "Ben", "Chloe"],
         ["Dev", "Eli", "Fay"],
         ["Gus", "Hana", "Ivan"]]
print(seats[2][1])
```

**2.5** Crashes with an `IndexError`. The grid has 2 rows and 3 columns.
```python
# filename: lists_2d/bug5.py
grid = [[1, 2, 3],
        [4, 5, 6]]
for row in range(len(grid[0])):
    for col in range(len(grid[row])):
        print(grid[row][col])
```

**2.6** Should print `True` because Ana **is** in the list. It prints `False`. Why? (Trace it.)
```python
# filename: lists_2d/bug6.py
names = ["Ana", "Ben", "Chloe"]
found = False
for name in names:
    if name == "Ana":
        found = True
    else:
        found = False
print(found)
```

**2.7** Should print each row's total (`247`, `222`, `252`), but the numbers keep growing.
```python
# filename: lists_2d/bug7.py
marks = [[72, 85, 90],
         [64, 70, 88],
         [95, 80, 77]]
row_total = 0
for row in range(len(marks)):
    for col in range(len(marks[row])):
        row_total = row_total + marks[row][col]
    print(row_total)
```

---

## Level 3: Write It ✏️

Paste each stub into its own file, fill in the `# TODO`s, then run it. Match the sample run
**exactly**. Functions **return** their answer unless the stub says to print.

**3.1** First and last letter.
```python
# filename: lists_2d/w1_first_last.py
def first_and_last(word):
    # TODO: return the first letter joined to the last letter (use len, not -1, for practice)
    pass


print(first_and_last("python"))
print(first_and_last("a"))
```
```
# sample run
pn
aa
```

**3.2** Count a letter (a search that counts).
```python
# filename: lists_2d/w2_count_letter.py
def count_letter(word, letter):
    # TODO 1: count = 0
    # TODO 2: loop over each character; if it equals letter, add 1
    # TODO 3: return count
    pass


print(count_letter("banana", "a"))
print(count_letter("banana", "z"))
```
```
# sample run
3
0
```

**3.3** Find the index (the 5 search steps).
```python
# filename: lists_2d/w3_find_index.py
def find_index(items, target):
    # TODO 1: position = -1 (this means "not found yet")
    # TODO 2: loop over every index with range(len(items))
    # TODO 3: if items[index] == target AND position is still -1, save the index
    # TODO 4: return position
    pass


names = ["Ana", "Ben", "Chloe"]
print(find_index(names, "Chloe"))
print(find_index(names, "Zed"))
```
```
# sample run
2
-1
```

**3.4** Print a grid as a table.
```python
# filename: lists_2d/w4_print_grid.py
marks = [[72, 85, 90],
         [64, 70, 88],
         [95, 80, 77]]

# TODO 1: outer loop over each row index
# TODO 2:     line = ""
# TODO 3:     inner loop over each column index: add str(marks[row][col]) + " " to line
# TODO 4:     print(line)   (inside the outer loop, after the inner loop)
```
```
# sample run
72 85 90 
64 70 88 
95 80 77 
```

**3.5** Row total and column total.
```python
# filename: lists_2d/w5_totals.py
def row_total(grid, row):
    # TODO: keep row fixed, loop over the columns, add them up, return the total
    pass


def column_total(grid, col):
    # TODO: keep col fixed, loop over the rows, add them up, return the total
    pass


marks = [[72, 85, 90],
         [64, 70, 88],
         [95, 80, 77]]
print("Row 0 total:", row_total(marks, 0))
print("Column 2 total:", column_total(marks, 2))
```
```
# sample run
Row 0 total: 247
Column 2 total: 255
```

**3.6** Find a seat (2D search). This one **prints**.
```python
# filename: lists_2d/w6_find_seat.py
def find_seat(seats, name):
    # TODO 1: found = False, found_row = -1, found_col = -1
    # TODO 2: nested loop over every row and column
    # TODO 3: if it matches, set found = True and save row and col
    # TODO 4: after the loops, print "<name> is in row R seat C" or "<name> is not here"
    pass


seats = [["Ana", "Ben", "Chloe"],
         ["Dev", "Eli", "Fay"],
         ["Gus", "Hana", "Ivan"]]
find_seat(seats, "Fay")
find_seat(seats, "Zed")
```
```
# sample run
Fay is in row 1 seat 2
Zed is not here
```

**3.7** Highest mark and where it is. No `max()`.
```python
# filename: lists_2d/w7_highest.py
marks = [[72, 85, 90],
         [64, 70, 88],
         [95, 80, 77]]

# TODO 1: highest = marks[0][0], high_row = 0, high_col = 0
# TODO 2: nested loop; if a mark is bigger than highest, update all three
# TODO 3: print the result
```
```
# sample run
Highest: 95 at row 2 column 0
```

---

## Level 4: Boss Round 🧠 (no stub)

Use the same `marks` grid. Each row is one student and each column is one test.

**4.1** Count how many marks are 80 or more.
```
# sample run
Marks of 80 or more: 5
```

**4.2** Which student (row) has the highest total? Reuse `row_total` from 3.5.
```
# sample run
Best student: row 2 with 252
```

**4.3 ✍️ On paper:** if the grid had 4 rows and 2 columns instead, which lines of your code
would you need to change? (If the answer is "none", you used `len()` correctly.)
