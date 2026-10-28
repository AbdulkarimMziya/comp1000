# Reading Files: Notes

> **How to use these notes:** read one lesson, then do the matching tasks in
> [`reading_files_practice.md`](reading_files_practice.md). Every example below was run,
> and the output shown is the real output. The practice sheet shows how to make each `.txt` file.
>
> This sheet only covers **reading** files. Writing and appending (like `scores.txt` in A2 Q5)
> get their own sheet.
>
> *Practice material only. Don't use AI tools or these notes on labs, assignments, or
> tests (course rules). A2 Q4 is graded, so these examples use different data on purpose.*

---

## Key Words (learn these first)

| Word | What it means | Tiny example |
|---|---|---|
| **file** | Information saved on the computer under a name, so it's still there after your program stops. | `fruits.txt` |
| **text file** | A file that's just lines of plain characters. You can open it in any editor. | ends in `.txt` |
| **file name** | The exact name, **including** the `.txt`. Spelling counts. | `"fruits.txt"` |
| **folder** | Where files live. Python looks for the file in the folder your `.py` runs from. | `reading_files/` |
| **`open()`** | Connects your program to a file so you can read it. | `open("fruits.txt", "r")` |
| **file object** | What `open()` gives back. You store it in a variable and read through it. | `file = open(...)` |
| **mode `"r"`** | "Read mode": you can look at the file but not change it. It's the default. | `open("x.txt", "r")` |
| **line** | One row of the file. It ends where the person pressed Enter. | `apple` |
| **newline `\n`** | The hidden character at the end of each line. It counts as 1 character. | `'apple\n'` |
| **`read()`** | Reads the **whole file** into one string. | `text = file.read()` |
| **`readline()`** | Reads the **next single line**. Gives `''` when there are no lines left. | `first = file.readline()` |
| **`readlines()`** | Reads **every line** into a list. | `lines = file.readlines()` |
| **`for line in file:`** | A loop that hands you one line at a time. | `for line in file:` |
| **`.strip()`** | Removes spaces and `\n` from both **ends** of a string. | `"apple\n".strip()` → `'apple'` |
| **`close()`** | Disconnects from the file when you're finished. **Always** do it. | `file.close()` |
| **string (`str`)** | Text. **Everything** you read from a file starts as a string, even numbers. | `"72"` |
| **converting** | Turning a string into a number so you can do maths with it. | `int("72")` → `72`, `float("6.5")` → `6.5` |
| **list** | One variable that holds many values in order. | `["Ana", "Ben"]` |
| **`.append()`** | Adds one value to the end of a list. | `names.append("Ana")` |
| **header line** | A title line at the top of a file that isn't data. | `MARKS` |
| **parallel lists** | Two lists where position 0 goes with position 0, 1 with 1, and so on. | `names[1]` and `ages[1]` are about the same person |
| **`FileNotFoundError`** | Python can't find the file. Usually a typo or the wrong folder. | `open("fruit.txt")` |
| **`ValueError`** | You tried to convert something that isn't that kind of number. | `int("12.25")`, `int("")` |
| **`TypeError`** | You mixed types, e.g. added a string to a number. | `0 + "72"` |

---

## The Big Picture: 5 Steps to Read a File

Every file-reading program follows the same 5 steps. Learn the order.

1. **Make it or put it in place.** The `.txt` file must be in the **same folder** as your `.py` file (R.0 shows how to make one).
2. **Open it.** `file = open("name.txt", "r")`
3. **Read it.** Pick one of the 4 ways (R.4). Most of the time it's `for line in file:`.
4. **Clean it up.** Use `.strip()` on words. Use `int()` or `float()` on numbers.
5. **Close it.** `file.close()`. **Then** use your data.

The same 5 steps as code:

```python
# STEP 1: names.txt is made and saved in the same folder as this .py file
file = open("names.txt", "r")      # STEP 2: open it
names = []
for line in file:                  # STEP 3: read it, one line at a time
    names.append(line.strip())     # STEP 4: clean it up, then store it
file.close()                       # STEP 5: close it

print(names)                       # now use the data
```
```
['Ana', 'Ben', 'Chloe']
```

**Say each step out loud:**
1. "Is the file next to my program?"
2. "Open it in read mode."
3. "Go through it line by line."
4. "Strip the `\n`, or turn it into a number."
5. "Close it before I do anything else."

