# Reading Files: Practice

> **Rules of the gym**
> 1. Do the levels **in order**. Each one builds on the one before.
> 2. **Start at Level 0** (words and steps on paper) even if it feels easy.
> 3. **Try first, look second.** Give every task an honest attempt before opening
>    [`reading_files_notes.md`](reading_files_notes.md).
> 4. There's **no answer key**. The computer checks your work: run your code and compare
>    it with the sample run.
> 5. **Retention rep:** 3–4 days later, delete your Level 3 files and write them again
>    from a blank file.
>
> Only use Ch1–6 tools plus what's in the notes: `open`, `read`, `readline`, `readlines`,
> `for line in file`, `.strip()`, `int()`/`float()`, lists with `.append()`, `close()`.
>
> *Practice material only. Not for labs, assignments or tests.*

**Setup:** make a folder called `reading_files/`. Save **every** `.py` file **and every
`.txt` file** in that one folder, so `open()` can find them.

**You make the `.txt` files yourself.** Whenever a question needs a new one, there's a
📄 **Make this file first** box right above it. Do the box, then the question. Once you've
made a file, later questions just reuse it.

> ⚠ **Making `.txt` files: 3 rules**
> 1. Make them **in your IDE** (VS Code, Thonny, IDLE, PyCharm: File → New File). On a Mac,
>    don't use TextEdit, because it saves rich text, not plain text.
> 2. The name must end in **`.txt`** and be spelled **exactly** as shown, lower case included.
>    `Names.txt` and `names.txt.txt` won't work.
> 3. Type **only** the lines shown: no spaces before or after, and no extra blank lines (unless
>    the box asks for one).

**Step 0 (do this first):** make your first file, then a 3-line program that reads it. If
you get `FileNotFoundError`, check the name and folder before going any further.

📄 **Make this file first: `fruits.txt`**
1. In your IDE: **File → New File**.
2. Type these lines exactly, one per line. Press **Enter** after the last line too.
```
apple
banana
cherry
```
3. **File → Save As** → type the name `fruits.txt` → save it in your `reading_files` folder.

Now make `step0.py` in the same folder, paste this in and run it. You should see the 3 fruits.
```python
# filename: reading_files/step0.py
file = open("fruits.txt", "r")
print(file.read())
file.close()
```

---

## Level 0: Words & Steps ✍️ (paper only, no computer)

Do this before you write any code. Check your answers against the **Key Words** and
**5 Steps** sections at the top of the notes. If you get any wrong, read that row again.

**0.1 Match each word to its meaning.** Write the pairs, e.g. `1-C`.

| Word | | Meaning |
|---|---|---|
| 1. `open()` | | A. Removes spaces and `\n` from both ends of a string |
| 2. `\n` | | B. Reads the next single line |
| 3. `.strip()` | | C. Connects your program to a file |
| 4. `close()` | | D. Reads the whole file into one string |
| 5. `read()` | | E. The hidden character at the end of each line |
| 6. `readline()` | | F. Disconnects from the file when you're done |
| 7. `readlines()` | | G. Adds one value to the end of a list |
| 8. `.append()` | | H. Reads every line into a list |

**0.2 Put the 5 steps in the right order.**
- Clean it up (`.strip()` or `int()` / `float()`)
- Close it
- Put the `.txt` in the same folder as the `.py`
- Read it
- Open it

**0.3 Fill in the blanks.** This program adds up the numbers in `marks.txt`. Write what goes
in each numbered blank.
```python
file = _____[1]_____("marks.txt", _____[2]_____)
total = 0
for line in file:
    total = total + _____[3]_____(line)
file._____[4]_____()
print(total)
```
Then: why don't you need `.strip()` in blank `[3]`? (Notes R.6)

**0.4 True or false?** If it's false, write the true version.
1. Numbers in a file are read in as `int`.
2. `readline()` crashes when there are no lines left.
3. `"apple\n"` has 6 characters.
4. If your program doesn't call `close()`, it can't read the file at all.
5. `.strip()` removes spaces from the middle of a string.
6. After `read()`, a second `read()` on the same open file gives `''`.

**0.5 Which way to read?** Choose `read()`, `readline()`, `readlines()` or `for line in file:`.
1. You want to print every line of a file, one at a time.
2. The first line is a title. You want to grab it, then handle the rest separately.
3. You want to know how many characters are in the whole file.

**0.6 Name that error.** Choose `FileNotFoundError`, `ValueError` or `TypeError`.
1. `open("Fruits.txt")` when the file is really called `fruits.txt`
2. `int("6.5")`
3. `total = 0 + line`, where `line` came straight from the file
4. `int(line)` when `line` is a blank line

