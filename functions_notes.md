# Functions: Notes (Ch5 + Ch8)

> **How to use these notes:** learn the **Key Words** and the **5 Steps** first. Then read one
> lesson and do the matching tasks in [`functions_practice.md`](functions_practice.md). Every
> output shown here is real: the code was run.
>
> *Practice material only. Don't use AI tools or these notes on labs, assignments, or
> tests (course rules). The examples are deliberately different from A2.*

---

## Key Words (learn these first)

| Word | What it means | Tiny example |
|---|---|---|
| **function** | A named block of code that does one job. You write it once and use it as many times as you like. | `square` |
| **define** | Create the function with `def`. Defining it does **not** run it. | `def square(number):` |
| **function name** | What you call it. Use a verb that says what it does. | `square`, `find_total` |
| **parameter** | A variable in the `def` line that **receives** a value. | `number` in `def square(number):` |
| **argument** | The actual value you **send** when you call the function. | `7` in `square(7)` |
| **body** | The indented lines under `def`. This is the code that runs. | `return number * number` |
| **call** | Run the function: its name plus `()`. | `square(7)` |
| **return** | Sends a value **back** to whoever called the function, and ends the function. | `return number * number` |
| **return value** | The value that comes back. You can store it or print it. | `answer = square(7)` → `49` |
| **`None`** | What a function gives back if it has no `return`. It means "nothing". | `print(say_hello())` → `None` |
| **local variable** | A variable made **inside** a function. It doesn't exist outside it. | `tax` inside `make_total` |
| **docstring** | A `"""triple-quoted"""` description on the first line inside a function. | see F.7 |
| **precondition** | What must be true **before** the function is called. | "count is greater than 0" |
| **postcondition** | What is true **after** the function finishes. | "returns a positive number" |
| **`main()`** | The function that runs the whole program by calling the other functions. | `main()` at the bottom |

---

## The Big Picture: 5 Steps to Write a Function

1. **Plan it.** What's the job? What goes **in** (parameters)? What comes **out** (return)?
2. **Write the `def` line.** `def name(parameter1, parameter2):` Don't forget the `:`.
3. **Write the docstring.** One sentence on what it does, plus types and conditions.
4. **Write the body.** Indent it. Use the **parameters**, not `input()` or made-up values.
5. **Return, then call it to test.** `return` the answer, then call the function and print the result.

```python
# STEP 1: job = square a number. In: one number. Out: the number times itself.
def square(number):                     # STEP 2: the def line
    """Return number multiplied by itself."""   # STEP 3: the docstring
    result = number * number            # STEP 4: the body (indented)
    return result                       # STEP 5a: send the answer back


print(square(7))                        # STEP 5b: call it and test
```
```
49
```

**Say each step out loud:** "What's the job, and what goes in and out?" → "def, name,
brackets, colon." → "Describe it." → "Indent and do the work." → "Return it, then test it."

---

## F.1 Defining does nothing until you call it *(Step 2)*

```python
def say_hello():
    print("Hello!")


print("Start")
say_hello()
say_hello()
print("End")
```
```
Start
Hello!
Hello!
End
```
Python reads the `def` and remembers it, but runs nothing. The body only runs when the
function is **called**, and it runs again every time it's called.

> ⚠ **Trap:** `say_hello` without `()` doesn't call it. `print(say_hello)` prints
> something like `<function say_hello at 0x...>`.

---

## F.2 Parameters and arguments line up in order *(Steps 1–2)*

```python
def greet(name, age):
    print(name, "is", age)


greet("Ana", 19)
greet(19, "Ana")
```
```
Ana is 19
19 is Ana
```
The **first** argument goes into the **first** parameter, the second into the second. Swap
them and Python won't complain. It just gives you the wrong answer (a **logic error**).

Send the wrong **number** of arguments and it crashes:
```
TypeError: square() missing 1 required positional argument: 'number'
```

---

## F.3 `print` vs `return`: the #1 confusion *(Step 5)*

```python
def add_print(first, second):
    print(first + second)


def add_return(first, second):
    return first + second


result1 = add_print(2, 3)
result2 = add_return(2, 3)
print(result1)
print(result2)
print(add_return(2, 3) * 10)
```
```
5
None
5
50
```
- `print` **shows** a value on the screen. The program can't use it afterwards.
- `return` **hands the value back**, so you can store it, print it or do maths with it.
- `add_print` has no `return`, so `result1` is `None`.

> ⚠ **Trap:** `add_print(2, 3) + 1` crashes:
> `TypeError: unsupported operand type(s) for +: 'NoneType' and 'int'`.
> If the instructions say a function **returns** something, use `return`.

---

## F.4 `return` ends the function right away *(Step 5)*

```python
def double(number):
    return number * 2
    print("This never prints")


print(double(5))
```
```
10
```
Any lines after a `return` that runs are skipped.

---

## F.5 Local variables stay inside *(Step 4)*

```python
def make_total(price):
    tax = price * 0.05
    return price + tax


print(make_total(100))
print(tax)
```
```
105.0
NameError: name 'tax' is not defined
```
`tax` only exists **while** `make_total` is running. To use a value outside the function,
**return** it and store it: `total = make_total(100)`.

---

## F.6 Functions calling functions, and `main()` *(Step 5)*

```python
def area(width, height):
    return width * height


def describe_room(width, height):
    room_area = area(width, height)
    print("The room is", room_area, "square metres")


def main():
    describe_room(3, 4)
    describe_room(5, 2)


main()
```
```
The room is 12 square metres
The room is 10 square metres
```
**Follow the arrows:** `main` calls `describe_room`, `describe_room` calls `area`, `area`
returns 12, then `describe_room` prints, then control goes back to `main`. The program only
starts at the last line, `main()`.

---

## F.7 Docstrings *(Step 3)*

A docstring goes on the **first line inside** the function, in triple quotes. It should say:
1. **One-line summary** of what the function does
2. Each **parameter** and its **type**
3. What it **returns** and the **type**
4. Any **preconditions** (what must be true before) and **postconditions** (what's true after)

```python
def average(total, count):
    """Return the average of a total split over a number of items.

    Parameters:
        total (float): the sum of all the values
        count (int): how many values were added up
    Returns:
        float: total divided by count
    Precondition: count is greater than 0
    Postcondition: nothing outside the function is changed
    """
    return total / count
```
Why the precondition? If `count` is `0`, you get `ZeroDivisionError`. The precondition
warns the caller not to do that.

> Follow the **exact docstring layout your instructor shows** (A2 gives one in `dieRoll`).
> This is just one common layout.

---

## F.8 Tracing a call ✍️

```python
def double(number):
    answer = number * 2
    return answer


def add_one(number):
    return number + 1


value = add_one(double(3))
print(value)
```
```
7
```
Work from the **inside out**: `double(3)` runs first and returns `6`. Then `add_one(6)`
returns `7`. Write it on paper like this: `add_one(double(3))` → `add_one(6)` → `7`.

---

## 60-second self-check

1. Name the 5 steps of writing a function, **in order**.
2. What's the difference between a **parameter** and an **argument**?
3. Does `def` run the code inside? When does the code run?
4. What does a function with no `return` give back?
5. Why does `print(tax)` crash after `make_total` has run?
6. `greet(19, "Ana")` doesn't crash. What kind of error is it?
7. What 4 things go in a docstring?
8. What's the difference between `print` and `return`, in one sentence?
