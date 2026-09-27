# Chapter 4 Practice: Loops & Strings

> **Rules of the gym**
> 1. Do the levels **in order**. Each one builds on the one before.
> 2. **Try first, look second.** Give every task an honest attempt before opening
>    [`chapter_04_notes.md`](chapter_04_notes.md). Getting stuck is how it sticks.
> 3. There's **no answer key**. The computer checks your work: run your code and compare
>    it with the sample run.
> 4. **Retention rep:** 3–4 days later, delete your Level 3 files and write them again
>    from a blank file.
>
> Only use what's been taught so far: `for`, `range`, strings, indexing, slicing, and
> the Ch1–3 tools. **No `if`, `while`, lists or `def` yet.**
>
> *Practice material only. Not for labs, assignments or tests.*

**Setup:** make a folder called `chapter_04/`. Each Level 3 and Level 4 task names its
file on the first line.

---

## Level 1: Predict the Output ✍️

Write your prediction **on paper first**. For loops, draw a trace table (Notes 4.3). Then
paste the code into Python and run it. If you got it wrong, find the exact line where your
trace went off track before moving on.

**1.1**
```python
for count in range(3):
    print("Go")
print("Stop")
```

**1.2**
```python
for number in range(2, 9, 3):
    print(number)
```

**1.3**
```python
for number in range(5, 0, -2):
    print(number)
```

**1.4** Look carefully at the indentation of the `print`.
```python
total = 0
for number in range(1, 5):
    total = total + number
    print(total)
```

**1.5**
```python
total = 0
for number in range(10, 0, -4):
    total = total + number
print(total)
```

**1.6**
```python
for number in range(4, 4):
    print(number)
print("finished")
```

**1.7**
```python
for letter in "hey":
    print(letter * 2)
```

**1.8**
```python
course = "COMP1000"
print(course[0], course[-1], len(course))
print(course[4:], course[:4].lower())
```

**1.9** This pattern shows up a lot on LeetCode.
```python
result = ""
for letter in "abc":
    result = letter + result
print(result)
```

---

## Level 2: Fix the Bug 🐞

Each program has **one** bug. Run it, read the error or the wrong output, and fix it.
Then write one sentence on paper saying *what kind* of error it was (syntax, runtime or
logic).

**2.1** *Goal: print 1 to 5.*
```python
for number in range(1, 5):
    print(number)
```

**2.2** *Goal: print "hi" three times.*
```python
for count in range(3):
print("hi")
```

**2.3** *Goal: add up 1 to 5 and print `Total: 15`.*
```python
for number in range(1, 6):
    total = 0
    total = total + number
print("Total:", total)
```

**2.4** *Goal: repeat a message as many times as the user asks.*
```python
times = input("How many times? ")
for count in range(times):
    print("Practice!")
```

**2.5** *Goal: print the last letter of any word.*
```python
word = input("Word: ")
print("Last letter:", word[len(word)])
```

**2.6** *Goal: print the name in capitals. This one doesn't crash, so look closely.*
```python
name = input("Name: ")
name.upper()
print("HELLO", name)
```

---

## Level 3: Write It 🛠

Paste the stub, replace the `TODO`s with code, and run it. Your output should match the
sample run **exactly**, spaces included.

**3.1 Times table**
```python
# filename: chapter_04/l3_01_times_table.py
# TODO 1: ask for a number, as an int
# TODO 2: loop from 1 to 10 and print one line of the table each pass

# sample run:
#   Which times table? 7
#   7 x 1 = 7
#   7 x 2 = 14
#   ...
#   7 x 10 = 70
```

**3.2 Sum from 1 to n**
```python
# filename: chapter_04/l3_02_sum_to_n.py
# TODO 1: ask for the limit
# TODO 2: set up an accumulator BEFORE the loop
# TODO 3: loop and add; make sure the limit itself is included

# sample run:
#   Add up 1 to: 10
#   The sum of 1 to 10 is 55
```