---

## Level 1: Predict the Output ✍️

Write your prediction **on paper first**, then run it. Use `repr()` in your head: where are
the `\n`s? If you got it wrong, work out **which** `\n` you forgot about.

**1.1** What type is it, and how long? *(uses `fruits.txt`)*
```python
# filename: reading_files/p1.py
file = open("fruits.txt", "r")
text = file.read()
file.close()
print(type(text))
print(len(text))
```

**1.2** *(uses `fruits.txt`)*
```python
# filename: reading_files/p2.py
file = open("fruits.txt", "r")
print(repr(file.readline()))
print(repr(file.readline()))
file.close()
```

**1.3** Two different reads on the same file. Where does the second one start?
```python
# filename: reading_files/p3.py
file = open("fruits.txt", "r")
print(file.readline().strip())
rest = file.read()
file.close()
print(repr(rest))
```

**1.4**
```python
# filename: reading_files/p4.py
file = open("fruits.txt", "r")
lines = file.readlines()
file.close()
print(len(lines))
print(lines[1].strip())
print(lines[0])
```

📄 **Make this file first: `names.txt`**
1. In your IDE: **File → New File**.
2. Type these lines exactly, one per line. Press **Enter** after the last line too.
```
Ana
Ben
Chloe
```
3. **File → Save As** → type the name `names.txt` → save it in your `reading_files` folder.

**1.5** How many lines get printed, counting the blank ones?
```python
# filename: reading_files/p5.py
file = open("names.txt", "r")
for line in file:
    print("Hello " + line + "!")
file.close()
```

📄 **Make this file first: `marks.txt`**
1. In your IDE: **File → New File**.
2. Type these lines exactly, one per line. Press **Enter** after the last line too.
```
72
85
90
64
```
3. **File → Save As** → type the name `marks.txt` → save it in your `reading_files` folder.

**1.6** Two lines of code, two very different answers.
```python
# filename: reading_files/p6.py
file = open("marks.txt", "r")
first = file.readline()
file.close()
print(first + first)
print(int(first) + int(first))
```

**1.7** Is the second print empty, or does it show the file again?
```python
# filename: reading_files/p7.py
file = open("fruits.txt", "r")
print(file.read())
print(file.read())
file.close()
```

📄 **Make this file first: `temps.txt`**
1. In your IDE: **File → New File**.
2. Type these lines exactly, one per line. Press **Enter** after the last line too.
```
-3.5
0
12.25
7
```
3. **File → Save As** → type the name `temps.txt` → save it in your `reading_files` folder.

**1.8**
```python
# filename: reading_files/p8.py
file = open("temps.txt", "r")
temps = []
for line in file:
    temps.append(float(line))
file.close()
print(temps[1], temps[3])
```

---

## Level 2: Fix the Bug 🔧

Each one crashes or prints the wrong thing. **First** predict what goes wrong, **then** run
it, **then** fix it with the smallest change you can.