> ⚠ **Trap:** if you can't name all 5 steps from memory, go back over them before you start
> the lessons. Every lesson below fits into one of these steps.

---

## R.0 Where does Python look for the file? *(Step 1)*

A text file is just lines of characters saved on disk. `fruits.txt` looks like this:

```
apple
banana
cherry
```

When you write `open("fruits.txt")`, Python looks in the **folder your program is running
from**. Usually that's the folder your `.py` file is in.

**Rule:** put the `.txt` file **in the same folder** as your `.py` file.

**How to make a `.txt` file yourself:**
1. In your IDE: **File → New File**.
2. Type the lines, one per line, with no extra spaces. Press Enter after the last one.
3. **File → Save As** → type the full name **with** `.txt` (e.g. `fruits.txt`) → save it in
   the same folder as your `.py` file.
4. Check it: the file should show up next to your `.py` file in the IDE's file list.

> ⚠ **Trap:** on a Mac, TextEdit saves rich text by default. Make the file in your IDE instead.
> On Windows, Notepad can quietly save `fruits.txt.txt`. Check the name in your IDE's file list.

If Python can't find it:
```
FileNotFoundError: [Errno 2] No such file or directory: 'fruit.txt'
```
Read the name in quotes. Here it says `fruit.txt` but the file is called `fruits.txt`.
A typo or the wrong folder is almost always the cause.

---

## R.1 Open → read → close *(Steps 2, 3, 5)*

```python
file = open("fruits.txt", "r")   # 1. open   ("r" = read mode, the default)
text = file.read()               # 2. read   (pulls in the WHOLE file)
file.close()                     # 3. close  (always do this when you're done)

print(text)
```
```
apple
banana
cherry

```

`open()` gives you a **file object**. Think of it as a finger pointing at the start of
the file. Reading moves the finger forward.

> ⚠ **Trap:** forget `close()` and your program usually still works, but it's bad practice
> and A2 specifically says to close the file. Make it a habit: every `open` gets a `close`.

---

## R.2 The invisible character: `\n` *(Step 3)*

Why was there an empty line at the bottom of that output? Use `repr()` to see what's
**really** in the string.

> 🔍 `repr()` is a **peeking tool for learning only**. It shows hidden characters like `\n`.
> Don't put it in your assignment.

```python
print(repr(text))
print(len(text))
```
```
'apple\nbanana\ncherry\n'
20
```

`\n` is the **newline character**. It's how a file marks "end of line". It counts as **1
character** (5 + 1 + 6 + 1 + 6 + 1 = 20). The file ends with a `\n`, and `print` adds its
own newline after that, which gives the blank line.

**Remember:** everything you read from a file is a **`str`**, and every line except maybe
the last one ends in `\n`.

---

## R.3 `.strip()` removes the junk on both ends *(Step 4)*

```python
print(repr(" banana\n".strip()))
```
```
'banana'
```

`.strip()` removes spaces, tabs and `\n` from the **start and end** of a string. It does
not touch the middle. You will use this on almost every line you read.

---

## R.4 The 4 ways to read *(Step 3)*

All four start with `file = open("fruits.txt", "r")`.

| Way | What you get | Output on `fruits.txt` |
|---|---|---|
| `file.read()` | the **whole file** as one `str` | `'apple\nbanana\ncherry\n'` |
| `file.readline()` | **one line** as a `str` (call it again for the next line) | `'apple\n'` |
| `file.readlines()` | a **list** of every line | `['apple\n', 'banana\n', 'cherry\n']` |
| `for line in file:` | each line, one per loop pass | `'apple\n'`, then `'banana\n'`, … |

### `readline()` one line at a time
```python
file = open("fruits.txt", "r")
print(repr(file.readline()))
print(repr(file.readline()))
print(repr(file.readline()))
print(repr(file.readline()))
file.close()
```
```
'apple\n'
'banana\n'
'cherry\n'
''
```
Once there are no lines left, `readline()` returns `''`, an **empty string**. It does not crash.

### `for line in file:` the one you'll use most
```python
file = open("fruits.txt", "r")
for line in file:
    print(line.strip())
file.close()
```
```
apple
banana
cherry
```

> ⚠ **Trap:** leave out `.strip()` and you get a blank line between every fruit, because
> the line's `\n` and print's newline both get printed.