**3.3 Countdown**
```python
# filename: chapter_04/l3_03_countdown.py
# TODO: ask where to start, count down to 1 with a negative step, then print Liftoff!

# sample run:
#   Count down from: 5
#   5
#   4
#   3
#   2
#   1
#   Liftoff!
```

**3.4 Even numbers**
```python
# filename: chapter_04/l3_04_evens.py
# TODO: print every even number from 0 up to AND including the limit.
#       No if-statement: let the range step do the work.

# sample run:
#   Up to: 10
#   0
#   2
#   4
#   6
#   8
#   10
```

**3.5 Letter by position**
```python
# filename: chapter_04/l3_05_positions.py
# TODO: print each index and the letter at that index. Loop by index (Notes 4.6).

# sample run:
#   Word: loop
#   0 l
#   1 o
#   2 o
#   3 p
```

**3.6 Letter counter**
```python
# filename: chapter_04/l3_06_letter_count.py
# TODO: ask for a word and a letter, then print how many times the letter appears

# sample run:
#   Word: banana
#   Letter to count: a
#   a appears 3 times in banana
```

**3.7 Slice it**
```python
# filename: chapter_04/l3_07_slices.py
# TODO: print the first 3 letters, the last 3 letters, and the word backwards

# sample run:
#   Word: computer
#   First 3: com
#   Last 3: ter
#   Backwards: retupmoc
```

**3.8 Average of five**
```python
# filename: chapter_04/l3_08_average.py
# TODO 1: loop 5 times; each pass, ask for a number (float) and add it to a total
# TODO 2: after the loop, print the average

# sample run:
#   Number: 4
#   Number: 8
#   Number: 15
#   Number: 16
#   Number: 23
#   Average: 13.2
```

---

## Level 4: LeetCode Warm-Ups 🚀

These are simplified versions of real LeetCode problems, cut down to what you know so
far. When you learn lists (Ch 9) and conditionals (Ch 6), come back and try the full
versions.

**4.1 Reverse a string** (LeetCode #344, *Reverse String*)
```python
# filename: chapter_04/l4_01_reverse.py
# TODO: reverse the word using a LOOP and string building. No [::-1] allowed.
#       When it works, check your answer against word[::-1].

# sample run:
#   Word: stressed
#   desserts
```

**4.2 Digit maths** (LeetCode #1281, *Subtract the Product and Sum of Digits*)
```python
# filename: chapter_04/l4_02_digits.py
# TODO: for a 3-digit number, find the product and the sum of its digits.
# Hint: number % 10 gives the last digit, and number // 10 removes it.
#       Loop 3 times.

# sample run:
#   3-digit number: 234
#   Product: 24
#   Sum: 9
#   Product - Sum: 15
```

**4.3 Star triangle**
```python
# filename: chapter_04/l4_03_triangle.py
# TODO: row 1 has 1 star, row 2 has 2 stars, and so on. One loop, plus string *.

# sample run:
#   Rows: 4
#   *
#   **
#   ***
#   ****
```

**4.4 Running total** (LeetCode #1480, *Running Sum of 1d Array*)
```python
# filename: chapter_04/l4_04_running_total.py
# TODO: ask for step counts for 4 days and print the running total after each day.
# Hint: to put the day number in the prompt, you'll need str().

# sample run:
#   Steps on day 1: 3000
#   Total so far: 3000
#   Steps on day 2: 4500
#   Total so far: 7500
#   Steps on day 3: 2500
#   Total so far: 10000
#   Steps on day 4: 6000
#   Total so far: 16000
```

**4.5 Every other letter**
```python
# filename: chapter_04/l4_05_every_other.py
# TODO: build a new string from the letters at index 0, 2, 4, ...
#       Use a loop with range and a step. No slicing allowed.

# sample run:
#   Word: programming
#   pormig
```

**Bonus:** once 4.5 works, do it again in **one line** with slicing. Then write two sentences on
paper comparing the two versions.

---

✅ **Finished every level?** Go back to the Self-Check at the bottom of the notes. If
every box is ticked, you're ready for Quiz 3.