**2.1** Crashes. Read the last line of the error first. *(Don't make a new file. The bug is in the code.)*
```python
# filename: reading_files/bug1.py
file = open("fruit.txt", "r")
print(file.read())
file.close()
```

**2.2** Crashes with a `TypeError`.
```python
# filename: reading_files/bug2.py
file = open("marks.txt", "r")
total = 0
for line in file:
    total = total + line
file.close()
print(total)
```

**2.3** Supposed to print `Hello Ana!` on one line, but the `!` lands on the next line.
```python
# filename: reading_files/bug3.py
file = open("names.txt", "r")
for line in file:
    print("Hello " + line + "!")
file.close()
```

**2.4** Crashes with a `ValueError`. Look at the value in the error message.
```python
# filename: reading_files/bug4.py
file = open("temps.txt", "r")
total = 0
for line in file:
    total = total + int(line)
file.close()
print(total)
```

**2.5** Should print the number of lines (3) and then every fruit, but nothing comes out
after the 3. Fix it **without** opening the file twice.
```python
# filename: reading_files/bug5.py
file = open("fruits.txt", "r")
print(len(file.readlines()))
for line in file:
    print(line.strip())
file.close()
```

📄 **Make this file first: `marks_blank.txt`**
1. In your IDE: **File → New File**.
2. Type these lines exactly, one per line. Press **Enter** after the last line too. This file is **meant** to have a blank 3rd line: type `72`, Enter, `85`, Enter, then press **Enter one more time**.
```
72
85

```
3. **File → Save As** → type the name `marks_blank.txt` → save it in your `reading_files` folder.

**2.6** Crashes on the last line of the file. Why? Open `marks_blank.txt` in your editor
and look. Fix the **code** so it skips blank lines (you have `if` from Ch6), and leave the
file alone.
```python
# filename: reading_files/bug6.py
file = open("marks_blank.txt", "r")
total = 0
for line in file:
    total = total + int(line)
file.close()
print(total)
```
Fixed output: `157`

**2.7** This runs fine, so what's wrong with it? (Hint: one line is missing.)
```python
# filename: reading_files/bug7.py
file = open("names.txt", "r")
names = []
for line in file:
    names.append(line.strip())
print(names)
```

---

## Level 3: Write It ✏️

Each task builds on the one before. Match the sample run **exactly**.

**3.1 Number the lines.** Print every line of `fruits.txt` with its line number.
```python
# filename: reading_files/w1_numbered.py
# TODO 1: open fruits.txt
# TODO 2: make a counter that starts at 1
# TODO 3: loop over the lines, print "counter: line" (strip the line!), add 1 to counter
# TODO 4: close the file
```
```
# sample run
1: apple
2: banana
3: cherry
```

**3.2 Count the lines.** Print how many lines `fruits.txt` has. Do it **twice**: once with
`readlines()` and once with a `for` loop and a counter. Both must print the same number.
```python
# filename: reading_files/w2_count.py
```
```
# sample run
3
3
```

**3.3 Average.** Read `marks.txt` and print the average. You'll need a total **and** a count.
```python
# filename: reading_files/w3_average.py
```
```
# sample run
Average: 77.75
```

**3.4 Longest name.** Read `names.txt` and print the longest name. (`if` + `len()`.
Remember to strip **before** measuring, because `\n` counts as a character.)
```python
# filename: reading_files/w4_longest.py
```
```
# sample run
Longest name: Chloe
```

**3.5 File → list function.** Write a function `read_temps(filename)` that opens the file,
turns each line into a `float`, adds it to a list, **closes the file**, and **returns** the
list. Then call it, print the list, and find the highest temperature **with a loop and an
`if`**. Start `highest` at the first item, `temps[0]`.
```python
# filename: reading_files/w5_read_temps.py
def read_temps(filename):
    # TODO 1: open the file using the parameter (no quotes around filename!)
    # TODO 2: make an empty list
    # TODO 3: loop, convert each line to float, append
    # TODO 4: close the file
    # TODO 5: return the list
    pass


temps = read_temps("temps.txt")
print(temps)
# TODO 6: highest = temps[0], then loop over temps and keep the bigger value
# TODO 7: print "Highest:" and highest
```
```
# sample run
[-3.5, 0.0, 12.25, 7.0]
Highest: 12.25
```

📄 **Make this file first: `marks_with_header.txt`**
1. In your IDE: **File → New File**.
2. Type these lines exactly, one per line. Press **Enter** after the last line too.
```
MARKS
72
85
90
64
```
3. **File → Save As** → type the name `marks_with_header.txt` → save it in your `reading_files` folder.

**3.6 Skip the header.** Read `marks_with_header.txt`. Use `readline()` to grab the header,
then add up the rest.
```python
# filename: reading_files/w6_header.py
```
```
# sample run
MARKS total: 311
```

📄 **Make this file first: `ages.txt`**
1. In your IDE: **File → New File**.
2. Type these lines exactly, one per line. Press **Enter** after the last line too. The ages line up with `names.txt`: Ana is 19, Ben is 22, Chloe is 20.
```
19
22
20
```
3. **File → Save As** → type the name `ages.txt` → save it in your `reading_files` folder.

**3.7 Two files, one index.** Read `names.txt` into a list of names and `ages.txt` into a
list of `int`s. Find the oldest person **by index**, so you can use that same index to get
their name.
```python
# filename: reading_files/w7_oldest.py
```
```
# sample run
Ben is the oldest at 22
```

---

## Level 4: Boss Round 🧠 (no stub, no hints)

**4.1** Write **one** function `read_any(filename)` that works on `names.txt`, `ages.txt`
**and** `temps.txt`. Names stay as stripped strings, whole numbers become `int`, and decimal
numbers become `float`. Test it on all three files.

> This is the closest you'll get to A2 Q4 here, and that's on purpose. Get it working on
> these files and you understand the idea. Then go write the assignment version
> **yourself**, from a blank file.

**4.2** Then think on paper ✍️: your function gets `"-3.5"`. Does your int/float check still
work for negative numbers? What about `"0"`?

**4.3 Make your own test file.** Make `mixed.txt` with 5 lines of your own: some whole numbers
and some decimals. Predict on paper what `read_any("mixed.txt")` should return, then run it.
A test file **you** made is the best way to check that your code works on ANY file, not
just the ones on this sheet.