### Which one should I use?
- Need **each line** to do something with? → `for line in file:` (the default choice)
- Need to **skip one line** first, like a header? → `readline()` once, then `for` (R.9)
- Need the whole thing as **one string**, e.g. to count characters? → `read()`

---

## R.5 The finger only moves forward *(Step 3)*

```python
file = open("fruits.txt", "r")
first = file.read()
second = file.read()
file.close()
print(repr(second))
```
```
''
```
The first `read()` moved the finger to the **end**, so there's nothing left for the second
one. If you need the data twice, **save it in a variable** the first time (or close and
re-open the file).

---

## R.6 Text → numbers *(Step 4)*

A file of numbers still gives you **strings**. Convert them before doing maths:

```python
print(int("72\n"), float("12.25\n"), int(" 7 "))
```
```
72 12.25 7
```
Good news: `int()` and `float()` ignore spaces and `\n` around the number, so you don't
need `.strip()` before converting.

| Conversion | Works? |
|---|---|
| `int("72")` | ✅ `72` |
| `float("72")` | ✅ `72.0` |
| `float("12.25")` | ✅ `12.25` |
| `int("12.25")` | ❌ `ValueError: invalid literal for int() with base 10: '12.25'` |
| `int("")` or `int("\n")` | ❌ `ValueError` (this happens when a file has a blank line) |

> ⚠ **Trap:** `total = total + line` without converting gives
> `TypeError: unsupported operand type(s) for +: 'int' and 'str'`.

---

## R.7 Adding up numbers from a file *(Steps 3 + 4)*

```python
file = open("marks.txt", "r")
total = 0
for line in file:
    total = total + int(line)
file.close()
print(total)
```
```
311
```
This is the same accumulator from Ch4. The only difference is that the loop goes over lines
instead of `range()`.

---

## R.8 File → list, one item per line *(Steps 3 + 4)*

```python
file = open("names.txt", "r")
names = []
for line in file:
    names.append(line.strip())
file.close()
print(names)
```
```
['Ana', 'Ben', 'Chloe']
```
Forget the `.strip()` and you get `['Ana\n', 'Ben\n', 'Chloe\n']`. Your list is now full
of hidden `\n` characters that will mess up any printing you do later.

For numbers, convert instead of strip:
```python
file = open("temps.txt", "r")
temps = []
for line in file:
    temps.append(float(line))
file.close()
print(temps)
```
```
[-3.5, 0.0, 12.25, 7.0]
```
Notice `0` became `0.0` and `7` became `7.0`. `float()` always gives a float.

> 🤔 **Think about it (A2 Q4):** the A2 report prints `3`, not `3.0`. So how could you tell,
> while reading a line, whether it should become an `int` or a `float`? Hint: what does
> `"." in "12.25"` give you, and what about `"." in "7"`? Try both. Building that into a
> function is your job.

---

## R.9 Skipping a header line *(Step 3)*

Some files start with a title line that isn't data:
```
MARKS
72
85
...
```
```python
file = open("marks_with_header.txt", "r")
header = file.readline().strip()   # eats line 1 and moves the finger to line 2
total = 0
for line in file:                  # the loop starts from where the finger is now
    total = total + int(line)
file.close()
print(header, "total:", total)
```
```
MARKS total: 311
```

---

## R.10 Two files that line up: parallel lists *(after Step 5)*

`names.txt` and `ages.txt` match **line by line**: line 1 of one file goes with line 1
of the other. Read each file into its own list, then use **one index** for both:

```python
for index in range(len(names)):
    print(names[index], "is", ages[index])
```
```
Ana is 19
Ben is 22
Chloe is 20
```

---

## 60-second self-check

1. Name the 5 steps of reading a file, **in order**.
2. In your own words: what is a **file object**? What does mode `"r"` mean?
3. What is `\n`, and why can't you see it when you open the file?
4. What type is **everything** you read from a file?
5. What's the difference between `read()`, `readline()` and `readlines()`?
6. What does `readline()` return when the file has no lines left?
7. Why do you get blank lines between items when you `print(line)`?
8. You call `read()` twice on the same open file. What does the second call give you, and why?
9. `int("4.5")` crashes. What should you use instead, and what's the name of that error?
10. Which way of reading do you use to skip a header and then loop over the rest?
11. What are **parallel lists**? How do you get the matching items from two of them?
