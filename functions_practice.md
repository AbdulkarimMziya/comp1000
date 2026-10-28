# Functions: Practice

> **Rules of the gym**
> 1. **Start at Level 0** (on paper). Then do the levels **in order**.
> 2. **Try first, look second.** Only open [`functions_notes.md`](functions_notes.md) after
>    an honest attempt.
> 3. There's **no answer key**. Run your code and compare it with the sample run.
> 4. **Retention rep:** 3–4 days later, delete your Level 3 files and write them again.
>
> Only use Ch1–8 tools: `def`, parameters, `return`, `if` / `elif` / `else`, `for`, strings,
> maths. **No lists yet** (that's Ch9).
>
> *Practice material only. Not for labs, assignments or tests.*

**Setup:** make a folder called `functions/`. Every code block starts with a
`# filename:` line. Make a new file with that name, paste the whole block in, and run it.

---

## Level 0: Words & Steps ✍️ (paper only)

**0.1 Match each word to its meaning.**

| Word | | Meaning |
|---|---|---|
| 1. parameter | | A. Runs the function |
| 2. argument | | B. Sends a value back and ends the function |
| 3. call | | C. A variable in the `def` line that receives a value |
| 4. return | | D. What you get back when there's no `return` |
| 5. `None` | | E. The real value you send in |
| 6. docstring | | F. A variable that only exists inside the function |
| 7. local variable | | G. The triple-quoted description inside a function |

**0.2 Put the 5 steps in order:** Write the body · Plan it (in / out) · Return, then call
it to test · Write the `def` line · Write the docstring

**0.3 Label the parts.** Copy this and label: the keyword, the function name, the
parameters, the body, the return value.
```python
def rectangle_area(width, height):
    area = width * height
    return area
```
Then: in the call `rectangle_area(4, 5)`, what are the **arguments**? Which parameter gets `5`?

**0.4 True or false?** If it's false, write the true version.
1. Writing `def` runs the function straight away.
2. A function can be called more than once.
3. A variable made inside a function can be printed outside it.
4. Code after `return` still runs.
5. `print` and `return` do the same thing.
6. A precondition is something that must be true before the function is called.

**0.5 `print` or `return`?** Which should the function use?
1. "The function **returns** the total price."
2. "The function **displays** a welcome message."
3. Another function needs to use the answer in a calculation.

---

## Level 1: Predict the Output ✍️

Write your prediction on paper, **then** paste it in and run it.

**1.1**
```python
# filename: functions/p1.py
def cheer():
    print("Go team!")


print("Before")
cheer()
print("After")
cheer()
```

**1.2** Careful: is the function ever called?
```python
# filename: functions/p2.py
def warning():
    print("Danger!")


print("All good")
```

**1.3**
```python
# filename: functions/p3.py
def show_sum(first, second):
    print(first + second)


answer = show_sum(4, 6)
print(answer)
```

**1.4**
```python
# filename: functions/p4.py
def give_sum(first, second):
    return first + second


answer = give_sum(4, 6)
print(answer)
print(give_sum(1, 1) * give_sum(2, 3))
```

**1.5**
```python
# filename: functions/p5.py
def describe(animal, sound):
    print("The", animal, "says", sound)


describe("cow", "moo")
describe("moo", "cow")
```

**1.6**
```python
# filename: functions/p6.py
def check_age(age):
    if age >= 18:
        return "adult"
    return "minor"
    print("done checking")


print(check_age(20))
print(check_age(12))
```

**1.7** Trace it inside out.
```python
# filename: functions/p7.py
def add_two(number):
    return number + 2


def times_three(number):
    return number * 3


print(times_three(add_two(4)))
print(add_two(times_three(4)))
```

**1.8**
```python
# filename: functions/p8.py
def half(number):
    result = number / 2
    return result


def main():
    value = half(10)
    print("Half is", value)
    print("Half of that is", half(value))


main()
```

---

## Level 2: Fix the Bug 🔧

Predict what goes wrong, run it, then fix it with the smallest change you can.

**2.1** Syntax error.
```python
# filename: functions/bug1.py
def square(number)
    return number * number


print(square(7))
```
Fixed output: `49`

**2.2** Prints something weird instead of `Hi!`.
```python
# filename: functions/bug2.py
def say_hi():
    print("Hi!")


print(say_hi)
```

**2.3** Crashes with a `TypeError` about `NoneType`.
```python
# filename: functions/bug3.py
def triple(number):
    print(number * 3)


print(triple(2) + 1)
```
Fixed output: `7`

**2.4** Crashes with a `NameError`.
```python
# filename: functions/bug4.py
def make_total(price):
    total = price + price * 0.05
    return total


make_total(100)
print(total)
```
Fixed output: `105.0` (keep `print(total)` and fix the line above it)

**2.5** Crashes: `missing 1 required positional argument`.
```python
# filename: functions/bug5.py
def rectangle_area(width, height):
    return width * height


print(rectangle_area(4))
```
Fixed output: `20`

**2.6** It runs, but the answer is wrong. It should be `"Ana Lopez"`.
```python
# filename: functions/bug6.py
def full_name(first, last):
    return first + " " + last


print(full_name("Lopez", "Ana"))
```

**2.7** Should print `A` for 85, but prints `D`.
```python
# filename: functions/bug7.py
def letter_grade(mark):
    if mark >= 50:
        return "D"
    elif mark >= 80:
        return "A"
    else:
        return "F"


print(letter_grade(85))
print(letter_grade(31))
```
Fixed output: `A` then `F`. (Hint: Python checks from the top and stops at the first `True`.)

---

## Level 3: Write It ✏️

Paste each stub into its own file, fill in the `# TODO`s, then run it. Match the sample run
**exactly**. Each function must **return** its answer, not print it.

**3.1**
```python
# filename: functions/w1_square.py
def square(number):
    # TODO 1: write a docstring
    # TODO 2: return number times itself
    pass


print(square(7))
print(square(-3))
```
```
# sample run
49
9
```

**3.2**
```python
# filename: functions/w2_is_even.py
def is_even(number):
    # TODO 1: docstring
    # TODO 2: return True if number divides by 2 with no remainder (hint: %)
    pass


print(is_even(4))
print(is_even(7))
```
```
# sample run
True
False
```

**3.3**
```python
# filename: functions/w3_full_name.py
def full_name(first, last):
    # TODO: return first and last joined with ONE space between
    pass


print(full_name("Ana", "Lopez"))
```
```
# sample run
Ana Lopez
```

**3.4** Celsius to Fahrenheit: `F = C × 9 / 5 + 32`
```python
# filename: functions/w4_c_to_f.py
def c_to_f(celsius):
    # TODO 1: docstring (parameter type, return type)
    # TODO 2: return the Fahrenheit value
    pass


print(c_to_f(100))
print(c_to_f(-40))
```
```
# sample run
212.0
-40.0
```

**3.5** 80+ = A, 70–79 = B, 60–69 = C, 50–59 = D, below 50 = F
```python
# filename: functions/w5_letter_grade.py
def letter_grade(mark):
    # TODO 1: docstring with a precondition (what range must mark be in?)
    # TODO 2: if / elif / else, return the letter. Think about the ORDER (see bug 2.7)
    pass


print(letter_grade(85), letter_grade(72), letter_grade(64), letter_grade(50), letter_grade(31))
```
```
# sample run
A B C D F
```

**3.6** Two functions plus `main()`.
```python
# filename: functions/w6_bill.py
def add_tip(subtotal, tip_percent):
    # TODO: return subtotal plus tip_percent percent of the subtotal
    pass


def main():
    # TODO 1: call add_tip(40, 15) and store it in a variable
    # TODO 2: print "Total with tip:" and that variable
    # TODO 3: call add_tip(20, 0) and print it the same way
    pass


main()
```
```
# sample run
Total with tip: 46.0
Total with tip: 20.0
```

**3.7 Docstring practice ✍️.** Go back to 3.4, 3.5 and 3.6. Check each docstring has all
4 parts (summary, parameter types, return type, pre/postconditions). Fix any that don't.

---

## Level 4: Boss Round 🧠 (no stub)

**4.1** Write `count_vowels(word)` that **returns** how many vowels (`a e i o u`) are in a
word. (Ch4 string loop + `if`.) `count_vowels("banana")` → `3`, `count_vowels("sky")` → `0`.

**4.2** Write `main()` that asks the user for a word with `input()`, calls `count_vowels`,
and prints `banana has 3 vowels`.
